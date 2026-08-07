# Week-2 Feature Cards — FieldPulse Dispatcher Workflow

> **Day 1 · Activity 1 handout.** Three candidate feature concepts your quad carries from Week 2. Re-read all three aloud, score each on the four dimensions, then commit to exactly one to PRD this week. (If your quad produced its own Week-2 cards, use those instead — these are a backstop set grounded in the FieldPulse canon.)

Each card is one candidate. None is "the right answer" — the discipline of choosing is the work.

---

## Feature Card A — Truck-Stock Quick View

**One-liner:** A one-tap inventory panel on the tech mobile app that shows what's on the truck, so dispatchers stop re-routing techs who are already out of the part.

**Origin friction (Week 1):** Maria R. keeps truck stock in a paper notebook; the in-app inventory view is 3 clicks deep and she never trusts it. Mid-day, she re-routes a tech to a supply house for a part that was already on another truck.

**Persona most helped:** Maria R. (12yr, 90-tech shop).

**Journey friction star:** "Assign job → check parts availability" — currently a guess, so re-routes happen after dispatch.

**Rough shape:** Surface a live truck-stock summary at the point of assignment (dispatcher web) and on the tech's job screen (mobile). Read-only in v1.

**Tier Sheet metric it targets:** Mid-day re-route rate (op-signal).

---

## Feature Card B — Reconcile Confidence Banner

**One-liner:** A pre-submit banner on the End-of-Day Reconcile flow that flags tickets with missing time or parts data before the dispatcher submits, so Susana's payroll run stops bouncing back.

**Origin friction (Week 1):** Susana O. runs payroll against reconcile data every Wednesday; incomplete tickets surface only after she's mid-run, and chasing techs for missing entries is the real bottleneck.

**Persona most helped:** Susana O. (18yr, 160-tech shop, owner's daughter).

**Journey friction star:** "Submit reconcile → payroll export" — incompleteness discovered too late, downstream of the dispatcher.

**Rough shape:** Before "Submit reconcile", scan selected tickets for missing required fields; show a banner listing incomplete tickets with a jump-to-fix action. Does not block submit.

**Tier Sheet metric it targets:** Reconcile completeness at submit (op-signal); secondary: payroll rework rate.

---

## Feature Card C — Re-Route Undo & Trace

**One-liner:** A short undo window plus a visible trace of who re-routed whom, so Trey stops confidently misremembering the day's changes and dispatchers can reverse a bad re-route.

**Origin friction (Week 1):** Trey W. (former tech, 3yr, 60-tech shop) confidently misremembers which techs he moved and when; there's no record, so disputes at end of shift are unresolvable.

**Persona most helped:** Trey W. (3yr, 60-tech shop).

**Journey friction star:** "Re-route tech mid-day" — no undo, no record, disputes at end of shift.

**Rough shape:** A 60-second undo on any re-route, plus an append-only re-route log visible on the dispatcher board (who, whom, when, why-note optional).

**Tier Sheet metric it targets:** End-of-shift dispute count (op-signal); secondary: re-route reversal rate.

---

### After you score these

Total each card across the four dimensions on the **Four-Dimension Scoring Sheet**, pick one, and write the **"Why this one" memo**. The memo seeds Section 1 (Context) of your PRD.
