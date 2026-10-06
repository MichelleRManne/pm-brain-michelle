# Toolchain Smoke Test

## Purpose

Make sure the commands and workflows work before you need them for real. The failure this prevents is reaching for a tool on a live problem and finding it broken.

## Pick two use cases from the new role

- **Use case A:** something you'll actually do in week 1 (e.g. Day 1 intake prep).
- **Use case B:** a real, specific business problem with a known metric. For example: "X% of users who start onboarding never reach first value." Pick something specific enough that generic output would be obvious.

---

## Phase 1 — Before Day 1 (personal machine)

| # | What to run | Surface | Input | Pass looks like | JTBD |
|---|---|---|---|---|---|
| 1 | `/braindump` | Claude Code | Your Day 1 situation | Asks 3–5 questions. Does NOT suggest a framework until you say you're ready. | 2 |
| 2 | `/start` | Claude Code | "Starting as [role] at [company]" | Runs a braindump first, then goes through the phases in order | 2 |
| 3 | Hypothesis gate | Claude Code | Use case B, then ask for a PRD | Asks for IF / THEN / BECAUSE first, and pushes back if there's no baseline or evidence | 2, 3 |
| 4 | `/discover` | Claude Code | Use case B | Produces a discovery plan, prioritized assumptions, and an experiment backlog. Doesn't jump to solutions. | 1, 2, 3 |
| 5 | Parking lot | Claude Code | During test 4, say "park this" about a tangent | `[PARKED]` tag at the end of the response, entry in `07-Parking-Lot/`, and the workflow continues | 2 |
| 6 | `/write-prd` | Claude Code | Output from test 4 | Section 3 (Assumptions & Confidence) is filled before Goals, claims are labeled `[EVIDENCE]`/`[ASSUMPTION]`, and success criteria are measurable | 3, 7 |
| 7 | `/exec-review` | Claude Code | PRD from test 6 | Names the hard problem, flags any input metric in the headline, returns ready / one more pass / not ready | 7 |
| 8 | "talk to Sam" | Claude Code | "Which analysis tells me whether onboarding change X worked?" | Asks what question you're answering before naming a method, and flags metrics the change can move mechanically | 1, 6 |
| 9 | Decision logs | Claude Code | "log this decision", then "log observed decision" | One-line confirmations, entries in the right file, and the observed entry has a confidence level | 3 |
| 10 | `/braindump` | Claude desktop | Same input as test 1 | Same behavior as Claude Code. Commands trigger conversationally | 2 |

### Phase 1 failure flags

- `/braindump` jumps straight to frameworks → `CLAUDE.md` isn't being loaded
- A command behaves differently in two tools → instruction files have drifted. Commands should live only in `00-Meta/commands/`
- `/discover` output is generic → `01-Company-Context/` is empty (fill it first) or PM-Skills is missing (it should say so and fall back to built-in frameworks)
- "park this" is ignored → the parking lot rule isn't in effect

---

## Phase 2 — Week 1 (work laptop + approved connectors)

| # | What to run | Surface | Input | Pass looks like | JTBD |
|---|---|---|---|---|---|
| 11 | Tracker read | Claude Desktop | "List my projects and summarize the current sprint" | Returns real project names, sprint status, and ticket counts | 1, 6 |
| 12 | Wiki write | Claude Desktop | "Create a test page called Smoke Test, then delete it" | Page appears and is deleted cleanly | 7 |
| 13 | Monday Briefing | Cowork | Repo folder + tracker connector | Produces priorities and a parking lot nudge without you present | 1, 6 |

---

## Definition of done

**Minimum viable pass:** Tests 1–7 produce output you'd actually use, and tests 11–12 run without errors.
**Full pass:** All tests pass. You can run braindump → discovery → PRD → exec review → publish end to end.
