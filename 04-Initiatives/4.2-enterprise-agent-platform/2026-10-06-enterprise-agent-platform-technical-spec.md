# Technical Specification: Extensible Enterprise Agent Platform

**Date:** 2026-10-06  
**Audience:** Engineering leaders, platform engineers, AI infrastructure teams, security architects  
**Status:** Non-proprietary reference technical specification  
**Companion document:** `2026-10-06-enterprise-agent-platform-prd.md`  
**Disclosure note:** This document intentionally avoids proprietary source code, internal prompts, private schemas, credentials, customer data, and company-specific implementation details. It describes a reusable architecture pattern for building a similar agent platform in any industry.

---

## 1. Purpose

This technical specification describes a reference architecture for an extensible enterprise AI agent platform. The system enables a language model to perform governed, tool-assisted work across local projects and enterprise systems while preserving safety, auditability, and extensibility.

This document is intended to help engineering teams design and build a similar platform from first principles.

---

## 2. System Goals

The platform must:

1. Provide an interactive agent workbench.
2. Support model-callable tools with typed schemas.
3. Support reusable skills loaded on demand.
4. Support extensions/plugins for custom runtime behavior.
5. Support enterprise integrations through typed adapters or MCP-style connectors.
6. Persist sessions with tool-call history and branchability.
7. Enforce safety controls at runtime, not only through prompts.
8. Support multiple model providers.
9. Provide programmatic APIs for embedding or automation.
10. Keep proprietary domain logic outside the core runtime.

---

## 3. Reference Architecture

```text
+---------------------------------------------------------------+
|                           User                                |
+------------------------------+--------------------------------+
                               |
                               v
+---------------------------------------------------------------+
|                    Interface Layer                            |
|  - Terminal UI                                                 |
|  - Web UI optional                                             |
|  - Print / JSON / RPC modes                                    |
|  - SDK embedding                                               |
+------------------------------+--------------------------------+
                               |
                               v
+---------------------------------------------------------------+
|                    Agent Session Runtime                      |
|  - Session state                                               |
|  - Model selection                                             |
|  - Agent loop                                                  |
|  - Tool registry                                               |
|  - Skill registry                                              |
|  - Extension runtime                                           |
|  - Context builder                                             |
|  - Compaction                                                  |
|  - Event bus                                                   |
+------------------+-----------+-----------+--------------------+
                   |           |           |
                   v           v           v
+---------------------+ +----------------+ +---------------------+
| Tool Execution      | | Skills Layer   | | Extensions Layer    |
| - Built-in tools    | | - Workflows    | | - Tools             |
| - Custom tools      | | - Procedures   | | - Commands          |
| - Permission gates  | | - References   | | - UI hooks          |
| - Result handling   | | - Scripts      | | - Policy hooks      |
+----------+----------+ +----------------+ +----------+----------+
           |                                           |
           v                                           v
+---------------------------------------------------------------+
|                    Integration Layer                          |
|  - Source control                                              |
|  - Issue tracker                                               |
|  - Docs/wiki                                                   |
|  - Messaging                                                   |
|  - Data warehouse                                              |
|  - Internal APIs                                               |
|  - Model providers                                             |
|  - MCP servers or equivalent tool gateways                     |
+---------------------------------------------------------------+
```

---

## 4. Major Runtime Components

## 4.1 Interface Layer

The interface layer presents the agent to users and external systems.

### Supported modes

| Mode | Use Case |
|---|---|
| Interactive UI | Human-in-the-loop workbench |
| Print mode | One-shot shell automation |
| JSON event mode | Machine-readable event streams |
| RPC mode | Integration from other processes/languages |
| SDK | Embedding inside custom applications |

### Responsibilities

- Capture user input
- Display assistant output
- Display tool calls and results
- Allow interruption or steering
- Render structured questions
- Render custom extension UI
- Show session metadata
- Show current model/provider state

---

## 4.2 Agent Session Runtime

The agent session runtime coordinates a single active work session.

### Responsibilities

- Maintain session state
- Build model context
- Route prompts through extensions and skills
- Execute agent loop
- Dispatch tool calls
- Persist messages and tool results
- Handle retries and compaction
- Support branching/forking
- Emit lifecycle events

