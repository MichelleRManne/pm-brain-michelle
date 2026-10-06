# Cowork Setup Guide
Scheduled and on-demand tasks for the PM Brain toolkit

> **Before you start:** Get written approval to connect Claude to company systems (issue tracker, wiki, BI) in week 1. Without it, every task below that reads the tracker or writes to the wiki stays blocked, sometimes for months. Then authenticate the connectors in Claude Desktop → Settings → Connectors (e.g. Atlassian for Jira + Confluence).
>
> **General setup pattern:** Cowork tab → New Task → Name it → Write instructions → Set schedule or leave as on-demand → Save.

---

## Prerequisites

1. Claude Desktop downloaded and open
2. Cowork tab visible (left sidebar)
3. This repo folder connected, so tasks can read `00-Meta/commands/`, `02-Methods-and-Tools/skills/`, and your context files
4. Issue tracker / wiki connectors authenticated and **approved by the company** (see above)
5. Optional: PM-Skills cloned into `02-Methods-and-Tools/pm-skills/`

---

## Scheduled Tasks

These run automatically at the configured time while Claude Desktop is open.

---

### Monday Morning Briefing
**Schedule:** Every Monday, 7am

**What it reads:**
- Issue tracker: current sprint status (via the issue-tracker connector)
- Repo: any files added to `.incoming/` in the past week
- Repo: `07-Parking-Lot/parking-lot.md`

**What it outputs:**
- This week's priorities based on sprint + notes
- Open decisions that need your attention
- Items to flag for exec team this week
- Parking lot items added last week — nudge to promote, keep, or dismiss each

**Instructions to paste into Cowork:**
```
You are my PM Brain assistant. Every Monday morning, produce my weekly briefing.

1. Read the current sprint status from the issue tracker via its connector. Summarize: what's in progress, what shipped last week, what's at risk.
2. Read any files added to the .incoming/ folder in the past 7 days. Extract themes, open questions, and anything that should inform priorities this week.
3. Read 07-Parking-Lot/parking-lot.md. List any items added in the past 7 days and suggest a disposition for each: promote to initiative / keep / archive.
4. Produce a briefing with four sections: (1) This Week's Priorities, (2) Open Decisions Needing Attention, (3) Flag for Exec Team, (4) Parking Lot Nudge.

Keep it concise. This should be scannable in under 3 minutes.
```

**Setup steps:**
1. Cowork → New Task → Name: "Monday Morning Briefing"
2. Paste instructions above
3. Set inputs: your repo folder + issue-tracker connector
4. Schedule: Weekly, Monday, 7:00am
5. Output: save to repo or send to notification (your preference)

---

### Nightly Note Synthesis
**Schedule:** Nightly (run only if new files exist in `.incoming/`)

**What it reads:**
- Any new files in `.incoming/` since last run

**What it outputs:**
- Structured summary of each file
- Filed to the appropriate initiative under `04-Initiatives/` (or flagged for manual routing if unclear)
- Themes extracted → appended to relevant parking lot or initiative doc
- Suggested follow-up question for the next conversation on this topic

**Instructions to paste into Cowork:**
```
You are my research synthesis assistant. Each night, process any new files in the .incoming/ folder.

For each new file:
1. Identify what type of content it is: interview notes, meeting notes, data observations, or other.
2. Extract key themes, insights, and open questions.
3. Determine which initiative it belongs to (check 04-Initiatives/ folder names). If it clearly belongs to one initiative, save a synthesis summary to 04-Initiatives/[initiative-name]/research/. If unclear, save to 03-Research-Artifacts/ and flag for manual routing.
4. If any item should go to the parking lot, append it to 07-Parking-Lot/parking-lot.md with today's date.
5. Suggest one follow-up question based on the content.

Do not delete or modify the original file in .incoming/. Synthesis only — I will clean up the incoming folder herself.
```

