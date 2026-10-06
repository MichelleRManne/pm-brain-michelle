# Product Requirements Document (PRD)

**Product Name:** [Product/Feature Name]  
**Product Manager:** [Name]  
**Date:** [Date]  
**Status:** [Draft | Under Review | Approved | In Development | Launched]  
**Related:** [Link to opportunity-assessment.md]

---

## 1. Executive Summary

**What:** [Brief description of the product/feature]  
**Why:** [Primary business/user value]  
**When:** [Target timeline]  
**Success:** [Top outcome metric + target/date]

**Context:** This PRD builds on [opportunity-assessment.md] which validated the problem and solution approach.

---

## 2. Problem Statement

### 2.1 The Problem
**Current State:** [What's happening now that's problematic]  
**Impact:** [Who is affected and how severely]  
**Evidence:** [Data, research, or feedback supporting this problem]

**Job Story:** "When I [situation], I want to [motivation], so I can [outcome]."

### 2.2 Target Users
**Primary Users:** [Main user segment with specific context]  
**Secondary Users:** [Additional affected users]  
**User Pain Points:** 
- [Specific pain point 1]
- [Specific pain point 2]
- [Specific pain point 3]

---

## 3. Assumptions & Confidence Levels

> **Why this matters:** Every PRD is built on beliefs about users, the problem, and the market. This section surfaces those beliefs explicitly, assigns confidence levels based on validation work, and identifies what still needs to be tested. This prevents requirements from treating assumptions as facts.
>
> **Instructions:** Link to your `opportunity-assessment.md` for the full discovery evidence. Copy validated facts and assumptions here, note confidence levels (High/Med/Low), and call out what you're betting on that you'll validate post-launch.

### 3.1 What We Know (Validated)

**From Discovery & Opportunity Assessment:**
- **[Fact 1]**: [What we validated] — Source: [interview/data/research link], Confidence: **High**
- **[Fact 2]**: [What we validated] — Source: [interview/data/research link], Confidence: **High**
- **[Fact 3]**: [What we validated] — Source: [interview/data/research link], Confidence: **High**

**Links to discovery work:**
- [Link to opportunity-assessment.md]
- [Link to 00-Meta/3-research-insight-log.md]
- [Link to user interview synthesis]

### 3.2 Key Assumptions (Confidence Level)

