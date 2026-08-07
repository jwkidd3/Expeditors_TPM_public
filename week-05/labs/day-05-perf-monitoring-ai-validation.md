# Day 5 — Performance Baselines, Monitoring & Validating AI-Generated Data Summaries

> **Activity packet** for participant quads. Today's job: write **Section 5** of the TMD — performance baselines, monitoring plan, and AI-summary validation log. Then **assemble the full TMD**, peer-review it, and ship it as the sibling artifact to TCD and PRD.

## Where we are in the week

The TMD has Sections 1–4 (data, cloud, API, sequences). Today produces Section 5 — **performance baselines + monitoring plan + AI-summary validation log** — and the integrated TMD ships.

The AI-summary validation log is the **new discipline this week**. AI is increasingly used to summarize dashboards, query results, and metric reports. The TPM job: validate those summaries against the source data and document the result.

## Today's cadence

Same as Mon–Thu (no special split like Week 3 Day 5 had). Block 4 is the cross-review + sign-off.

## Inputs

- TMD Sections 1–4 (Days 1–4)
- TCD Section 4 SLOs (anchor for baselines + targets)
- The Tier Sheet from Week 2 — operational signals point at what to monitor
- The PRD — context for what dashboards stakeholders need

---

## What Section 5 contains

```markdown
## 5. Performance baselines & monitoring

### Baselines
- Pre-launch numbers we measure today (or expect at launch)
- Historical context where applicable

### Targets
- From TCD Section 4 SLOs (do not redefine — reference)

### Monitoring plan
- Dashboards (operator-level, executive-level)
- Alerts (thresholds, severities, on-call routing)
- The "fire before users notice" check

### AI-summary validation log
- Each AI-assisted summary used in this TMD or referenced in
  upstream artifacts: prompt, output, validation status
```

---

## Performance baselines — measuring "where we start"

A baseline is what the metric reads **today** (or at launch, for new features). Without a baseline, you can't tell if you've improved.

### Two kinds of baselines

| Kind | When | Source |
|------|------|--------|
| **Existing-system baseline** | Brownfield work — improving something that exists | Production data (current dashboards, query histories) |
| **Expected-launch baseline** | Greenfield work — new feature | Estimated from comparable features, load-test data, or "we expect X based on [reasoning]" |

For greenfield, the discipline is to **state the assumption** rather than skip the baseline. "We expect ~200 reconcile-submits/day in the first 30 days, based on dispatcher count × shifts/day × (estimated adoption rate)." That assumption gets tested at launch + 7 days.

### What to baseline

For each TCD Section 4 SLO, capture the corresponding baseline:

- **Latency:** what the system does today (or expects to)
- **Availability:** what the system has done historically
- **Throughput:** current volume + projected
- **Error rate:** historical or expected

Plus any **operational signal** from the Tier Sheet that doesn't show up in the SLOs.

---

## The monitoring plan — fire before users notice

A monitoring plan has three layers:

| Layer | Audience | Rhythm |
|-------|----------|--------|
| **On-call alerts** | Engineers on rotation | Real-time |
| **Operator dashboards** | TPM, eng lead, SREs | Daily / weekly |
| **Executive dashboards** | Leadership | Weekly / monthly |

Each layer has a different question:

- On-call: "Is something on fire right now?"
- Operator: "Is the system trending the right way?"
- Executive: "Are we meeting our SLOs / KPIs / NS?"

### Alert design — the four-question check

For each alert, answer:

1. **What does it mean?** (Plain English)
2. **What does the on-call do when it fires?** (Specific runbook step)
3. **What's the threshold + window?** (e.g., "5xx rate > 1% over 5 min")
4. **What's the severity?** (Page / Slack / log only)

If you can't answer all four, the alert is noise — it'll be muted within a sprint.

---

## AI-summary validation — the new discipline

This week's prompts produced AI-assisted critiques, summaries, and structuring. Today's discipline: **validate each AI-assisted summary** against the underlying data and document the result.

### Why this matters

AI summarization of data — query results, dashboards, metric reports, performance test outputs — is increasingly common. The failure modes:

| Failure | What happens |
|---------|--------------|
| **Wrong number** | AI cites "p95 = 800ms" when the chart shows 1200ms |
| **Wrong direction** | AI says "improving" when the trend is flat or declining |
| **Wrong attribution** | AI explains a spike with the wrong cause |
| **Missing context** | AI summarizes the headline; misses the relevant footnote |

### The validation procedure

For each AI-assisted summary used in any week's artifact:

