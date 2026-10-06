# JTBD → Stack Mapping

## Purpose
Maps the toolkit's seven jobs (`JTBDs.md`) to the parts of the stack. Use it to decide whether a new tool is really needed or whether something you already have covers the job.

---

## The stack
- **PM Brain (this repo)** — context, orchestration, frameworks, decision logs
- **Commands** (`00-Meta/commands/`) — braindump-first workflows, plus structured PM work that can use PM-Skills
- **Agents** (`00-Meta/agents/`) — Sam (data analyst), exec reviewer, context broker. One at a time
- **Skills** (`02-Methods-and-Tools/skills/`) — `analysis-rigor` for any work with real data
- **Claude desktop (Cowork)** — scheduled and on-demand tasks (`cowork-setup-guide.md`)
- **Connectors** — issue tracker, wiki, BI. **Only once the company has approved them**

---

## Mapping

| # | Job | Covered by | Typical dependency |
|---|---|---|---|
| 1 | Data synthesis & insights | Sam + `analysis-rigor` + nightly `.incoming/` synthesis | Data source and access confirmed (week 1 email to analytics) |
| 2 | Structured thinking | PM Brain Coach, hypothesis gate, `/navigate`, `/framework` | None |
| 3 | Requirements & change management | `/write-prd` (PRD v2), implementation brief, decision logs, requirements-sharding task | Tracker connector approval |
| 4 | Task partners | Agents in `00-Meta/agents/` | None |
| 5 | Prototyping | Claude artifacts / HTML mockups | Design tokens from the UX designer |
| 6 | KPI tracking & analysis | `05-KPIs-and-Data/kpi-framework.md` + Friday KPI Pulse | Confirmed data source and format |
| 7 | Exec artifacts | Exec Brief Generator, `/exec-review`, `CLAUDE.md` output defaults | None |

---

## Gaps to check in each new role
- [ ] Which connectors are approved, and which are blocked?
- [ ] Is the core funnel instrumented, and is there one source of truth for it?
- [ ] Does the company have an AI usage policy that restricts what can go into prompts?
