# /evaluate

Deep quality check on an artifact using PM-Brain's full evaluation rubrics. Use before major reviews or exec presentations.

## What Claude does

1. **Identifies what to evaluate**
   - Artifact options: PRD, opportunity assessment, north star, one-pager, OKR, roadmap, stakeholder avatar, or any other artifact
   - Asks you to paste the doc or point to the file path

2. **Runs full artifact evaluation**
   - Finds the relevant evaluation file: `02-Methods-and-Tools/[section]/3-*-evaluation.md`
   - Walks through Quick Quality Checks first
   - Then runs deeper evaluation questions from the `3-*-evaluation.md` file
   - Scores or flags each criterion explicitly

3. **Cross-checks against context**
   - Does the artifact reflect the company's actual context from `01-Company-Context/`?
   - Does it align with KPI definitions in `05-KPIs-and-Data/kpi-framework.md`?
   - Are claims labeled `[EVIDENCE]` or `[ASSUMPTION]`, and does the PRD's Assumptions & Confidence section match what the evidence supports?
   - Are stakeholder assumptions consistent with the avatars in `01-Company-Context/1.1-Stakeholder-Avatars/` and the politics map in `01-Company-Context/1.2-Organization-Survival/`?

4. **Returns a structured verdict**
   - What's strong — don't change it
   - What needs improvement — specific fixes with suggested language
   - What's missing — gaps that would get flagged in a review
   - Overall readiness: ready for exec / needs one more pass / not ready

## Evaluation files by artifact type

| Artifact | Evaluation file |
|---|---|
| PRD | `02-Methods-and-Tools/2.3-Execution/2.3.4-PRD/3-prd-evaluation.md` |
| Opportunity Assessment | `02-Methods-and-Tools/2.2-Discovery/2.2.4-Opportunity-Assessment/3-opportunity-assessment-evaluation.md` |
| OKR | `02-Methods-and-Tools/2.1-Strategy/2.1.2-Strategic-Execution/1-OKR/3-okr-evaluation.md` |
| Roadmap | `02-Methods-and-Tools/2.1-Strategy/2.1.2-Strategic-Execution/2-Roadmap/3-roadmap-evaluation.md` |
| North Star | `02-Methods-and-Tools/2.1-Strategy/2.1.2-Strategic-Execution/3-North-Star/3-north-star-evaluation.md` |
| One-Pager | `02-Methods-and-Tools/2.4-Communication/2.4.3-One-Pagers/3-one-pager-evaluation.md` |

## Output

- Criterion-by-criterion evaluation (pass / flag / fail)
- Cross-context alignment check
- Specific fixes with suggested language where possible
- Overall readiness verdict

## When to use

- Before sharing a PRD with engineering
- Before an exec review or roadmap presentation
- Before publishing to your team wiki
- When something feels off but you can't pinpoint why

## Difference from /pm-review

- `/pm-review` — fast lightweight check, catches obvious gaps, use before sharing internally
- `/evaluate` — full rubric, use before major reviews or anything going to exec or engineering

## Related commands

- `/pm-review` — lighter-touch version for faster checks
- `/framework` — if evaluation reveals a structural problem with the approach
