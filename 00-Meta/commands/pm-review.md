# /pm-review

Quick quality check on a draft artifact. Use this before /evaluate for a lighter-touch pass.

## What Claude does

1. **Identifies what's being reviewed**
   - Asks which artifact (PRD, opportunity assessment, one-pager, OKR, roadmap, stakeholder avatar, etc.)
   - Asks you to paste the doc or point to the file path

2. **Runs Quick Quality Checks**
   - Finds the relevant framework file in `02-Methods-and-Tools/` (`1-*-framework.md`)
   - Runs the quick quality checks defined there — typically 5–8 questions
   - Flags anything that doesn't pass with a specific suggestion, not just "improve this"

3. **Checks PM-Brain alignment**
   - Is the artifact using the right template structure? (`02-Methods-and-Tools/0-Template-Structure/`)
   - Does it reflect what's in `01-Company-Context/` — or is it making assumptions that contradict what you know?
   - Is the "why" clear, or is it jumping to solution?

4. **Returns a short verdict**
   - Ready to share / needs one more pass / needs significant rework
   - Specific list of what to fix before sharing

## Output

- Quick quality check results (pass/flag per criterion)
- PM-Brain alignment notes
- Verdict: ready / one more pass / rework
- Specific fixes needed (not vague feedback)

## When to use

- After drafting any artifact before sharing it with stakeholders
- When you've iterated on a doc and want a fast sanity check
- When you're unsure if something is "done enough"

## Difference from /evaluate

- `/pm-review` — fast, lightweight, catches obvious gaps. Use before sharing internally.
- `/evaluate` — deep quality check using full evaluation rubrics. Use before major reviews or exec presentations.

## Related commands

- `/evaluate` — when you need the full rubric check
- `/framework` — if review reveals you used the wrong framework
- `/braindump` — if review reveals the "why" is unclear and you need to think it through again