**Setup steps:**
1. Cowork → New Task → Name: "Nightly Note Synthesis"
2. Paste instructions above
3. Set input: watch `.incoming/` folder for new files
4. Schedule: Nightly, 11pm (or whenever you're unlikely to still be working)
5. Condition: only run if new files detected since last run

---

### Friday KPI Pulse
**Schedule:** Every Friday, 4pm
**Status: BLOCKED** — configure once the data source is confirmed (usually week 1–2)

**What it reads:**
- KPI data export (source TBD: CSV from the BI tool or an internal dashboard)
- `05-KPIs-and-Data/kpi-framework.md` for metric definitions and thresholds

**What it outputs:**
- Week-over-week delta for top 5 metrics
- Any metric outside defined threshold flagged in amber/red
- 3-sentence narrative summary ready to paste into Friday stakeholder update

**Instructions template (fill in data source once confirmed):**
```
You are my KPI analyst. Every Friday afternoon, produce the weekly KPI pulse.

1. Read the latest KPI data from [DATA SOURCE — fill in after Week 1].
2. Read 05-KPIs-and-Data/kpi-framework.md for metric definitions and targets.
3. Calculate week-over-week delta for each metric in the framework.
4. Flag any metric more than [X]% outside target in amber (watch) or red (act).
5. Write a 3-sentence narrative: what moved, what's worth noting, what needs attention next week.

Format: metrics table first, narrative below. Keep total length under one page.
```

---

### Sprint Retro Prep
**Schedule:** Bi-weekly, day before retro
**Status: Set up in Phase 3 once retro cadence is confirmed with engineering**

**What it reads:**
- Completed and incomplete tickets for the closing sprint (via the issue-tracker connector)
- Previous retro notes (if stored in repo)

**What it outputs:**
- What shipped, what slipped, what's carried over
- Recurring patterns across last 3 sprints (if data available)
- Draft retro agenda with data-grounded observations

**Instructions template:**
```
You are my retro prep assistant. The day before each sprint retro, produce a retro briefing.

1. Pull completed and incomplete tickets from the current sprint via the issue-tracker connector.
2. If previous retro notes exist in 06-Weekly-Ops/, read the last 2 retros for recurring patterns.
3. Produce: (a) what shipped, (b) what slipped and why (from ticket notes/comments), (c) any pattern appearing in multiple sprints, (d) suggested retro agenda — 3–4 discussion items max.

Be specific. The goal is to start the retro from facts, not memory.
```

---

## On-Demand Tasks

These are saved workflows you trigger manually when needed.

---

### Exec Brief Generator

**When to use:** After completing a PRD or strategy doc and before sharing with leadership.

**Input:** Path to a PRD, strategy doc, or discovery output in the repo.

**Output:** 1-page exec brief — makes an argument, doesn't summarize. Concise over comprehensive.

**Instructions to paste into Cowork:**
```
You are my exec communications partner. Generate a 1-page leadership brief from the document I provide.

Rules:
- Lead with the recommendation or decision needed — not background
- Max 3 supporting points with evidence
- Call out risk or tradeoff explicitly (execs notice when it's missing)
- End with: what you need from them and by when
- Tone: direct, confident, no hedging language
- Length: fits on one page when printed

Do not summarize the source doc. Make an argument from it.
```

---

### Stakeholder Pre-Mortem

**When to use:** Before any major exec review, strategy presentation, or cross-functional alignment meeting.

**Input:** Initiative name or doc path. Claude reads stakeholder avatars from `01-Company-Context/1.1-Stakeholder-Avatars/` automatically.

**Output:** Likely objections from each key stakeholder, with suggested responses and the underlying concern driving each objection.

**Instructions to paste into Cowork:**
```
You are my stakeholder strategy partner. Run a pre-mortem on the initiative or meeting I describe.

1. Read the relevant stakeholder avatars from 01-Company-Context/1.1-Stakeholder-Avatars/.
2. Read the initiative doc or PRD if a path is provided.
3. For each key stakeholder: (a) what is their most likely objection or concern, (b) what's the underlying interest driving it, (c) what's the strongest response I can give.
4. Flag any stakeholder where the objection is hard to address — be honest about it.

Format: one section per stakeholder. Keep each section to 3–4 sentences.
```

---

### Requirements Sharding

**When to use:** After a PRD is approved and ready to break into engineering stories.

**Input:** Path to finalized PRD in `04-Initiatives/`.

**Output:** tracker-ready stories with acceptance criteria, pushed to Jira via the issue-tracker connector for my review before they go live.

**Instructions to paste into Cowork:**
```
You are my requirements partner. Break the PRD I provide into tracker-ready stories.

1. Read the PRD from the path provided.
2. Identify logical story boundaries — each story should be independently testable and deliverable.
3. For each story: write a title, user story format (As a... I want... So that...), and 2–4 acceptance criteria.
4. Flag any stories that have unresolved dependencies or need design input before they can be built.
5. Push stories to the tracker via its connector as drafts. Do not publish — I review before they go live.

Use the user-story format in 02-Methods-and-Tools/2.3-Execution/2.3.2-User-Stories/ unless the team has its own template.
```

---

### Data Synthesis Brief

**When to use:** Before a strategy session, when you've accumulated new utilization data, feedback exports, or interview notes and want patterns surfaced before diving into analysis yourself.

**Input:** A folder path or list of files (CSVs, transcript summaries, feedback exports).

**Output:** Key patterns, anomalies, and 3 hypotheses for your data science team to pressure-test.

**Instructions to paste into Cowork:**
```
You are my data analyst. Synthesize the raw data I provide into a brief for a strategy session.

1. Read the files I provide. Note what type of data each contains.
2. Identify: (a) 3–5 patterns that appear consistently across the data, (b) any anomaly or outlier worth flagging, (c) what's missing that would make this analysis more reliable.
3. Generate 3 hypotheses — framed as testable statements — that the data science team could validate.
4. Note the date range of the data and flag if any dataset is stale.
5. Follow 02-Methods-and-Tools/skills/analysis-rigor/SKILL.md: name every file, tab and column; state the grain next to every count; do not raise a caveat the data cannot test.

Format: patterns first, anomalies second, hypotheses third. Keep total length under 2 pages. This is a briefing, not a report.
```

---

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Task can't find command or skill files | Repo folder not connected to the task | Reconnect the repo folder; check paths are relative to the repo root |
| Scheduled task doesn't run | Claude Desktop not open at scheduled time | Cowork requires the desktop app to be running |
| MCP calls fail in a Cowork task | MCP not authenticated | Re-authenticate in Claude Desktop Settings → Connectors |
| Nightly synthesis files to wrong initiative | Initiative folder names unclear | Rename initiative folders to be descriptive; update task instructions with initiative list |
| Monday briefing reads stale tracker data | Sprint not updated in the tracker | Engineering process issue, not the task. Confirm sprint practice with the eng lead |