### Key abstractions

```text
AgentSession
  - id
  - cwd
  - currentModel
  - thinkingLevel
  - activeTools
  - messages
  - sessionManager
  - resourceLoader
  - extensionRuntime
  - prompt()
  - steer()
  - followUp()
  - abort()
  - compact()
  - navigateTree()
```

---

## 4.3 Model Runtime

The model runtime abstracts over model providers.

### Responsibilities

- Maintain provider catalog
- Resolve credentials
- Select active model
- Support model switching
- Support provider-specific capabilities
- Expose model limits and cost metadata where available
- Support custom providers and internal gateways

### Provider requirements

A provider definition should include:

```yaml
provider_id: string
name: string
auth_type: api_key | oauth | managed | none
api_type: anthropic_messages | openai_responses | openai_chat | custom
base_url: string optional
models:
  - id: string
    name: string
    context_window: number
    max_output_tokens: number
    supports_tools: boolean
    supports_images: boolean
    supports_reasoning: boolean
    cost_metadata: optional
```

### Credential resolution order

Recommended order:

1. Runtime override
2. Secure local credential store
3. Environment variable
4. Enterprise credential broker
5. Provider-specific login flow

Credentials must never be requested through ordinary model text prompts.

---

## 4.4 Resource Loader

The resource loader discovers and loads runtime resources.

### Resource types

- Skills
- Extensions
- Prompt templates
- Themes/UI configuration
- Context files
- Model/provider configuration
- Project settings

### Discovery scopes

1. Global user scope
2. Organization-managed scope
3. Project scope
4. Package scope
5. CLI/runtime overrides

### Trust model

Project-local executable resources, such as extensions, must only load after the user or admin has trusted the project.

Static context files may be loaded more permissively, but implementations should still consider prompt-injection and sensitive-content risks.

---

## 5. Agent Loop

The core agent loop turns a user prompt into one or more model calls and tool executions.

### 5.1 High-Level Flow

```text
User prompt submitted
  |
  v
Input event hooks
  |
  v
Command / skill / template expansion
  |
  v
Before-agent-start hooks
  |
  v
Build context
  |
  v
Model request
  |
  v
Assistant response streams
  |
  +--> Text output
  |
  +--> Tool calls
          |
          v
       Tool preflight hooks
          |
          v
       Tool execution
          |
          v
       Tool result hooks
          |
          v
       Persist result
          |
          v
       Continue model loop if needed
  |
  v
Agent settled
```

### 5.2 Pseudocode

```typescript
async function runAgentTurn(prompt: UserPrompt) {
  const input = await extensionRuntime.runInputHooks(prompt);
  if (input.handled) return;

  const expandedPrompt = await expandCommandsSkillsTemplates(input);

  await extensionRuntime.beforeAgentStart(expandedPrompt);

  while (true) {
    const context = await contextBuilder.build(sessionState);
    const response = await modelRuntime.stream(context);

    sessionState.appendAssistantMessage(response.message);

    if (response.toolCalls.length === 0) break;

    const results = await toolExecutor.executeBatch(response.toolCalls);
    sessionState.appendToolResults(results);

    if (results.every((r) => r.terminate)) break;
  }

  await extensionRuntime.agentSettled();
}
```

---

## 6. Tool System

## 6.1 Tool Definition

A tool is a typed capability callable by the model.

```typescript
interface ToolDefinition<TInput, TResultDetails> {
  name: string;
  label?: string;
  description: string;
  parameters: JsonSchema;
  promptSnippet?: string;
  promptGuidelines?: string[];
  execute: (
    toolCallId: string,
    params: TInput,
    signal: AbortSignal,
    onUpdate: (partial: ToolPartialResult) => void,
    ctx: ToolExecutionContext
  ) => Promise<ToolResult<TResultDetails>>;
  renderCall?: ToolRenderer;
  renderResult?: ToolRenderer;
}
```

### Required tool behavior

- Validate input against schema.
- Return structured content.
- Throw errors to indicate failure.
- Respect cancellation signals.
- Truncate large outputs.
- Avoid leaking secrets.
- Persist meaningful details for audit/debugging.

