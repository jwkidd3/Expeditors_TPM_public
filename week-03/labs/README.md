# Week 3 — Requirements Engineering & Mini-Capstone

> *"A PRD is a contract between the customer's problem and the engineering work that solves it. If either side cannot read it, the contract is void."*

Week 3 is the **first capstone week** of the academy. Quads convert their Week-2 strategy package — North Star, design principles, journey map, top feature concepts — into a single **Technical PRD** that an engineering lead would accept as input to scoping. The PRD ships Friday after a structured peer-review cycle.

This week is **explicitly non-AI**. The discipline of writing a PRD by hand, with your quad, is the muscle being built. AI returns in Week 4.

## Learning outcomes

By Friday afternoon, each participant can:

1. Convert a customer problem into a structured **Technical PRD** with context, problem framing, goals, scope, AC, NFRs, risks, and open questions.
2. Write **granular, testable Acceptance Criteria** in Given/When/Then form that an engineer can implement against without a clarifying call.
3. Document **Non-Functional Requirements** across performance, security, accessibility, observability, and compliance — and defend each as a constraint, not a wishlist.
4. Conduct a structured **PRD peer review** that surfaces specific defects rather than general impressions.
5. Revise a PRD in response to peer review and produce a **review-resolution log** that shows which feedback was adopted, deferred, or rejected, with reasoning.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | Drafting Technical PRDs | PRD Sections 1–3 (context, problem, goals, scope) |
| 2 | Writing granular Acceptance Criteria | 8–12 testable ACs |
| 3 | Documenting Non-Functional Requirements | NFR section across 5 categories |
| 4 | Mini-capstone — PRD assembly (non-AI) | **Complete PRD** ready for review |
| 5 | PRD Review — morning reviews, afternoon revisions + secondary | **Revised PRD + review-resolution log** |

The artifact is cumulative: each day's output is added to the PRD until Friday's revised version ships.

## Daily cadence (applies Mon–Thu; Friday differs)

| Clock | Block | Mix |
|-------|-------|-----|
| 09:00 – 09:15 | Opening & objectives | Instructor |
| 09:15 – 10:30 | Teaching Block 1 + Activity 1 | ~25 min teach / 50 min quad work |
| 10:30 – 10:45 | **Break** | |
| 10:45 – 12:00 | Teaching Block 2 + Activity 2 | ~25 min teach / 50 min quad work |
| 12:00 – 13:00 | **Lunch** | |
| 13:00 – 14:15 | Teaching Block 3 + Activity 3 | ~25 min teach / 50 min quad work |
| 14:15 – 14:30 | **Break** | |
| 14:30 – 16:00 | Teaching Block 4 + Activity 4 + Wrap | ~25 min teach / 45 min quad / 20 min wrap |

### Friday cadence (PRD review day)

| Clock | Block | Mix |
|-------|-------|-----|
| 09:00 – 09:15 | Opening; review pairings posted | Instructor |
| 09:15 – 10:45 | **Primary review round 1** | Two reviewing quads on each PRD |
| 10:45 – 11:00 | **Break** | |
| 11:00 – 12:00 | Author response + clarifying conversations | Author quads receive feedback |
| 12:00 – 13:00 | **Lunch** | |
| 13:00 – 14:30 | **Revisions** | Authors revise based on review |
| 14:30 – 14:45 | **Break** | |
| 14:45 – 15:45 | **Secondary review** | Different reviewers; read the revision |
| 15:45 – 16:00 | Wrap + sign-off | Final PRDs + resolution logs delivered |

## The "non-AI" rule (Mon–Thu)

This week is the discipline of **producing a defensible written artifact without a generative tool**. The reasoning:

- AI fills in vagueness with confident generic prose. Vagueness is the bug we're trying to eliminate.
- An engineer who reads an AI-drafted PRD often spots the generic prose and discounts the document.
- The TPM muscle being built is **structured thinking expressed as written words**. AI co-writing skips the thinking.

What's allowed: spell-check, dictionary, project notes, transcripts of customer interviews, your Week-1 and Week-2 artifacts. What's not allowed: generative AI for drafting, summarizing, or critiquing any part of the PRD.

The honor system holds. Friday's reviews surface generic prose quickly.

## The PRD anatomy (the same template all week)

```markdown
# PRD — <Feature name>
**Author quad:** <names>  |  **Date:** <date>  |  **Status:** Draft / In review / Approved

## 1. Context
Why this work, why now. Customer signal. Strategy fit.

## 2. Problem
The user's job-to-be-done; the friction they hit today. Tied to your Week-1 problem statement and Week-2 journey map.

## 3. Goals & non-goals
- Goals: what success looks like in user terms
- Non-goals: what we explicitly will not do (often more valuable than the goals)

## 4. Scope (in / out)
The boundary. What ships, what doesn't, in this iteration.

## 5. Solution sketch
Enough description that an engineer can imagine the shape; not enough that you've designed it for them.

## 6. Acceptance Criteria
Given/When/Then form. Granular, testable, falsifiable. (Day 2)

## 7. Non-Functional Requirements
Performance, security, accessibility, observability, compliance. (Day 3)

## 8. Metrics & validation
Tied to the Tier Sheet from Week 2. How we'll know it worked in 30 days.

## 9. Risks & open questions
Named honestly. The mark of a senior author.

## 10. Dependencies
Other teams, systems, decisions, data we need.

## 11. Out-of-scope follow-ups
Things this PRD acknowledges but doesn't ship.
```

## Quads

Quads from Weeks 1–2 carry through. They authored together, they ship together. Friday's review pairings are different from authoring pairings (we cross-pollinate).

## Friday review rubric

Reviewers score each PRD on:

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| Problem clarity | 20% | Engineer could scope without clarifying call |
| AC testability | 25% | Each AC is implementable + falsifiable; no "system should be intuitive" |
| NFR completeness | 20% | 5 categories present; each tied to a measurable target |
| Strategy linkage | 15% | Goals tie to Week-2 NS / KPIs / journey friction |
| Risk honesty | 10% | Real risks named; "no risks" is a fail |
| Writing discipline | 10% | Clear, specific, no AI-generic prose |

## Bridge to Week 4

Week 4 turns from "what do we want" to "what's technically possible / constrained": monolith vs microservices, security & compliance, system mapping, latency/availability/rate-limit targets. Each quad's PRD becomes the input to the **technical architecture** conversation. The NFRs written this week are the **first draft** of the architectural constraints discussed Week 4.
