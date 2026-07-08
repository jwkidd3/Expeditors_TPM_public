# Access Pattern Sheet

> **Day 1 handout.** Fill this in *before* you draw any schema. List every read and every write the feature needs, with frequency and freshness — the schema exists to serve these rows.

**Triad:** ______________________  **Feature:** ______________________

Surface every read and write first. The high-frequency reads (mark them) drive your index choices.

| # | Pattern | Type (R/W) | Data | Frequency | Freshness req. |
|---|---------|------------|------|-----------|-----------------|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |
| 4 | | | | | |
| 5 | | | | | |
| 6 | | | | | |

---

## How to fill each column

- **Pattern** — a one-line description of the query or action ("List a dispatcher's open tickets, sorted by latest activity").
- **Type** — R (read) or W (write).
- **Data** — what it reads/writes, roughly: `tickets WHERE dispatcher_id = ? AND status = open`.
- **Frequency** — how often it runs: every screen load / once per shift / rare.
- **Freshness req.** — how fresh the data must be: real-time / last-minute / last-hour / n/a.

## Two checks before you leave this sheet

- **Real-time is rare.** Most B2B features tolerate last-minute. If you wrote "real-time," be ready to defend it.
- **Every write needs an invariant.** For each write, ask "what would I *never* want to allow?" ("a ticket can only be reconciled once"). That's the invariant — carry it into the entity model.

## Highlight the high-volume reads

Circle the 1–2 reads that run **most often**. Those are the reads your indexes must serve.
