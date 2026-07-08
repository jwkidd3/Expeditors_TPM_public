# Surprise-Objection Set — Round 1 (Architecture / SLO)

> **Day 5 · Round 1 handout.** For the triad **playing the technical stakeholder**. In Round 1, the author triad already has the objection map they wrote Day 4 — so you use these **surprise objections** (not in their map) to push past the rehearsed answers. Deliver one, listen, then escalate with the second if the author is holding up.

**Public surface (both triads may read):** the stakeholder type and role.
**Hidden (roleplayer only):** the two surprise objections and how hard to push. Do **not** show the author triad the Hidden section before the round — the point is that these aren't in their prep.

All objections are grounded in the FieldPulse "End-of-Day Reconcile" world (async audit write, inventory-service dependency, dispatcher p95 SLO).

---

## Stakeholder A — Architect

**Public surface**
- Owns FieldPulse's architectural posture
- Cares about long-term coherence, not this quarter's ship date
- Skeptical of adding load to shared services

**Hidden — roleplayer only**

*Surprise objection 1 (open here):*
> "I just talked to the inventory-service team lead. They're **rebuilding that pipeline next quarter**. Why are we coupling Reconcile to it *now*, right before they tear it up?"

*Surprise objection 2 (escalate if the author recovers):*
> "Your latency budget assumes the Tickets module sits at **p95 = 100ms**. I just pulled data — it's at **p95 = 250ms** today. Your whole SLO math is built on a stale number."

*How to play it:* Objection 1 tests whether they'll re-sequence or defer. Objection 2 tests whether they'll defend the SLO or fold it. Reward a TPM who asks *when* the rebuild lands and whether a temporary coupling is acceptable. Give ground only if they surface a real trade-space move.

---

## Stakeholder B — Security Lead

**Public surface**
- Signs off on Reconcile before launch; files what they approve with regulators
- Wants everything in writing
- Will block, not just comment, if evidence is missing

**Hidden — roleplayer only**

*Surprise objection 1 (open here):*
> "I need your **data-retention policy in writing** before I sign off. What you described verbally doesn't match what I'd have to file with a regulator — and I'm the one who files it."

*Surprise objection 2 (escalate if the author recovers):*
> "Your idempotency-key approach for the audit events — **what stops a malicious client from replaying old keys** to forge or duplicate audit records?"

*How to play it:* Objection 1 tests whether they'll over-promise ("we'll get you that") vs commit to a specific artifact and date. Objection 2 is technical and hostile — push hard; a TPM who hand-waves the replay question should not get sign-off. Reward one who names the actual mitigation (key expiry, signed events, dedup window).

---

## Stakeholder C — Eng Director

**Public surface**
- Owns the squad's capacity and sprint slots
- Accountable for the launch date (RACI A)
- Weighs Reconcile against everything else competing for the team

**Hidden — roleplayer only**

*Surprise objection 1 (open here):*
> "We have **3 other features competing for sprint slots** this quarter. Make the case: why should Reconcile win over the others?"

*Surprise objection 2 (escalate if the author recovers):*
> "I want to see your **engineering capacity model**. What velocity assumption is this plan built on? Because the last two estimates from this squad were 30% light."

*How to play it:* Objection 1 tests prioritization framing in *business* terms, not passion. Objection 2 tests whether the plan has a defensible capacity basis or is wishful. Reward a TPM who cites the customer/renewal impact and offers a trade-space move (cut scope, extend date) rather than insisting the estimate is fine.

---

### Roleplayer reminders

- Open with objection 1. Let the author respond fully — restate their answer back before you escalate.
- Escalate to objection 2 only if they've handled the first; if they're drowning, stay on the first and let them recover or close.
- You are pushing hard, but you are **not immovable** — a genuine trade-space offer (scope / time / quality / resources) can earn a "deferred to next QBR" or a conditional yes.
- Keep the whole exchange to 12–15 minutes. Help them reach a specific outcome — agreement, deferral, or a named escalation path.
