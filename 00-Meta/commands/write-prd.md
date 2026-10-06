# /write-prd

> **Uses the optional PM-Skills library.** If `02-Methods-and-Tools/pm-skills/skills/` does not exist, tell the user it can be installed with `git clone https://github.com/deanpeters/Product-Manager-Skills 02-Methods-and-Tools/pm-skills` (Dean Peters, CC BY-NC-SA 4.0), then fall back to the built-in PM Brain frameworks in `02-Methods-and-Tools/2.3-Execution/2.3.4-PRD/` (framework, template, evaluation). Do not improvise the PM-Skills content from memory.

Generate a PRD for: $ARGUMENTS

Read and chain these skills in sequence:
1. `02-Methods-and-Tools/pm-skills/skills/problem-statement/SKILL.md` — Define the problem context
2. `02-Methods-and-Tools/pm-skills/skills/proto-persona/SKILL.md` — Align user assumptions
3. `02-Methods-and-Tools/pm-skills/skills/prd-development/SKILL.md` — Build the full document
4. `02-Methods-and-Tools/pm-skills/skills/user-story/SKILL.md` — Draft initial stories
5. `02-Methods-and-Tools/pm-skills/skills/user-story-splitting/SKILL.md` — Split larger items

Checkpoints:
- State the hypothesis (IF / THEN / BECAUSE) before drafting. If it cannot be completed with evidence, send the user back to `/braindump` or `/discover`.
- Write the final document in `02-Methods-and-Tools/2.3-Execution/2.3.4-PRD/2-prd-template.md` format, filling Section 3 (Assumptions & Confidence Levels) before Section 4 (Goals & Metrics).
- Label claims `[EVIDENCE]` or `[ASSUMPTION]`; put missing data under Open Questions instead of inventing it.
- Validate scope boundaries before writing requirements
- Keep success criteria measurable and tied to outcome metrics
- Ensure at least one anti-pattern is called out in risks

Complete each phase before moving to the next. Offer /plan-roadmap when PRD is done.
