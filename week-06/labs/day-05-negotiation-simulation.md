# Day 5 — Negotiating Priorities & Roadmaps (Live Simulations)

> **Activity packet** for participant triads. Today's job: run **three rounds of simulated negotiation**, capture outcomes, and ship the SEP — the fourth and final sibling artifact alongside PRD / TCD / TMD.

## Where we are in the week

§§1–4 of the SEP are ready. Today is the live exercise: three rounds of simulated negotiation, with triads playing each other's stakeholders. By 16:00, every triad has logged outcomes, written the §5 outcomes log, and shipped the SEP.

## Today's cadence

| Clock | Block | What happens |
|-------|-------|--------------|
| 09:00 – 09:15 | Opening; sim pairings posted; rubric reminder | Pair triad A with triad B (and so on); each triad plays "stakeholder" for one of their counterpart's negotiations |
| 09:15 – 10:45 | **Round 1 — Architecture / SLO negotiation** | First triad negotiates one TCD §4 SLO or §5 trade-off |
| 10:45 – 11:00 | Break | |
| 11:00 – 12:00 | Round 1 debrief + Round 2 prep | Capture outcomes; swap setups |
| 12:00 – 13:00 | Lunch | |
| 13:00 – 14:30 | **Round 2 — Scope negotiation** | Negotiate a non-goal challenge or scope-creep ask |
| 14:30 – 14:45 | Break | |
| 14:45 – 15:45 | **Round 3 — Resource / timeline negotiation** | Cross-team dependency or roadmap ask |
| 15:45 – 16:00 | Wrap + sign-off | SEP §5 outcomes log finalized |

## The three rounds — what each is for

### Round 1: Architecture / SLO
**Triad A is the author**; **triad B plays a high-power technical stakeholder** (architect, security lead, eng director).

The author triad pitches the trade-off they wrote up Day 3. The stakeholder triad pushes back using the objection map from Day 4 — and improvises further objections.

### Round 2: Scope
**Triad B is the author**; **triad A plays a non-technical stakeholder** (PM director, customer success lead, sales VP).

The author triad defends their PRD scope. The stakeholder triad challenges with a scope-creep ask: "we need this feature to also do X" or "we need this earlier."

### Round 3: Resource / timeline
Triads pair freshly. **One triad plays an executive** (CFO, GM); the other negotiates a resource or timeline change.

Specifically: an executive demands the feature ship 30% sooner, OR cuts the team by one engineer, OR demands a feature added without scope cuts. The author negotiates against impossible asks.

---

## The negotiation rubric (live scoring)

Each triad scores both sides of each round on:

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| **Listened first** | 20% | Restated the stakeholder's concern before responding |
| **Translated tech to business** | 20% | No unexplained jargon; framed cost in business terms |
| **Held the line where it mattered** | 15% | Did not surrender constraints under social pressure without rationale |
| **Found the trade space** | 20% | Surfaced what could move (scope, time, quality, resources) |
| **Captured the outcome** | 15% | Specific, written, with owner + next step |
| **Body / pacing / closure** | 10% | Conversation reached a decision (or explicit deferral) |

Each round runs ~30 minutes:

- **5 min** prep (re-read packet)
- **15 min** live negotiation
- **10 min** debrief + capture

---

## The outcomes log template (SEP §5)

For each round, capture:

```markdown
### Round N: <topic>
**Triad A (author):** <names>  |  **Triad B (stakeholder):** <names>
**Stakeholder role played:** <e.g., Architect>

**The ask:**
<What the author triad asked for>

**Stakeholder's response:**
<What the stakeholder pushed back with — top 1-2 objections>

**The trade space surfaced:**
<What the author offered to move; what they held>

**Agreement:**
<What was agreed, or "deferred to <date>" or "disagreed; escalation
to <person>">

**Owner + next step:**
<Who does what, by when>

**What we learned:**
<One sentence — the muscle this round built>

**Score:**
- Author: total /4.0
- Stakeholder: total /4.0
```

---

## Round 1 — Architecture / SLO Negotiation

**Format:** Triad pairs &bull; **90 min total** (5 prep + 15 negotiate + 10 debrief, repeated to swap)

### The setup

