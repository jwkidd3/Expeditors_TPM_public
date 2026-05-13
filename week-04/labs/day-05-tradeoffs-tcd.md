# Day 5 — Technical Trade-Offs & Constraints (TCD Assembly + Review)

> **Activity packet** for facilitators and participant triads. Today's job: name the **top 5 trade-offs** in your architecture (TCD §5), build the **stakeholder sign-off matrix** (TCD §6), assemble the integrated TCD, peer-review it, and ship it as the sibling artifact to your PRD.

## Where we are in the week

Days 1–4 produced TCD §§1–4 (stance, integrations + diagrams, security, SLOs). Today produces:

- **§5 — Top 5 trade-offs** (the section that distinguishes mature architecture documents)
- **§6 — Stakeholder + sign-off matrix** (who owns each constraint, what's the status)
- **The integrated TCD** — read top-to-bottom, polished, peer-reviewed, signed off

## Inputs

- TCD §§1–4 (Days 1–4)
- The PRD it pairs with
- The "Known Trade-offs" subsection from Week 3 Day 3 — Today's trade-offs build on it
- The owner names from PRD §10 — they go on the sign-off matrix

---

## What a trade-off looks like (mature vs immature)

The TCD §5 is the section that **separates senior architectural thinking from feature-list thinking**. A trade-off is not a list of risks; it's a structured statement of: *we considered A and B, we chose A, we accept this cost, this is what would change our minds*.

| Immature | Mature |
|----------|--------|
| "We considered microservices but chose a monolith" | "Option A: modular monolith. Option B: extract reconcile into a service. We chose A. We accept that future service-extraction will require coordinated refactoring; we will revisit if traffic exceeds 5x rest-of-app or if a second team starts contributing reconcile features." |
| "Performance vs observability is a trade-off" | "Logging full event detail adds ~30ms to the hot path; we accept that until p95 nears the SLO; if the budget closes, we move to async event publication." |
| "We don't have time to build offline-first" | "Offline-first sync would add 8–12 weeks. We chose offline-draft + manual reconcile. Accepted cost: dispatchers without coverage during outages do paper, then re-enter. Revisit if outage frequency exceeds 1/quarter." |

The pattern is always: **Option A vs Option B → choice → accepted cost → revisit trigger.**

---

## The stakeholder sign-off matrix (TCD §6)

A constraint without an owner is a constraint nobody implements. The sign-off matrix lists every load-bearing constraint with:

- The **constraint** (link to the TCD section it's in)
- The **stakeholder** who must approve (a person, not a team)
- The **status**: proposed / discussed / approved
- The **next step** if status isn't "approved"

This section is the **action list** for Week 6 (stakeholder negotiation). Today the triad pre-loads it with everyone they'll need to talk to.

---

## Activity 1 — Surface the Trade-Offs

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Identify the actual trade-offs your architecture made. Most teams under-report — they describe the choice and skip the alternative.

### Setup
Each triad needs TCD §§1–4 from this week. AI optional; use the Critique-hat prompt if you do.

### The five categories of architectural trade-off

For most features, trade-offs fall into one of these:

| Category | Example tension |
|----------|-----------------|
| **Coupling vs independence** | Module in monolith vs new service |
| **Consistency vs availability** | Strong-consistency reads vs replica reads |
| **Latency vs durability** | Sync write vs async with retry |
| **Speed vs robustness** | Ship the happy path now, harden later |
| **Generality vs simplicity** | Build the generic capability or just this case |

A well-written §5 covers **multiple categories**. A §5 with 5 trade-offs all in the same category usually missed real tensions.

### Triad protocol

1. **Brainstorm 8–10 candidate trade-offs** (15 min). Pull from §§1–4. Look for places where your TCD said "we chose X" — for each, what was the alternative?
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

### Facilitation cues

- Strawman alternatives ("the other option was obviously worse") signal under-thinking. Push for a real Option B.
- All-one-category lists usually missed real tensions; mix coupling, consistency, latency, speed, or generality.

---

## Activity 2 — Write the Top 5 Trade-Offs

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Convert the structure from Activity 1 into the final §5 prose.

### Setup
Each triad needs the trade-off sketches from Activity 1 and the §5 template. AI optional.

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
**Option B:** Async publish to Kafka audit topic; consumer writes to store.
**Choice:** Option B.
**Why:** Synchronous would add 30–80ms to the reconcile latency budget,
        breaking the p95 ≤ 1000ms SLO. Async with Kafka durability is sufficient
        for SOC 2 audit requirements. The DLQ on the consumer handles the rare
        write failures.
**Accepted cost:** Audit events may lag 1–10 seconds behind user action; a
        regulator querying within seconds of an event may see stale state.
**Revisit trigger:** A regulator or customer requires synchronous audit visibility
        within < 1 second.
```

### Triad protocol

1. **Solo drafts** (15 min). Each member drafts 2 of the 5 final trade-offs.
2. **Pool and refine** (15 min). The triad polishes each — clarity, specificity.
3. **Consistency check** (10 min). Do the trade-offs **contradict** each other? If yes, that's a finding — surface it.

### Deliverable

TCD §5 with five fully written trade-offs using the template, plus a note on any internal contradictions surfaced during the consistency check.

### Facilitator coaching cues

- A trade-off that ends "we chose A because A is better" with no actual reasoning — push back. Force the cost and trigger.
- Watch for "we accept complexity" — that's vague. What complexity? What does it cost in maintenance, debugging, on-call?
- Trade-offs that align suspiciously well with personal preference are a smell. The reasoning should come from the system, not from "I like X better."

---

## Activity 3 — Stakeholder Sign-Off Matrix

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Build §6. Every constraint that requires another team's buy-in goes on the matrix with an owner and a status.

### Setup
Each triad needs TCD §§1–5 from this week, PRD §10 (Dependencies), and any owner names surfaced earlier. AI optional.

### The matrix template

```markdown
## 6. Stakeholders + sign-off matrix

| # | Constraint (link) | Stakeholder | Status | Next step |
|---|-------------------|-------------|--------|-----------|
| 1 | §1 Architecture stance | <Architect name> | Proposed | Schedule 30-min walkthrough |
| 2 | §3 Threat model | <Security lead name> | Proposed | Send security brief, 30-min walk-through |
| 3 | §3 Compliance NFRs (SOC 2 audit retention) | <Compliance lead name> | Proposed | Email + 15-min sync |
| 4 | §4 Latency SLO | <Eng lead name> | Discussed | Confirm in next sprint review |
| 5 | §4 Rate-limit policy | <Platform lead name> | Proposed | Slack thread + review |
| 6 | §5 Trade-off 1 (module vs service) | <Architect name> | Proposed | Same walkthrough as #1 |
| 7 | §10 PRD: SSO scope addition | <Identity team lead> | Confirmed (Slack 2026-04-15) | None |
```

**Status** values:
- **Proposed**: TPM has drafted; stakeholder hasn't reacted yet
- **Discussed**: Conversation happened; no formal sign-off yet
- **Approved**: Stakeholder said yes (capture how — Slack, meeting note, email)
- **Blocked**: Stakeholder pushed back; needs different proposal

### Triad protocol

1. **List every constraint that needs sign-off** (15 min). Walk through TCD §§1–5; for each load-bearing decision, who has to agree?
2. **Assign a real person** (10 min). Use names from PRD §10 + anyone new. "TBD" is not allowed.
3. **Set the next step** (10 min). For each Proposed: how will the conversation happen?
4. **Status sanity check** (5 min). Honest status — most should be Proposed.

### What "good" looks like

- **At least 6 entries** — most architectural features touch this many stakeholders
- Every entry has a **real person**, not a team
- "Next step" is **specific** — "schedule a 30-min walkthrough" beats "talk to security"
- One entry probably says "Confirmed" because Week-3 Day-1 dependency work caught it; rest are Proposed

### Deliverable

TCD §6 sign-off matrix with at least 6 named entries, each with constraint link, real-person stakeholder, honest status, and a specific next step.

### Facilitation cues

- "TBD" stakeholders signal an unowned constraint that will slip. Force a real name even if it's the architect placeholder.
- Matrices that overstate status ("Approved" without evidence) become Week 6 surprises; coach toward honesty.

---

## Activity 4 — Integration + Cross-Review + Sign-Off

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Final TCD assembly. Cross-review by another triad. Internal sign-off. The TCD ships alongside the PRD.

### Setup
Instructor confirms pairings. Each triad needs the full TCD §§1–6 draft, the integration checklist, and the Friday TCD rubric.

### The integration checklist

| Check | Pass criterion |
|-------|----------------|
| **§1 stance ↔ §2 diagrams** | Modular monolith stance shows as one container with internal modules |
| **§2 integrations ↔ §3 threats** | Every integration boundary appears in the threat model or has an explicit "no threat" rationale |
| **§3 NFRs ↔ §4 SLOs** | Security NFRs don't conflict with latency SLOs; if they do, that's §5 trade-off 2 |
| **§4 SLOs ↔ §5 trade-offs** | If you accepted a latency cost, it should appear in §5 |
| **§6 stakeholders ↔ §§1–5 constraints** | Every load-bearing decision has an owner |
| **No fortune-cookie prose** | Every paragraph is specific to *this* feature |

### Cross-review (20 min)

Pair with another triad. The reviewer focuses on:

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

### Triad action (15 min)

Adopt / defer / reject reviewer findings. Same Week-3 discipline. Update sections.

### Internal sign-off (10 min)

The triad declares the TCD **Status: Approved** (or "Approved with gaps", as Week 3). The TCD is now a sibling artifact to the PRD.

### Deliverable

Signed-off TCD (Status: Approved or Approved with gaps) with adopted cross-review findings, rubric scores, and an AI provenance log covering all AI-assisted sections.

### Facilitation cues

- Watch for "Approved" without an honest gap list. The rubric should set the bar, not the triad's confidence.
- Reviewers who score generously should be calibrated against the rubric mid-block.

### Wrap (last 15 min)

Each triad shares **one of their five trade-offs**, including the revisit trigger. The cohort gets to hear how others reasoned through architecture decisions.

---

## End-of-week (Week 4) checkpoint

Each triad ships:

- [x] **TCD** with §§1–6 complete and integrated
- [x] **Architecture stance** with trade-off + revisit trigger (§1)
- [x] **Integration map + C4 diagrams** (§2)
- [x] **STRIDE threat model + revised security/compliance NFRs** (§3)
- [x] **Three SLOs + latency budget + rate-limit policy + error-budget consequence** (§4)
- [x] **Top 5 trade-offs** with full structure (§5)
- [x] **Stakeholder sign-off matrix** with named owners (§6)
- [x] AI provenance log for all AI-assisted sections

The TCD goes into Week 5 alongside the PRD. Week 5 (Technical Infrastructure & Modeling) uses the TCD's component map for data modeling, the SLOs for performance baselines, and the threat model for encryption / key-management decisions.

## Facilitator wrap (15 min, end of day)

- Read aloud one trade-off from each triad's TCD that the cohort should learn from.
- Surface the **most common pattern of trade-off avoidance** the cohort exhibited (this is a Week 5 + 6 coaching theme).
- Preview Week 5: TCD becomes the spine. Data modeling will reference §2; performance baselines will reference §4; APIs will reference §3 (auth) and §4 (rate limits).

## Facilitator reflection prompts (end of week)

- Which triad's TCD reads like an architect could pick it up? They are the Week-5 positive example.
- Which triad's stakeholder matrix is the weakest? Coach individually before Week 5.
- Did any triad over-specify and accidentally make architectural decisions? Coach toward "surface trade-offs, don't decide."
- AI use this week: was the discipline maintained? If not, surface for the cohort.