---

## 6.2 Built-In Tools

Minimum recommended built-in tools:

| Tool | Description |
|---|---|
| read | Read text or image files with truncation |
| write | Create or overwrite files |
| edit | Apply exact text replacements |
| bash | Execute shell commands in current workspace |
| grep/search | Search file contents |
| find/list | Discover files and directories |
| question | Ask user structured questions |

Built-in tools should be replaceable or wrappable by extensions for logging, sandboxing, or policy enforcement.

---

## 6.3 Tool Execution Lifecycle

```text
tool_execution_start
  |
  v
tool_call preflight hooks
  |     
  +--> block/modify/allow
  |
  v
execute tool
  |
  v
stream partial updates optional
  |
  v
tool_result hooks
  |     
  +--> modify/redact/augment
  |
  v
tool_execution_end
  |
  v
persist tool result
```

### Batch execution

Tool calls from a single assistant message may execute in parallel. File-mutating tools must participate in a per-file mutation queue to avoid lost updates.

---

## 6.4 Tool Result Schema

```typescript
interface ToolResult<TDetails = unknown> {
  content: Array<{
    type: "text" | "image" | "json";
    text?: string;
    data?: unknown;
    mediaType?: string;
  }>;
  details?: TDetails;
  usage?: UsageMetadata;
  terminate?: boolean;
}
```

### Error handling

- Tool execution errors should be represented by thrown exceptions.
- The runtime catches exceptions and sends an error result to the model.
- Tool error results should be persisted with `isError: true`.

---

## 6.5 Output Truncation

All tools must enforce output limits.

Recommended default:

- Maximum bytes: 50 KB
- Maximum lines: 2,000

For truncated output, the tool should:

1. Return the visible truncated content.
2. State that truncation occurred.
3. Save or reference the full output only if safe and necessary.
4. Avoid placing large raw payloads into model context.

---

## 7. Skills System

## 7.1 Skill Purpose

Skills package procedural knowledge. They are instructions, not executable runtime plugins by default.

A skill should answer:

- When should this skill be used?
- What steps should the agent follow?
- What tools or integrations are relevant?
- What constraints apply?
- What outputs should be produced?

---

## 7.2 Skill File Structure

Recommended structure:

```text
skill-name/
  SKILL.md
  references/
    domain-guide.md
    examples.md
  scripts/
    helper-script.py
  assets/
    template.md
```

### SKILL.md metadata

```yaml
---
name: skill-name
description: Clear explanation of when to use the skill.
version: 1.0.0 optional
owner: team-name optional
---
```

### Required fields

- `name`
- `description`

---

## 7.3 Skill Loading Flow

```text
Startup
  |
  v
Discover skill metadata
  |
  v
Expose name/description to model
  |
  v
Task matches skill
  |
  v
Agent reads full SKILL.md
  |
  v
Agent follows procedure
```

This pattern minimizes base context while still making specialized behavior available.

---

## 7.4 Skill Governance

Recommended controls:

- Version skills in source control.
- Require review for shared organizational skills.
- Distinguish personal, team, and enterprise-approved skills.
- Track skill usage in session metadata.
- Test high-value skills with evaluation scenarios.

---

## 8. Extension System

## 8.1 Extension Purpose

Extensions are executable plugins that can alter runtime behavior.

They should be used for:

- New tools
- New commands
- UI components
- Safety gates
- Integration adapters
- Provider registration
- Event hooks
- Session automation

---

## 8.2 Extension API

A representative extension API:

```typescript
interface ExtensionAPI {
  on(eventName: string, handler: ExtensionEventHandler): void;
  registerTool(tool: ToolDefinition<any, any>): void;
  registerCommand(name: string, command: CommandDefinition): void;
  registerShortcut(shortcut: string, handler: ShortcutHandler): void;
  registerProvider(provider: ProviderDefinition): void;
  setActiveTools(names: string[]): void;
  getActiveTools(): string[];
  getAllTools(): ToolMetadata[];
  sendUserMessage(content: string, options?: SendOptions): void;
  appendEntry(customType: string, data: unknown): void;
}
```

