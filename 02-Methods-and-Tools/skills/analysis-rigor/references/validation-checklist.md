# Validation Checklist

Run every applicable gate before you report. If a gate fails, the result is invalid. Debug it, don't footnote it.

## 1. Source

- [ ] Every number traces to a named file, tab, and column (or table and field).
- [ ] If the user named a source of truth, your figures reproduce from it. Report the match rate (e.g. "identical on 100% of rows").
- [ ] Each column name is quoted exactly, not paraphrased.

## 2. Grain

- [ ] One sentence per table: "one row = ___."
- [ ] Before summing a count across rows, ask whether the same entity can appear in more than one row. If it can and there's no ID, don't sum counts. Use max-across-rows as a labeled lower bound.
- [ ] Ratios computed on summed values: check them against row-level medians. They should be close if the double counting cancels.
- [ ] Clustered rows: if child rows share the parent's outcome (every seat inherits its account's renewal status), effective n is the number of parents, not the number of rows.
- [ ] Reconciliation: parts that should partition a whole sum exactly to the whole.

## 3. Field semantics

- [ ] **State or event?** A column defined as "flagged and not yet resolved" falls when items get resolved, so it is not a cumulative count of flags.
- [ ] **Current state or history?** A "currently active" count isn't "ever activated." Check whether reopenings are netted out.
- [ ] **What does missing or zero mean?** An item with no activity is often one that was already resolved, not one that failed. Check status transitions first.
- [ ] **Stage order:** confirm the funnel order with the data owner. Stage names often suggest an order that isn't the real one.
- [ ] **Blocking codes:** if an item has zero qualifying units but a large rejected pool, check the rejection reasons before blaming supply. Catch-all reason codes deserve a look first.

## 4. Time

- [ ] **Censoring:** units that haven't reached the checkpoint yet can't count against it. Exclude them, or make every checkpoint use the same eligible population.
- [ ] **Undated totals:** lifetime counts favor older units, which had more time to accumulate. Use timestamps.
- [ ] **Snapshot vs. flow:** a current inventory that differs from weekly arrivals is a stock-versus-flow difference, not an error.

## 5. Claim

- [ ] Thresholds were set before looking, or they're shown as disjoint buckets with the full distribution.
- [ ] The comparison group excludes the bucket being tested (compare against the complement, not against an overall baseline that includes the bucket).
- [ ] Every predictor you report has variance (not mostly zeros).
- [ ] Every null is phrased with its detectable effect size (see `power-and-design.md`).
- [ ] Caveats are testable in this dataset, or labeled as limitations.
- [ ] Robustness checked where it matters: drop one segment at a time, trim outliers, drop the zero cell, bootstrap.
