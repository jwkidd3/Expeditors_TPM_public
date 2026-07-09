# Day 5 — Negotiating Priorities & Roadmaps (Live Simulations) · Facilitator Guide

> Companion to `labs/day-05-negotiation-simulation.md`. Facilitator-only — do not hand to participants.

## Pre-flight

- Post sim pairings at 09:00: pair triad A with triad B (and so on). Each triad plays "stakeholder" for one of their counterpart's negotiations.
- Have the three role-play card sets ready to hand to the **stakeholder-side** triad each round (do not give them to the author side):
  - Round 1: `week-06/handouts/surprise-objection-set.md`
  - Round 2: `week-06/handouts/scope-creep-ask-cards.md`
  - Round 3: `week-06/handouts/executive-demand-scenario-cards.md`
- Only the **public surface** of each card is shared with both triads (stakeholder type / role / demand). The roleplayer-only Hidden section goes to the stakeholder triad alone — the author must not see it before the round.

## Round 1 — Architecture / SLO Negotiation

**How to run the surprise:** the author already has the objection map they wrote Day 4, so the stakeholder triad uses **surprise objections not in that map** to push past rehearsed answers. Deliver objection 1, let the author respond fully and restate their answer back, then escalate to objection 2 only if they're holding up. If they're drowning, stay on the first and let them recover or close. Keep the exchange to 12–15 minutes and drive to a specific outcome (agreement, deferral, or named escalation). These live in `week-06/handouts/surprise-objection-set.md`; the answer-key content per stakeholder type:

**Architect**
- Surprise objection 1 (open here): "I just talked to the inventory-service team lead. They're **rebuilding that pipeline next quarter**. Why are we coupling Reconcile to it *now*, right before they tear it up?"
- Surprise objection 2 (escalate if the author recovers): "Your latency budget assumes the Tickets module sits at **p95 = 100ms**. I just pulled data — it's at **p95 = 250ms** today. Your whole SLO math is built on a stale number."
- How to play it: Objection 1 tests whether they'll re-sequence or defer. Objection 2 tests whether they'll defend the SLO or fold it. Reward a TPM who asks *when* the rebuild lands and whether a temporary coupling is acceptable. Give ground only if they surface a real trade-space move.

**Security Lead**
- Surprise objection 1 (open here): "I need your **data-retention policy in writing** before I sign off. What you described verbally doesn't match what I'd have to file with a regulator — and I'm the one who files it."
- Surprise objection 2 (escalate if the author recovers): "Your idempotency-key approach for the audit events — **what stops a malicious client from replaying old keys** to forge or duplicate audit records?"
- How to play it: Objection 1 tests whether they'll over-promise ("we'll get you that") vs commit to a specific artifact and date. Objection 2 is technical and hostile — push hard; a TPM who hand-waves the replay question should not get sign-off. Reward one who names the actual mitigation (key expiry, signed events, dedup window).

**Eng Director**
- Surprise objection 1 (open here): "We have **3 other features competing for sprint slots** this quarter. Make the case: why should Reconcile win over the others?"
- Surprise objection 2 (escalate if the author recovers): "I want to see your **engineering capacity model**. What velocity assumption is this plan built on? Because the last two estimates from this squad were 30% light."
- How to play it: Objection 1 tests prioritization framing in *business* terms, not passion. Objection 2 tests whether the plan has a defensible capacity basis or is wishful. Reward a TPM who cites the customer/renewal impact and offers a trade-space move (cut scope, extend date) rather than insisting the estimate is fine.

**Debrief prompts (per round):**

- What was the highest-leverage moment?
- What did the author triad *not* hear from the stakeholder?
- What language did the author triad use that should be retired?
- Score both sides on the rubric, then swap roles and repeat.

## Round 2 — Scope Negotiation

**How to run it:** the non-technical stakeholder triad arrives with a pre-loaded **scope-creep ask** from `week-06/handouts/scope-creep-ask-cards.md` (PM Director / Customer Success Lead / Sales VP). Only the public ask is shared with the author; any roleplayer-only pressure notes stay with the stakeholder side. The author defends PRD §3 non-goals and PRD §11 out-of-scope follow-ups.

**Watch-for:** which trade-space axis (scope / time / quality / resources) the stakeholder pushes vs which the author offers. A skilled author identifies the axis the stakeholder cares most about and offers movement on a *different* one. If nothing can move, it's a yes/no, not a negotiation.

**Debrief prompts:**

- Which axis did the stakeholder push? Which did the author offer?
- Did the author hold any non-goal? Which one?
- What "yes-but" was offered?

## Round 3 — Resource / Timeline Negotiation

**How to run the surprise:** fresh pairing; one triad plays an executive (CFO / GM) from `week-06/handouts/executive-demand-scenario-cards.md`. The executive opens with the **demand only** and offers no give — the author must find the trade space. Each card's Hidden section carries the real driver and the actual settle point; do not reveal it — make the author find the real constraint. Agree somewhere by the end (a hard executive who never yields teaches nothing). Force the close: no round ends without an owner + next step. The answer-key content per card:

- **Card 1 — "Ship 30% sooner." (CFO):** Real driver is a **board update in six weeks** — the CFO wants something *demoable* by then, not the whole feature. Settle for a **thin, demoable slice** on the earlier date with the full feature on the original date, if the author surfaces that scope-axis trade themselves. Reject "we'll just work harder"; reward naming what moves (cut demo scope, add a contractor, lower demo polish). Hold firm until they offer movement on at least two axes.
- **Card 2 — "You've lost an engineer." (GM):** The reassignment is **non-negotiable** — that engineer is gone. But the *date* has more give than admitted; the customer commitment is soft for ~two weeks. Accept a **date slip of up to ~2 weeks** or a **scope cut** to the original date — whichever the author proposes with reasoning. Do *not* accept "everything's fine, we'll manage" — that's the fold you're testing for. Reward capacity math (velocity × headcount) and a concrete cut or slip.
- **Card 3 — "Add the adjacent feature." (GM / CFO):** The inventory-sync feature depends on the **inventory-service** the Eng lead is already worried about — genuinely risky. The executive doesn't know that yet; a good author surfaces it and *that* changes the ask. Settle for a **phased commitment** (inventory-sync in the *next* release with a committed date) or a **scope-for-scope swap** (drop a lower-value item to fit a thin version). Reject a flat "no"; reward an author who protects the dependency risk as a non-negotiable while offering a real path on time or scope.

**What "good" looks like (author side):**

- Surfaces all four trade-space axes; offers movement on **at least two**.
- **Protects the non-negotiables** from Day 4 — names them out loud rather than quietly conceding.
- Names the **capacity or cost math**, not just a feeling.
- Closes with a specific outcome: agreement, phased commitment, deferral to a date, or a clean escalation.

**Debrief prompts:**

- Which axes did the author offer? Which did the stakeholder accept?
- Did anyone fold a non-negotiable? Why?
- What's the "owner + next step"? (Force this — don't let the round end without it.)

## Facilitator wrap (15 min, end of week)

- Read aloud the **best line of negotiation** from each triad.
- Surface the **most common fold pattern** — coach for next time.
- Preview Week 7: the negotiated commitments become the **input to sprint planning**. Constraints that survived become the work; deferred items become the backlog; rejected asks get a documented "no" with reasoning.

## Facilitator reflection prompts (end of week)

- Which triad held the line most credibly? They are the Week-7 positive example.
- Which triad **discovered** the trade space rather than improvising? Hold up Friday.
- Did anyone have a moment of "I wish I'd said X" that they should rehearse for next time?
- Which triad's outcomes log is most actionable — owners, dates, specifics? That's the senior signal.
