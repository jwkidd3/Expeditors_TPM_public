# DP Template

> **Day 1 handout.** The 5-section Delivery Plan (DP) skeleton your quad builds across Week 7 — the fifth and final sibling to your PRD, TCD, TMD, and SEP, and the artifact that turns a specified, negotiated design into a plan you can actually deliver and track. Print it, pin it, fill it section by section. Each section carries a `[Day X]` tag telling you when it gets written. Friday it ships, peer-reviewed.

---

```markdown
# Delivery Plan — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>, SEP <link>  |  **Authors:** <quad>  |  **Status:** Draft / Reviewed

## 1. Outcome map                                       [Day 1]
The customer-visible / business outcomes this feature is meant to produce,
tied to NS (North Star) / Tier-Sheet metrics. Each outcome carries a
leading indicator (measurable ≤7 days) and a guardrail (so we can't game it).

## 2. ADO backlog (loaded)                              [Day 2]
- Epic <link> → Features <links> → User Stories <links> → Tasks <links>
Hierarchy, fields, tags, and iteration paths populated in Azure DevOps.
Each story tags back to its PRD capability; saved queries work.

## 3. Tracking plan                                     [Day 3]
Output / Outcome / Leading-indicator triples per feature.
Each indicator has an ADO home (saved query, dashboard chart, or the board CFD).
Sprint + monthly review cadence named.

## 4. Value stream map                                  [Day 4]
End-to-end flow: idea → discovery → spec → build → ship → measure → iterate.
Per step: process time (PT), lead time (LT), flow efficiency, queue.
Name the dominant queue.

## 5. Bottleneck removal                                [Day 5]
Top 2–3 bottlenecks (from §4) with evidence + an experiment to test removal.
Each experiment: hypothesis, test, success criterion (baseline, target, window).
Plus the DP integration pass — references to PRD / TCD / TMD / SEP resolved.
```

---

## How the sections build on each other

- **§1 outcome map** is the *why* — it fixes the user-visible outcomes (tied to the North Star / Tier Sheet) that everything below has to serve. An output with no outcome here is a finding.
- **§2 ADO backlog** is the *what* — the Epic→Feature→Story tree that will deliver §1's outcomes; every story should trace to a PRD capability, not exist for its own sake.
- **§3 tracking plan** closes the loop between them — each **output** (a §2 story) is paired to an **outcome** (§1) and a **leading indicator** you can read within a week; an indicator with no ADO home is unverifiable.
- **§4 value stream** is the *how-fast* — it measures where time actually goes idea→value and names the dominant **queue**; the lead times here must be consistent with the SLOs in the TCD/TMD.
- **§5 bottleneck removal** acts on §4 — it attacks the queue §4 exposed (not a convenient one) with a falsifiable experiment, and the integration pass makes the DP cite its sibling artifacts by section.

**The bar:** a DP a delivery team could run the next sprint from — outcomes tied to metrics, a real ADO board, tracking that reads weekly, and one honest experiment on the actual bottleneck. It ships alongside the PRD, TCD, TMD, and SEP; together the five carry into Week 8's capstone.

*Each section has dedicated component handouts — `outcome-map-template` (§1); `ado-hierarchy-template`, `ado-saved-queries` (§2); `output-outcome-leading-indicator-triples`, `sprint-review-template`, `monthly-outcome-review-template` (§3); `vsm-canvas-template` (§4); `bottleneck-experiment-template` (§5); plus the `dp-integration-checklist`. Friday's scoring is on the separate `friday-review-rubric` handout.*
