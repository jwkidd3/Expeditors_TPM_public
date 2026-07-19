# Objection Map Template

> **Day 4 · Activity 2 handout.** For each predicted objection from your stakeholder, capture the honest response, the pivot, and the smallest ground you'd give. This is the spine of SEP Section 4 meeting prep.

---

## How to build it

1. Predict the stakeholder's **top 5 objections**, ranked by intensity. Voice them honestly — not strawmen. At least one should be **hostile** (the one they'd push hardest).
2. For each, write an **honest response** (what's actually true — do not over-promise), a **pivot** (where to redirect if pushback continues), and **the line you hold** (the smallest ground you'd give if the objection wins).
3. Flag the **highest-stakes objection** — the one most likely to derail the meeting — and rehearse it aloud.

## Per-objection template

```markdown
### Objection N: <short name>
**The stakeholder says:** <quoted, in their voice>

**The honest response:** <what's actually true; do not over-promise>

**The pivot (if pushback continues):** <where to redirect — usually
to a deeper "why" or to a documented trade-off>

**The line we hold:** <if this objection wins, what's the smallest
ground we give up?>
```

## Worked example — Compliance, async audit write

```markdown
### Objection 3: Regulator can't see events in real time
**The stakeholder says:** "If an auditor pulls the log mid-incident,
they'll see stale state. That's on me to explain."

**The honest response:** Events are durable at action-time (Kafka + DLQ);
the store lags 1–10s, not the record itself. Nothing is lost — only
delayed in the read model.

**The pivot (if pushback continues):** We can bound the lag with an SLO
(≤ 10s p99) and alert on breach, so you have a defensible number to cite.

**The line we hold:** We hold durability and the ≤10s p99 bound. We would
NOT commit to synchronous < 1s write unless a contract requires it — that
breaks the dispatcher p95 SLO.
```

## The bar for "good"

- Objections sound **like the stakeholder would actually say them**, not strawmen.
- "The honest response" states what's **true**, not just what persuades.
- "The line we hold" is **specific** — not "we'll compromise."
- The highest-stakes objection has a **rehearsed** response by the end.

---

## Non-negotiables (pairs with the objection map)

The 1–3 things you cannot give up. Knowing these before the meeting is the defense against folding under pressure.

- Each non-negotiable is **specific** — not "quality" or "the user."
- Each has a **fallback** — the scope / time / approach you'd give up to protect it.
- The list is **short**: 3 maximum. (Teams with 6+ non-negotiables fold, because they can't defend them all.)

| Non-negotiable | Fallback (what we'd cut to protect it) |
|----------------|----------------------------------------|
| | |
| | |
| | |

_Examples:_ "We will not compromise the audit-trail retention requirement." · "We will not slip launch past July 1 — we'll cut scope first." · "We will not break the SSO scope contract with Identity."
