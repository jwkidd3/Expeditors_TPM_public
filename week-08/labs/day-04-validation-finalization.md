# Day 4 — Technical Logic Validation & Finalization

> **Activity packet** for participant quads. Today's job: catch every inconsistency across the artifact set, add the **SEP-light** and **DP-light**, integrate everything, and rehearse the presentation. Tomorrow you present.

## Where we are in the week

The 4 documents from Day 3 (PRD-light, TCD-light, TMD-light, AI Spec v1) need to be **internally consistent** before they ship. Today's discipline is **technical logic validation** — checking that the data model supports the API, the SLOs match the architecture, the metrics align with the outcome map, and the trade-offs don't contradict.

Plus today produces the last 2 documents: **SEP-light** and **DP-light**, in compressed form.

## Inputs

- All 4 documents from Day 3
- Day-3 cross-quad findings
- The SEP / DP templates from Weeks 6–7

---

## What "technical logic validation" means

A common rookie failure: each artifact is fine in isolation, but together they don't fit. Examples:

- The PRD's NFR says "p95 < 500ms" but the TMD's sequence diagram totals 800ms
- The TCD says "modular monolith" but the TMD shows components that need to deploy independently
- The data model has no foreign key for a relationship the API requires
- The outcome map's "leading indicator" isn't measurable with the observability NFR

Technical logic validation = **walk every cross-artifact reference** and verify they're consistent.

---

## The 7-point validation checklist

| # | Check | Where to look |
|---|-------|---------------|
| 1 | Outcome map → metrics → SLOs aligned | DP-light Section 1, PRD-light Section 7, TCD-light Section 4 |
| 2 | Data model supports the API contract | TMD-light Section 1 ↔ Section 3 |
| 3 | API contract supports the AC | TMD-light Section 3 ↔ PRD-light Section 6 |
| 4 | SLO budget fits the sequence diagram | TCD-light Section 4 ↔ TMD-light Section 4 |
| 5 | NFRs don't contradict the architecture stance | PRD-light Section 7 ↔ TCD-light Section 1 |
| 6 | Trade-offs don't contradict each other | TCD-light Section 5 |
| 7 | Stakeholder sign-off captures all constraints | TCD-light Section 6 |

A quad that passes all 7 has a coherent artifact set. Most fail 2–3 on first pass — that's expected; that's why this day exists.

---

## Activity 1 — The 7-Point Validation

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Walk every check; document what passes and what doesn't.

### Quad protocol

For each of the 7 checks, the quad walks the cross-references:

