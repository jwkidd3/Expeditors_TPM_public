# Day 3 — Documenting Non-Functional Requirements

> **Activity packet** for facilitators and participant triads. Today's job: write the NFR section that an engineer treats as a **contract for what could otherwise be hand-waved** — performance, security, accessibility, observability, compliance.

## Where we are in the week

PRD has §§1–6 (context, problem, goals, scope, sketch, AC). Today adds §7 — Non-Functional Requirements. NFRs are the requirements that determine whether the feature **survives contact with reality**: real load, real users, real attackers, real compliance regimes.

Tomorrow assembles the full PRD. Friday reviews ship it.

## The non-AI rule (still)

Day 3 of 4. Hold the line.

---

## What an NFR is (and isn't)

| Is | Is not |
|----|--------|
| A constraint the system must hold under specified conditions | "The system should be reliable" |
| Measurable at runtime | "It should be fast" |
| Defended with a target value (e.g., p95 latency &lt; 400ms) | A wish |
| Tied to a real cost-of-failure scenario | A boilerplate copied from a template |

NFRs are where many PRDs die: written as boilerplate, ignored at scoping, dropped at delivery. Today's discipline: every NFR is **specific, measurable, defended, and testable**.

---

## The five NFR categories (today's reference)

We use five categories. Cover all five — each gets at least one NFR. Most PRDs need 6–10 NFRs total.

### 1. Performance
- Latency targets (p50 / p95 / p99)
- Throughput (requests / second)
- Resource usage caps (memory, CPU, payload size)
- Time-to-interactive on cold start

### 2. Security
- AuthN/AuthZ requirements
- Data classification (PII, PCI, internal, public)
- Encryption (in transit, at rest)
- Audit logging requirements

### 3. Accessibility
- WCAG conformance level (2.1 AA is the standard floor)
- The 8 checks from Week 2 Day 3
- Specific to feature (keyboard reachability, screen reader announcements)

### 4. Observability
- What logs (events, levels, structured fields)
- What metrics (operational signals from your Week-2 Tier Sheet)
- What traces (cross-service)
- What alerts (when to page, when not to)

### 5. Compliance / regulatory
- Data residency (e.g., EU data stays in EU)
- Retention windows
- Industry-specific (HIPAA, SOC2, PCI, etc.)
- Audit trail requirements

---

## The NFR template

Each NFR follows a four-part shape:

```markdown
### NFR — <short name>
**Category:** Performance / Security / Accessibility / Observability / Compliance

**Requirement:** <specific, measurable target>

**Defense:** <why this number, in plain language; what scenario justifies it>

**Verification:** <how we will test/observe this in production or pre-prod>
```

The **Defense** is the section that distinguishes a TPM-quality NFR from boilerplate. "p95 latency &lt; 400ms because dispatchers tap this 40 times per shift; 1 second feels slow at that frequency, and 400ms is below the threshold of feeling sluggish" — that defense is the work.

---

## Activity 1 — NFR Triage

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Calibrate the eye on real-world NFR examples — most PRD templates ship with terrible boilerplate NFRs. The cohort needs to see what bad looks like before writing their own.

### Setup
Each triad receives the **NFR Triage Pack**: 10 NFR examples drawn from real PRDs. Some clean. Most have at least one of these failures:

| NFR failure mode | Example |
|------------------|---------|
| **Boilerplate** | "Performance must be acceptable" |
| **Unmeasurable** | "The system shall be highly available" |
| **No defense** | "p95 latency &lt; 100ms" (with no rationale; why this number?) |
| **No verification** | "The system shall be secure" (how would we know?) |
| **Wrong category** | A "Performance" NFR that's actually a feature requirement |

### Triad protocol

1. Triage all 10 NFRs (15 min). Identify failures. Mark "clean" if applicable.
2. Rewrite the 5 worst (15 min). Use the NFR template.
3. Pick the one that is hardest to defend even after rewriting (5 min) — discuss in the readout.

### Readout (60 sec per triad)

> "The hardest NFR to defend was [X] because [why]. Our cleanest rewrite was [example]."

