# Idempotency Card

> **Day 3 handout.** The "safe to retry" guarantee. Networks fail, clients retry — idempotency saves you from creating duplicate records. Decide, per mutating endpoint, *which* mechanism and *how long* the window is.

A request is **idempotent** if the same request, sent twice, produces the same result.

## Three ways to achieve idempotency

1. **Natural idempotence** — PUT and DELETE are idempotent by default.
2. **Idempotency-Key header** — the client sends a unique key; the server stores key + response and returns the same response on retry.
3. **Conditional requests** — `If-Match` / `If-None-Match` headers gate the operation.

## For each mutating endpoint, decide

- **Which** endpoints support idempotency.
- **How** — which of the three mechanisms above.
- **How long** the idempotency window is (typical: **24 hours**).

---

## Fill-in table

| Mutating endpoint | Mechanism | Window | Notes |
|-------------------|-----------|--------|-------|
| | | | |
| | | | |
| | | | |

## The half-decided trap

Idempotency without a **stated window** is half-decided. "We use an Idempotency-Key" is incomplete until you name the retention: 24 hours, 7 days — pick one and write it down. The invariant you're protecting reads like: *at most one record per (Idempotency-Key) per 24h.*
