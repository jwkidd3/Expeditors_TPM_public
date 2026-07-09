# Day 5 — Identifying & Removing Delivery Bottlenecks

> **Activity packet** for facilitators and participant triads. Today's job: take the top queues from Day 4, design **bottleneck-removal experiments** with hypothesis / test / success criterion, integrate the full DP, peer-review, and ship.

## Where we are in the week

The VSM exists (Day 4). Today turns its top queues into **experiments**: specific tests with specific success criteria, run on a real cadence. Then the full DP integrates and ships as the fifth and final sibling artifact.

By 16:00, every triad has the **complete sibling artifact set**: PRD / TCD / TMD / SEP / DP.

## Inputs

- DP §§1–4
- The top 3 queues from Day 4
- The full sibling set (PRD / TCD / TMD / SEP)

---

## The Theory of Constraints — one principle

Eli Goldratt's central claim: **a system's throughput is constrained by exactly one bottleneck at a time**. Not many. One. If you optimize anything other than the current bottleneck, you don't speed up the system — you just add inventory in front of the constraint.

For software delivery: if your slowest step is "code review takes 2 days," speeding up coding doesn't help — it just creates more code waiting for review. The TPM job is to **find the current bottleneck** and remove it; **then** find the new bottleneck.

This is also why "we're working on 5 improvements simultaneously" rarely works. Pick the constraint. Move it. Then pick the next one.

---

## Bottleneck experiment — the structure

For each top queue, design an experiment:

```markdown
### Experiment N: <short name>
**Bottleneck addressed:** <queue from VSM>

**Hypothesis:** We believe that <doing X> will <result>
because <reasoning>.

**Test:** <what we'll do, for how long, on what scope>

**Success criterion:** <measurable outcome that decides
adopt/reject>
- Baseline: <current measurement>
- Target: <improved measurement>
- Window: <duration>

**What could go wrong:**
<2–3 risks of running this experiment>

**Who runs it:** <named person>
**By when:** <date>

**Decision after:**
- If success criterion is met: <adopt / scale / institutionalize>
- If not met: <abandon / iterate / escalate>
```

The experiment **must** have a success criterion that's measurable. "We'll see if it feels better" is not an experiment — it's a vibe.

---

## Activity 1 — Design 3 Experiments

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Convert the top 3 queues from Day 4 into 3 specific experiments.

### Triad protocol

1. **Re-read your top 3 queues** (5 min) from DP §4.
2. **For each, draft an experiment** (25 min) using the template above. Commit to:
    - A specific change (not "improve code review" — "auto-assign reviewers based on path")
    - A duration (typically 2–4 sprints)
    - A success criterion with baseline, target, and window
3. **Sanity-check** (5 min). For each: would your team actually try this in the next 60 days? If not, the experiment is too ambitious or too vague.

### Worked example — FieldPulse

```markdown
### Experiment 1: Auto-assign code reviewers

**Bottleneck:** Build → Code review queue (1.5 days average wait).

**Hypothesis:** We believe that auto-assigning code reviewers
based on file paths (using CODEOWNERS) will reduce time-to-first-
review from 1.5 days to ≤ 4 hours, because the current 1.5-day
wait is mostly "who's going to review this" decision time.

**Test:** Configure CODEOWNERS for the reconcile module; run
for 4 sprints (8 weeks); compare time-to-first-review and time-
to-merge against the 8 sprints prior.

**Success criterion:**
- Baseline: time-to-first-review p50 = 1.5 days, p90 = 3 days
- Target: p50 ≤ 4 hours, p90 ≤ 1 day, over the 4 sprints
- Window: 8 weeks; min sample 30 PRs

**What could go wrong:**
- Reviewers feel burdened by constant assignment → measure complaints / opt-outs
- Auto-assigned reviewer is on PTO → fall-back to next-in-list
- One reviewer becomes overloaded → measure per-reviewer load

**Who runs it:** <eng lead> with <TPM> support
**By when:** Pilot starts next sprint (2026-05-13)

**Decision after:**
- Met: institutionalize CODEOWNERS for the whole codebase
- Not met: examine why; possibly try paired-review during dev
```

---

## Activity 2 — DP Integration Pass

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Read the full DP top to bottom. Fix incoherences. Lock the version that goes into Friday's review.

### The integration checklist

| Check | Pass criterion |
|-------|----------------|
| **§1 outcomes ↔ §2 backlog** | Every output in §2 maps to an outcome in §1 |
| **§2 backlog ↔ §3 tracking** | Every leading indicator in §3 corresponds to backlog items |
| **§3 tracking ↔ §4 VSM** | Cycle-time leading indicators are consistent with VSM measurements |
| **§4 queues ↔ §5 experiments** | Every top queue has at least one experiment |
| **References to PRD/TCD/TMD/SEP** | DP cites prior artifacts by section |
| **No fortune-cookie prose** | Specific to this feature |

