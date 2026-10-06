# Toolkit Reference
Open this when you're stuck. Not a manual — a cheatsheet.

---

## The Golden Rule

**Before ANY framework or template: braindump first.**

Think messily → `/braindump` → `/navigate` → `/framework` → artifact.

Never jump straight to templates. The thinking comes first; structure organizes the thinking. See [PRODUCT-SENSE-RULES.md](../PRODUCT-SENSE-RULES.md) for the full philosophy.

---

## Agent States (What Mode Are You In?)

When you talk to the agent, you're always in one of 4 states:

| State | What happens | Example |
|---|---|---|
| **product_sense** | Messy thinking. Agent asks hard questions, challenges assumptions, doesn't offer structure yet. | You: "I'm thinking about building X" → Agent: "What problem are you actually solving?" |
| **execution_mode** | Ready to build artifacts. Agent suggests frameworks, templates, helps you fill them. | You: "Write a PRD for X" → Agent: "Here's the template..." |
| **meta_reflection** | Post-decision learning. Agent helps you capture learnings, track forecast accuracy. | After shipping: "What did we learn? What surprised you?" |
| **conversation** | Everything else (navigation, general questions). | "Where do I find the stakeholder avatars?" |

The agent infers your state from what you ask. You don't need to say it explicitly — but knowing it helps when behavior seems off.

**Rule:** If the agent jumps to templates without asking questions, you're in the wrong state. Say: "Let me braindump first" to re-enter product_sense.

---

## Framework Flow (The Overall Shape)

PM work flows through 5 layers:

1. **2.0 Foundations** — HOW TO THINK (mental models, bias, reflection)
2. **2.1 Strategy** — WHERE ARE WE GOING? (OKRs, roadmap, north star)
3. **2.2 Discovery** — WHAT TO BUILD? (research, JTBD, opportunity assessment)
4. **2.3 Execution** — BUILD, SHIP, MEASURE (PRD, personas, metrics)
5. **2.4 Communication** — ALIGN STAKEHOLDERS (one-pagers, meetings, crisis management)

**Common path for a new initiative:** Foundations → Strategy → Discovery → Prioritization → Execution → Communication

**If you're stuck:** Work backward through the layers to find the gap. Missing discovery? Go back to 2.2. Unclear strategy? Go back to 2.1.

---

## Hypothesis Protocol (Hard Gate Before Templates)

**Before writing any PRD, Roadmap, or major artifact, state your hypothesis in this format:**

**IF** [Action/Feature]: What are we building or changing?  
**THEN** [Outcome/Metric]: What measurable business or user value will change?  
**BECAUSE** [Evidence/Rationale]: Why do we believe this? (Link to `00-Meta/3-research-insight-log.md`, business-review data, or a customer insight)

**Example:**
*(Illustrative.)*
- **IF** we add an in-app checklist for the first three setup steps...
- **THEN** 7-day activation rises from 32% to 40% within six weeks...
- **BECAUSE** session recordings show most new accounts stall at step 2 with no prompt to continue.

**Rule:** If you can't complete this in clear, evidence-backed language, you're not ready for PRD/Roadmap yet. Go back to `/braindump` and `/discover [problem]`.

---

## Evaluation Framework (Quick Check vs. Deep Eval)

**Quick Quality Check** (`/pm-review`) — Use during creation
- 5–8 criteria, 5 min max
- Before sharing with team or asking for feedback
- Catches obvious gaps (missing metrics, vague success criteria, etc.)
- Run this FIRST

**Full Evaluation** (`/evaluate`) — Use before exec review or publishing to the team wiki
- Comprehensive rubric, weighted scoring, peer-review style
- Detailed feedback on what's strong vs. what needs work
- Takes 10–15 min
- Run this ONLY after quick check is green, or before shipping to executives

**Rule:** Always quick check first. Full eval only if quick check flagged issues you've fixed, OR before a major stakeholder review.

---

## I need to...

