# KPI Framework — [Company / Product Area]

**Status:** [Draft / Official as of YYYY-MM-DD, source: e.g. weekly business review]
**Owner:** [Name]
**Last verified against source dashboards:** YYYY-MM-DD

The agent reads this file whenever it writes metrics, so it can use the company's own definitions without asking again each session. Keep it short. Record definitions here and link to the dashboard for the values.

---

## Business goals (this year)

1. **[Goal]:** [Metric and target, e.g. "X at or below N"]
2. **[Goal]:** [Metric and target]
3. **[Goal]:** (Metric TBD) — [what it is meant to capture]

---

## North star

> **[Metric]** — [exact definition, including the event that counts and the time window]
>
> *Why this metric:* [EVIDENCE] [Why it is the constraint or best proxy for value]
> *Leading indicator:* **[Metric]** — [what it predicts and how early]

---

## Outcome vs. input metrics

| Metric | Type | Use it for |
|---|---|---|
| [Portfolio / outcome metric] | **Headline** | What leadership reports on. Always shown with a baseline. |
| [Input metric, e.g. adoption, treatment usage] | Diagnostic | Explains *why* the headline moved or didn't. Never the headline. |

**Validity check for any success metric.** If a change you are measuring can raise the metric mechanically, the metric cannot tell you whether the change worked. For example, loosening a lead-qualification rule raises "qualified leads" without closing a single deal. Use a metric that stays the same when the parameter you are changing moves. See `02-Methods-and-Tools/skills/analysis-rigor/SKILL.md`.

---

## Funnel — standardized stage mapping

Map the business's stage names to the system's stage names once. Stage names in different tools rarely line up, and the order of stages is not always what the names suggest, so confirm it with the data owner.

| Level 1 (Milestone) | Level 2 (Stage) | Level 3 (Action) | System stage name | Plain-language explanation |
|---|---|---|---|---|
| [Milestone] | [Stage] | [Action code] | [Exact system value] | [What actually happened] |

---

## Reporting conventions

- Every KPI callout includes **trend direction** and a one-line **"so what."**
- Lead with the outcome metric and its baseline. Then state the expected direction and **how soon** the signal will show.
- State the **grain** next to every count (per order, per line item, per person). A count summed across child rows is not a headcount.
- Data sources and dashboard links: [list, with which one is the source of truth when they disagree]
