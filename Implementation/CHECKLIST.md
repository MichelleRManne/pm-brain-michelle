# Implementation Checklist — New Role Setup

> **How to use:** Copy this file at the start of a new role and check items off as you go. When you ask "where am I on setup?", this file is the source of truth. Scheduled-task instructions live in `cowork-setup-guide.md`.
>
> **Automation philosophy:** Hold off on background automations until Month 2. You need real working context before you can design automation that's worth having.

---

## Phase 0 — Before Day 1 (personal machine, no work accounts)

- [ ] **Decide where company content will live.** This repo is the toolkit. Filled-in company context, initiative docs, and data belong in a private repo on the employer's GitHub or on employer systems. Don't push them to this personal repo (the `.gitignore` guard catches the common cases).
- [ ] Clone this repo for the new role; clear out last role's `Active context` in `CLAUDE.md`
- [ ] Fill in the "Who I am" block in `CLAUDE.md` (role, scope, team)
- [ ] Brain-dump everything you know about the company into `.incoming/`, then distribute it into `01-Company-Context/` with gaps flagged
- [ ] Draft stakeholder avatars for your manager and one or two key partners (`01-Company-Context/1.1-Stakeholder-Avatars/`, using the template in `02-Methods-and-Tools/2.4-Communication/2.4.8-Stakeholder-Avatars/`)
- [ ] Tailor `day1-intake.md` for engineering, ops, and UX
- [ ] Email the head of analytics three questions: What's the BI tool? Is self-serve access realistic at my level? Is the core funnel instrumented, and where does it live?
- [ ] Optional: clone PM-Skills into `02-Methods-and-Tools/pm-skills/`
- [ ] Run smoke test Phase 1 (`Smoke-Test.md`) to check commands work before you need them

---

## Phase 1 — Week 1

**Approvals (do these first; they gate everything else)**
- [ ] Ask IT and your manager which AI tools are approved (enterprise agreement, data-handling terms such as a BAA if the company is in healthcare)
- [ ] Get written approval to connect Claude to company systems (issue tracker, wiki, BI). Record the decision with `/log-decision`
- [ ] Ask what the chat retention policy is. If messages expire (for example after 30 days), `/log-observed` is how you keep other people's decisions

**Tool setup (work laptop)**
- [ ] Set up the work repo for company content (see Phase 0) and connect it in Claude Desktop
- [ ] Authenticate approved connectors → test read, then a reversible write (create and delete a test page)
- [ ] Create a Claude Project for the role → add `CLAUDE.md` as project instructions
- [ ] Run Day 1 intake conversations → raw notes into `.incoming/`
- [ ] Run smoke test Phase 2

**Context**
- [ ] Fill `01-Company-Context/` with what you learned this week
- [ ] Fill `05-KPIs-and-Data/kpi-framework.md` with the official goals and metric definitions, and note which dashboard is the source of truth
- [ ] Map funnel stage names to system stage names, and confirm the order with the data owner (don't infer it from the names)
- [ ] Collect the feature inventory, architecture doc, integrations list, and data dictionary
- [ ] Add links to external storage for raw data (data stays out of git)

---

## Phase 2 — Weeks 2–3

- [ ] Write the intake synthesis: what the teams agree on, where they contradict each other, what surprised you, and what you expected to hear but didn't
- [ ] Run the first full workflow on a real problem: `/braindump` → hypothesis gate → `/discover` → `/write-prd` → `/exec-review`
- [ ] Set up the Monday Morning Briefing and Nightly Note Synthesis (if connectors are approved)
- [ ] Collect operational SOPs from the teams you depend on
- [ ] Run a stakeholder pre-mortem before your first leadership review

---

## Phase 3 — Month 2 (evaluate, expand, automate)

- [ ] Review the parking lot → promote the best ideas into initiatives
- [ ] Decide whether there is enough data volume for trend analysis; if so, design how it accumulates
- [ ] Set up the Friday KPI Pulse once the data source and format are confirmed
- [ ] Set up Sprint Retro Prep once the retro cadence is confirmed with engineering
- [ ] **Promote lessons into the toolkit.** Anything you learned about how you work (writing style, analysis rules, exec preferences) that lives only in Claude's memory or a work repo should be written into `CLAUDE.md` or `02-Methods-and-Tools/skills/` here, with company specifics removed

---

## Blocked / Waiting

| Item | Blocked on |
|---|---|
| [Item] | [Approval, data source, or person] |