| Situation | Start here |
|---|---|
| Think through a fuzzy problem before structuring it | `/braindump` |
| Orient myself on what to work on today | `/day` |
| Plan or review my week | `/week` |
| Too many things competing — cut through noise | `/focus` |
| Know which framework applies to my situation | `/navigate` |
| Turn a braindump into a structured artifact | `/framework` |
| Kick off a new initiative end-to-end | `/start` |
| Run a full discovery loop on a problem | `/discover [problem]` |
| Write a PRD | `/write-prd [topic]` — **Remember: Section 3 (Assumptions & Confidence) comes first** |
| Prioritize a backlog or set of options | `/prioritize [context]` |
| Build a roadmap | `/plan-roadmap [horizon + goals]` |
| Develop product strategy | `/strategy [product + question]` |
| Quick quality check on a draft | `/pm-review` |
| Deep quality check before exec or eng review | `/evaluate` |
| Something isn't moving — diagnose the block | `/unstuck` |
| Pressure-test a doc from an exec's point of view | `/exec-review` |
| Pick the right analysis method or check a metric | "talk to Sam" (data analyst agent) |
| Analyze real data without fooling myself | `analysis-rigor` skill (loads automatically for data work) |
| Capture my own decision | "log this decision" or `/log-decision` |
| Capture someone else's decision that affects me | "log observed decision" or `/log-observed` |
| Clean up a long, messy session | `/broker-audit` or "checkpoint" |

---

## Command quick reference

### PM-Brain (daily workflow)
`/braindump` → `/navigate` or `/framework` → `/start` or the relevant structured command

| Command | One-liner |
|---|---|
| `/braindump` | Think out loud. Questions first, frameworks after. |
| `/day` | Daily planning ritual — morning, midday, or evening wrap |
| `/week` | Weekly review + priorities |
| `/focus` | Eisenhower sort + LNO framework for competing obligations |
| `/navigate` | Routes you to the right phase and framework |
| `/framework` | Matches your situation to a specific template and runs it |
| `/start` | Full initiative launch — braindump → foundations → discovery → PRD |
| `/pm-review` | Fast quality check (5–8 criteria). Use before sharing internally. |
| `/evaluate` | Full rubric. Use before exec review or publishing. |
| `/exec-review` | Adversarial review from an operations-minded exec. |
| `/log-decision` | Log your own decision with rationale and alternatives. |
| `/log-observed` | Log a decision someone else made, with confidence level. |
| `/broker-audit` | Context hygiene: what's loaded, what's stale, what's unsaved. |
| `/unstuck` | Diagnoses block across 7 categories (A–G). Gives action plan. |

### Structured PM work (uses the optional PM-Skills library, falls back to built-in frameworks)
`/discover` → `/write-prd` → `/plan-roadmap` is the core chain for new initiatives.

| Command | One-liner |
|---|---|
| `/discover [problem]` | Problem framing → interviews → OST → PoL probes → execution plan |
| `/write-prd [topic]` | Problem → persona → PRD → stories → story splitting |
| `/prioritize [context]` | Framework selection → feature ROI → channel quality → recommendation |
| `/plan-roadmap [horizon]` | Roadmap context → epic hypotheses → prioritization → delivery slices |
| `/strategy [question]` | Positioning → problem → OST → strategy session → roadmap sequencing |
| `/leadership-transition [scenario]` | Altitude/horizon → readiness → 30-60-90 plan |

---

## Common chains

**New problem, don't know where to start**
`/braindump` → `/navigate` → `/discover [problem]` → state hypothesis → `/write-prd [topic]`

**Ready to build something (hypothesis already formed)**
`/write-prd [topic]` → **[Assumptions & Confidence section FIRST]** → `/plan-roadmap [horizon]` → `/pm-review` → ready to share

