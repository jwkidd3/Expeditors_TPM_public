# Day 1 — Product Delivery Outcomes + Agile Manifesto & Principles

> **Activity packet** for facilitators and participant triads. Today's job: name the **outcomes** the feature is meant to produce (not the outputs), and use the **Agile Manifesto values** as a decision-making aid for real product trade-offs.

## Where we are in the week

The week opens by separating the muscle of **delivery** from the muscle of **outputs**. Most teams ship work; few teams clearly ship outcomes. Today builds the outcome map (DP §1), and uses the Agile Manifesto as the decision-frame underneath it.

## Inputs

- The full sibling artifact set: PRD / TCD / TMD / SEP
- The triad's NS Defense Card and Tier Sheet (Week 2)
- The negotiated outcomes log from SEP §5 (Week 6 Day 5)

---

## Output vs outcome — the foundational distinction

| Output | Outcome |
|--------|---------|
| What we built or shipped | What changed for the user / business |
| "Reconcile flow shipped on July 15" | "Dispatchers spend 30 min less per shift on reconciliation" |
| Easy to measure | Harder to measure |
| Can be hit while losing | If hit, you actually won |

Most product teams confuse the two. They say "the outcome is shipping the feature." That's an output dressed in outcome's clothes.

The discipline:

- Every output ought to map to **one or more outcomes**
- Every outcome ought to have **at least one leading indicator** (Day 3)
- The team can **hit all outputs and miss all outcomes** — that's the most common shipping-but-failing pattern

---

## The Agile Manifesto — values, not ceremony

The Manifesto:

> **Individuals and interactions** over processes and tools
> **Working software** over comprehensive documentation
> **Customer collaboration** over contract negotiation
> **Responding to change** over following a plan

That is, while there is value in the items on the right, we value the items on the left more.

### What the Manifesto **doesn't say**

- "No documentation" — the PRD/TCD/TMD/SEP/DP are valuable; they support working software
- "No plans" — plans are essential; rigid adherence to plans isn't
- "No process" — processes serve people; people don't serve processes
- "Stand-ups daily" — the Manifesto says nothing about meetings

The Manifesto is a **prioritization aid for trade-offs**, not a checklist.

### The 12 Principles (today's reference)

The 12 Principles deepen the four values. We highlight 6 most relevant for TPM work:

1. **Satisfy the customer through early and continuous delivery** — small, frequent shipments beat one big launch.
2. **Welcome changing requirements, even late** — change is information, not failure.
3. **Deliver working software frequently** — weeks, not months.
4. **Business and developers must work together daily** — the TPM is the bridge.
5. **Continuous attention to technical excellence and good design** — speed without quality is cowardice.
6. **Self-organizing teams produce the best results** — top-down task assignment is a smell.

The 6 we de-emphasize aren't wrong; they're harder for a junior TPM to drive directly. (See Wrap.)

---

## Activity 1 — Output / Outcome Sort

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Calibrate the output/outcome distinction with examples before applying it to the triad's feature.

### The sort pack — 12 statements

For each, the triad labels: Output / Outcome / Both (a thing stated as both) / Neither.

1. "We shipped the new reconcile flow on July 15."
2. "Dispatchers spend 30 minutes less per shift on after-shift reconciliation."
3. "We delivered all 23 user stories in the sprint."
4. "Customer NPS for the dispatcher persona increased by 6 points."
5. "The mobile app was downloaded 5,000 times this quarter."
6. "Reconcile-flow abandonment rate dropped from 18% to 9% in the first 30 days."
7. "We hired 3 engineers."
8. "Time-to-first-value for new dispatchers dropped from 2 weeks to 4 days."
9. "We refactored the auth layer to use SAML."
10. "5 customers cited the reconcile flow as a key reason for renewal."
11. "We held 4 user research sessions this quarter."
12. "Active dispatchers (defined as: completed at least one reconcile in the past 7 days) grew 15% MoM."

### Triad protocol

1. **Label all 12** (15 min).
2. **Argue when you disagree** (15 min). At least 2 should produce useful disagreement.
3. **For each "Both"-labeled statement**, rewrite it to be cleanly one or the other (5 min).

### Readout (60 sec per triad)

> "The trickiest one was [#X] because [why]. The cleanest outcome was [#Y]."

---

## Activity 2 — Build Your Outcome Map

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
For the triad's feature, name the outcomes it's meant to produce. Each gets pulled directly from the NS / Tier Sheet / journey map.

### The outcome map template

```markdown
## DP §1 — Outcome Map

### Primary outcome (the one we're staking the feature on)
> <user-visible outcome statement>
> Tied to: <NS / KPI from Tier Sheet>
> Target movement: <baseline → target> by <timeline>
> Leading indicator: <what we'd watch first to know we're on track>

### Supporting outcomes (2–4)
For each:
> <outcome statement>
> Tied to: <Tier Sheet metric>
> Why it matters: <one sentence>

### Counter-outcomes (the guardrails)
> <outcome we DON'T want to produce — if this happens, we won
> for the wrong reasons>

### What this feature explicitly does NOT outcome on
> <claims we are NOT making — usually pulled from PRD §3 non-goals>
```

