# /exec-review

Pressure-test a PRD, strategy doc, readout, or proposal from an operations-minded executive's point of view before it goes to leadership.

## What Claude does

1. Loads the persona and principles in `00-Meta/agents/exec-reviewer.md`.
2. Checks `01-Company-Context/1.1-Stakeholder-Avatars/` for an avatar of the executive you're presenting to and layers in their stated priorities. The avatar wins wherever it disagrees with the defaults.
3. Asks you to paste the document or point to the file.
4. Names the hard problem, asks 2–3 uncomfortable questions, checks the metrics against the reporting rules (outcome metric up front with a baseline and time to signal, inputs as diagnostics only), and asks for the machine mapping if a solution is proposed.
5. Returns a verdict: **ready** / **one more pass** (with the fixes) / **not ready** (with the missing evidence).

## When to use

- The day before a leadership review
- When a proposal looks expensive and you need to tie it to an outcome metric
- When you suspect you're reporting activity instead of results

## Related

- `/pm-review` — quick quality check during drafting
- `/evaluate` — full rubric check against the framework's evaluation file