**Writing a PRD: Order matters**
1. Section 3: Assumptions & Confidence Levels (FIRST — surface what you know vs. guess)
2. Section 4: Goals & Success Metrics (THEN — what success looks like)
3. Sections 5+: Solution, Requirements, etc. (NOW — informed by assumptions)
4. `/pm-review` — quick quality check before sharing

**Need to make a prioritization call**
`/braindump` → `/prioritize [context]` → decision ready

**Prepping for exec review**
`/pm-review` (during creation) → `/evaluate` (before shipping) → fix gaps → `/exec-review` → publish

**Stuck mid-initiative**
`/unstuck` → diagnose block → follow action plan → resume with relevant command

**Long session, context feels degraded**
Say: **"checkpoint"** → agent saves to `checkpoints/session-[timestamp].md` → start fresh conversation and resume

---

## How to invoke by surface

**Claude Code (CLI)**
Type `/commandname` — slash commands are wired in `.claude/commands/`.
Pass context after the name: `/discover onboarding drop-off at step 2`

**Claude desktop (Cowork)**
Type the command naturally: *"run /discover for onboarding drop-off at step 2"*
Connect this repo folder so the command files and context are readable.

**Claude Projects**
Type the command or describe the job: *"/braindump"* or *"I need to run discovery on..."*
Commands work because the CLAUDE.md is loaded as project instructions.

**Connectors (wiki, issue tracker, BI)**
Natural language: *"publish this PRD to the wiki"* or *"show me the current sprint"*
Prerequisite: the connector is authenticated in Settings → Connectors, **and** your company has approved connecting it. Get that approval in week 1, because it blocks every automation.

---

## Agents

Agent files live in `00-Meta/agents/`. Load one only when the task calls for it.

- **Sam (data analyst)** — picks the analysis method, designs experiments, checks whether a metric measures what you think it does. Say *"talk to Sam"*.
- **Exec reviewer** — operations-minded adversarial review before leadership sees a doc. `/exec-review`.
- **Context-Broker** — finds what's loaded, what's stale, and what's been said but not saved. `/broker-audit`.

**BMAD (bundled in `_bmad/`):** John (PM) for PRDs, requirements and epics/stories, and Mary (Analyst) for market and competitive research and product briefs. You can also run the workflows: brainstorming, advanced elicitation, party mode (multi-agent), adversarial review, edge-case hunting, editorial review, and doc sharding. Say *"talk to John"*, *"run BMAD brainstorming"*, and so on. Keep it to two agents per session for token budget, and never run the full dev loop.

---

## Parking Lot Rule

Say **"park this"** at any point during work. The idea gets a `[PARKED]` tag at the end of the response.

Current workflow continues uninterrupted. You don't lose context.

Revisit parked items in `07-Parking-Lot/`. Weekly: review parked list and decide: ship, prioritize, or defer further.

---

## When Something Isn't Working

| Symptom | Likely cause | Fix |
|---|---|---|
| Command jumps to frameworks before asking questions | CLAUDE.md braindump rule not loading | Check Claude Code is reading root CLAUDE.md — run `/help` to confirm |
| `/discover` output is generic | Skill files not being read, or `01-Company-Context/` is empty | Verify `.claude/commands/discover.md` has correct file paths; fill in company context files |
| Agent seems confused or forgets context | Long conversation (>25 turns) with heavy context loaded | Say: "checkpoint" → start fresh conversation → resume from checkpoint |
| Structured command says PM-Skills is missing | Optional library not installed | `git clone https://github.com/deanpeters/Product-Manager-Skills 02-Methods-and-Tools/pm-skills`, or let it fall back to built-in frameworks |
| A command behaves differently in two tools | Instruction files have drifted | Commands live only in `00-Meta/commands/`. Platform files should be thin pointers. Run `/broker-audit` to find conflicts |
| Connector can't write | Authentication, or the space or project is wrong | Re-auth in Settings → Connectors; confirm the space or project key |
| "park this" gets ignored | Parking lot rule not in effect | State it explicitly: *"park this per my CLAUDE.md rule"* |

---

