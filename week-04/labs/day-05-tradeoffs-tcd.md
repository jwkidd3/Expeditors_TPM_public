# Day 5 — Technical Trade-Offs & Constraints (TCD Assembly + Review)

> **Activity packet** for your quad. Today's job: name the **top 5 trade-offs** in your architecture (TCD Section 5), build the **stakeholder sign-off matrix** (TCD Section 6), assemble the integrated TCD, peer-review it, and ship it as the sibling artifact to your PRD.

## Where we are in the week

Days 1–4 produced TCD Sections 1–4 (stance, integrations + diagrams, security, SLOs). Today produces:

- **Section 5 — Top 5 trade-offs** (the section that distinguishes mature architecture documents)
- **Section 6 — Stakeholder + sign-off matrix** (who owns each constraint, what's the status)
- **The integrated TCD** — read top-to-bottom, polished, peer-reviewed, signed off

## Inputs

- TCD Sections 1–4 (Days 1–4)
- The PRD it pairs with
- The "Known Trade-offs" subsection from Week 3 Day 3 — Today's trade-offs build on it
- The owner names from PRD Section 10 — they go on the sign-off matrix

---

## What a trade-off looks like (mature vs immature)

The TCD Section 5 is the section that **separates senior architectural thinking from feature-list thinking**. A trade-off is not a list of risks; it's a structured statement of: *we considered A and B, we chose A, we accept this cost, this is what would change our minds*.

| Immature | Mature |
|----------|--------|
| "We considered microservices but chose a monolith" | "Option A: modular monolith. Option B: extract reconcile into a service. We chose A. We accept that future service-extraction will require coordinated refactoring; we will revisit if traffic exceeds 5x rest-of-app or if a second team starts contributing reconcile features." |
| "Performance vs observability is a trade-off" | "Logging full event detail adds ~30ms to the hot path; we accept that until p95 nears the SLO; if the budget closes, we move to async event publication." |
| "We don't have time to build offline-first" | "Offline-first sync would add 8–12 weeks. We chose offline-draft + manual reconcile. Accepted cost: dispatchers without coverage during outages do paper, then re-enter. Revisit if outage frequency exceeds 1/quarter." |

The pattern is always: **Option A vs Option B → choice → accepted cost → revisit trigger.**

---

## The stakeholder sign-off matrix (TCD Section 6)

A constraint without an owner is a constraint nobody implements. The sign-off matrix lists every load-bearing constraint with:

- The **constraint** (link to the TCD section it's in)
- The **stakeholder** who must approve (a person, not a team)
- The **status**: proposed / discussed / approved
- The **next step** if status isn't "approved"

This section is the **action list** for Week 6 (stakeholder negotiation). Today the quad pre-loads it with everyone they'll need to talk to.

---

## Activity 1 — Surface the Trade-Offs

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Identify the actual trade-offs your architecture made. Most teams under-report — they describe the choice and skip the alternative.

### Setup
Each quad needs TCD Sections 1–4 from this week. AI optional; use the Critique-hat prompt if you do.

### The five categories of architectural trade-off

For most features, trade-offs fall into one of these:

| Category | Example tension |
|----------|-----------------|
| **Coupling vs independence** | Module in monolith vs new service |
| **Consistency vs availability** | Strong-consistency reads vs replica reads |
| **Latency vs durability** | Sync write vs async with retry |
| **Speed vs robustness** | Ship the happy path now, harden later |
| **Generality vs simplicity** | Build the generic capability or just this case |

A well-written Section 5 covers **multiple categories**. A Section 5 with 5 trade-offs all in the same category usually missed real tensions.

### Quad protocol

1. **Brainstorm 8–10 candidate trade-offs** (25 min). Pull from Sections 1–4. Look for places where your TCD said "we chose X" — for each, what was the alternative?
2. **Categorize each** (5 min). Which of the 5 categories?
3. **Cull to 5 finalists** (10 min). Pick the trade-offs that are most consequential — the ones a senior architect would interrogate.
4. **Rough out the structure** (5 min). For each, jot Option A / Option B / Choice / Accepted cost / Revisit trigger.

### What "good" looks like

- Trade-offs span **at least 3 categories**
- Each names a **real alternative**, not a strawman
- The "accepted cost" is concrete — not "complexity"
- The "revisit trigger" is a metric or organizational change, not "later"

### Deliverable

5 trade-off finalists with sketch structure (Option A / Option B / Choice / Accepted cost / Revisit trigger), spanning at least 3 categories.

---

## Activity 2 — Write the Top 5 Trade-Offs

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Convert the structure from Activity 1 into the final Section 5 prose.

### Setup
Each quad needs the trade-off sketches from Activity 1 and the Section 5 template. AI optional.

### The trade-off template

```markdown
### Trade-off N — <short name>
**Tension:** <category> — <one sentence framing the tension>
**Option A:** <description, 1–2 sentences>
**Option B:** <description, 1–2 sentences>
**Choice:** Option A.
**Why:** <2–3 sentences — defended in business + operational terms>
**Accepted cost:** <what we give up, concretely>
**Revisit trigger:** <metric or organizational change>
```

### Worked example — FieldPulse reconcile

```markdown
### Trade-off 1 — Module vs new service
**Tension:** Coupling vs independence.
**Option A:** Reconcile lives as a module inside the existing backend monolith.
**Option B:** Extract reconcile into a new microservice with its own database.
**Choice:** Option A.
**Why:** Only one team owns reconcile; deploy-cadence contention is zero.
        Reconcile depends on Tickets and Auth; new service buys no resilience.
        Reconcile has the same scaling curve as the rest of the app (dispatcher-shift
        bounded). Modular monolith is the cheaper, more reversible choice.
**Accepted cost:** Future service-extraction will require coordinated refactoring,
        especially of the Tickets boundary.
**Revisit trigger:** Reconcile traffic exceeds 5× rest-of-app, OR a second team
        begins contributing reconcile features.

### Trade-off 2 — Sync vs async write to audit
**Tension:** Latency vs durability.
**Option A:** Synchronous write to audit event store before responding to user.
**Option B:** Async publish to Event Hubs audit stream; consumer writes to store.
**Choice:** Option B.
**Why:** Synchronous would add 30–80ms to the reconcile latency budget,
        breaking the p95 ≤ 1000ms SLO. Async with Event Hubs durability is sufficient
        for SOC 2 audit requirements. The DLQ on the consumer handles the rare
        write failures.
**Accepted cost:** Audit events may lag 1–10 seconds behind user action; a
        regulator querying within seconds of an event may see stale state.
**Revisit trigger:** A regulator or customer requires synchronous audit visibility
        within < 1 second.
```

### Quad protocol

1. **Solo drafts** (25 min). Each member drafts 2 of the 5 final trade-offs.
2. **Pool and refine** (15 min). The quad polishes each — clarity, specificity.
3. **Consistency check** (10 min). Do the trade-offs **contradict** each other? If yes, that's a finding — surface it.

### Deliverable

TCD Section 5 with five fully written trade-offs using the template, plus a note on any internal contradictions surfaced during the consistency check.

---

## Activity 3 — Stakeholder Sign-Off Matrix

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Build Section 6. Every constraint that requires another team's buy-in goes on the matrix with an owner and a status.

### Setup
Each quad needs TCD Sections 1–5 from this week, PRD Section 10 (Dependencies), and any owner names surfaced earlier. AI optional.

### The matrix template

```markdown
## 6. Stakeholders + sign-off matrix

| # | Constraint (link) | Stakeholder | Status | Next step |
|---|-------------------|-------------|--------|-----------|
| 1 | Section 1 Architecture stance | <Architect name> | Proposed | Schedule 30-min walkthrough |
| 2 | Section 3 Threat model | <Security lead name> | Proposed | Send security brief, 30-min walk-through |
| 3 | Section 3 Compliance NFRs (SOC 2 audit retention) | <Compliance lead name> | Proposed | Email + 15-min sync |
| 4 | Section 4 Latency SLO | <Eng lead name> | Discussed | Confirm in next sprint review |
| 5 | Section 4 Rate-limit policy | <Platform lead name> | Proposed | Slack thread + review |
| 6 | Section 5 Trade-off 1 (module vs service) | <Architect name> | Proposed | Same walkthrough as #1 |
| 7 | Section 10 PRD: SSO scope addition | <Identity team lead> | Approved (Slack 2026-04-15) | None |
```

**Status** values:
- **Proposed**: TPM has drafted; stakeholder hasn't reacted yet
- **Discussed**: Conversation happened; no formal sign-off yet
- **Approved**: Stakeholder said yes (capture how — Slack, meeting note, email)
- **Blocked**: Stakeholder pushed back; needs different proposal

### Quad protocol

1. **List every constraint that needs sign-off** (25 min). Walk through TCD Sections 1–5; for each load-bearing decision, who has to agree?
2. **Assign a real person** (10 min). Use names from PRD Section 10 + anyone new. "TBD" is not allowed.
3. **Set the next step** (10 min). For each Proposed: how will the conversation happen?
4. **Status sanity check** (5 min). Honest status — most should be Proposed.

### What "good" looks like

- **At least 6 entries** — most architectural features touch this many stakeholders
- Every entry has a **real person**, not a team
- "Next step" is **specific** — "schedule a 30-min walkthrough" beats "talk to security"
- One entry probably says "Approved" because Week-3 Day-1 dependency work caught it; rest are Proposed

### Deliverable

TCD Section 6 sign-off matrix with at least 6 named entries, each with constraint link, real-person stakeholder, honest status, and a specific next step.

---

## Activity 4 — Integration + Cross-Review + Sign-Off

**Format:** Quad &bull; **55 min** + Wrap &bull; Block 4

### Purpose
Final TCD assembly. Cross-review by another quad. Internal sign-off. The TCD ships alongside the PRD.

### Setup
Instructor confirms pairings. Each quad needs the full TCD Sections 1–6 draft, the integration checklist, and the Friday TCD rubric.

### Integration pass (10 min)

As a quad, work the checklist below and fix any inconsistency before the cross-review.

| Check | Pass criterion |
|-------|----------------|
| **Section 1 stance ↔ Section 2 diagrams** | Modular monolith stance shows as one container with internal modules |
| **Section 2 integrations ↔ Section 3 threats** | Every integration boundary appears in the threat model or has an explicit "no threat" rationale |
| **Section 3 NFRs ↔ Section 4 SLOs** | Security NFRs don't conflict with latency SLOs; if they do, that's Section 5 trade-off 2 |
| **Section 4 SLOs ↔ Section 5 trade-offs** | If you accepted a latency cost, it should appear in Section 5 |
| **Section 6 stakeholders ↔ Sections 1–5 constraints** | Every load-bearing decision has an owner |
| **No fortune-cookie prose** | Every paragraph is specific to *this* feature |

### Cross-review (20 min)

Pair with another quad. The reviewer focuses on:

1. **Is each trade-off really a trade-off** or just a description of the choice?
2. **Does the stakeholder matrix have any obvious gaps?** (e.g., no security person)
3. **Are the SLOs and the trade-offs internally consistent?**

The reviewer also reads with the **Friday TCD rubric** in mind:

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| Stance defensibility | 20% | Defended in business; framework hype absent |
| Threat-model rigor | 20% | 3–5 named threats with concrete mitigations |
| Component clarity | 15% | C4 diagram readable; externals named |
| SLO realism | 20% | Anchored to user behavior; error budget honest |
| Trade-off honesty | 15% | Both sides named; trigger to revisit specified |
| Stakeholder map | 10% | Owners are people; sign-off status honest |

### Quad action (10 min)

Adopt / defer / reject reviewer findings. Same Week-3 discipline. Update sections.

### Internal sign-off (5 min)

The quad declares the TCD **Status: Approved** (or "Approved with gaps", as Week 3). The TCD is now a sibling artifact to the PRD.

### Deliverable

Signed-off TCD (Status: Approved or Approved with gaps) with adopted cross-review findings, rubric scores, and an AI provenance log covering all AI-assisted sections.

### Wrap (last 15 min)

Each quad shares **one of their five trade-offs**, including the revisit trigger. The cohort gets to hear how others reasoned through architecture decisions.

---

## End-of-week (Week 4) checkpoint

Each quad ships:

- [x] **TCD** with Sections 1–6 complete and integrated
- [x] **Architecture stance** with trade-off + revisit trigger (Section 1)
- [x] **Integration map + C4 diagrams** (Section 2)
- [x] **STRIDE threat model + revised security/compliance NFRs** (Section 3)
- [x] **Three SLOs + latency budget + rate-limit policy + error-budget consequence** (Section 4)
- [x] **Top 5 trade-offs** with full structure (Section 5)
- [x] **Stakeholder sign-off matrix** with named owners (Section 6)
- [x] AI provenance log for all AI-assisted sections

The TCD goes into Week 5 alongside the PRD. Week 5 (Technical Infrastructure & Modeling) uses the TCD's component map for data modeling, the SLOs for performance baselines, and the threat model for encryption / key-management decisions.