### Triad protocol

1. **Solo read-through** (15 min). Each member reads §§1–5; marks issues in margins.
2. **Pool issues** (10 min). De-dupe.
3. **Fix in priority order** (15 min). Coherence first, then prose.

---

## Activity 3 — Cross-Review with Friday Rubric

**Format:** Triad-pair &bull; **40 min** &bull; Block 3

### Purpose
Cross-review the full DP with another triad using the Friday rubric.

### The Friday rubric (DP)

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| Outcome clarity | 20% | Outcomes user-visible; tied to NS / Tier Sheet |
| ADO discipline | 15% | Hierarchy, fields, tags, iterations populated; queries work |
| Output ↔ outcome pairing | 20% | Each output has outcome AND leading indicator |
| Value stream realism | 20% | Lead times measured (or honestly estimated); queues named |
| Bottleneck experiments | 15% | Each has hypothesis, test, success criterion |
| Integration with prior artifacts | 10% | DP references PRD/TCD/TMD/SEP appropriately |

Score 0–4 per dimension. Apply weights for total /4.0. Same convention as prior weeks.

### Cross-review protocol (40 min)

1. **Pair triads** (5 min). Same pair as prior weeks if possible.
2. **20 min cross-read** with the rubric.
3. **10 min author-triad responds** to feedback.
4. **5 min final score** captured.

---

## Activity 4 — Sign-Off + Bridge to Week 8

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Sign off the DP. Bridge to Week 8's capstone work.

### Sign-off

The triad declares the DP **Status: Approved** (or "Approved with gaps") — same convention as prior weeks. The DP joins PRD / TCD / TMD / SEP as the fifth sibling artifact.

### Bridge to Week 8 — what the capstone needs

Week 8 is the capstone. Each triad picks a real-world project (typically not FieldPulse — a project from their actual work or a designated capstone scenario). They produce an integrated artifact set in shorter form, anchored on the Week-8 topic: **AI Spec Development**.

**What carries over to Week 8:**

- The artifact templates (PRD/TCD/TMD/SEP/DP) — used in shorter form
- The AI provenance discipline
- The negotiation / outcome / tracking muscles
- The cumulative AI-validation log

**What's new in Week 8:**

- **AI Spec Development** — using AI to draft technical specs that integrate with the artifact set
- A **real-world capstone project** (not FieldPulse)
- **Final artifact presentations** Friday

### Triad protocol — Week 8 readiness check (30 min)

1. **Pick a capstone candidate** (15 min). Brainstorm 3–5 real-world projects that could be the Week-8 subject. Criteria:
    - Real product / feature you've encountered (work, school, hobby, public)
    - Substantive enough for a week of work
    - Different enough from FieldPulse to test transferability
    - Permission to discuss publicly (no NDA conflicts)
2. **Pre-flight** (10 min). What inputs would you need? Who would you ask?
3. **Declare a candidate** (5 min). Triad's preferred Week-8 capstone. Bring it Monday.

### Final wrap (last 15 min)

Each triad shares:

- The **bottleneck experiment** they're most excited to run
- The **single sharpest insight** the DP added beyond the rest of the artifact set
- Their **declared Week-8 capstone candidate**

---

## End-of-week (Week 7) checkpoint

Each triad ships:

- [x] **Full DP** with §§1–5
- [x] §1 Outcome map
- [x] §2 Loaded ADO backlog (or paper equivalent) with field discipline
- [x] §3 Tracking plan (output / outcome / leading indicator triples + cadences)
- [x] §4 Value stream map with PT / LT / flow efficiency
- [x] §5 Bottleneck removal experiments (hypothesis / test / success criterion)
- [x] AI provenance log entries
- [x] Cross-reviewed + signed off
- [x] **Week 8 capstone candidate declared**

The DP joins the PRD / TCD / TMD / SEP. Together they are the **complete sibling artifact set** built across Weeks 3–7 — the input to the Week-8 capstone.

## Facilitator wrap (15 min, end of week)

- Read aloud one experiment from each triad.
- Surface the **most common bottleneck pattern** across the cohort — usually code review or sprint-planning queue.
- Preview Week 8: capstone subjects + AI Spec Development.

## Facilitator reflection prompts (end of week)

- Which triad's experiments are most actionable? They are the Week-8 positive example.
- Which triad has the strongest integrated artifact set? Hold up Friday Week 8.
- Did anyone treat experiments as ceremony rather than tests? Coach in Week 8.
- Did the cohort declare strong Week-8 capstone candidates? If not, prep alternative scenarios.
