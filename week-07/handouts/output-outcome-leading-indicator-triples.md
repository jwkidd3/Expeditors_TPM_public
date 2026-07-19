# Output / Outcome / Leading-Indicator Triples (DP Section 3)

> **Day 3 · Activity 1 handout.** The central tracking table: every meaningful output paired with the outcome it should produce and the earliest signal you'd watch.

For every meaningful output, the tracking plan has three columns. The **leading indicator** is the muscle — without it, the team waits 30 days to learn the outcome failed. With it, they know within a week whether the trend is right.

## Fill in your triples

| Output (what shipped) | Outcome (what changed for users / business) | Leading indicator (the early signal) |
|-----------------------|---------------------------------------------|--------------------------------------|
| <output> | <outcome> | <leading indicator, measurable within 7 days> |
| | | |
| | | |
| | | |
| | | |

Aim for **5–8 outputs** (not every story produces a distinct outcome). Several outputs may share an outcome — that's fine.

---

## Worked sample — FieldPulse

| Output | Outcome | Leading indicator |
|--------|---------|-------------------|
| Reconcile mobile flow shipped | Median reconcile time 45→12 min in 30d | First-attempt completion ≥ 80% by week 2 |
| Idempotent submission | Submission error rate < 0.1% | Duplicate-submit rate < 0.5% in week 1 |
| Audit event publishing | SOC 2 audit passes Q3 review | Event volume + DLQ depth steady through week 4 |
| Inline error states + recovery | Customer support tickets about reconcile drop 50% | Tickets per dispatcher per week declining starting week 3 |
| WCAG AA conformance | Zero accessibility complaints in 90 days | axe-core scan pass rate 100% on every PR from week 1 |

---

## What "good" looks like

- Each triple is **specific**, not "we'll watch some metrics."
- Leading indicators are **measurable within 7 days** of launch.
- Outcomes are **user-visible** (not an output dressed up).
- **Counter-metrics** are referenced (from your NS Defense Card).
