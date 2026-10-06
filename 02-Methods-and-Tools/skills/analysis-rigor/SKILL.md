---
name: analysis-rigor
description: Use for any analysis of real data — queries, exports, spreadsheets, funnel or cohort readouts, "does X predict Y", sample size or power questions, or any deliverable that reports counts, rates, or a metric moving. Enforces source naming, grain checks, metric validity, honest nulls, and outcome-first reporting.
metadata:
  author: Michelle Manne
  version: 1.0.0
  category: workflow
  tags: [analysis, metrics, data-quality, experiment-design, reporting]
---

# Analysis Rigor

Rules for analysis that a skeptical exec or data partner can't easily knock down. Each rule here was learned by getting it wrong once.

## Installation

- **Claude Code:** copy this folder to `~/.claude/skills/analysis-rigor/` (all projects) or `<repo>/.claude/skills/analysis-rigor/` (one project).
- **Claude desktop:** save it as a skill in Settings, or ask Claude to "save this folder as a skill."
- **Other agents:** pass the `SKILL.md` path directly.

## Required workflow

1. **Pin the question and the sources.** Restate the question in one sentence. List every source by **file, tab, and column** (or table and field). Ask which one is the source of truth if two could answer it. When the user says "use only X for Y," treat it as a **precedence rule** (X wins for Y), not a whitelist. If you're about to leave a source out, say what and why before you build.
2. **Establish the grain.** For every table, state what one row represents (person, order, line item, event, snapshot). Read [validation-checklist.md](references/validation-checklist.md) → Grain before you sum anything.
3. **Check the metric is valid for the decision.** Read [metric-validity.md](references/metric-validity.md). If the change being evaluated can move the metric mechanically, stop and propose a metric that stays the same when the parameter changes.
4. **Check state vs. event fields.** Is a column current state or a cumulative log? Can a record leave the numerator? Does "missing" mean failed, or already resolved? Check the transitions before you attribute failure.
5. **Run the analysis, then the gates.** Run every applicable gate in [validation-checklist.md](references/validation-checklist.md). If a grain, reconciliation, censoring, or threshold gate fails, the result is invalid. Fix it before you report.
6. **Size the claim to the evidence.** For "does X separate/predict Y," read [power-and-design.md](references/power-and-design.md). A null from an underpowered test means "too small to detect," not "no effect."
7. **Report.** Follow the reporting rules below. For spreadsheet deliverables, read [spreadsheet-delivery.md](references/spreadsheet-delivery.md).

## Non-negotiable rules

- **Name the file, tab, and column every time** you report a number. Never write "your tab," "the corrected CSV," or "the export." When sources disagree, label one PRIMARY and the other REFERENCE ONLY, and say in one line why they differ. If the user names a source of truth, reproduce your figures from it and report the match rate.
- **Don't assert a caveat the data in front of you can't test.** If there's no ID column, say "this export has no ID, so I can't check for duplicates" rather than claiming duplicates exist. Never carry a grain or de-duplication concern over from a different export. Look for an indirect test before you raise a caveat at all.
- **Counts summed across child rows aren't headcounts.** Ratios usually survive summing because the double counting cancels. Counts don't. Report max-across-children as a labeled lower bound, or get a real ID.
- **Don't cross construct boundaries.** A measure taken before a filter can't confirm or refute a claim about what happens after it. Volume before a filter and inventory after it are different quantities.
- **Thresholds chosen after looking are artifacts.** If a top "N or more" bucket separates, rebuild as disjoint buckets. If the pattern isn't monotonic, don't report the threshold.
- **Don't report a stage that has restriction of range.** If most units sit at zero for a predictor, a null for that predictor is untestable, not negative.
- **Separate fact, inference, and limitation.** Label `[EVIDENCE]` / `[ASSUMPTION]`. Observational results support "X is the strongest early predictor of Y," not "X causes Y."
- **When corrected, take the correction.** Then check whether it changes the result, and say plainly if it doesn't.

## Reporting defaults

- **Lead with the outcome metric and its baseline**, then the expected direction and how soon the signal will show. Input metrics (volume, adoption, usage) go in a diagnostic section.
- **State the grain and n next to every number.** Identify units by name or ID, never by a shared attribute ("the West region account" is ambiguous when there are many).
- **Write thresholds as "not enough," not "none."** Most thresholds are minimums.
- Keep each finding to: what the data shows, how sure we are, what would change the conclusion, and the next analysis.

## References

| File | Read when |
|---|---|
| [validation-checklist.md](references/validation-checklist.md) | Before reporting any number |
| [metric-validity.md](references/metric-validity.md) | Choosing or defending a success metric |
| [power-and-design.md](references/power-and-design.md) | Any "does X predict/separate Y" or "how long do we need to run this" |
| [spreadsheet-delivery.md](references/spreadsheet-delivery.md) | Building a workbook with live formulas, or delivering to Google Sheets |
