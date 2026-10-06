# Metric Validity

## The core test

**Could the change you're evaluating raise this metric without improving the outcome?** If yes, the metric can't tell you whether the change worked.

Common ways it fails:

- **Volume-driven scores.** Any score that combines per-unit chances (for example `1 − ∏(1 − pᵢ)`) rises with the number of units, even when each unit is weak. Check the formula. If many weak units can add up to a high score, the score is mostly a headcount in disguise.
- **Loosening a filter.** Relaxing a qualification rule or lowering a bar mechanically adds qualifying units and lifts any metric built on their count. The outcome (conversions, revenue, retention) doesn't have to change at all.
- **Two "independent" axes that aren't.** If one input feeds the other by construction, agreement between them isn't confirmation.
- **Count as a supply measure.** A count of qualifying units is the output of a filter applied to a denominator you may not be able to see (hard rejections may never create rows). A low count isn't evidence of a sourcing problem.

## What to use instead

- An **outcome** measured downstream of the parameter you're changing (conversion rate per unit, time-to-convert, a paid or completed event).
- If the outcome is too slow, a **handoff rate** at the step the change targets (qualified → contacted, offer → accepted), measured on units that would exist either way.

## How to say it

- "This score mostly reflects how many qualifying leads an account has, so loosening the rule will raise it whether or not anything converts. Use conversion rate per account to judge the change."
- Call a volume-driven score a **triage list**, not a measurement instrument.

## Scorecard vs. learning instrument

A metric can be good for ranking what to look at today and still be useless for learning whether a change worked. Say which job the metric is doing.
