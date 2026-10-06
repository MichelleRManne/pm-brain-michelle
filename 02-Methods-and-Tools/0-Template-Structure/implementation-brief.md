# Implementation Brief (PRD → Builder Handoff)

**Status:** Handoff template, from PM to builder (an engineer or a coding agent)
**Objective:** Turn approved PRD requirements into atomic, testable technical tasks without losing the hypothesis behind them.

---

## 1. Context (the why)

- **Linked PRD:** [Path to PRD]
- **Hypothesis:** IF [action], THEN [outcome metric moves from X to Y], BECAUSE [evidence].
- **Key constraints:** [e.g. must use the existing data source; no changes to a third-party API]

---

## 2. Technical scope (the what)

- **Primary system(s):** [System names]
- **Entry points / triggers:** [Events that start the flow, e.g. "record created", "status changed"]
- **Logic change:** [Describe the change in small, atomic steps. One state change per line.]
- **Output signals:** [Which yes/no events must be logged, so you can tell whether each step worked]

---

## 3. Task breakdown (the how)

1. **Task 1:** [Clear technical instruction]
2. **Task 2:** [Clear technical instruction]
3. **Task 3:** [Clear technical instruction]

---

## 4. Definition of done

- **Test case:** [One specific real-world case to run end to end]
- **Success criteria:** [Observable result and time bound, e.g. "status updates within 1 second of trigger"]
- **Signal check:** Does each task produce a yes/no signal you can see in the data?

---

## 5. Handoff checklist

- [ ] PRD signed off, with the Assumptions & Confidence section complete
- [ ] Hypothesis passed the IF / THEN / BECAUSE gate
- [ ] Context trimmed for implementation (`/broker-audit`)
