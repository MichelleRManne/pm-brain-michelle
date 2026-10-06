# /log-observed

Capture a decision someone *else* made that affects your scope. Appends to `00-Meta/decisions-observed.md`.

Use this for decisions that show up in Slack, meetings, or async threads where you weren't the decider but you need to track-back later. Chat history often expires or gets buried, so this file is the institutional memory.

## What Claude does

1. **Asks up to seven questions** (skip any already clear from context):
   - When did you observe this? (defaults to today)
   - Who decided?
   - What was decided? (one sentence)
   - What was the rationale? (prefix `[INFERRED]` if you're guessing)
   - How does this affect your scope?
   - Where did you see it? (channel, meeting, or thread title — no link, since links may expire)
   - Confidence: firsthand, secondhand, or inferred?
   - Any open questions you'd want to verify with the decider?

2. **Appends a structured entry** to the top of the log in `00-Meta/decisions-observed.md` (newest first).

3. **Confirms** with a single line: `[OBSERVED DECISION LOGGED — decisions-observed.md]`

4. **Does not break conversation flow** — resumes whatever you were doing.

## When to use

- A decision dropped in Slack and you need to remember it past 30 days
- Someone else's call that constrains your roadmap or priorities
- A meeting where direction was set without you in the room
- Inferred decisions you piece together from multiple signals

## Quick version

Mid-conversation, just say **"log observed decision"** — Claude will infer fields from context and log it without asking. Use `/log-observed` when you want to be deliberate and fill in all fields.

## Confidence levels

- `firsthand` — you were in the room or thread when decided
- `secondhand` — heard from someone who was
- `inferred` — pieced together from signals; rationale is your best guess

## Related

- Your own decisions: `/log-decision` → `00-Meta/decisions-log.md`
- Parking lot: say "park this" to capture an idea without deciding on it