Each author triad has the 1-page brief from Day 3 + the objection map from Day 4. The stakeholder triad plays a high-power technical role (architect, security lead, or eng director) and has the brief and the objection map (so they know what's coming), plus a **surprise-objection card** from `week-06/handouts/surprise-objection-set.md` — objections **not** in the author's prep, to push past their rehearsed answers.

The **public surface** of each surprise-objection card (the stakeholder type and role) is visible to both triads. The card's roleplayer-only content is for the stakeholder triad; the author triad does not see it before the round — that's the point.

### Triad protocol (per round)

1. **Author triad opens** (60 sec) — using their rehearsed opening from Day 4.
2. **Stakeholder triad responds** with their first objection. Author responds.
3. **Stakeholder triad escalates** with the surprise objection. Author improvises.
4. **The conversation runs 12–15 minutes total**, including pivots, restatements, attempts to find trade space.
5. **Both sides try to close** with a specific outcome — agreement, deferral, or escalation path.

### Debrief (10 min)

- What was the highest-leverage moment?
- What did the author triad *not* hear from the stakeholder?
- What language did the author triad use that should be retired?
- Score both sides on the rubric.

### Roles swap; repeat.

---

## Round 2 — Scope Negotiation

**Format:** Same setup; new pairing **or** same pair with role swap; **90 min**

### The setup

The non-technical stakeholder triad arrives with a **scope-creep ask** from the scope-creep ask cards (`week-06/handouts/scope-creep-ask-cards.md`). Examples of the kind of ask:

- **PM Director:** "Marketing wants us to add a manager-view dashboard before launch. It's a small ask but they're committed to a campaign."
- **Customer Success Lead:** "Our top-3 customer just asked for tablet support. They've made it a renewal condition."
- **Sales VP:** "We have a deal in flight that requires this feature to support multi-shop manager view. Help us make the deal."

The **public surface** (the stakeholder role and the ask) is visible to both triads. Any roleplayer-only content on the card is for the stakeholder triad only.

### The author triad's challenge

Defend the **non-goals** in PRD §3 and the **out-of-scope follow-ups** in PRD §11. Honestly evaluate whether to:

- Hold the line (and capture the no with reasoning)
- Cut existing scope to add the new ask
- Offer a phased plan
- Escalate (because the stakeholder has authority you'd defer to)

### The trade space (key concept introduced)

Negotiation surfaces when **at least one of these can move**:

- **Scope** (what's in)
- **Time** (when it ships)
- **Quality** (what level of polish)
- **Resources** (who's working on it)

If nothing can move, you're not negotiating — you're saying yes or no. A skilled TPM identifies which axis the stakeholder cares most about, and offers movement on a different axis.

### Debrief (10 min)

- Which axis did the stakeholder push? Which did the author offer?
- Did the author hold any non-goal? Which one?
- What "yes-but" was offered?

---

## Round 3 — Resource / Timeline Negotiation

**Format:** Fresh pairing; one triad plays executive; **60 min**

### The setup (the hard one)

The executive arrives with one of the demands from the executive-demand scenario cards (`week-06/handouts/executive-demand-scenario-cards.md`):

1. **"Ship 30% sooner."** No scope cut offered. The author negotiates on the trade space.
2. **"You've lost an engineer to a higher priority. Same scope, same date."** Same exercise from a different angle.
3. **"We need [adjacent feature] added. Same date, same team."** Scope expansion against constraints.

The **public surface** (the executive role and the demand) is visible to both triads. What's really driving the executive and where they'll settle is roleplayer-only content on the card — the author's job is to find it.

### What "good" looks like

The author triad surfaces all four trade-space axes and offers movement on at least two, while protecting their non-negotiables.

The stakeholder triad pushes hard but **agrees somewhere**, even if it's "deferred to next QBR."

### Debrief (10 min)

- Which axes did the author offer? Which did the stakeholder accept?
- Did anyone fold a non-negotiable? Why?
- What's the "owner + next step"? (Force this — don't let the round end without it.)

---

## SEP §5 — The Outcomes Log

By 15:45, every triad has §5 with three round entries. The polish:

- All three rounds documented in the template
- Owner + next step for each (no "TBD")
- Specific score totals
- One sentence per round on **what the team learned**

---

## End-of-week (Week 6) checkpoint

Each triad ships:

- [x] **Full SEP** with §§1–5
- [x] §1 Stakeholder map (Power × Interest + RACI + watch list)
- [x] §2 Engagement plan
- [x] §3 1-page trade-off brief
- [x] §4 Meeting prep + objection map
- [x] §5 **Three negotiation outcome logs**, with owners and next steps
- [x] AI provenance log entries from Days 4–5

The SEP joins the PRD / TCD / TMD as the fourth sibling artifact. Together they are the input to Week 7's delivery work.