1. **Pull both sides of the check** (e.g., for #4: latency SLO target + sequence diagram totals)
2. **Compare** — do they agree?
3. **If yes**: mark pass.
4. **If no**: document the gap. Decide:
    - Tighten the artifact in question (often the answer)
    - Adjust the SLO / NFR (only if evidence demands)
    - Mark as a known gap to call out in the presentation

The validation log:

```markdown
| # | Check | Status | Gap / fix |
|---|-------|--------|-----------|
| 1 | Outcome → metrics → SLOs | Pass | None |
| 2 | Data model ↔ API | Partial | Missing FK on User → Order; added |
| 3 | API ↔ AC | Pass | None |
| 4 | SLO budget ↔ sequence | Fail → Fixed | Sequence totaled 800ms; SLO was 500ms; tightened SLO to p95 < 1000ms with defense |
| 5 | NFRs ↔ architecture | Pass | None |
| 6 | Trade-offs internal consistency | Pass | None |
| 7 | Stakeholders ↔ constraints | Partial | Compliance not on sign-off list; added |
```

### Output

A validation log + updated artifacts.

---

## Activity 2 — SEP-Light + DP-Light

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Compressed Weeks 6 + 7 in 50 minutes. SEP-light captures stakeholder + 1 trade-off brief + 1 simulated negotiation; DP-light captures outcome map + backlog skeleton + 1 experiment.

### SEP-light template

```markdown
# SEP-light — <feature>

## 1. Stakeholder map (compressed)
3 high-power stakeholders. Power × Interest placement + RACI for 1 decision (the most consequential).

## 2. 1 Trade-off brief
1 page. Pick one TCD-light Section 5 trade-off; brief for the relevant stakeholder.

## 3. 1 Simulated negotiation outcome
For one of the 5-most-consequential asks, document:
- The ask
- Anticipated stakeholder response (top 1 objection + your response)
- Anticipated agreement / deferral / escalation path
```

### DP-light template

```markdown
# DP-light — <feature>

## 1. Outcome map (compressed)
Primary outcome + 2 supporting outcomes + 1 counter-outcome.

## 2. Backlog skeleton
1 Epic + 1 Feature + 5 User Stories (top-priority subset of PRD-light Section 6).

## 3. Tracking plan (compressed)
3 leading indicators. 1 monthly review cadence.

## 4. Value stream (compressed)
Top 3 queues identified.

## 5. 1 Bottleneck removal experiment
Hypothesis / test / success criterion for one queue.
```

### Quad protocol

1. **SEP-light** (30 min):
    - 5 min: 3 stakeholders + RACI for the most consequential decision
    - 10 min: 1 trade-off brief (pull from TCD-light Section 5)
    - 5 min: 1 simulated negotiation outcome
2. **DP-light** (20 min):
    - 5 min: outcome map (primary + 2 supporting + counter)
    - 5 min: backlog skeleton
    - 5 min: 3 leading indicators
    - 5 min: 1 bottleneck experiment

### What "good" looks like

- SEP-light's 1 trade-off brief is in the **stakeholder's currency** (not technical)
- DP-light's primary outcome is **user-visible**
- The leading indicators are **measurable within 7 days**
- The bottleneck experiment has a **measurable success criterion**

---

## Activity 3 — Cross-Artifact Integration Pass

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Read all 6 documents top-to-bottom. Catch any remaining contradictions. Add forward / backward references between artifacts.

### The 6 documents

1. PRD-light
2. TCD-light
3. TMD-light
4. SEP-light
5. DP-light
6. AI Spec v1

### Integration check

For every cross-artifact reference, confirm:

- The reference is **specific** (cite Section, not "see the TCD")
- The referenced section **exists** and **says what's claimed**
- The reference **adds value** (linking provides context the reader needs)

### Quad protocol

1. **Solo read-through** (25 min). Each member reads all 6 documents.
2. **Pool issues** (10 min).
3. **Fix in priority order** (15 min): coherence first, prose second.

### What "good" looks like

- Every cross-reference is verified
- The 6 documents read as a coherent set, not 6 standalone pieces
- The AI Spec correctly synthesizes the others (the synthesis test)

---

## Activity 4 — Presentation Rehearsal

**Format:** Quad &bull; **55 min** + Wrap &bull; Block 4

### Purpose
Rehearse the 15-minute Friday presentation. Time it. Get feedback. Fix what doesn't land.

### The presentation structure (15 min)

| Time | Section | What's covered |
|------|---------|-----------------|
| 1 min | Customer + problem | Real customer; specific friction |
| 2 min | Outcome | Primary outcome; tied to user/business value |
| 3 min | Architecture stance + top trade-off | Defended in business terms |
| 3 min | Data + API + sequence highlights | Engineering-ready summary |
| 2 min | SLO + key constraint | Latency / availability / one compliance item |
| 2 min | Stakeholder + delivery readiness | SEP-light + DP-light highlights |
| 2 min | What you'd do differently with more time | Honesty + reflection |

Plus 5 min Q&A.

### Quad protocol

1. **Decide who speaks** (5 min). All 3 quad members on stage; assign sections.
2. **Run-through #1 with timer** (25 min). One pass; nobody interrupts.
3. **Capture what didn't work** (10 min). Where did the timer break? Where did a section drag?
4. **Run-through #2** (15 min). Apply fixes. Time again.

### What "good" looks like

- The 15-min limit is held (within 30 sec)
- All three quad voices speak
- The customer + problem section grounds the rest
- The trade-off section is **defended in business terms**, not technical jargon
- The "what we'd do differently" section is **honest**, not performative

### Wrap (last 15 min)

Each quad shares:

- Their **opening sentence**
- The **section they're least sure of**
- One **anticipated Q&A question**

---

## End-of-day checkpoint

Each quad ends Day 4 with:

- [x] **Validation log** — all 7 checks marked
- [x] **SEP-light** (1 page)
- [x] **DP-light** (1 page)
- [x] **AI Spec v2** (after integration pass)
- [x] **Final 6-document set**, integrated
- [x] **Presentation rehearsed** at least twice with timer
- [x] Final provenance log entry