## Working with raw data

The rule: **analysis and synthesis live in the repo. Raw files live externally (Drive/SharePoint/Teams) with a link.**

---

**Have an interview recording or transcript?**
1. Save the raw file externally — link it from the analysis doc
2. Drop a text summary or key quotes into `.incoming/` — the nightly synthesis task (if set up) will file it
3. For active initiative research: analysis goes to `04-Initiatives/[initiative-name]/research/`
4. For general/reusable research: analysis goes to `03-Research-Artifacts/3.1-User-Interviews/`
5. To analyze manually right now: `/discover [theme] — reference transcripts in 03-Research-Artifacts/3.1-User-Interviews/`

**Have Excel or utilization data?**
1. Save the raw file externally — link it from `05-KPIs-and-Data/`
2. Paste a summary or key numbers into `.incoming/` for nightly synthesis
3. To analyze right now: ask "talk to Sam" or point Claude at the file. The `analysis-rigor` skill applies.

**Have customer feedback tickets?**
1. Tickets stay in the tracker — reference by ticket ID or sprint in your analysis doc
2. To synthesize a batch: export a CSV → drop into `.incoming/` or ask Claude to synthesize it directly
3. Analysis goes to `03-Research-Artifacts/3.2-Qualitative-Research/`

**Want to find patterns across everything you've gathered?**
- In Claude Code: `/discover [theme]` — point it at `03-Research-Artifacts/` for broad synthesis, or `04-Initiatives/[name]/research/` for initiative-specific
- Drop a synthesis question into `.incoming/` overnight — nightly task will attempt a pass

**Want to track trends over time?**
- Usually a Month 2 item, once the data pipeline is confirmed with the data team
- In the meantime: append rolling summaries manually to `05-KPIs-and-Data/kpi-framework.md`

---

## When Your Version Changes

Check `version.json` occasionally. If it bumped significantly:
- Re-read `ORCHESTRATION.md` (behavior may have changed)
- Check `breakingChanges` array for what's different
- 10-minute re-orient beats 2 hours debugging.

Current version: see `version.json` (root)

---

## Key file locations

| What | Where |
|---|---|
| Command source (single source of truth) | `00-Meta/commands/` |
| Claude Code slash-command shims | `.claude/commands/` (one-line pointers, never edit content here) |
| Agents (Sam, exec reviewer, context broker) | `00-Meta/agents/` |
| Skills (portable, copy to `~/.claude/skills/` to install) | `02-Methods-and-Tools/skills/` |
| Optional PM-Skills library | `02-Methods-and-Tools/pm-skills/` (not included; clone it if wanted) |
| Session checkpoints | `checkpoints/` |
| Parking lot | `07-Parking-Lot/` |
| KPI definitions + data analysis | `05-KPIs-and-Data/` |
| Stakeholder avatars | `01-Company-Context/1.1-Stakeholder-Avatars/` |
| Active initiatives | `04-Initiatives/` |
| General/reusable research | `03-Research-Artifacts/` |
| Initiative-specific research | `04-Initiatives/[name]/research/` |
| Raw notes for nightly synthesis | `.incoming/` |
| New-job setup kit + scheduled tasks | `Implementation/` |

---

## Core Reference Docs (Read if Confused)

This toolkit is a cheatsheet. If you need the full picture:

- **[ORCHESTRATION.md](../ORCHESTRATION.md)** — How the agent routes and moves between states; what loads when
- **[PRODUCT-SENSE-RULES.md](../PRODUCT-SENSE-RULES.md)** — The braindump workflow + hypothesis protocol + confidence-based decision rules
- **[AGENTS.md](../AGENTS.md)** — Agent persona, philosophy, and priority (thinking before structure)
- **[MEMORY.md](../MEMORY.md)** — What context to wake when; sleeping memory manifest
- **[CLAUDE.md](../CLAUDE.md)** — Your working agreement with Claude; logging rules, parking lot rule, output formats