### Deliverable

10 triaged NFRs with failure-mode labels, 5 rewrites using the four-part template, and one NFR flagged as hardest-to-defend.

---

## Activity 2 — Performance + Observability NFRs

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Cover two related categories that TPMs most often own jointly. Performance NFRs are the "what should we expect" side; observability NFRs are the "how would we know" side.

### Setup
Each triad needs their Week-2 Tier Sheet operational signals and the NFR four-part template. No AI.

### Performance NFR examples (FieldPulse reconcile feature)

```
### NFR — Reconcile flow latency
**Category:** Performance
**Requirement:** Modal opens within 1 second (p95) on the median dispatcher device
            (mid-tier Android, 2-year-old hardware) on a 4G LTE connection.
**Defense:** Dispatchers tap "Reconcile all" 30+ times per shift. At p95 = 1s,
            cumulative wait ≤ 30s/shift. At p95 = 3s, cumulative wait = 90s/shift,
            crossing the threshold dispatchers reported as "I'd rather use paper."
**Verification:** Synthetic transaction in Datadog from a fleet of mid-tier devices.
            p95 reported daily; alert if 7-day trailing p95 > 1.2s.
```

### Observability NFR examples

```
### NFR — Reconcile-flow event coverage
**Category:** Observability
**Requirement:** The reconcile flow emits structured events for: open_modal,
            ticket_select, ticket_deselect, submit_attempt, submit_success,
            submit_failure (with reason), abandon (modal closed without submit).
**Defense:** Three of the operational signals on our Week-2 Tier Sheet
            (abandonment rate, submit-failure reasons, time-to-submit) require
            these events. Without them, we cannot measure success.
**Verification:** Smoke test in staging asserts each event fires; production
            dashboard tracks event counts per dispatcher per shift.
```

### Triad protocol

1. **Performance first** (15 min). Each member proposes 1 performance NFR. Triad picks 2–3 to keep. Write defenses.
2. **Observability next** (15 min). Same drill. The observability NFRs should explicitly reference the Tier Sheet operational signals from Week 2.
3. **Cross-check** (10 min). Does each performance NFR have an observability NFR that allows us to **see whether we hit the target**?

### What "good" looks like

- Each NFR's **defense** is grounded in user behavior or a metric, not abstraction
- Every Tier Sheet operational signal has at least one observability NFR enabling it
- Performance targets are at p95 or p99, not "average" (which lies)

### Deliverable

2–3 Performance NFRs and 2–3 Observability NFRs in PRD §7, each pair cross-checked so every performance target is observable in production.

---

## Activity 3 — Security + Accessibility + Compliance

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Cover the three remaining categories. These are the categories most often delegated to "the security team will tell us" or "the legal team will tell us" — the TPM job is to **draft the first version** so those conversations have a starting point.

### Setup
Each triad needs the Week-2 Day-3 A11y Floor Checklist, knowledge of any compliance regime touching the feature, and the NFR template. No AI.

### Security NFRs — the standard set

For most B2B features, the security NFR set should answer:

1. **AuthN:** How do we know who the user is? (SSO? SAML? Same as parent app?)
2. **AuthZ:** What can this user do? (RBAC mapping; explicit not-allowed list)
3. **Data classification:** What data does this feature touch? PII? PCI? Internal?
4. **Encryption:** In transit (TLS 1.2+ minimum); at rest (managed keys?)
5. **Audit:** What user actions are logged? Where? Retained how long?

### Accessibility NFRs

Pull from the **A11y Floor Checklist** from Week 2 Day 3. State the conformance target:

```
### NFR — Accessibility floor
**Category:** Accessibility
**Requirement:** The reconcile flow conforms to WCAG 2.1 AA. All interactive elements
            keyboard-focusable; visible focus indicators; 4.5:1 text contrast minimum;
            form fields labeled; error messages identify the field.
**Defense:** Customer base includes dispatchers using assistive technology (Interview 3:
            screen-reader user). ADA exposure is non-trivial in our segment.
**Verification:** axe-core scan on every PR; manual screen-reader pass before launch.
```

