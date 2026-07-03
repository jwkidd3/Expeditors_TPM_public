# Product Analytics Export — FieldPulse Dispatcher App

> **Ambient context introduced Day 1; the section-time chart is used Day 3, the reconcile funnel Day 4.** Two aggregated views from the dispatcher web app. Analytics tell you **what** happens, not **why** — pair every number here with a quote or observation before you call it a pain. Aggregated across 90 dispatchers over a 30-day window; no individual is identifiable.

---

## View 1 — Average time-in-app per section (per dispatcher, per day)

*Where dispatchers actually spend their time in the product. Minutes/day, averaged across 90 dispatchers.*

| Section | Avg min/day | Relative |
|---|---:|---|
| Dispatch / schedule board | 47 | `█████████████████████████` |
| End-of-day reconcile | 38 | `████████████████████` |
| Job detail | 21 | `███████████` |
| Reports | 9 | `█████` |
| Inventory | 6 | `███` |
| Messaging | 5 | `███` |

> Reading note: the reconcile section consumes nearly as much time as the core dispatch board, and far more than inventory or messaging — despite reconcile being a once-a-day task and dispatch being all-day. What that *means* is for you to determine.

---

## View 2 — End-of-Day Reconcile funnel (7 steps)

*Share of started reconcile sessions that reach each step. Same 30-day window, 90 dispatchers, ~2,400 reconcile sessions.*

| Step | Stage | % of sessions reaching step |
|---|---|---:|
| 1 | Open reconcile | 100% |
| 2 | Review completed jobs | 96% |
| 3 | Match field tickets | 88% |
| 4 | **Confirm parts used** | **35%** |
| 5 | Adjust job times | 31% |
| 6 | Sign-off | 29% |
| 7 | Submit | 27% |

> **Headline:** ~**65% of reconcile sessions are abandoned at step 4 ("Confirm parts used")** — the single largest drop in the flow. Only about 1 in 4 sessions reach Submit inside the app. Where the other sessions go (paper? spreadsheet? next morning?) is not visible in this export — that's a question for the interviews and tickets.

---

## View 3 — Field-submit success rate (technician mobile app)

*Supporting cut, included for context. Share of field ticket-submit attempts that succeed on first try, by connectivity.*

| Connectivity | First-try submit success |
|---|---:|
| Strong signal (Wi-Fi / LTE) | 94% |
| Weak signal (1–2 bars) | 41% |
| No signal (offline attempt) | 6% |

---

*Methodology: event data from the dispatcher web app and technician mobile app, 30-day window, aggregated across 90 dispatchers and their technicians. Percentages rounded. This export is descriptive only — it contains no conclusions and no prioritization.*
