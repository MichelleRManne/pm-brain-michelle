# /navigate

Find the right framework or phase for your situation. Your entry point when you know the problem but not the approach.

## What Claude does

1. **Asks 1–2 diagnostic questions** if your situation isn't clear
2. **Routes you to the right phase** in `02-Methods-and-Tools/`
3. **Recommends 1–2 frameworks** with a reason why each fits your situation
4. **Points to exact files** — framework guide + template
5. **Tells you where to save your work** (usually `04-Initiatives/`)

## Routing logic

| Your situation | Phase | Where to go |
|---|---|---|
| Don't know what to build / need customer insight | Discovery | `02-Methods-and-Tools/2.2-Discovery/` — research, JTBD, opportunity assessment |
| Need direction or strategy | Strategy | `02-Methods-and-Tools/2.1-Strategy/` — foundations, OKRs, roadmap, prioritization |
| Ready to specify and build | Execution | `02-Methods-and-Tools/2.3-Execution/` — PRD, personas, metrics |
| Need to align stakeholders or communicate | Communication | `02-Methods-and-Tools/2.4-Communication/` — one-pagers, agendas, stakeholder management |
| Stuck or overwhelmed | Foundations | `02-Methods-and-Tools/2.0-Foundations/` — mental models, self-reflection |
| Starting something new | → use `/start` | |
| Too many priorities | Prioritization | `02-Methods-and-Tools/2.1-Strategy/2.1.2-Strategic-Execution/4-Prioritization/` → use `/focus` |

Reference: `02-Methods-and-Tools/0-template-finder.md`

## Output

- Your current phase (strategy / discovery / execution / communication / foundations)
- Primary framework path with file pointers
- 1–2 supporting frameworks
- Where to save your work

## When to use

- When you have a situation but don't know which framework applies
- When you're new to a type of problem (e.g. first time doing an opportunity assessment at a new company)
- When you've finished a braindump and need to structure next

## Related commands

- `/braindump` — if you haven't thought it through yet, start here first
- `/framework` — once you know the phase, to match to a specific template
- `/start` — if this is a new initiative
- `/focus` — if the issue is too many competing priorities