---

## 8.3 Extension Lifecycle Events

Recommended event categories:

### Session events

- `session_start`
- `session_shutdown`
- `session_before_switch`
- `session_before_fork`
- `session_before_compact`
- `session_compact`

### Agent events

- `input`
- `before_agent_start`
- `agent_start`
- `turn_start`
- `turn_end`
- `agent_end`
- `agent_settled`

### Tool events

- `tool_execution_start`
- `tool_call`
- `tool_result`
- `tool_execution_end`

### Model/provider events

- `model_select`
- `before_provider_request`
- `after_provider_response`

### UI events

- Custom command invocation
- Shortcut handling
- User confirmation/input dialogs

---

## 8.4 Extension Security

Extensions are powerful and should be treated as code execution.

Required controls:

- Project-local extensions require trust.
- Extensions can be disabled.
- Source provenance should be visible.
- Enterprise distributions should review and pin extension versions.
- Extension errors should be isolated.
- Extensions should not access secrets except through approved APIs.

---

## 9. Context Builder

## 9.1 Context Inputs

The context builder assembles the model request from:

- System prompt
- Tool definitions
- Active skill metadata
- Loaded skill contents
- Context files
- Session messages
- Tool results
- Extension-injected messages
- User prompt
- Model/provider constraints

---

## 9.2 Context Assembly Rules

Recommended rules:

1. Put stable high-priority system instructions first.
2. Include only active tool definitions.
3. Include skill metadata globally but full skill contents only after invocation.
4. Include project context when trusted or safe.
5. Include recent session history.
6. Use compaction summaries for older history.
7. Avoid including raw large tool outputs.
8. Avoid including secrets.

---

## 9.3 Compaction

Compaction summarizes older conversation entries when context grows too large.

Compaction should preserve:

- User goals
- Decisions made
- Files changed
- Tool results that matter
- Open tasks
- Verification evidence
- Known constraints

Compaction should not preserve:

- Raw secrets
- Excessive logs
- Redundant intermediate outputs
- Sensitive data beyond what is needed

---

## 10. Session Persistence

## 10.1 Session Model

Sessions should be persisted as append-only structured records.

Recommended top-level concepts:

```typescript
interface Session {
  sessionId: string;
  createdAt: string;
  cwd?: string;
  entries: SessionEntry[];
  currentLeafId: string;
  metadata: SessionMetadata;
}
```

### Entry model

```typescript
type SessionEntry =
  | MessageEntry
  | ToolResultEntry
  | CustomEntry
  | LabelEntry
  | CompactionEntry;

interface BaseEntry {
  id: string;
  parentId?: string;
  timestamp: string;
  type: string;
}
```

The `parentId` field enables tree-structured branching.

---

## 10.2 Message Entry

```typescript
interface MessageEntry extends BaseEntry {
  type: "message";
  role: "user" | "assistant" | "toolResult" | "system" | "custom";
  content: ContentBlock[];
  model?: string;
  provider?: string;
  usage?: UsageMetadata;
}
```

---

## 10.3 Tool Result Entry

```typescript
interface ToolResultEntry extends BaseEntry {
  type: "tool_result";
  toolCallId: string;
  toolName: string;
  input: unknown;
  output: ContentBlock[];
  details?: unknown;
  isError: boolean;
  usage?: UsageMetadata;
  durationMs?: number;
}
```

---

## 10.4 Branching

Branching allows users to return to an earlier point and continue differently.

Requirements:

- Preserve all branches.
- Allow labeling important entries.
- Support summaries when abandoning or switching branches.
- Keep session export understandable.

---

## 11. Integration Architecture

## 11.1 Integration Adapter Pattern

Each enterprise integration should be represented as one or more typed tools.

```text
Model
  |
  v
Tool schema
  |
  v
Integration adapter
  |
  v
Auth provider / credential broker
  |
  v
External system API
```

### Adapter responsibilities

- Validate input
- Resolve auth
- Call external API
- Handle pagination/rate limits
- Normalize response
- Redact sensitive fields if needed
- Return structured result
- Emit audit metadata

