# PRD Template

> **Day 1 · Activity 2 handout.** The 11-section PRD skeleton your triad drafts across Week 3. Print it, pin it, fill it section by section. Sections carry a `[Day X]` tag telling you when each gets written.

---

```markdown
# PRD — <Feature name>
**Author triad:** <names>  |  **Date:** <date>  |  **Status:** Draft

## 1. Context                       [Day 1]
Why this work (customer signal) · Why now (strategic fit) · What changed.
Half a page max.

## 2. Problem                       [Day 1]
The user's job-to-be-done (verb-based, their language) · the friction they
hit today (specific, observed) · why today's workarounds are inadequate.
Quote a real customer at least once. Half to three-quarters of a page.

## 3. Goals & non-goals             [Day 1]
Goals (3–5): each a user outcome, observable within 30 days of ship.
Non-goals (2–4): what you explicitly will not do.

## 4. Scope (in / out)              [Day 1]
Two-column table. The "out" column is the negotiation tool.

## 5. Solution sketch               [Day 1]
User-visible flow (4–8 steps) · key surfaces affected · hard interactions
with other systems · a happy-path paragraph. No schema, no API contracts,
no framework choices.

## 6. Acceptance Criteria           [Day 2]
8–12 testable AC in Given / When / Then form. Covers happy / sad / weird
paths. Each passes the 5-failure-mode check.

## 7. Non-Functional Requirements   [Day 3]
6–10 NFRs, at least one per category (Performance / Security / Accessibility
/ Observability / Compliance). Each uses the four-part template. Ends with a
"Known trade-offs" subsection.

## 8. Metrics & validation          [Day 4]
One primary metric · one counter-metric · up to three secondaries · a
four-checkpoint validation plan.

## 9. Risks & open questions        [Day 4]
Risks (with mitigations) · open questions (owned, with deadlines) ·
assumptions (with basis). "No risks" is a fail.

## 10. Dependencies                 [Day 4]
Table: dependency · named owner · what we need · by when · status.

## 11. Out-of-scope follow-ups      [Day 4]
Specific items with ticket placeholders — not "future work".
```

---

## How the sections relate (the integration you'll be checked on Day 4)

- Section 1 → Section 2 should motivate the reader before they learn what to build.
- Every Section 3 goal ties to a Section 8 metric; every Section 8 metric traces to a Section 3 goal.
- Every Section 5 happy-path step has a matching Section 6 happy-path AC.
- Section 7 NFRs cover the system *properties* that Section 6 AC (system *behaviors*) don't.
- Section 4 scope-out items reappear in Section 11 follow-ups.
