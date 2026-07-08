# AI-Summary Validation Log

> **Day 5 handout.** This week's new discipline. AI is used to summarize dashboards, query results, and metric reports — the TPM job is to validate each summary against the source data and document the result. This log is cumulative across weeks.

For each AI-assisted summary used in any week's artifact, capture one row.

| # | Summary purpose | Prompt (link) | Source data | Validation |
|---|-----------------|---------------|-------------|------------|
| | | | | |
| | | | | |
| | | | | |
| | | | | |

---

## Why this matters — the failure modes

| Failure | What happens |
|---------|--------------|
| **Wrong number** | AI cites "p95 = 800ms" when the chart shows 1200ms |
| **Wrong direction** | AI says "improving" when the trend is flat or declining |
| **Wrong attribution** | AI explains a spike with the wrong cause |
| **Missing context** | AI summarizes the headline; misses the relevant footnote |

## Status values (use these in the Validation column)

- **Cross-checked all citations** — best; every claim verified against source.
- **Spot-checked** — rougher; N claims sampled and verified.
- **Adopted with rationale** — used the suggestion; correctness was self-evident or cheap to verify.
- **Pending** — used as input but not yet validated; **must have a deadline**.
- **Rejected** — output was wrong; cut.

## What "good" looks like

- Every AI use across the weeks has a **row** — enumerate from the Pattern Library, don't just log what you remember.
- Status values are **honest** (distinguish correct / partly correct / wrong, with evidence).
- Every **Pending** entry has a **named deadline** — Pending without a date becomes permanent.
- The log is a tool the **next TPM can audit**, not a checkbox.