---

## 11.2 MCP-Style Connector Pattern

An MCP-style connector exposes external capabilities through a standardized server/tool protocol.

Recommended use cases:

- Data warehouse access
- Enterprise SaaS tools
- Internal APIs
- Systems where centralized auth is preferred

Benefits:

- Separates integration runtime from agent runtime
- Enables centralized governance
- Provides tool discovery
- Can support OAuth or managed credentials
- Keeps service-specific logic out of the core agent

---

## 11.3 Data Warehouse Integration

Data access should be especially controlled.

Recommended capabilities:

- List clusters/workgroups
- List databases/schemas/tables
- List columns
- Run approved SQL
- Return limited results
- Save large outputs safely
- Attach query metadata

Recommended safety requirements:

- Use managed credentials.
- Enforce read-only access by default.
- Apply row/column-level access policies upstream.
- Require domain-context skills for business metrics.
- Limit result size.
- Log query text and execution metadata.
- Redact sensitive columns where required.

---

## 11.4 Source Control Integration

Recommended capabilities:

- Inspect status/diff
- Create branches or worktrees
- Prepare pull request text
- List issues/PRs
- Comment on review findings
- Fetch CI status

Safety requirements:

- Treat default branches as protected.
- Confirm destructive operations.
- Prefer project task runners for build/test.
- Avoid auto-push or merge without explicit user instruction.

---

## 11.5 Issue Tracker Integration

Recommended capabilities:

- Fetch ticket details
- Summarize requirements
- Identify acceptance criteria
- Link implementation plans
- Draft status updates
- Transition statuses where allowed

Safety requirements:

- Do not change ticket status without user confirmation unless policy allows it.
- Preserve links to generated artifacts.
- Avoid exposing private ticket content outside approved contexts.

---

## 12. Security Architecture

## 12.1 Trust Boundaries

Key trust boundaries:

1. User input
2. Model output
3. Local filesystem
4. Shell execution
5. Project-local resources
6. Extensions
7. Enterprise integrations
8. External model providers
9. Session storage

The model should be treated as untrusted for authorization decisions. Runtime policy should enforce sensitive controls.

---

## 12.2 Permission Model

Recommended permission levels:

| Level | Description |
|---|---|
| No tools | Chat only |
| Read-only | Can inspect files/resources |
| Local write | Can modify local files |
| Shell | Can run commands |
| External read | Can read integrated systems |
| External write | Can update integrated systems |
| Admin | Can manage platform resources |

Permissions can be assigned by:

- User role
- Workspace
- Project trust state
- Session mode
- Tool allowlist
- Integration policy

---

## 12.3 Safety Gates

Runtime safety gates should intercept high-risk actions.

Examples:

```text
Tool call generated
  |
  v
Policy checks
  |-- blocked path?
  |-- destructive command?
  |-- untrusted project?
  |-- protected branch?
  |-- external write?
  |-- sensitive data request?
  v
allow | require confirmation | block
```

---

## 12.4 Secrets Handling

Requirements:

- Do not put secrets in prompts.
- Do not store secrets in session logs.
- Use environment variables, OS keychain, enterprise vault, or provider auth files.
- Redact likely secrets from tool output.
- Prevent the model from directly requesting credentials where possible.
- Avoid echoing commands that include secrets.

---

## 12.5 Prompt Injection Mitigation

Prompt injection can come from files, web pages, tickets, docs, or tool results.

Mitigations:

- Treat retrieved content as data, not instructions.
- Keep system and policy instructions above retrieved content.
- Use skills and tools that remind the agent of source boundaries.
- Require confirmation for sensitive actions.
- Restrict tools in risky contexts.
- Add policy checks outside the model.

---

## 13. UI and User Interaction

## 13.1 UI Primitives

The platform should expose UI primitives to extensions and tools:

- Notification
- Confirmation dialog
- Select list
- Text input
- Multi-line editor
- Custom component
- Status widget
- Footer/header customization
- Tool result renderer

---

## 13.2 Structured Question Tool

The agent should be able to ask structured questions rather than burying questions in prose.

Example schema:

```typescript
interface Question {
  id: string;
  label?: string;
  prompt: string;
  options: Array<{
    value: string;
    label: string;
    description?: string;
  }>;
  allowOther: boolean;
}
```

Use cases:

- Clarifying requirements
- Approval gates
- Choosing between approaches
- Collecting preferences
- Confirming risky actions

---

## 14. Configuration Model

## 14.1 Global Configuration

Examples:

```json
{
  "defaultModel": "provider/model-id",
  "enabledModels": ["provider/*"],
  "tools": ["read", "edit", "bash"],
  "extensions": ["/path/to/extension"],
  "skills": ["/path/to/skills"],
  "projectTrustDefault": "ask"
}
```

---

## 14.2 Project Configuration

Project settings should override or extend global settings only after project trust is established.

Examples:

```json
{
  "tools": ["read", "grep", "find"],
  "skills": ["./.agent/skills"],
  "extensions": ["./.agent/extensions/project-policy.ts"]
}
```

---

## 14.3 Package Configuration

Organizations may distribute resources as packages.

Package contents may include:

- Skills
- Extensions
- Prompt templates
- Themes
- Provider configs

Package risks:

- Extensions execute code.
- Skills can instruct the model to take actions.
- Packages should be reviewed and pinned.

---

## 15. Deployment Models

## 15.1 Local CLI Deployment

Best for:

- Engineering teams
- Power users
- Local codebase work
- Fast iteration

Characteristics:

- Runs on user workstation
- Accesses local filesystem
- Uses local credentials or enterprise auth
- Can invoke local development tools

---

## 15.2 Managed Desktop or Enterprise Distribution

Best for:

- Broader employee rollout
- Centralized policy
- Controlled updates

Characteristics:

- Bundled skills/extensions
- Managed model provider settings
- Admin-controlled integration availability
- Centralized telemetry or audit logs where appropriate

---

## 15.3 Server-Hosted Web Workbench

Best for:

- Non-engineering users
- Standardized workflows
- Centralized compute and security

Characteristics:

- Server-side tool execution or sandboxing
- Browser UI
- Centralized auth
- Stronger admin controls
- Less direct local-file access unless connected through workspace sync

---

## 15.4 Hybrid Model

Recommended long-term:

- Local CLI for engineering-heavy workflows
- Web workbench for business workflows
- Shared skills, integrations, policies, and session schema

---

## 16. Observability and Audit

## 16.1 Events to Capture

- Session created/resumed
- User prompt submitted
- Model selected
- Skill invoked
- Tool call started
- Tool call blocked/confirmed
- Tool result completed
- Integration API called
- External write performed
- Session compacted
- Session exported
- Error occurred

---

## 16.2 Audit Record

Example audit event:

```json
{
  "event_id": "uuid",
  "timestamp": "2026-10-06T00:00:00Z",
  "session_id": "session-id",
  "user_id": "user-id",
  "event_type": "tool_call",
  "tool_name": "data_query",
  "integration": "warehouse",
  "risk_level": "medium",
  "approval_required": false,
  "outcome": "success",
  "metadata": {
    "duration_ms": 1234,
    "rows_returned": 100
  }
}
```

Sensitive inputs and outputs should be redacted or omitted according to policy.

---

## 17. Testing Strategy

## 17.1 Unit Tests

Test:

- Tool schema validation
- Tool output truncation
- Context builder ordering
- Skill discovery
- Extension loading
- Permission checks
- Session tree operations
- Provider resolution

---

## 17.2 Integration Tests

Test:

- Model call with mock provider
- Tool execution loop
- Extension event hooks
- MCP/integration adapters with mocked external APIs
- Session persistence and resume
- Compaction behavior
- Auth resolution

---

## 17.3 End-to-End Tests

Test representative workflows:

- Create a PRD
- Modify a sample repo and run tests
- Debug a seeded bug
- Query a fake warehouse
- Block a dangerous command
- Require confirmation for external write

---

## 17.4 Skill Evaluations

High-value skills should have scenario-based evaluations.

Example evaluation dimensions:

