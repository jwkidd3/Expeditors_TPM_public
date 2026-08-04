# Day 3 — Communicating Technical Trade-Offs to Non-Technical Partners

> **Activity packet** for participant triads. Today's job: take **one trade-off** from your TCD Section 5 or TMD, translate it for a non-technical executive, and produce a 1-page brief that wins (or honestly loses) the call.

## Where we are in the week

The TCD Section 5 has top-5 trade-offs documented. Each is named in technical terms — the right framing for an architect or eng lead. Today we **translate one** into a brief that lands with a CFO, a Customer Success lead, or an executive sponsor.

By 16:00, every triad has SEP Section 3 — a one-page trade-off brief.

## Inputs

- TCD Section 5 (top-5 trade-offs)
- TMD Section 1–Section 5 (data, cloud, API, sequence, baselines — sources of additional trade-offs)
- SEP Section 1–Section 2 (stakeholder map and engagement plan — informs *which* stakeholder)

---

## The translation discipline (today's mental model)

Translating technical to business is not "use simpler words." It's **re-framing**: same trade-off, expressed in terms the audience already cares about.

| Technical framing | Business framing |
|-------------------|------------------|
| "We chose async write to audit because sync would breach our p95 SLO" | "We chose to ship 50ms faster on the dispatcher screen, accepting that audit logs may lag 10 seconds — important for compliance Q3 review timing" |
| "We accepted denormalized ticket_ids array in ReconcileEvent" | "We're optimizing reconcile reads at the cost of a future query type. We'd revisit if that query becomes hot" |
| "We're ship a modular monolith, not a service" | "We're shipping faster by not separating this code; we accept the cost of a future split if traffic grows 5x" |

A non-technical exec doesn't need the technical framing. They need:

- **What's at stake** (in their currency: cost, customer outcome, regulatory exposure, time)
- **What we're choosing** (in plain language)
- **What we're *not* choosing**, and why
- **What we'd need to change our mind**
- **What we're asking from them** (decision / approval / information)

---

## The "what they need to know vs what they need to decide" frame

A common rookie mistake: a brief tries to teach the executive everything. They don't have time, and they shouldn't need it.

| What they need to know | What they need to decide |
|------------------------|--------------------------|
| The headline outcome | Whether to approve the choice |
| The cost we're accepting | Whether the cost is acceptable |
| The trigger to revisit | Whether the trigger is well-chosen |
| What we need from them | Whether to provide it |

Strip everything else. Detail goes in the appendix or "available on request."

---

## The 1-page brief template

