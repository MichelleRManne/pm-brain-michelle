# _bmad — BMAD Method core (v6.1.0)

This folder bundles the [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) core module (MIT License). It was installed with `npx bmad-method install`, and two things were added on top:

- **`core/agents/bmad-agent-data-analyst.md` (Sam):** a custom agent in BMAD format. The canonical, BMAD-independent version is `00-Meta/agents/data-analyst-sam.md`.
- **Scope rule:** at most two agents per session (John + Mary by default), and never the full dev loop. See `CLAUDE.md` → Token budget.

| What | Where |
|---|---|
| Agents | `core/agents/`: John (PM), Mary (Analyst), Amelia (Dev, on request), BMad Master, Sam |
| Workflows | `core/workflows/`: brainstorming, advanced elicitation, party mode |
| Tasks | `core/tasks/`: adversarial review, edge-case hunter, editorial review (prose + structure), shard doc, index docs, help |
| Manifests | `_config/`: agent, workflow, task, skill and file manifests the agents read on activation |

To upgrade, reinstall BMAD into a scratch folder and diff it against this one. Keep Sam and this README.
