# Day 3 — Outcome-Based Planning vs Output-Based Tracking

> **Activity packet** for participant quads. Today's job: wire **tracking** on top of yesterday's ADO backlog so the team sees both outputs (work shipped) and outcomes (impact produced) — and surfaces failure early. Draft DP Section 3.

## Where we are in the week

The outcome map exists (Day 1). The backlog is loaded (Day 2). Today builds the **tracking plan** that pairs every output with an outcome metric AND a leading indicator. Without this, the team ships features and never learns whether they worked.

## Inputs

- DP Section 1 (outcome map)
- DP Section 2 (loaded ADO)
- Tier Sheet from Week 2
- TCD Section 4 (SLOs and error budgets)
- TMD Section 5 (baselines + monitoring plan)

---

## Why most tracking plans fail

| Failure | Symptom |
|---------|---------|
| **Output-only** | "We shipped 12 stories this sprint." Nobody asks if anything moved. |
| **Lagging-only** | The first time you know the feature failed is when retention drops 90 days later. |
| **Vanity-only** | DAU went up. (But nobody knows from what — push notifications? promotions?) |
| **No counter-metric** | The metric moved up; nobody noticed it moved up *the wrong way* (gaming). |
| **Dashboard-without-action** | Beautiful charts; no decisions ever change. |

A mature tracking plan avoids all five. The discipline:

- Every output has an outcome
- Every outcome has a leading indicator
- Every metric has a counter-metric (or an explicit "no" with rationale)
- Every dashboard has a **decision** it informs

---

## The output / outcome / leading-indicator triple

For every meaningful output, the tracking plan has three rows:

| Output (what shipped) | Outcome (what changed for users / business) | Leading indicator (the early signal) |
|------------------------|---------------------------------------------|--------------------------------------|
| Reconcile mobile flow | Median reconcile time per dispatcher drops 45→12 min | Reconcile-flow first-attempt completion ≥ 80% by week 2 |
| Auto-suggest top 5 tickets | Time-to-select drops 30s→10s | % of dispatchers using suggestion ≥ 50% by week 4 |
| Manager view dashboard (deferred) | (n/a — out of scope) | (n/a) |

The **leading indicator** is the muscle. Without it, the team waits 30 days to learn the outcome failed. With it, they know within a week whether the trend is right.

---

## The tracking cadence (today's mental model)

Tracking is wasted unless someone looks at it on a regular rhythm:

| Cadence | Audience | What's reviewed |
|---------|----------|-----------------|
| **Daily** | Engineers / on-call | Alerts, error budget, immediate breaks |
| **Sprint (2 weeks)** | Quad + eng lead | Output velocity, leading indicators trending right? |
| **Monthly** | TPM + PM director | Outcome metrics — is the feature winning? |
| **Quarterly** | Quad + leadership | NS movement, KPI roll-up, the big picture |

If a metric has no cadence, it has no audience. If a metric has an audience but no cadence, it's reviewed when there's a fire — too late.

---

## Activity 1 — Output / Outcome / Leading-Indicator Triples

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Build the central tracking table — every meaningful output paired with an outcome and a leading indicator.

### Quad protocol

1. **List the outputs** (10 min). Pull from DP Section 2 — the User Stories that produce user-visible behavior. Aim for 5–8 outputs (not all stories produce distinct outcomes).
2. **For each output, name the outcome** (10 min). Use DP Section 1's outcome map. Several outputs may share an outcome — that's fine.
3. **For each outcome, name the leading indicator** (10 min). The earliest signal you'd watch.
4. **Sanity-check** (5 min). Is each leading indicator measurable within 7 days of launch?

### Sample triple table — FieldPulse

| Output | Outcome | Leading indicator |
|--------|---------|-------------------|
| Reconcile mobile flow shipped | Median reconcile time 45→12 min in 30d | First-attempt completion ≥ 80% by week 2 |
| Idempotent submission | Submission error rate < 0.1% | Duplicate-submit rate < 0.5% in week 1 |
| Audit event publishing | SOC 2 audit passes Q3 review | Event volume + DLQ depth steady through week 4 |
| Inline error states + recovery | Customer support tickets about reconcile drop 50% | Tickets per dispatcher per week declining starting week 3 |
| WCAG AA conformance | Zero accessibility complaints in 90 days | axe-core scan pass rate 100% on every PR from week 1 |

### What "good" looks like

- Each triple is **specific**, not "we'll watch some metrics"
- Leading indicators are **measurable within 7 days**
- Outcomes are user-visible (not output dressed up)
- Counter-metrics are referenced (from NS Defense Card)

---

## Activity 2 — Sprint-Level Tracking (the 2-week loop)

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Design the sprint review where outputs and outcomes are inspected together.

### The sprint-review structure

A typical sprint review covers:

1. **What shipped** (outputs) — pull from "Done in this sprint" query
2. **What's still open** — pull from "Open in current sprint" query
3. **Velocity** — points completed
4. **Leading indicators** — which moved? Which didn't?
5. **Anomalies** — unusual patterns from the week
6. **Adjustments for next sprint** — what to do differently

