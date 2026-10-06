# /framework

Match your braindump or situation to the right framework and template, then execute step-by-step.

## What Claude does

1. **Confirms your situation**
   - Restates what it thinks you're dealing with (strategy / discovery / execution / communication)
   - Asks 1–2 clarifying questions if anything is ambiguous

2. **Proposes candidate frameworks**
   - Suggests 1–2 frameworks from `02-Methods-and-Tools/`
   - Explains *why each fits your situation* — not just what it is

3. **Shows you exactly where to go**
   - Points to the framework guide (`1-*-framework.md`)
   - Points to the template (`2-*-template.md`) if one exists

4. **Runs preflight for non-trivial docs**
   - For PRDs, strategy docs, opportunity assessments, roadmaps: asks 2–3 preflight questions before drafting
   - "Why this, why now?" / "Who is this for?" / "What do you know vs. guess?"
   - Reference: `02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/2-product-sense-prompts.md`

5. **Moves into execution mode**
   - Once framework is picked, guides step-by-step through it
   - Pulls from your braindump where possible — doesn't make you repeat yourself

## When to use

- After `/braindump` when you're ready to structure
- When you know roughly what you need (e.g. "I need to do prioritization") but want guidance on which approach fits
- Before drafting any significant artifact

## Output

- Confirmed situation summary
- Recommended framework(s) with rationale
- File pointers (framework + template)
- Preflight questions (for major artifacts)
- Step-by-step execution once framework is confirmed

## Related commands

- `/braindump` — do this first if you haven't thought it through yet
- `/navigate` — if you're not sure which phase you're in
- `/pm-review` — after you've drafted, to check quality
- `/evaluate` — for deep quality check before sharing