### Triad protocol

1. **Pull the primary outcome from your NS** (10 min). It should be one of:
    - Movement on a Tier Sheet operational signal
    - Movement on a KPI
    - Movement on the NS itself (rare for a single feature)
2. **List supporting outcomes** (10 min). 2–4 outcomes the feature contributes to without owning.
3. **Name counter-outcomes** (10 min). The "we cheated" guardrails (from NS Defense Card).
4. **Name what we're NOT outcoming on** (5 min). This catches scope creep before it ships.
5. **Sanity check** (5 min). Does each outcome have a Tier Sheet metric attached?

### What "good" looks like

- The primary outcome is **not** "the feature is shipped"
- Supporting outcomes are **fewer than 5** and named in user terms
- Counter-outcomes prevent gaming
- The "explicitly NOT" line catches stakeholders who'd otherwise expect more

---

## Activity 3 — Agile Values in Trade-offs

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Use the Manifesto values as a decision aid on real trade-offs from the triad's prior weeks' work.

### The trade-off scenarios

The triad walks through 4 real trade-offs (3 from prior weeks + 1 new) and applies the Manifesto:

1. **From Week 5:** "Should we hand-write a longer technical spec or get to coding faster?"
   - Manifesto frame: **Working software over comprehensive documentation**
   - But: a TPM still ships a PRD/TCD/TMD/SEP. The Manifesto doesn't say "no docs."
   - Discussion: when does documentation become a substitute for working software?

2. **From Week 6:** "A senior stakeholder asked for a contract change to your scope mid-sprint."
   - Manifesto frame: **Customer collaboration over contract negotiation**
   - But: contracts (incl. PRDs, sign-offs) are how teams stay aligned
   - Discussion: when is the contract serving alignment vs blocking it?

3. **New scenario:** "Mid-quarter, customer behavior data shifts and your top user pain shifts to a different friction. Do you keep building what's planned, or pivot?"
   - Manifesto frame: **Responding to change over following a plan**
   - Discussion: how to pivot without thrashing the team

4. **From Week 7 setup:** "An engineer wants to skip the standup but the standup is 'the agile way.'"
   - Manifesto frame: **Individuals and interactions over processes and tools**
   - Standups are a tool, not a value
   - Discussion: when is the ceremony serving collaboration vs replacing it?

### Triad protocol

1. **For each scenario** (8 min each):
    - State the Manifesto value at play
    - State what the value implies
    - State what the value does *not* imply
    - Decide: what would your triad do?

2. **Final synthesis** (8 min): Which Manifesto value did your triad invoke most? Least? Why?

### What "good" looks like

- Each Manifesto value is named **with its non-implication** ("doesn't mean no docs / no plan / no process")
- The triad's decision is grounded in evidence (data, customer signal, team capacity) — not "the Manifesto says so"

---

## Activity 4 — Outcome Map Cross-Review + Wrap

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Cross-review the outcome map with another triad. Surface where outputs are masquerading as outcomes.

### Cross-review questions

The reviewer triad reads the outcome map and asks:

1. **Is each "outcome" actually an outcome, or is one a dressed-up output?**
2. **Do the supporting outcomes overlap?** (a sign of weak distinction)
3. **Is the counter-outcome specific enough to detect a real cheat?**
4. **What outcome is missing?**

### Triad protocol

1. **Pair triads** (instructor assigns).
2. **20 min cross-review** with the 4 questions.
3. **15 min author-triad revisions.**
4. **AI sanity check** (10 min):

```
Role: Senior PM coaching outcome thinking.
Context: <paste the outcome map>
Task: Identify where outputs are masquerading as outcomes,
      where outcomes are too vague to measure, and any
      counter-outcome that could be gamed.
Constraints:
  - Be specific to the statements given
  - Suggest a concrete rewrite
Format: 3 numbered findings.
```

### Wrap (last 15 min)

Each triad shares:

- Their **primary outcome** read aloud
- **One Manifesto value** they invoked in their map
- **One output that almost masqueraded** as an outcome — caught and fixed

---

## End-of-day checkpoint

Each triad ends Day 1 with:

- [x] Calibration on output/outcome distinction (12-statement sort)
- [x] **Outcome map** with primary + supporting + counter-outcomes + explicit not-claims
- [x] Trade-off thinking grounded in Manifesto values
- [x] Cross-reviewed
- [x] AI provenance entry
- [x] DP §1 drafted

## Facilitator reflection prompts (end of day)

- Which triad's primary outcome was sharpest? Hold up Friday.
- Did anyone list "ship the feature" as the primary outcome? Coach back.
- Did the Manifesto discussions stay grounded or drift to ceremony talk? Steer toward decisions, not vocabulary.
- Did anyone over-list supporting outcomes (8+)? Cull tomorrow before ADO loading.