```markdown
# Trade-off brief: <short feature name>
**For:** <stakeholder name>  |  **From:** <triad>  |  **Date:** <today>

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

The discipline: the **whole brief** fits on one page. The appendix is references, not body.

---

## Activity 1 — Translation Drill

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Calibrate the translation muscle on examples before applying it to the triad's own trade-off.

### The translation pack — 6 technical statements

For each, the triad writes the business-framing version targeting a specific stakeholder.

| # | Technical statement | Stakeholder | Their currency |
|---|---------------------|-------------|----------------|
| 1 | "We're using read replicas which will introduce up to 3-second consistency lag" | Customer Success | Customer impact |
| 2 | "p99 latency budget can't fit our happy path; we propose relaxing to p95" | Eng Director | Engineering velocity |
| 3 | "We need an additional region to satisfy data residency for 8% of customers" | CFO | Cost |
| 4 | "Token-based auth requires a new SSO scope" | Identity team lead | Operational risk |
| 5 | "We're deferring tablet support to v2" | Sales lead | Revenue / deal velocity |
| 6 | "Audit-log retention requires 24 months of cold storage" | Compliance lead | Regulatory exposure |

### Triad protocol

1. **Pick 3 of the 6** (5 min). Mix of stakeholders.
2. **Translate each** (20 min) using the audience's currency.
3. **Critique the translations** (10 min). For each: would the stakeholder act on this brief? Would they have follow-up questions? What's missing?

### Readout (60 sec per triad)

> "The translation we're proudest of was [#X] for [stakeholder]. The hardest one was [#Y] because [why]."

---

## Activity 2 — Pick Your Trade-Off + Pick Your Stakeholder

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Pick one of your TCD Section 5 trade-offs (or a TMD trade-off) AND one stakeholder, then design the brief together.

### Triad protocol

1. **Review your top-5 trade-offs** (5 min). Pull from TCD Section 5 + any from TMD Sections 1–4.
2. **Pick the trade-off** (10 min). Criteria:
    - It's **decision-shaped** — there's a real call to make
    - The stakeholder you'd brief has **power to approve or block**
    - Trade-off has a **non-obvious cost** that needs explaining
3. **Pick the stakeholder** (10 min). Pull from SEP Section 1. Ideally a **high-power** stakeholder (HI or LI quadrant).
4. **Predict 5 questions they'll ask** (15 min). Their first 5 questions; rank by likelihood.

### What "good" looks like

- The trade-off has **a real call** the stakeholder can make
- The stakeholder is in the **right quadrant** for this kind of decision
- The 5 predicted questions include **at least one hostile** one

### Worked example — FieldPulse

| Trade-off | Stakeholder | Why this pairing |
|-----------|-------------|------------------|
| Async audit write (TCD trade-off 2) | Compliance Lead | Decides if 10-sec lag is acceptable |
| Modular monolith vs new service (TCD trade-off 1) | Architect | Decides architectural posture |
| ticket_ids denormalization (TMD trade-off) | Eng Director | Decides if "future query may be hard" is acceptable |
| Region/AZ active-passive vs active-active (TMD Section 2) | CFO + Architect | Cost + architecture together |

---

## Activity 3 — Draft the 1-Page Brief

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Draft the brief. The 1-page constraint is hard.

### Triad protocol

1. **Write "the decision" sentence** (5 min). One sentence. If it requires two, the trade-off isn't sharp enough.
2. **Write "why this matters to you"** (10 min). 1–2 sentences in their currency. Run through the predicted 5 questions to make sure this answers their #1.
3. **Write "the choice"** (10 min). 2–3 bullets each: what we're doing / not doing / cost.
4. **Write "what would change our mind"** (5 min). One concrete trigger.
5. **Write "what we need from you"** (5 min). Checkboxes; specific.
6. **Write the appendix linkbox** (5 min).

### What "good" looks like

- **Whole brief on one page** — the page constraint is forcing
- **Plain language** in the headline; technical terms only in the appendix references
- **Cost in their currency** — dollars for CFO, customer experience for CS, audit risk for Compliance
- **Specific ask** at the end — not "thoughts welcome"

### Worked example — Async audit write brief for Compliance

```markdown
# Trade-off brief: Reconcile audit write timing
**For:** Pat Lee, Compliance Lead  |  **From:** Reconcile triad  |  **Date:** 2026-04-29

## The decision
We are choosing async audit write (1–10s lag) over synchronous (instant)
to keep dispatcher reconcile screens fast.

## Why this matters to you
This affects the audit-trail timing your SOC 2 process depends on. Audit
events are still durable (Event Hubs stream + DLQ) — they just appear in the
audit store 1–10 seconds after the user action.

## The choice
- **What we're doing:** Publish audit events to a durable Event Hubs stream at
  user-action time; consumer writes to audit store within 1–10 seconds.
- **What we're explicitly not doing:** Synchronous write to audit store
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

---

## Activity 4 — Cross-Review + AI Critique

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Cross-review with another triad **playing the stakeholder role**. Use AI to predict objections.

### Cross-review protocol (20 min)

1. **Pair up triads** — instructor assigns.
2. **Reviewer triad reads the brief in role** (10 min). They read as if they were the named stakeholder. They underline:
    - Sentences that lose them (jargon, irrelevant, unclear)
    - Sentences they'd push back on
    - The first question they'd ask
3. **Author triad listens to feedback** (10 min). Capture; do not defend. Same Week-3 review discipline.

### AI critique (15 min)

```
Role: <stakeholder type — e.g., CFO, Compliance Lead, Sales VP>
Context: <paste the brief>
Task: Read this as if you were the named stakeholder.
  - What's the first question you'd ask?
  - What concern is unaddressed?
  - What word or phrase loses you?
Constraints:
  - Be specific to the brief, not generic
  - Voice the stakeholder's perspective honestly
Format: Numbered list — Question / Concern / Word that loses you.
```

### Triad action (10 min)

Adopt / defer / reject. Update Section 3.

### Wrap (last 15 min)

Each triad shares:

- Their **decision sentence** read aloud (the test of clarity)
- The **stakeholder question** they're least sure how to answer
- One **word they cut** from the technical version

---

## End-of-day checkpoint

Each triad ends Day 3 with:

- [x] **One TCD/TMD trade-off** picked + stakeholder paired
- [x] **5 predicted questions** ranked
- [x] **One-page brief** in the SEP Section 3 template
- [x] Cross-reviewed (in role) + AI-critiqued
- [x] Provenance log entry
- [x] SEP Section 3 drafted