- Did the agent invoke the skill?
- Did it follow required steps?
- Did it ask clarifying questions?
- Did it avoid prohibited actions?
- Did it produce the expected artifact?
- Did it verify before claiming completion?

---

## 18. MVP Implementation Plan

## Phase 1: Core Runtime

Build:

- Agent session abstraction
- Model provider abstraction
- Basic interactive UI
- Built-in read/edit/write/shell tools
- Tool execution lifecycle
- Session persistence

Exit criteria:

- User can ask the agent to inspect and modify local files.
- Tool calls are visible and persisted.
- Session can be resumed.

---

## Phase 2: Skills and Context

Build:

- Skill discovery
- Skill invocation
- Context file loading
- Prompt template support optional
- Project trust for dynamic resources

Exit criteria:

- Agent can load a skill on demand.
- Project instructions influence behavior.
- Untrusted project resources are not executed.

---

## Phase 3: Extensions

Build:

- Extension loading
- Tool registration
- Command registration
- Event hooks
- UI primitives
- Safety gate examples

Exit criteria:

- A custom extension can add a new tool.
- A custom extension can block a risky command.
- A custom command can run inside the UI.

---

## Phase 4: Enterprise Integrations

Build:

- Source-control adapter
- Issue-tracker adapter
- Documentation adapter
- One governed data/system adapter
- Auth and credential resolution

Exit criteria:

- Agent can complete one end-to-end workflow using at least two integrations.
- Integration actions are recorded in session/audit events.

---

## Phase 5: Governance and Scale

Build:

- Admin-configured tool policies
- Audit export
- Extension review/distribution process
- Skill versioning
- Observability dashboard
- Evaluation harness

Exit criteria:

- Platform can be rolled out to multiple teams with controlled capabilities.
- Admins can review usage and manage risk.

---

## 19. Suggested Technology Choices

These are examples, not requirements.

### Runtime

- TypeScript / Node.js for plugin ecosystem and CLI tooling
- Rust or Go for stricter sandbox/runtime components if needed
- Python for data/reporting helper scripts where appropriate

### Interface

- Terminal UI for developer workflows
- Web frontend for business workflows
- JSON/RPC for automation

### Storage

- Local JSONL for individual sessions
- SQLite for local indexed history
- Central event store for enterprise audit
- Object storage for exported artifacts

### Integrations

- Native SDKs where mature
- CLI wrappers where existing enterprise tools already work well
- MCP-style servers for governed external systems
- Internal API gateway for sensitive systems

### Security

- OS keychain or enterprise vault for secrets
- OAuth for SaaS integrations
- Policy engine for tool permissions
- Sandboxed execution for untrusted commands

---

## 20. Open Technical Questions

1. Should tool execution be local, remote, sandboxed, or hybrid?
2. What is the minimum viable permission model?
3. How should extension packages be reviewed and distributed?
4. Should sessions be stored locally, centrally, or both?
5. Which integrations require centralized audit logging?
6. How should model provider fallback work?
7. How should sensitive data be redacted from tool output?
8. What workflows require deterministic approval gates?
9. How should skill evaluations be run in CI?
10. What is the policy for project-local instructions from untrusted repositories?

---

## 21. Build-vs-Buy Considerations

A team should build a dedicated platform when it needs:

- Custom runtime controls
- Local tool execution
- Enterprise-specific workflows
- Internal system integrations
- Multiple model providers
- Auditability
- Safety gates outside the model
- Extensible skills and plugins

A team may rely on a vendor assistant with skills/integrations when:

- Workflows are mostly conversational
- Integrations are generic and already supported
- Tool execution risk is low
- Audit requirements are light
- Vendor lock-in is acceptable
- Custom UI/runtime behavior is not required

---

## 22. Summary

An enterprise agent platform consists of a model runtime, session manager, tool execution layer, skills system, extension system, integration layer, and safety/governance framework.

The key architectural decision is to keep the language model replaceable and put durable company value into:

- Workflow definitions
- Tool integrations
- Runtime safety
- Session auditability
- Extensible plugin mechanisms
- Domain-specific skills

This design allows organizations in any industry to build a similar agent workbench while replacing all domain-specific content with their own workflows, systems, policies, and terminology.
