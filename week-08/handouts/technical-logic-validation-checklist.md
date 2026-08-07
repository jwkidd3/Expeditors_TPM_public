# Technical Logic Validation — 7-Point Checklist + Log

> **Day 4 handout.** Each artifact can be fine in isolation yet inconsistent together. Technical logic validation = **walk every cross-artifact reference** and verify they fit. Most quads fail 2–3 checks on first pass — that's expected; that's why this day exists.

---

## The failure this catches

- The PRD's NFR says "p95 < 500ms" but the TMD's sequence diagram totals 800ms.
- The TCD says "modular monolith" but the TMD shows components that need to deploy independently.
- The data model has no foreign key for a relationship the API requires.
- The outcome map's "leading indicator" isn't measurable with the observability NFR.

---

## The 7-point validation checklist

| # | Check | Where to look |
|---|-------|---------------|
| 1 | Outcome map → metrics → SLOs aligned | DP-light Section 1, PRD-light Section 7, TCD-light Section 4 |
| 2 | Data model supports the API contract | TMD-light Section 1 ↔ Section 3 |
| 3 | API contract supports the AC | TMD-light Section 3 ↔ PRD-light Section 6 |
| 4 | SLO budget fits the sequence diagram | TCD-light Section 4 ↔ TMD-light Section 4 |
| 5 | NFRs don't contradict the architecture stance | PRD-light Section 7 ↔ TCD-light Section 1 |
| 6 | Trade-offs don't contradict each other | TCD-light Section 5 |
| 7 | Stakeholder sign-off captures all constraints | TCD-light Section 6 |

For each check: pull **both sides**, compare, and if they disagree — decide to tighten the artifact (usually the answer), adjust the SLO/NFR only if evidence demands, or mark it a known gap to call out in the presentation.

---

## The validation log

```markdown
| # | Check | Status | Gap / fix |
|---|-------|--------|-----------|
| 1 | Outcome → metrics → SLOs | Pass | None |
| 2 | Data model ↔ API | Partial | Missing FK on User → Order; added |
| 3 | API ↔ AC | Pass | None |
| 4 | SLO budget ↔ sequence | Fail → Fixed | Sequence totaled 800ms; SLO was 500ms; tightened SLO to p95 < 1000ms with defense |
| 5 | NFRs ↔ architecture | Pass | None |
| 6 | Trade-offs internal consistency | Pass | None |
| 7 | Stakeholders ↔ constraints | Partial | Compliance not on sign-off list; added |
```

*(The example rows above show the log's shape — replace them with your own findings.)*

---

### The bar to clear
Don't mark a check "Pass" without walking the references — be ready to **show the section reference** for every pass. A quad that genuinely passes all 7 has a coherent artifact set.
