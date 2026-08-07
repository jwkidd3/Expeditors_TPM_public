# Translation Drill Pack — 6 Technical Statements

> **Day 3 · Activity 1 handout.** Six technical statements, each paired with a stakeholder and their currency. Your quad picks 3, and writes the **business-framing** version for each — the same trade-off, re-framed in terms the audience already cares about. Then critique: would they act on it? What's their first follow-up?

Re-framing is not "use simpler words." It is naming the trade-off in the audience's currency: cost, customer outcome, regulatory exposure, revenue, operational risk, or velocity. All statements are drawn from the FieldPulse "End-of-Day Reconcile" work.

---

| # | Technical statement | Stakeholder | Their currency |
|---|---------------------|-------------|----------------|
| 1 | "We're using read replicas, which will introduce up to 3-second consistency lag." | Customer Success | Customer impact |
| 2 | "The p99 latency budget can't fit our happy path; we propose relaxing to p95." | Eng Director | Engineering velocity |
| 3 | "We need an additional region to satisfy data residency for 8% of customers." | CFO | Cost |
| 4 | "Token-based auth requires a new SSO scope from the Identity team." | Identity team lead | Operational risk |
| 5 | "We're deferring tablet support to v2." | Sales lead | Revenue / deal velocity |
| 6 | "Audit-log retention requires 24 months of cold storage." | Compliance owner | Regulatory exposure |

---

## Per-statement worksheet

For each of the 3 you pick:

```markdown
### Statement #_ — for <stakeholder>

**Business-framing version:**
<Same trade-off, in their currency. State what we're choosing, what we're
giving up, and — where relevant — the number that makes it concrete.>

**Would they act on this?** yes / needs more
**Their likely first follow-up:**
<The obvious next question. Answer it in the brief if you can.>
**What's still missing:**
```

## Calibration notes (read before you start)

- **#2 (Eng Director)** — an eng director does **not** need re-framing into business terms. Keep it technical; just name the trade-off clearly (what p95-instead-of-p99 costs in tail latency, and why the happy path can't hold p99).
- **#3 (CFO)** — "an additional region" without a **dollar number** is a non-answer. Compute the cost, or the CFO can't decide.
- **#5 (Sales lead)** — anticipate the obvious next question: **"what's the revenue at risk?"** A deferral note that doesn't name the deals or ARR exposed will bounce.
- **#1 (Customer Success)** — translate "3-second lag" into what a dispatcher like Maria actually sees on screen, not milliseconds.
- **#6 (Compliance)** — frame retention in terms of what an auditor asks for, and what happens if the window is shorter than a regulation requires.
- **#4 (Identity lead)** — operational risk means: what breaks in *their* system, and what they'd own if the new scope is misused.

## The bar for "good"

- The re-frame names a **specific** thing the stakeholder cares about — not "this is important to you."
- Where money or time is the currency, there is an **actual number** (or an honest "we owe you this number by <date>").
- You've written down the **first follow-up** and, ideally, answered it.
