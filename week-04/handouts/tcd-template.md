# TCD Template

> **Day 1 handout.** The 6-section Technical Concept Document (TCD) skeleton your quad builds across Week 4 — the sibling artifact to your Week-3 PRD. Print it, pin it, fill it section by section. Each section carries a `[Day X]` tag telling you when it gets written. Friday it ships, peer-reviewed and signed off.

---

```markdown
# Technical Concept Document — <feature name>
**Sibling to:** PRD <link>  |  **Authors:** <quad>  |  **Status:** Draft / Reviewed

## 1. Architecture stance                              [Day 1]
Monolith / microservice / hybrid. One paragraph defending the call from
business + operational angles (deploy cadence, failure domain, scaling axis) —
not framework hype.

## 2. Integration map                                  [Day 1 + Day 3]
Which existing systems / services this feature depends on, calls, or extends.
Drafted Day 1 as the 5-column table (system / owner / sync-async / R-W /
failure handling); references the C4 Container diagram drawn on Day 3.

## 3. Security & compliance constraints                [Day 2]
STRIDE pass summary — the 3–5 highest-priority threats and their concrete
mitigations. Updated security and compliance NFRs (replaces the Week-3 first
draft). Name which compliance frame applies (SOC 2 / privacy / industry).

## 4. SLO + rate-limit policy                          [Day 4]
- Latency: p50 / p95 / p99 targets, each with a one-line defense
- Availability: monthly target + error budget
- Rate limits: per-user / per-tenant / global, and what each protects

## 5. Top 5 trade-offs                                  [Day 5]
Each trade-off names: Option A, Option B, the call we made, the cost we accept,
and the trigger that would cause us to revisit. Span at least 3 categories.

## 6. Stakeholders + sign-off matrix                    [Day 5]
| Constraint (TCD section) | Stakeholder (a person) | Status | Next step |
|--------------------------|------------------------|--------|-----------|
|                          |                        |        |           |

Status vocabulary: Proposed / Discussed / Approved / Blocked.
```

---

## How the sections build on each other

- **§1 stance** sets the shape everything else documents. A modular-monolith stance shows in §2 as one container with internal modules.
- **§2 integrations** are the boundaries §3 threat-models — every integration either appears in the threat model or has an explicit "no threat" rationale.
- **§3 security NFRs** must not silently conflict with **§4 SLOs**; if they do, that tension is a **§5 trade-off**.
- **§5 trade-offs** and **§6 owners** are what a senior architect interrogates first — every load-bearing decision has an owner in §6.

## Friday review rubric (score 0–4 per dimension)

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| Stance defensibility | 20% | Architecture call defended in business terms; framework hype absent |
| Threat-model rigor | 20% | 3–5 named threats with concrete mitigations; not boilerplate |
| Component clarity | 15% | C4 diagram readable; external dependencies named |
| SLO realism | 20% | Targets anchored to user behavior; error budget the team will actually keep |
| Trade-off honesty | 15% | Both sides named; trigger to revisit specified |
| Stakeholder map | 10% | Each constraint has an owner; sign-off status is honest |

**The bar:** a one- to two-page TCD an architect or engineering lead would accept as scoping input. The TCD ships alongside the PRD into Week 5.
