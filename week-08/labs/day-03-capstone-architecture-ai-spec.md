# Day 3 — Capstone Architecture + AI Spec Drafted

> **Activity packet** for participant triads. Today's job: produce **TCD-light + TMD-light**, then run the **AI Spec 5-prompt sequence** on the capstone to produce AI Spec v1. The most ambitious day of the week.

## Where we are in the week

PRD-light shipped yesterday. Today compresses Weeks 4–5 into one day, then applies Day-1's AI Spec pattern to integrate everything. By 16:00, every triad has 4 documents: PRD-light, TCD-light, TMD-light, and AI Spec v1.

## Inputs

- PRD-light from Day 2
- Day-3 plan: 3 architectural questions, integration sketch, critical path
- The 5-prompt AI Spec sequence (rehearsed Day 1 on FieldPulse)

---

## TCD-light template (compressed)

A 1.5-page version of TCD:

```markdown
# TCD-light — <feature>

## 1. Architecture stance
1 paragraph. Mono / micro / hybrid + the deploy/failure/scale frame.

## 2. Integration map
Table: system / owner / sync-async / R-W / failure handling.

## 3. Threat-model summary
3 highest-priority STRIDE threats + mitigations.

## 4. SLOs (3)
1 latency / 1 availability / 1 rate-limit. Target + defense + verification.

## 5. Top 3 trade-offs
Each: Option A / B / Choice / Cost / Revisit trigger.

## 6. Stakeholder sign-off
3–5 stakeholders + status.
```

## TMD-light template (compressed)

A 1.5-page version of TMD:

```markdown
# TMD-light — <feature>

## 1. Data model
3–5 entities with PK + indexes + relationships. 1 storage trade-off.

## 2. Cloud topology
Region / managed vs self / tenancy / network boundary. ROM cost.

## 3. API contract
3–5 endpoints with method / path / status codes / idempotency.

## 4. Sequence
Happy path; 1 sad path; 1 weird path with named invariant.

## 5. Performance baseline + monitoring
3 baselines + 3 alerts + 1 leading indicator.
```

## AI Spec template (recap from Day 1)

```markdown
# AI Spec — <feature>

## 1. Headline
## 2. Engineering-ready summary
## 3. Data + API contract
## 4. Sequence + failure handling
## 5. Constraints
## 6. Decisions made (and not made)
## 7. Stakeholders + sign-off
## 8. Provenance log
```

---

## Activity 1 — TCD-light

**Format:** Triad &bull; **40 min** &bull; Block 1

### Purpose
Compressed Week-4 work in 40 minutes. Architecture stance + integration + threat model + SLOs + top trade-offs + sign-off.

### Triad protocol

1. **Architecture stance** (10 min). 1 paragraph applying the three-question frame (deploy / failure / scale).
2. **Integration map** (10 min). Pull from PRD-light §10 (deps) + sketch from Day 2. Sync/async + R/W + failure handling.
3. **Threat model summary** (10 min). 3 STRIDE-flagged threats. Apply walk-the-data-flow frame.
4. **SLOs** (5 min). 1 each of latency / availability / rate-limit. Target + defense.
5. **Top trade-offs** (5 min). 3 trade-offs in Option A/B/Choice/Cost/Revisit format.

### What "good" looks like

- Architecture stance defended in business terms (not framework hype)
- Integration map has failure-handling stance per row
- Threats are specific, with mitigations
- SLOs have defenses tied to user behavior
- Trade-offs have revisit triggers

---

## Activity 2 — TMD-light

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Compressed Week-5 work in 40 minutes. Data + cloud + API + sequence + monitoring.

### Triad protocol

1. **Data model** (10 min). 3–5 entities with PK + key indexes + relationships. 1 storage trade-off (often: normalize vs denormalize).
2. **Cloud topology** (10 min). Region / managed vs self / tenancy / network. ROM cost — even rough.
3. **API contract** (10 min). 3–5 endpoints. Method + path + status codes + idempotency approach.
4. **Sequence** (5 min). Happy path narrative + 1 sad + 1 weird with **named invariant**.
5. **Baselines + monitoring** (5 min). 3 baselines + 3 alerts + 1 leading indicator.

### What "good" looks like

- Data model entities have access patterns that drove them
- Cloud topology has a ROM cost number (even if rough)
- API endpoints have status codes and idempotency
- The weird path has a named invariant
- The leading indicator is measurable within 7 days

---

## Activity 3 — Run the 5-Prompt AI Spec Sequence

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Apply the Day-1-rehearsed sequence to the capstone subject.

### Triad protocol

Same 5 prompts as Day 1, with capstone inputs this time:

1. **Prompt 1 — Headline + summary** (8 min). Inputs: PRD-light §§1–5, TCD-light §1, TMD-light §3.
2. **Prompt 2 — Data + API synthesis** (8 min). Inputs: TMD-light §1 + §3.
3. **Prompt 3 — Sequence + failure** (8 min). Inputs: TMD-light §4.
4. **Prompt 4 — Constraints** (8 min). Inputs: TCD-light §3 + §4 + PRD-light §7.
5. **Prompt 5 — Decisions + stakeholders** (8 min). Inputs: TCD-light §5 + §6.

### Validation discipline (between every prompt)

- **Read** the output against the source
- Mark each claim: cross-checked / spot-checked / pending / rejected
- Cut hallucinated claims
- Preserve verbatim: trade-off costs, revisit triggers, named invariants, customer quotes

### Output

AI Spec v1 — assembled from the 5 outputs, plus the provenance log.

---

## Activity 4 — Cross-Triad Spot-Check + Day-4 Setup

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Cross-triads validate each other's AI Specs against the source artifacts. Catch what the author triad missed.

### Cross-validation protocol

1. **Pair triads** (5 min).
2. **Reviewer triad receives** the source PRD-light + TCD-light + TMD-light AND the AI Spec v1.
3. **20 min validation pass:** the reviewer triad takes 5–10 specific claims from the AI Spec and checks each against the source. Mark wrong / partly right / right.
4. **5 min author triad listens** to findings.
5. **15 min author revises** AI Spec.

### Day-4 setup (last 5 min, before wrap)

Tomorrow's job: technical logic validation + finalization. Plan ahead.

- What gaps in the artifact set would a senior architect catch?
- What integration check would surface inconsistency between PRD/TCD/TMD/AI Spec?
- What's the "bow on it" task — the polish that makes Friday's presentation land?

### Wrap (last 15 min)

Each triad shares:

- The **AI Spec section** they're proudest of
- The **claim** the cross-triad caught as wrong / weak
- One **gap** they want to address tomorrow

---

## End-of-day checkpoint

Each triad ends Day 3 with:

- [x] **TCD-light** (1.5 pages)
- [x] **TMD-light** (1.5 pages)
- [x] **AI Spec v1** (assembled from 5-prompt sequence)
- [x] Cross-triad validation findings captured
- [x] Provenance log entry
- [x] Day-4 plan
