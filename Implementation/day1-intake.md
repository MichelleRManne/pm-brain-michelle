# Day 1 Intake Questions
[Company] — [Your role]

> **How to use:** One doc per conversation. Go in curious, not confirmatory. Your hypotheses stay in your head — these questions are designed to surface *their* view of reality before you share yours. 30 minutes each. Let them talk. The best information will come after the obvious answer — pause and wait.
>
> **After each session:** Drop your raw notes into `.incoming/` with the person's name and date. If nightly synthesis is set up, it will file them and extract themes.

---

## Engineering

**Who:** Tech lead or engineering manager for your product area
**Goal:** Understand the technical landscape, current state of the product, and where the biggest constraints and friction points are — from engineering's perspective, not product's.

**Warm up**
1. Tell me about what you own — what systems and parts of the product are yours?
2. How long have you been working on this area specifically?

**Substantive**

3. Walk me through the user's experience from a technical perspective — what are the major systems a user touches from first contact through the moment they get value?

4. Where does the current architecture work well? Where does it create the most pain — for the team or for the product?

5. What's on the team's plate right now — what are you building toward, and what's been taking longer than expected?

6. What are the technical constraints I should understand early — things that would make me write a PRD and have you come back and say "that's actually a 3-month refactor"?

7. What does a good week look like for this team? What does a bad week look like?

**Close**

8. What do you wish a PM understood about this product that most PMs don't?

9. What should I know that I haven't asked?

---

**What to listen for:**
- Where do they hesitate or qualify? That's usually where the real constraint is
- Anything described as a "workaround" or "we handle that manually" — these are product gaps
- Debt they've stopped talking about because no one ever prioritizes it
- What they light up about — what they're proud of or excited to build

---

## Operations

**Who:** Ops leader or senior operator who runs the workflow day-to-day
**Goal:** Understand what actually happens inside the funnel — the operator experience, the manual work, the workarounds, and where things break — before you look at any data.

**Warm up**
1. Tell me about your team — how is it structured and what does your day-to-day look like?
2. How long have you been running this part of the operation?

**Substantive**

3. Walk me through what happens after a request or signup comes in — what does your team do, step by step, to get it to done?

4. Where does your team spend the most time? What's the most manual or repetitive part of the workflow?

5. What does your team do outside the product — spreadsheets, texts, their own notes, things the tool doesn't handle?

6. What happens when someone falls off mid-process — how does your team find out, and what do you do about it?

7. What data do you look at most regularly to understand how things are going?

**Close**

8. What's broken that you've stopped asking to fix?

9. What would make your team's job meaningfully easier — not someday, but tomorrow?

---

**What to listen for:**
- Everything that happens outside the product — that's your feature backlog
- Where they express frustration about something product-related that's been that way for a long time
- What metrics they actually use vs. what they're told to track
- The moment they say "we've tried that before" — ask what happened

---

## UX

**Who:** UX designer on your product area
**Goal:** Understand the current state of the user and operator experience, what research exists, and how design fits into the team's workflow.

**Warm up**
1. Tell me about what you're working on right now — what's your current focus?
2. How do you typically work with the product and engineering teams here?

**Substantive**

3. Walk me through the user-facing experience as it exists today — what are you most proud of, and where do you think it falls short?

4. What research have you done recently? What did you learn — and what surprised you?

5. Where do users or operators seem most confused or frustrated when you watch them use the product?

6. What design or UX constraints should I understand early — things that aren't obvious from looking at the product?

**Close**

7. What's a design decision that was made that you'd revisit if you had the chance?

8. What should I know about how this team works that would help me be a good partner to you?

---

**What to listen for:**
- Research that already exists that product hasn't acted on — this is gold
- Where they've been blocked by engineering constraints vs. where product hasn't prioritized design
- What they're excited to work on vs. what they feel stuck on
- Their read on how the team works together — this will tell you something about team dynamics

---

## Cross-cutting: questions to ask everyone

These work in any of the three conversations when the moment is right — don't force them, but have them ready:

- "If you could fix one thing about how we work together as a team, what would it be?"
- "What's something you think leadership doesn't fully understand about this product or this team?"
- "What does success look like for you personally in the next 6 months?"

---

## After all three conversations

Before your first week is out, write a short synthesis note — even just bullet points — and drop it into `.incoming/`. The questions to answer:

- What do the three teams agree on without knowing they agree?
- Where do they contradict each other? (These are your highest-information gaps)
- What did you hear that surprised you?
- What did you *not* hear that you expected to? (Absence of signal is signal)
- What hypothesis did you walk in with that you need to update?
