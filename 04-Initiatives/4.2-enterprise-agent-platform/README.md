# 4.2 – Enterprise Agent Platform

Reference specs for an extensible enterprise workflow agent: a governed workbench where employees delegate multi-step work across code, documents, data systems, and internal tools. It is a runtime around the model, with tools, skills, extensions, integrations, session persistence, approvals, and verification.

Both documents are written as **non-proprietary reference specs**. They describe a reusable pattern and contain no company code, prompts, schemas, or data.

## Files

| File | What it is | Audience |
|---|---|---|
| [`2026-10-06-enterprise-agent-platform-prd.md`](2026-10-06-enterprise-agent-platform-prd.md) | Product requirements: vision, users, JTBD, scope, capability areas, representative workflows, FRs/NFRs, MVP, metrics, risks, open questions | Product, engineering and platform leaders, AI enablement |
| [`2026-10-06-enterprise-agent-platform-technical-spec.md`](2026-10-06-enterprise-agent-platform-technical-spec.md) | Reference architecture: interface layer, session runtime, model runtime, agent loop, tool / skill / extension systems, context builder and compaction, session persistence, integration adapters | Engineering leaders, platform engineers, security architects |

## How this connects to the rest of the repo

- **Skills system (PRD §8.3, spec §7):** `02-Methods-and-Tools/skills/analysis-rigor/` is a working example of the skill pattern the spec describes: a SKILL.md with metadata, a required workflow, validation gates, and reporting defaults.
- **Context management (PRD §8.6, spec §9):** the checkpoint protocol (`checkpoints/`) and `/broker-audit` are the manual version of compaction and context assembly.
- **Verification before completion (FR9):** the same rule as the `[EVIDENCE]` / `[ASSUMPTION]` labeling in `CLAUDE.md` and the validation gates in `analysis-rigor`.

## Suggested next steps

- [ ] Run `/exec-review` on the PRD. Check that §14 Metrics leads with an outcome metric that has a baseline. Adoption and usage counts belong in the diagnostic section.
- [ ] Add an Assumptions & Confidence pass, as in Section 3 of `02-Methods-and-Tools/2.3-Execution/2.3.4-PRD/2-prd-template.md`, before treating the MVP scope as fixed.
- [ ] Turn §16 Open Product Questions into entries in a `decisions.md` file in this folder (create it on first use) as they get answered.
