# Day 1 — Operational Signals & KPIs

> **Activity packet for participant quads.** This file is the single source of truth for your small-group work, examples, and deliverable templates.

## Where we are in the week

Week 2 opens by giving each quad a vocabulary for "what better looks like." Today's job is to install three terms that will be used every day for the rest of the academy: **operational signal**, **KPI**, and **North Star** (which gets its full treatment on Day 2).

Inputs from Week 1: each quad arrives with its **problem statement** and **Prompt Pattern Library**. Both are referenced today.

---

## The Metrics Tier Sheet (today's main artifact)

Each quad ends Day 1 with a Metrics Tier Sheet for the FieldPulse problem they framed in Week 1. The sheet has three rows:

| Tier | Definition | How many today | Purpose |
|------|------------|----------------|---------|
| North Star (NS) | The single metric that, if it goes up, the customer is winning AND the business is winning | 1 candidate (placeholder) | Day 2 will replace this |
| KPI | Business-level outcome that the NS rolls up to or that signals NS health | 2–3 | Quarterly board view |
| Operational signal | Daily/hourly leading indicator a team can act on | 4–6 | What the squad watches in standups |

A "well-formed" tier sheet has a believable **causal chain**: a change in an operational signal plausibly ripples up to a KPI, which ripples to the NS.

---

## Activity 1 — "Metric or Vanity?"

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Ground the room in the difference between metrics that move because the customer's life got better, and metrics that move because the team got clever.

### Setup
Each quad receives the **Vanity-Metric Card Pack** (12 metrics drawn from FieldPulse-adjacent SaaS products). Examples in the pack:

- Daily Active Users
- Number of features shipped per quarter
- Average session length
- % of dispatchers who completed onboarding
- Support tickets closed per agent per day
- Mean time to first dispatch after login
- Reconcile-flow completion rate
- New trial sign-ups per week

### Steps

For each card, the quad places it on a 2x2:

```
                Easy to game
                    |
                    |
Lagging  -----------+----------- Leading
                    |
                    |
                Hard to game
```

Then they pick the **two cards** they would bet on for FieldPulse and the **two cards** they would never report up.

### Deliverable

A sorted 2x2 with bet-on and never-report-up cards labeled, plus a one-sentence rationale per pick.

### Readout (60 seconds per quad)

> "We would bet on [X] and [Y] because [reason rooted in causal chain]. We would never report up [A] or [B] because [reason]."

---

## Activity 2 — Operational signal sprint

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Generate a credible bench of operational signals for the quad's Week-1 problem statement.

### Setup
Each quad has its Week-1 problem statement pinned visibly. Each member needs sticky notes or a shared doc for solo brainstorm.

### Steps

1. Re-read the quad's problem statement aloud.
2. Each quad member independently writes 4 candidate operational signals (12 total).
3. The quad culls to **6 finalists**. For each, capture:
    - **What it measures**
    - **Where the data comes from** (system, log, instrumentation gap)
    - **How fast it moves** (real-time, hourly, daily, weekly)
    - **What action a team would take** if it dropped 30%

### The "instrumentation gap" check

For at least 2 of the 6 finalists, the quad will discover the data **does not exist yet**. That is intentional. Mark these in red — they become input for the Week 4–5 technical infrastructure conversations.

### Output (added to Metrics Tier Sheet)

The 6 operational signals populate the bottom row.

### Deliverable

6 operational signals with what they measure, source, cadence, and action-if-dropped. At least 2 marked as instrumentation gaps.

---

## Activity 3 — KPI laddering

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Bridge from operational signals (squad-level) to KPIs (org-level). This is where TPMs earn their seat in cross-functional rooms.

### Setup
Each quad has the 6 operational signals from Activity 2 visible.

### Steps

### The laddering exercise

Take the 6 operational signals from Activity 2. For each, the quad answers:

> "If this signal moved 30% in the right direction for an entire quarter, what business KPI would that show up in?"

Cluster operational signals that ladder to the same KPI. Aim for **2–3 KPI clusters**.

### KPI quality bar

A well-formed KPI for FieldPulse passes all four:

- [ ] Spoken in business terms (revenue, retention, time-to-value, NPS)
- [ ] A senior leader cares about it without translation
- [ ] You can imagine a single chart that shows it weekly
- [ ] You can name what's "good" without inventing a number

### Output (added to Metrics Tier Sheet)

The 2–3 KPIs populate the middle row.

### Deliverable

2–3 candidate KPIs added to the Tier Sheet, each passing the four-question KPI quality bar, with the operational signals that ladder into each one explicitly named.

---

## Activity 4 — Tier Sheet defense + North Star placeholder

**Format:** Quad &bull; **55 min** + Readouts &bull; Block 4

### Purpose
Complete the Tier Sheet, do a peer-defense round, and seed Day 2's North Star work.

### Setup
Pair each quad with another. Both quads have draft Tier Sheets (NS placeholder + KPIs + operational signals).

### Steps

### Quad workflow

1. **Draft a North Star placeholder** (15 min). The quad invents a one-sentence NS using the template:
   > "We are winning when [customer outcome] increases for [user segment], measured by [single number]."
   This will be revisited tomorrow. Today, just get a placeholder to react to.

2. **Pair-defense round** (20 min). Each quad pairs with another quad. Defender presents the Tier Sheet for 4 minutes. Challenger uses the **Three Standard Challenges**:
    - **Causal chain:** "Show me how a change in operational signal #3 plausibly moves your KPI."
    - **Gameability:** "Pick the easiest of these to game. How would a sales-incentivized team game it?"
    - **Instrumentation:** "Which two of these can you actually measure today, in production?"

3. **Refine** (10 min). Capture the strongest challenge in a "known weaknesses" line at the bottom of the Tier Sheet.

### Readout structure (60 seconds per quad)

> "Our NS placeholder is [X]. Our hardest challenge was [Y]. Our biggest instrumentation gap is [Z]."

### Deliverable

A complete Metrics Tier Sheet (NS placeholder + KPIs + 6 operational signals) plus a "known weaknesses" line capturing the strongest challenge from the defense round.

---

## End-of-day checkpoint

Each quad leaves the day with:

- [x] A complete Metrics Tier Sheet (NS placeholder + 2–3 KPIs + 6 operational signals)
- [x] At least one named instrumentation gap
- [x] One "known weakness" of the current Tier Sheet (from the defense round)
- [x] A Day 2 commitment: bring a candidate alternative to your NS placeholder
