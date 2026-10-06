# Power and Design

## Phrase nulls with what they could detect

With n units and a baseline rate p, a two-group comparison at 80% power and α = 0.05 can only detect differences of roughly:

`MDE ≈ 2.8 × sqrt(2 · p(1−p) / n_per_group)`

So "nothing separates" usually means "no group differs by enough to detect." Say the detectable effect size out loud (e.g. "with 200 units split evenly and a 30% baseline, this can only see differences of about 18 points or more").

## Calendar math turns power into a decision

Required n ÷ observed intake per day = how long you have to wait. If detecting a 10-point effect at the outcome level would take months of intake, the outcome metric works as a **scorecard**, not a **learning instrument**. Anything you need to learn in days has to be measured at a faster, higher-volume step (a handoff).

## Clustering and the design effect

When the analysis unit is nested in a parent (sessions within users, users within accounts):

`DE = 1 + (m − 1) · ICC`, where `effective n = total rows ÷ DE`

- If every child shares its parent's outcome (ICC = 1), effective n equals the number of parents. Extra rows add nothing.
- Measuring at a lower grain only helps if the outcome **varies within the parent**.
- Don't assume an ICC. Estimate it from a first pull, then read the required n off a table of ICC values.

## Bucket tables vs. models

Many small bucket cells with interval estimates fragment the sample. Prefer a single model (logistic regression with the predictor as continuous, controls for the main confounders such as segment and size, standard errors clustered on the parent or random intercepts). Then check robustness: leave one segment out, trim the top 5%, drop the zero cell, run a permutation test, and bootstrap the confidence interval.

## Heterogeneity is often the biggest problem

If outcome rates differ across segments (markets, regions, cohorts) by more than the effect you're looking for, control for segment or stratify before you read anything else.

## Restriction of range

If most units sit at zero for a predictor, the test can't see anything. Report that predictor as **untestable**, not null.

## Observational limits

A predictor that survives controls is "the strongest early predictor," not a cause. Name the confounder you can't rule out (e.g. some units are easier to fulfill to begin with). Then name the lever that would test causality directly, and when it would read.