**About the Problem:**
- **[Assumption 1]**: [What we believe to be true about the problem]
  - **Confidence:** [High/Med/Low]
  - **Why we believe this:** [Evidence, prior work, or reasoning]
  - **Risk if wrong:** [What happens if this assumption breaks]
  - **How we'll validate:** [Method, post-launch or pre-launch]
  - **Timeline:** [When we'll test this]

- **[Assumption 2]**: [What we believe about user behavior or motivation]
  - **Confidence:** [High/Med/Low]
  - [Similar structure]

**About the Solution:**
- **[Assumption 3]**: [What we believe users will do with this feature]
  - **Confidence:** [High/Med/Low]
  - [Similar structure]

- **[Assumption 4]**: [What we believe about adoption or usage patterns]
  - **Confidence:** [High/Med/Low]
  - [Similar structure]

**About Business Impact:**
- **[Assumption 5]**: [What we believe about business outcome if metrics move]
  - **Confidence:** [High/Med/Low]
  - [Similar structure]

### 3.3 Confidence Levels Explained

| Level | Meaning | Example |
|-------|---------|----------|
| **High** | Validated through research, data, or prior shipping. Low risk if we're wrong—we have contingencies. | "Users hate manual handoffs" — 47 interviews confirm this. |
| **Med** | Some evidence but not conclusive. We've tested with a subset or heard it multiple times but haven't observed at scale. | "Users will adopt if we make it frictionless" — we've heard this, but haven't measured adoption at scale. |
| **Low** | Educated guess or extrapolation. We haven't tested directly. High risk if wrong. | "This will increase revenue by 20%" — we're modeling, not measuring yet. |

### 3.4 Validation Plan

**What we'll test post-launch (or pre-launch if time allows):**

| Assumption | Validation Method | Owner | Timeline | Success Criteria |
|---|---|---|---|---|
| [Assumption] | [Interview / analytics / experiment / beta feedback] | [Owner] | [When we'll test] | [What "validated" looks like] |
| [Assumption] | [Method] | [Owner] | [Timeline] | [Success criteria] |

**Decision gates:**
- **If [Assumption 1] proves false:** [Pivot plan or contingency]
- **If [Assumption 2] is only partially true:** [What we'll do instead]

---

## 4. Goals & Success Metrics

### 4.1 Business Goals
**Primary Goal:** [Main business objective]  
**Secondary Goals:** [Supporting objectives]

### 4.2 Success Metrics
**Key Metrics:**
- [Metric 1]: [Current baseline] → [Target] by [Date]
- [Metric 2]: [Current baseline] → [Target] by [Date]
- [Metric 3]: [Current baseline] → [Target] by [Date]

**Timeline for Measurement:** [When we'll evaluate success]

**Guardrails:**
- [Constraint 1]: [Threshold/limit]
- [Constraint 2]: [Threshold/limit]

---

## 5. Solution Overview

### 5.1 Proposed Solution
[Describe the solution at a conceptual level - avoid detailed specifications]

**Key Principles:**
- [Principle 1]
- [Principle 2]
- [Principle 3]

### 5.2 Key User Flows
*Main paths users will take*

**Flow 1: [Primary Flow Name]**
1. User [action/trigger]
2. System [response]
3. User [next action]
4. System [outcome]
5. User achieves [desired outcome]

**Flow 2: [Secondary Flow Name]**
[Similar step-by-step breakdown]

**Flow 3: [Edge Case Flow]**
[How edge cases are handled]

### 5.3 Core Requirements

**Must Have (P0):**
- **[Requirement 1]**
  - **Description:** [What it does]
  - **Acceptance Criteria:**
    - Given [context], When [action], Then [expected outcome]
    - Given [context], When [action], Then [expected outcome]
  - **Dependencies:** [What's needed]
  
- **[Requirement 2]**
  - [Similar structure]

**Should Have (P1):**
- **[Requirement 3]**
  - [Similar structure]

**Could Have (P2):**
- **[Requirement 4]**
  - [Nice-to-have, deferrable]

---

## 6. Detailed Features & Acceptance Criteria

### Feature 1: [Feature Name]

**Description:** [What this feature does and why]

**User Story:** "As a [user], I want [capability], so that [benefit]"

**Acceptance Criteria:**
- ✅ **AC1:** Given [precondition], When [action], Then [expected result]
- ✅ **AC2:** Given [precondition], When [action], Then [expected result]
- ✅ **AC3:** [Edge case handling]

**Technical Requirements:**
- [Technical constraint 1]
- [Technical constraint 2]

**Dependencies:**
- [Internal dependency]
- [External dependency]

**Success Metrics:**
- [Metric name]: [How to measure]

---

### Feature 2: [Feature Name]

[Similar structure for each feature]

---

## 7. Scope & Constraints

### 7.1 In Scope (This Version)
- [Feature/component 1]
- [Feature/component 2]
- [Feature/component 3]

### 7.2 Out of Scope (Explicitly NOT Doing)
- [Feature 1]: [Why not - technical/business/priority reason]
- [Feature 2]: [Why not]
- [Feature 3]: [Why not]

### 7.3 Future Considerations
- [Feature that may be added later]: [Conditions for adding]
- [Enhancement]: [When to consider]

### 7.4 Constraints
**Technical:** [Technology limitations, API constraints, platform restrictions]  
**Timeline:** [Schedule constraints, deadlines]  
**Resources:** [Team capacity, budget limitations]  
**Business:** [Policy, regulatory, or strategic constraints]  
**Compliance:** [Legal, privacy, security requirements]

---

## 8. User Experience & Interface Requirements

### 8.1 User Interface Requirements
- [UI requirement 1]: [Description]
- [UI requirement 2]: [Description]

### 8.2 User Experience Principles
- [Principle 1]: [How it applies]
- [Principle 2]: [How it applies]

### 8.3 Accessibility Requirements
- [Accessibility requirement 1]
- [Accessibility requirement 2]

---

## 9. Technical Specifications

### 9.1 Architecture Overview
[High-level system architecture - link to detailed technical docs]

### 9.2 Data Requirements
- **Data Sources:** [Where data comes from]
- **Data Storage:** [Where data is stored]
- **Data Processing:** [How data is processed]
- **Data Privacy:** [Privacy considerations]

### 9.3 Integration Requirements
- [Integration 1]: [What it integrates with, how]
- [Integration 2]: [What it integrates with, how]

### 9.4 Performance Requirements
- [Performance metric 1]: [Target/threshold]
- [Performance metric 2]: [Target/threshold]

### 9.5 Security & Compliance
- [Security requirement 1]
- [Security requirement 2]
- [Compliance requirement 1]

---

## 10. Dependencies & Risks

### 10.1 Dependencies
**Internal:**
- [Team/System]: [What's needed and by when]

**External:**
- [Vendor/API/Service]: [What's needed and by when]

**Technical:**
- [Technology/Infrastructure]: [What's needed]

### 10.2 Key Risks & Mitigation
**Risk 1: [Risk Description]**
- **Probability:** [High/Med/Low]
- **Impact:** [High/Med/Low]
- **Mitigation:** [How we'll address it]
- **Contingency:** [Backup plan]

**Risk 2: [Risk Description]**
[Similar structure]

---

## 11. Implementation Plan

### 11.1 High-Level Timeline
**Phase 1: [Phase Name]** - [Timeframe]
- [Milestone 1]
- [Milestone 2]
- [Deliverable]

**Phase 2: [Phase Name]** - [Timeframe]
- [Milestone 1]
- [Milestone 2]
- [Deliverable]

**Phase 3: [Phase Name]** - [Timeframe]
- [Milestone 1]
- [Milestone 2]
- [Deliverable]

### 11.2 Development Approach
- [Agile/Sprint approach, Waterfall, etc.]
- [Sprint duration, release cadence]
- [Testing strategy]

### 11.3 Go-to-Market Plan
**Launch Strategy:** [How we'll roll out]
- [Beta/Alpha testing]
- [Phased rollout]
- [Full launch]

**Marketing/Communication:** [How users will learn about it]  
**Support Plan:** [Customer support considerations]  
**Training:** [Training requirements]

---

## 12. Testing & Validation

### 12.1 Testing Strategy
**Unit Tests:** [What will be unit tested]  
**Integration Tests:** [What will be integration tested]  
**User Acceptance Tests:** [UAT criteria]  
**Performance Tests:** [Performance testing approach]

### 12.2 Validation Plan
**Validation Method:** [How we'll validate success]
- [Method 1]: [What we'll measure]
- [Method 2]: [What we'll measure]

**Success Criteria:** [What "done" looks like]
- [Criteria 1]
- [Criteria 2]

---

## 13. Post-Launch Plan

### 13.1 Monitoring & Metrics
**Key Metrics to Track:**
- [Metric 1]: [How to measure, dashboard link]
- [Metric 2]: [How to measure, dashboard link]

**Alert Thresholds:**
- [Alert condition]: [Action to take]

### 13.2 Iteration Plan
**Feedback Collection:** [How we'll gather user feedback]
- [Method 1]
- [Method 2]

**Review Timeline:** [When we'll assess and iterate]
- [Review 1]: [Date, focus area]
- [Review 2]: [Date, focus area]

**Success Criteria for Iteration:**
- [When to iterate]
- [When to pivot]
- [When to kill]

---

## 14. Open Questions & Decisions Needed

### 14.1 Open Questions
- ❓ **[Question 1]:** [Owner, decision date]
- ❓ **[Question 2]:** [Owner, decision date]

### 14.2 Decisions Needed
- [ ] **[Decision 1]:** [Context, options, recommendation]
- [ ] **[Decision 2]:** [Context, options, recommendation]

---

## 15. Appendix

### 15.1 Research & Data
- [Link to user research]
- [Link to competitive analysis]
- [Link to data analysis]

### 15.2 Wireframes/Mockups
- [Link to design assets]
- [Link to prototypes]

### 15.3 Technical Specifications
- [Link to detailed technical documentation]
- [Link to API specifications]
- [Link to database schema]

### 15.4 Related Documents
- [Link to opportunity-assessment.md]
- [Link to roadmap.md]
- [Link to decisions.md]

---

## 16. Document History

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| [Date] | 1.0 | Initial PRD | [Name] |
| [Date] | 1.1 | [Change description] | [Name] |

---

## 17. Stakeholder Sign-off

**Product Manager:** [ ] Reviewed and Approved - [Name, Date]  
**Engineering Lead:** [ ] Reviewed and Approved - [Name, Date]  
**Design Lead:** [ ] Reviewed and Approved - [Name, Date]  
**Marketing:** [ ] Reviewed and Approved - [Name, Date]  
**Legal/Compliance:** [ ] Reviewed and Approved - [Name, Date]  
**Leadership:** [ ] Reviewed and Approved - [Name, Date]

---

**Next Steps:**
1. [Action 1] - [Owner] - [Due Date]
2. [Action 2] - [Owner] - [Due Date]

---

## 18. Product Sense Hooks (Strongly Recommended)

Before you treat this PRD as “done”, run a quick product-sense pass and, if it’s a meaningful initiative, capture it in your personal logs.

**Where to reflect/log:**
- Quick check-in: `00-Meta/daily-log-*.md`
- Bigger bets / roadmap-shaping work:
  - Decision context in `00-Meta/2-prioritization-decision-log.md`
  - Key research learnings in `00-Meta/3-research-insight-log.md`

**Prompts to sanity-check this PRD:**
- Who specifically is this for, and what job are they really hiring this for?
- What are the second- and third-order effects if this works? If it fails?
- What’s the most important assumption this PRD is betting on?
- What qualitative and quantitative evidence are we actually using?
- What would make us change our mind 4–8 weeks after launch?

You don’t need pages of extra writing—2–5 thoughtful lines in the relevant `00-Meta` log is enough to keep your day-to-day execution anchored in product sense.

-----

## References

- PRD Framework: `1-prd-framework.md`
- PRD JTBD Template: `3-prd-jtbd-template.md`
- PRD README: `README.md`
- Strategy: `../../2.1-Strategy/README.md` (Strategic Foundations, OKR Framework)
- Discovery: `../../2.2-Discovery/README.md` (Opportunity Assessment, Idea Validation, Jobs to Be Done)
- Foundations: `../../2.0-Foundations/README.md` (Self-Reflection, Mental Models, Bias)