### Compliance NFRs (FieldPulse-flavored examples)

```
### NFR — Audit trail retention
**Category:** Compliance
**Requirement:** Reconcile-flow events are retained for 24 months in the audit
            event store, queryable by dispatcher_id and date range.
**Defense:** SOC 2 Type II requires user-action audit trail; dispatch decisions
            are subject to wage-and-hour audit by some state authorities.
**Verification:** Quarterly audit-trail test: random user-event from 18 months
            ago must be retrievable in <10 minutes.
```

### Triad protocol

1. **Security NFRs (3–5)** — 15 min
2. **Accessibility NFRs (1–2)** — 10 min (pull from A11y Floor)
3. **Compliance NFRs (1–2)** — 10 min — what regulatory regime is your feature touching?
4. **Cross-check** (5 min) — defenses are real, not boilerplate

### Deliverable

3–5 Security NFRs, 1–2 Accessibility NFRs, and 1–2 Compliance NFRs appended to PRD §7, each with a concrete defense.

---

## Activity 4 — NFR Cross-Review + Trade-Off Discussion

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Cross-review the NFR sections (same pairing as Day 2 if possible — the reviewer is now familiar with the PRD). Surface trade-offs explicitly: NFRs interact, and several often pull in opposite directions.

### Setup
Instructor pre-assigns triad pairs (re-use Day 2 pairs when possible). Each triad needs the full §§1–7 draft and the four classic trade-off prompts. No AI.

### The four classic NFR trade-offs

| Trade-off | The tension |
|-----------|-------------|
| Performance vs Observability | Heavy logging slows the hot path; light logging blinds you when it breaks |
| Security vs Time-to-first-value | Strict authZ blocks the new-user happy path |
| Compliance vs Latency | EU data residency requirements add cross-region hops |
| Accessibility vs Visual Polish | Some animation patterns conflict with reduced-motion / screen-reader |

A mature NFR section **names the trade-offs** and explains how they were resolved (or left open as a known tension).

### Cross-review protocol

1. **Pair triads** (same pair as Day 2 ideally)
2. **Read the NFR section** (10 min). For each NFR, ask:
    - Is the **defense** specific or boilerplate?
    - Is the **verification** real or aspirational?
    - Does this NFR **trade off** with another in the section?
3. **Reviewer surfaces trade-offs** (10 min). Identify at least one place where two NFRs in the section pull in opposite directions.
4. **Author triad responds** (10 min). Adopt / defer / push back.
5. **Authors revise + add a "Known trade-offs" subsection** (15 min) at the end of §7.

### The Known Trade-offs subsection

```markdown
### Known trade-offs (in this section)

- **Audit logging vs latency:** NFR-7 (full event logging) adds ~30ms to the
  hot path tested in NFR-1. We accept this; if hot-path latency becomes
  the bottleneck, we will move logging to async dispatch.
- **Strict RBAC vs onboarding:** NFR-10 (managers cannot view dispatcher
  reconciles in their first week) blocks an onboarding scenario. Resolved:
  managers see read-only view in week 1; full view in week 2.
```

### Deliverable

Revised PRD §7 with a "Known trade-offs" subsection naming at least one explicit tension and its resolution.

### Wrap (last 15 min)

Each triad shares **one trade-off they made explicit** in their NFR section. The cohort gets to hear how others resolved tensions.

---

## End-of-day checkpoint

Each triad's PRD now has §7 with:

- [x] At least one NFR per category (Performance / Security / Accessibility / Observability / Compliance)
- [x] 6–10 NFRs total
- [x] Each NFR uses the four-part template (requirement / defense / verification / category)
- [x] A "Known trade-offs" subsection
- [x] An updated review-resolution note covering the Day 3 review

## Facilitator reflection prompts (end of day)

- Which triad's defenses were strongest? Hold up Friday as positive example.
- Which triad has the most boilerplate? Coach privately tomorrow morning.
- Did anyone skip Compliance? Probably yes. Surface tomorrow.
- Did anyone use AI? Last day to course-correct.