```markdown
| # | Summary purpose | Prompt (link) | Source data | Validation |
|---|-----------------|---------------|-------------|------------|
| 1 | Strategy brief pain themes (Wk 2 D4) | Pattern Lib #3 | 14 tickets + 3 interviews | Cross-checked all citations; 1 hallucinated; cut |
| 2 | Architecture critique (Wk 4 D1) | Pattern Lib #5 | TCD Section 1 stance | Adopted 2/3 objections; rejected 1 (irrelevant scenario) |
| 3 | API contract critique (Wk 5 D3) | Pattern Lib #8 | TMD Section 3 | Adopted 4/5 issues; deferred 1 to v2 |
| 4 | Cloud topology risk scan (Wk 5 D2) | Pattern Lib #7 | TMD Section 2 | All 3 valid; 1 added as TCD risk; 2 already known |
```

The log is **cumulative across weeks** — the team should know which AI outputs have been validated and which are pending.

### Status values

- **Cross-checked all citations** (best — every claim verified against source)
- **Spot-checked** (rougher — N claims sampled and verified)
- **Adopted with rationale** (we used the AI suggestion; the suggestion's correctness was self-evident or cheap to verify)
- **Pending** (used as input but not yet validated; track to closure)
- **Rejected** (output was wrong; cut)

---

## Activity 1 — Performance Baselines

**Format:** Quad &bull; **35 min** &bull; Block 1

### Purpose
Set baselines for each SLO + key operational signal.

### Setup
Each quad needs the TCD Section 4 SLOs, the Week-2 Tier Sheet, and the baseline template. AI optional.

### Quad protocol

1. **List the metrics that need baselines** (5 min). One per SLO + 2–3 op-signals from Tier Sheet.
2. **For each, classify** (5 min). Existing-system baseline or expected-launch?
3. **Capture the baseline value** (15 min). For existing: production number (real or assumed). For expected: the assumption + reasoning.
4. **Set the "test at launch + N days" plan** (10 min). When will we check the baseline against reality?

### What "good" looks like

- Every SLO has a paired baseline
- Greenfield baselines name **the assumption** (not "we don't know")
- The "test at launch + N days" plan has dates
- The baseline format is reusable for future TMDs

### Deliverable

A baselines table covering every TCD Section 4 SLO and 2–3 Tier Sheet operational signals, each with a value, source/assumption, and a verify-at date.

### Worked example — FieldPulse reconcile

```markdown
| Metric | Baseline | Source / assumption | Verify at |
|--------|----------|----------------------|-----------|
| Reconcile-flow p95 latency | Expected ~700ms | Sequence diagram totals + 30% buffer | Launch + 7d |
| Reconcile-flow availability | Expected 99.5% (= TCD Section 4 target) | Inherits monolith availability | Launch + 30d |
| Reconcile-submits/day | Expected 200 | Dispatcher count × 1 reconcile per shift | Launch + 7d |
| Submission error rate | Expected < 2% | Comparable features in this app run < 2% | Launch + 14d |
| 5xx rate | Expected < 0.5% | Inherits monolith baseline | Launch + 7d |
```

---

## Activity 2 — The Monitoring Plan

**Format:** Quad &bull; **40 min** &bull; Block 2

### Purpose
Design dashboards + alerts across the three layers.

### Setup
Each quad needs the baselines from Activity 1, the four-question alert template, and the three-layer dashboard prompts. AI optional.

### Quad protocol

#### Step 1 — On-call alerts (15 min)

For each alert, fill the four-question template:

```markdown
### Alert: <name>
**What it means:** <plain English>
**What on-call does:** <specific first step>
**Threshold + window:** <X over Y minutes>
**Severity:** Page / Slack / log
```

Aim for **3–5 alerts** per feature. More = noise.

#### Step 2 — Operator dashboard (15 min)

What does a TPM look at every Monday morning to see if the feature is healthy?

A short list:

- Top-line metric (the SLO you care most about)
- Operational signals trending
- Alert volume / mute reasons
- Any deferrals from the previous week

#### Step 3 — Executive dashboard (10 min)

What does leadership see in the weekly review?

A shorter list:

- The NS-relevant operational signal (from Tier Sheet)
- The KPI the feature is meant to move
- Status: green / yellow / red against SLOs

### What "good" looks like

- Alerts pass the four-question test
- The operator dashboard has < 6 charts (more = nobody reads)
- The executive dashboard has < 4 charts
- "Mute reasons" tracking is included on the operator level — captures the alert-tuning conversation

### Deliverable

3–5 alerts answering the four-question template, plus operator and executive dashboard charts lists capped at 6 and 4 respectively.

---

## Activity 3 — AI-Summary Validation Log

**Format:** Quad &bull; **40 min** &bull; Block 3

### Purpose
Walk back through every AI-assisted summary used across Weeks 1–5 and document its validation status.

### Setup
Each quad needs the cumulative AI provenance notes from Weeks 2, 4, and 5, the Pattern Library reference, and the validation log template.

### Quad protocol

1. **Inventory the AI uses** (15 min). List every AI-assisted output you used in any artifact: prompts from Weeks 2, 4, 5.
2. **For each, capture the validation row** (15 min):
    - Summary purpose
    - Prompt link (Pattern Library entry)
    - Source data the AI was working with
    - Validation status (using the values above)
3. **Highlight any "Pending"** (5 min). For each, decide: validate now, defer to specific date, or accept the risk.
4. **Sanity check** (5 min). Are there places you used AI without logging it? Add them.

### Worked log entry

```markdown
| # | Summary purpose | Prompt | Source | Validation |
|---|-----------------|--------|--------|------------|
| 5 | Sequence diagram critique (Wk 5 D4) | Pattern Lib #11 | TMD Section 4 | Adopted 2/3 issues; AI flagged missing audit-publish on weird path — added |
| 6 | API critique (Wk 5 D3) | Pattern Lib #8 | TMD Section 3 | Spot-checked: AI pointed to inconsistent error format; verified vs Section 3; fixed |
| 7 | Cloud risk scan (Wk 5 D2) | Pattern Lib #7 | TMD Section 2 | All 3 valid; 1 added to TCD Section 5 trade-offs; 2 already in stakeholder matrix |
```

### What "good" looks like

- Every AI use across Weeks 2–5 has a row
- Status values are honest
- Pending entries have a deadline
- The log is **a tool the next TPM can audit**, not a checkbox

### Deliverable

A cumulative AI-summary validation log covering Weeks 2–5, with honest status values and named deadlines for Pending entries.

---

## Activity 4 — TMD Integration + Cross-Review + Sign-Off

**Format:** Quad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Assemble the full TMD, cross-review with another quad, and sign off. Same Week-3 / Week-4 review pattern.

### Setup
Instructor confirms pairings. Each quad needs the full TMD Sections 1–5 draft and the Friday TMD rubric.

### Quad protocol

1. **Solo read-through** (10 min). Each member reads Sections 1–5 and marks coherence issues.
2. **Pool issues** (5 min). De-dupe.
3. **Cross-review** (20 min). Pair with another quad. Reviewer scores with the **Friday TMD rubric**:

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| Data model clarity | 20% | Entities, keys, indexes, trade-offs all named |
| Cloud topology realism | 15% | Region/AZ stance fits SLOs; tenancy honest |
| API contract sharpness | 20% | Resources noun-shaped; idempotency, errors, versioning explicit |
| Sequence model completeness | 20% | Happy + sad/weird; protocols + invariants |
| Baselines + monitoring | 15% | Baselines real; alerts pass 4-question test |
| AI-validation discipline | 10% | Log distinguishes correct / partly correct / wrong with evidence |

4. **Adopt / defer / reject** (10 min). Same Week-3 discipline.
5. **Sign-off** (no separate block — done within Activity 4). Status: "Approved" or "Approved with gaps."

### Deliverable

Signed-off TMD (Approved or Approved with gaps) with adopted cross-review findings, final rubric score, and cumulative AI-validation log attached.

### Wrap (last 15 min)

Each quad shares:

- The **single sharpest insight** the TMD added beyond the TCD
- The **one open question** for Week 6 stakeholder negotiation
- Their **TMD final score** (peer + instructor average)

---

## End-of-week (Week 5) checkpoint

Each quad ships:

- [x] **Full TMD** with Sections 1–5 integrated
- [x] Section 1 Data model
- [x] Section 2 Cloud topology + ROM cost
- [x] Section 3 API contract with idempotency / versioning / errors
- [x] Section 4 Three sequence diagrams (happy / sad / weird)
- [x] Section 5 Performance baselines + monitoring plan + AI-validation log
- [x] Cross-reviewed + signed off
- [x] Cumulative AI-validation log across Weeks 1–5

The TMD goes into Week 6 alongside the PRD and TCD. Week 6 (Stakeholder Alignment & Negotiation) **negotiates** the constraints documented across all three artifacts.
