# Performance Baselines Template

> **Day 5 handout.** A baseline is what a metric reads *today* (or at launch). Without one, you can't tell whether you've improved. Set a baseline for every SLO plus a few operational signals — and a date to verify it against reality.

**Quad:** ______________________  **Feature:** ______________________

| Metric | Baseline | Source / assumption | Verify at |
|--------|----------|----------------------|-----------|
| | | | |
| | | | |
| | | | |
| | | | |
| | | | |

---

## Two kinds of baseline

| Kind | When | Source |
|------|------|--------|
| **Existing-system baseline** | Brownfield — improving something that exists | Production data (current dashboards, query histories) |
| **Expected-launch baseline** | Greenfield — new feature | Estimated from comparable features, load-test data, or "we expect X based on [reasoning]" |

For **greenfield**, state the **assumption** rather than skip the baseline. Example: "We expect ~200 reconcile-submits/day in the first 30 days, based on dispatcher count × shifts/day × estimated adoption rate." That assumption gets tested at launch + 7 days.

## What to baseline

For each TCD Section 4 SLO, capture the corresponding baseline — **latency**, **availability**, **throughput**, **error rate** — plus any **operational signal** from the Week-2 Tier Sheet that doesn't appear in the SLOs.

## What "good" looks like

- Every SLO has a **paired** baseline.
- Greenfield baselines **name the assumption** — never "we don't know."
- The **verify-at date is a concrete day**, not "TBD." A "TBD" verify date never gets audited.