The TPM-owned twist: **at least one slide / segment is about outcome**, not output. The team sees the leading indicators next to the velocity.

### Quad protocol

1. **Design the sprint review template** (15 min). 6 sections, with content per section.
2. **Decide the cadence anchor** (5 min). Day of week; time; recurring.
3. **Build the "leading indicator dashboard"** (15 min). What charts go on it? Each chart references one or more leading indicators from Activity 1.
4. **Identify the alarm** (5 min). For each leading indicator: at what threshold do we say "this isn't moving — what should we change next sprint"?

### What "good" looks like

- Sprint review template has **a slot for outcome**, not just output
- The leading indicator dashboard has **3–5 charts** (more = ignored)
- Each chart has a **threshold** that triggers a specific conversation

---

## Activity 3 — Monthly + Quarterly Tracking

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Design the monthly outcome review and the quarterly NS roll-up.

### Monthly outcome review

The monthly review answers: **is the feature winning?**

Structure:

```markdown
## Monthly Outcome Review — <feature>

### The primary outcome
Baseline: <X>
Current: <Y>
Target by <date>: <Z>
Status: 🟢 / 🟡 / 🔴

### Supporting outcomes
[same table]

### Counter-outcomes (the guardrails)
[same table]

### What we learned this month
<2–3 bullets — what surprised us, what changed our model>

### Decisions for next month
<3–5 specific decisions: invest more / pivot / stop>
```

The "What we learned" + "Decisions for next month" sections are what make the review **actionable** rather than ceremonial.

### Quarterly NS roll-up

The quarterly review answers: **did the feature contribute to the NS?**

- Did the primary outcome move?
- Did the supporting outcomes contribute?
- Did counter-outcomes stay flat?
- Did the NS itself move? (Often hard to attribute to one feature; that's fine — name what you can.)

### Quad protocol

1. **Monthly review template** (15 min). Customize the structure above for your feature.
2. **Quarterly roll-up template** (15 min). Same.
3. **Identify the **author + audience** for each (5 min). Who writes? Who reads?
4. **Identify the **cadence anchor** (5 min). First Tuesday of every month? Day after sprint? Pick.

### What "good" looks like

- Monthly review template has **decisions** as a non-skippable section
- Quarterly roll-up explicitly **attributes (or de-attributes)** outcome movement
- Author + audience are **named** — not "the team"
- Cadence is **calendar-anchored**, not "monthly-ish"

---

## Activity 4 — Build the Tracking Plan + AI Pattern Detection

**Format:** Quad &bull; **55 min** + Wrap &bull; Block 4

### Purpose
Combine Activities 1–3 into a single tracking plan section of the DP. Add the AI-pattern-detection prompt that helps spot anomalies.

### DP Section 3 structure

```markdown
## 3. Tracking plan

### Output / Outcome / Leading-Indicator triples
[Activity 1 table]

### Counter-metrics
[from NS Defense Card]

### Sprint-level tracking
- Cadence: <day, time, frequency>
- Template: <link>
- Leading indicator dashboard: <link>
- Thresholds + actions: <table>

### Monthly outcome review
- Cadence: <day, time, frequency>
- Template: <link>
- Author / audience: <names>

### Quarterly NS roll-up
- Cadence: <day, frequency>
- Template: <link>

### AI pattern detection
- Prompt: <link to Pattern Library entry>
- Frequency: weekly / per sprint review
- Validation: cross-check against ADO query results
```

### The AI pattern-detection prompt

```
Role: Senior PM doing pattern detection across a sprint's work.
Context: <ADO query results — items shipped, items blocked,
         leading indicator readings>
Task: Identify the top 3 patterns:
  1. A leading indicator moving the wrong direction (or flat
     when expected to move)
  2. A category of work over- or under-represented in this sprint
  3. An anomaly worth investigating (specific stories /
     timing / volume)
Constraints:
  - Use only the data provided
  - For each pattern, name the specific items / numbers
  - Suggest one investigation step per pattern
Format: 3 numbered patterns; each with: pattern / evidence / suggested investigation.
```

### Quad protocol

1. **Combine into Section 3** (15 min). All four sections.
2. **Run the AI prompt** on a synthetic sprint (10 min).
3. **Validate** (10 min). Cross-check claims.
4. **Cross-review with another quad** (10 min). The reviewer asks: is each leading indicator measurable within 7 days?

### Wrap (last 15 min)

Each quad shares:

- One **leading indicator** they're proudest of
- One **anomaly** they expect to see in the first sprint
- One **decision** they imagine making in the first monthly review

---

## End-of-day checkpoint

Each quad ends Day 3 with:

- [x] Output/outcome/leading-indicator triples (5–8 outputs)
- [x] **Sprint-level review template** + cadence + dashboard
- [x] **Monthly outcome review template** with named author + audience
- [x] **Quarterly NS roll-up template**
- [x] AI pattern-detection prompt + provenance
- [x] DP Section 3 drafted
