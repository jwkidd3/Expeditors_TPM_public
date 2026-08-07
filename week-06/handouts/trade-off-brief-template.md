# One-Page Trade-Off Brief Template

> **Day 3 · Activity 3 handout.** Translate one technical trade-off into a brief a non-technical stakeholder can act on. The discipline: the **whole brief fits on one page**; the appendix is references, not body. This becomes SEP Section 3.

---

## The translation discipline

Translating technical to business is not "use simpler words." It is **re-framing**: the same trade-off, expressed in terms the audience already cares about.

| Technical framing | Business framing |
|-------------------|------------------|
| "We chose async write to audit because sync would breach our p95 SLO" | "We chose to ship 50ms faster on the dispatcher screen, accepting that audit logs may lag 10 seconds — relevant to compliance Q3 review timing" |
| "We accepted a denormalized ticket_ids array in ReconcileEvent" | "We're optimizing reconcile reads at the cost of a future query type. We'd revisit if that query becomes hot" |
| "We're shipping a modular monolith, not a service" | "We're shipping faster by not separating this code; we accept the cost of a future split if traffic grows 5x" |

## What they need to know vs decide

| What they need to know | What they need to decide |
|------------------------|--------------------------|
| The headline outcome | Whether to approve the choice |
| The cost we're accepting | Whether the cost is acceptable |
| The trigger to revisit | Whether the trigger is well-chosen |
| What we need from them | Whether to provide it |

Strip everything else. Detail goes in the appendix or "available on request."

## The template

```markdown
# Trade-off brief: <short feature name>
**For:** <stakeholder name>  |  **From:** <quad>  |  **Date:** <today>

## The decision (1 sentence)
We are choosing [X] over [Y] for the <feature> work, accepting [cost].

## Why this matters to you (1–2 sentences in their currency)
<Cost / customer outcome / regulatory exposure / time>

## The choice
- **What we're doing:** <plain language; 2–3 bullets>
- **What we're explicitly not doing:** <2–3 bullets>
- **The cost we're accepting:** <1 bullet>

## What would change our mind
<Concrete trigger; metric or organizational change>

## What we need from you
☐ Approval to proceed as proposed
☐ Specific concern you want us to address
☐ Information we don't have

## Appendix (linked, not pasted)
- Technical detail in TCD Section 5 / TMD SectionX
- Sequence diagram
- SLO budget
```

## Worked example — async audit write brief for Compliance

```markdown
# Trade-off brief: Reconcile audit write timing
**For:** Pat Lee, Compliance Owner  |  **From:** Reconcile quad  |  **Date:** 2026-04-29

## The decision
We are choosing async audit write (1–10s lag) over synchronous (instant)
to keep dispatcher reconcile screens fast.

## Why this matters to you
This affects the audit-trail timing your SOC 2 process depends on. Audit
events are still durable (Event Hubs stream + DLQ) — they just appear in the
audit store 1–10 seconds after the user action.

## The choice
- **What we're doing:** Publish audit events to a durable Event Hubs stream at
  user-action time; consumer writes to the audit store within 1–10 seconds.
- **What we're explicitly not doing:** Synchronous write to the audit store
  on the user's hot path (would add 30–80ms; breaks our p95 SLO).
- **The cost we're accepting:** A regulator querying within 5 seconds of
  an event sees stale state.

## What would change our mind
A regulator or customer contractually requires synchronous audit
visibility within < 1 second.

## What we need from you
☐ Approval that the 1–10s lag is acceptable for our SOC 2 process
☐ Confirmation of acceptable lag bound (we propose ≤ 10s p99)
☐ Note of any contract requiring sync audit (we know of none)

## Appendix
- Technical detail: TCD Section 5 trade-off 2, TMD Section 4 sequence diagrams
- Latency budget: TCD Section 4
```

## The bar for "good"

- **Whole brief on one page** — the constraint is forcing.
- **Plain language** in the headline; technical terms only in appendix references.
- **Cost in their currency** — dollars for CFO, customer experience for CS, audit risk for Compliance.
- **Specific ask** at the end — not "thoughts welcome."
