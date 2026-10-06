# /log-decision

Capture a decision with full context and append it to `00-Meta/decisions-log.md`.

## What Claude does

1. **Asks four questions** (if not already clear from context):
   - What was decided?
   - Why this over the alternatives?
   - What alternatives were on the table?
   - Is this firm, provisional, or does it need revisiting by a specific date?

2. **Appends a structured entry** to `00-Meta/decisions-log.md` with today's date and all four fields.

3. **Confirms** with a single line: `[DECISION LOGGED — decisions-log.md]`

4. **Does not break conversation flow** — resumes whatever you were doing.

## When to use

- After a significant product or strategy call
- When you've chosen a direction and want to remember why
- When a decision was made in a meeting and you're capturing it after the fact
- When something is provisional and you want a reminder to revisit it

## Quick version

Mid-conversation, just say **"log this decision"** — Claude will infer the decision and rationale from context and log it without asking questions. Use `/log-decision` when you want to be deliberate and fill in all fields.

## Status options

- `decided` — firm, no revisit planned
- `provisional` — working assumption, expect to revisit
- `revisit by [date]` — explicitly time-boxed

## Related

- Parking lot: say "park this" to capture an idea without deciding on it
- Decisions log: `00-Meta/decisions-log.md`
