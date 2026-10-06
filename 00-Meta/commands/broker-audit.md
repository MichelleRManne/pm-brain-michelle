# /broker-audit

Context hygiene for long sessions. Lists what's actually loaded, marks stale files as sleeping, and finds facts you said in chat that aren't saved anywhere.

## What Claude does

1. Loads `00-Meta/agents/context-broker.md` and follows it.
2. Reports which files were actually read this session, which can go to sleep, and any **ghost context** (facts from the chat that aren't saved in the repo), with a suggested home for each.
3. Flags any conflict between instruction files and asks you which one wins.
4. Offers a checkpoint if the session is long or about to change state.

## When to use

- Around 20 turns into a working session
- Before moving from braindump to writing an artifact
- When answers start drifting or repeating

## Related

- Say **"checkpoint"** to save session state to `checkpoints/`
