# Day 2 — Defining the North Star Metric

> **Activity packet for participant triads.** Today's job: take yesterday's NS placeholder and stress-test it into a North Star you can defend in front of a CEO and a dispatcher in the same conversation.

## Where we are in the week

Day 1 produced a Metrics Tier Sheet with a placeholder NS. Today we replace the placeholder with a defensible NS — and along the way, the cohort encounters the **three standard pitfalls** that catch even seasoned PMs.

By 16:00, every triad will have:

- A **North Star statement** that names the customer outcome, the segment, and the measurement
- A **defense card** that names the three pitfalls applied to their own NS and rebuts each
- A **revised Metrics Tier Sheet** with the placeholder replaced

---

## The three standard pitfalls (today's mental model)

| Pitfall | What it looks like | The tell |
|---------|--------------------|----------|
| **1. Vanity dressed up** | "Total active users" or "ARR" — sounds north-star-ish, isn't | Customers don't feel it directly when this number moves |
| **2. Leading-indicator confusion** | "Time-to-first-value" — actually a KPI or even op-signal | A team can move it without the customer being any better off long-term |
| **3. Gameable target** | "Daily Active Users" with no usage-quality gate | A team can hit the target with sales tactics or notification spam |

Every well-formed NS has been challenged against all three and survived.

---

## Activity 1 — Three Pitfalls Triage

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Recognize the three pitfalls in real-world examples before applying them to your own NS — pattern-recognition before self-diagnosis.

### Setup
Each triad has the example pack of 8 anonymized public-company NS candidates.

### Steps

### The example pack (8 NS candidates from public companies, anonymized)

1. "Monthly Active Riders" — ride-share co.
2. "Total Bookings Volume" — hospitality marketplace
3. "Hours Watched per Day" — streaming service
4. "Songs Saved to Library" — music streaming
5. "Daily Active Users" — social network
6. "Annual Recurring Revenue" — vertical SaaS
7. "Successful Deliveries per Active Customer per Month" — logistics SaaS (Expeditors-adjacent)
8. "Queries Resolved without Human Escalation" — customer support SaaS

### Triad protocol

For each card, the triad assigns **0, 1, 2, or 3** pitfalls present and writes a 1-line argument.

### Readout (60 seconds per triad)

> "We give [X] a clean bill of health because [reason]. We give [Y] all three pitfalls because [reason]."

### Deliverable

A scored card pack per triad: each card tagged with 0–3 pitfalls and a one-line argument; one clean-bill-of-health pick and one all-three pick identified.

---

## Activity 2 — Re-write Your NS

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Apply yesterday's placeholder + today's pitfalls to draft a defensible NS for the triad's Week-1 problem.

### Setup
Each triad has its Day-1 NS placeholder visible, plus the Day-2 three-pitfalls vocabulary fresh from Activity 1.

### Steps

### Triad protocol

1. **Read your placeholder NS aloud** (each triad member, then a 2-minute discussion of dissatisfaction).
2. **Generate three NS candidates** (15 min). Each member proposes one. They must:
    - Name a customer outcome (verb-based, not feature-based)
    - Specify a user segment narrowly
    - Be expressible as a single number
3. **Pitfall-test each candidate** (15 min). For each: which of the three pitfalls is closest to true? Can you rebut?
4. **Converge on one** (10 min). The winner gets written into the **NS Defense Card** template (below).

### NS Defense Card template

```markdown
## North Star
We are winning when [outcome] increases for [segment],
measured by [number].

## Pitfall rebuttals
- **Vanity:** Why does this number changing mean a customer's life got better?
  > [your answer in <30 words]
- **Leading-indicator:** Could a team move this without the customer being meaningfully better off?
  > [your answer]
- **Gameable:** What's the most cynical way a team could hit this without earning it?
  > [your answer + the guardrail you'd add]

## Counter-metric (the guardrail)
A second metric that, if it moves *the wrong way*, signals we're winning the NS for the wrong reasons.
> [counter-metric]
```

The **counter-metric** concept is new today. Examples:

- NS = "Hours of returned dispatcher time" &rarr; Counter = "% of dispatchers calling support after the new flow"
- NS = "Tickets resolved without escalation" &rarr; Counter = "Rate of repeated tickets from the same customer"

### Deliverable

A completed NS Defense Card per triad: NS statement, three pitfall rebuttals, and a named counter-metric.

---

## Activity 3 — The "CEO and Dispatcher" Test

**Format:** Triad pairs &bull; **40 min** &bull; Block 3

### Purpose
A defensible NS sounds right to two audiences at once. Today we rehearse.

### Setup

Triads pair off. Each triad has its NS Defense Card from Activity 2 and the two persona scripts below.

### Steps

Each triad takes turns being the **defender** and the **challenger**.

- Challenger plays **CEO** for 4 minutes: probe whether the NS will move the company forward, scale, and survive a board review.
- Challenger plays **Dispatcher (target customer)** for 4 minutes: probe whether the NS reflects something they would actually feel.
- Defender records the strongest challenge from each role.

### The two persona scripts (challengers can extend or paraphrase)

**CEO Maria (FieldPulse):**
> "I have eight squads competing for engineering budget. Sell me on why your NS is the one I should care about for the next 12 months. What if it goes up 20%? What does that earn the company?"

**Dispatcher Maria (FieldPulse):**
> "Look — I've used four of these apps. I don't care about your charts. Tell me what changes about my Wednesday afternoon if you hit your number."

### After the round

Each triad updates its NS Defense Card with:

- The CEO's strongest challenge + how the triad would address it
- The dispatcher's strongest challenge + how the triad would address it

If the NS doesn't survive both — that's the artifact for tomorrow's coaching, not a failure.

### Deliverable

An updated NS Defense Card with two new lines: the CEO's strongest challenge + response, and the dispatcher's strongest challenge + response.

---

## Activity 4 — NS Lock-in + Tier Sheet Refresh

**Format:** Triad &bull; **45 min** + Readouts &bull; Block 4

### Purpose
Replace yesterday's placeholder, walk the new NS up and down the Tier Sheet to confirm coherence, and present.

### Setup
Each triad has its NS Defense Card (updated through Activity 3) and Day-1 Tier Sheet visible.

### Steps

### Triad workflow

1. **Lock in the NS** (10 min). Confirm wording. Confirm the counter-metric. Confirm the NS rebuttal answers.
2. **Walk it down** (15 min). Re-examine the operational signals from yesterday — does each one *plausibly* contribute to this NS? Drop or replace any that don't.
3. **Walk it up** (5 min). Does the NS roll up clearly to a business outcome that leadership cares about?
4. **Polish** (15 min). Final Tier Sheet, final Defense Card. Both shareable.

### Readout structure (90 seconds per triad)

> 1. "Our NS is [X], measured by [Y], for [segment]."
> 2. "The strongest challenge it survived was [Z]."
> 3. "Our counter-metric is [counter] — if that moves wrong, we know we're cheating."

### Deliverable

A locked NS + counter-metric, a refreshed Tier Sheet with the placeholder replaced, and a 90-second readout ready to deliver.

---

## End-of-day checkpoint

Each triad leaves the day with:

- [x] A locked-in **North Star** with explicit pitfall rebuttals
- [x] A **counter-metric** that guards against gameability
- [x] A **revised Metrics Tier Sheet** (placeholder replaced)
- [x] A Day 3 commitment: bring one product surface (FieldPulse mobile or web) you want to UX-audit tomorrow
