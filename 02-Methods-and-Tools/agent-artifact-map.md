# Agent → Artifact Reference Map

> Source: PM Agent OS (Deepesh Kumar Gupta, Mar 2026) — adapted for PM Brain
> Use this to identify which agent type and artifact to invoke for a given work product.

---

## Full Agent Map

| Agent | Artifact Type | Use When |
|---|---|---|
| `discovery` | `problem_brief` | Diagnosing a funnel drop-off, sizing a user pain point |
| `research` | `research_summary` | Competitive research, market benchmarking |
| `market_competition` | `competitive_matrix` | Mapping competitor acquisition tactics |
| `strategy_roadmap` | `strategy_memo` | Quarterly roadmap planning, OKR alignment |
| `prd` | `prd` | Any feature going to engineering |
| `ux_flow` | `ux_spec` | Signup flow, onboarding redesign, portal UX |
| `feasibility_architecture` | `tech_brief` | Pre-engineering feasibility check |
| `execution_planning` | `delivery_plan` | Sprint planning, launch sequencing |
| `analytics_experiment` | `experiment_plan` | A/B tests, funnel experiments, activation tests |
| `qa_test` | `qa_suite` | Acceptance criteria, test cases |
| `launch` | `launch_plan` | Feature rollouts, ops change management |
| `post_launch_monitoring` | `health_report` | Weekly KPI pulse, post-launch retro |
| `product_ops` | `decision_log` | Logging product decisions (maps to existing decision-log rule) |
| `stakeholder_alignment` | `strategy_memo` | Exec updates, cross-functional alignment docs |
| `monetization_packaging` | `monetization_brief` | Pricing or incentive structure changes |
| `trust_safety_policy` | `safety_spec` | Verification policy, data handling rules |

---

## Pipeline Sequences

Use these chains for end-to-end initiative work. Each step's output becomes input for the next.

| Pipeline | Use When |
|---|---|
| `Discovery → Strategy → PRD` | New initiative — problem not yet framed |
| `PRD → UX → Feasibility` | Pre-engineering handoff — solution defined, needs spec |
| `Analytics → QA → Launch` | Shipping — experiment designed, ready to validate and go live |
| `Launch → Monitoring → Stakeholders` | Post-launch — shipped, now watch and communicate |

