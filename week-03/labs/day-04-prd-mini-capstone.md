# Day 4 — Mini-Capstone: PRD Assembly (Non-AI)

> **Activity packet** for participant quads. Today's job: complete the remaining PRD sections, integrate the whole document, and lock the version that goes into Friday's review. **No AI**, all day.

## Where we are in the week

Sections 1–7 are drafted. Today adds:

- **Section 8 Metrics & validation** — how we'll know it worked in 30 days
- **Section 9 Risks & open questions** — named honestly
- **Section 10 Dependencies** — other teams, systems, decisions, data
- **Section 11 Out-of-scope follow-ups** — what this PRD acknowledges but won't ship

And then the **integration pass**: read the whole PRD top-to-bottom, fix incoherences, lock a version for tomorrow's review.

## The non-AI rule (final day)

This is the keystone day. Tomorrow is reviews; AI is restored Monday. Today the discipline holds.

What's allowed today: spell-check, your prior-week artifacts, your draft sections, dictionary, calculator, conversations across quads.

What's not: ChatGPT, Claude, Copilot, AI features built into your editor (turn them off), or asking another team's AI for "just a structure."

---

## Activity 1 — Section 8: Metrics & Validation

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Connect the PRD to the **Tier Sheet from Week 2 Day 1** and the **NS from Week 2 Day 2**. This section is what Week 7's Agile Delivery work will measure against.

### Setup
Each quad needs the Week-2 Tier Sheet, the NS Defense Card, and the Section 8 template. No AI.

### What Section 8 contains

```markdown
## 8. Metrics & validation

### Primary metric (the one we're trying to move)
> [Single op-signal or KPI from your Tier Sheet]
> Baseline: <current value>
> Target: <30-day target>
> Why this number: <2-sentence defense>

### Counter-metric (the guardrail)
> [Counter-metric from your NS Defense Card]
> If this moves *the wrong way*, we are winning the primary for the wrong reasons.

### Secondary metrics (3 max)
- <op-signal 1>: directional indicator
- <op-signal 2>: directional indicator
- <op-signal 3>: directional indicator

### Validation plan
- **Pre-launch:** smoke tests (link to AC verification)
- **Launch + 7 days:** check primary metric directional correctness
- **Launch + 30 days:** measure primary against target
- **Launch + 90 days:** check counter-metric for guardrail violation

### What "good enough" looks like
We'll consider this feature successful if [primary metric] moves
≥ [target delta] within 30 days, AND [counter-metric] stays within
[acceptable band].
```

### Quad protocol

1. **Pull from Tier Sheet** (10 min). Pick the primary metric, the counter, and 3 secondaries.
2. **Set targets** (25 min). Concrete numbers, with a sentence of defense.
3. **Validation plan** (10 min). The four-checkpoint cadence above.

### What "good" looks like

- Primary metric is **one** number, not "we'll watch a few things."
- Targets are **specific deltas**, not "improve."
- Counter-metric is the same one from Week 2 Day 2 — consistency.

### Deliverable

Section 8 appended to the PRD: one primary metric, one counter-metric, up to three secondaries, and a four-checkpoint validation plan.

---

## Activity 2 — Section 9: Risks & Open Questions

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Name the things that could go wrong, the things you don't yet know, and the things you'll find out only after launch. **A PRD with "no risks" is a fail.**

### Setup
Each quad needs Sections 1–8 and the three-list template (Risks, Open questions, Assumptions). No AI.

### Three lists in Section 9

**Risks** (named, with mitigation):

```markdown
| Risk | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation |
|------|--------------------|----------------|------------|
| Dispatchers refuse the new flow because it's longer | M | H | Optional toggle in v1; observe adoption; remove old flow only if adoption > 70% by week 4 |
| Audit-log volume blows our log budget | L | M | Tier-2 sample for non-error events; full sample for errors |
| Auth integration breaks if SSO IdP changes | L | H | Pre-coordinate with SecOps; document fallback to local auth |
```

**Open questions** (we don't know yet; need to answer before or during build):

```markdown
- Will operations VP accept the temporary read-only manager view in week 1?
  (Owner: <name>; needed by: <date>)
- Does the audit store handle 24-month retention at this volume,
  or do we need archival tier?
  (Owner: <name>; needed by: <date>)
```

**Assumptions** (things we're treating as true; we'll learn if we're wrong):

```markdown
- Median dispatcher device is mid-tier Android on 4G LTE
  (basis: device-fleet snapshot Q3; revisit if changes)
- 30-day adoption signal is sufficient to declare success
  (basis: prior reconcile rollout; revisit if behavior is non-stationary)
```

### Quad protocol

1. **Risks brainstorm** (25 min). Aim for 5 candidates. Cull to 3–4 with non-trivial impact.
2. **Open questions** (10 min). Each member contributes; pool. 3–5 questions.
3. **Assumptions** (10 min). Often the hardest section — what are we taking for granted?
4. **Owner + by-when assignment** (5 min). Every open question and risk gets an owner and a deadline.

### Deliverable

Section 9 appended to the PRD: 3–4 risks with mitigations, 3–5 owned open questions with deadlines, and 2–4 named assumptions with basis.

---

## Activity 3 — Sections 10 & 11: Dependencies + Out-of-Scope Follow-ups

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Make the network of "things outside our PRD that this PRD depends on or hands off to" explicit. Most PRDs hand-wave this; mature ones tabulate.

### Setup
Each quad needs Section 3 (non-goals), Section 4 (scope), and any cross-team context surfaced during the week. No AI.

### Section 10 Dependencies

A simple table:

```markdown
## 10. Dependencies

| Dependency | Owner | What we need | By when | Status |
|------------|-------|--------------|---------|--------|
| Auth team — SSO scope addition | <name> | New scope `reconcile.write` | Week of build kickoff | Confirmed in Slack 2026-04-15 |
| Data platform — event schema | <name> | Schema review for 7 new events | Day 1 of sprint 1 | Pending |
| Mobile build pipeline — signing | <name> | New signing cert for the new bundle ID | Pre-launch | Pending |
| Customer success — release messaging | <name> | Customer comms 1 week pre-launch | T-7 days | Pending |
```

### Section 11 Out-of-scope follow-ups

What this PRD acknowledges but won't ship:

```markdown
## 11. Out-of-scope follow-ups (for the backlog)

- **Tablet layout** — same flow, different breakpoint. Tracked: TICKET-1234.
- **Spanish localization** — copy + reading order. Tracked: TICKET-1235.
- **Multi-shop manager view** — pulls reconcile data across shops. Tracked: TICKET-1236.
- **Offline-first sync** — current PRD supports offline draft + manual reconnect; full
  offline-first deferred. Tracked: TICKET-1237.
```

### Quad protocol

1. **Dependencies** (30 min). Brainstorm the dependency network. For each: owner, what, when, status.
2. **Out-of-scope follow-ups** (15 min). Pull from Section 3 non-goals + Section 4 scope-out + anything that came up this week.
3. **Status sanity check** (5 min). Have you confirmed any of these? If not, "Pending" is honest.

### What "good" looks like

- Every dependency has a **named owner**, not a team name.
- "Status" is honest — most will be Pending. That's fine; pretending they're confirmed is the bug.
- Out-of-scope items are **specific**, not "future work."

### Deliverable

Sections 10 and 11 appended to the PRD: dependency table with named owners and honest statuses, plus a specific out-of-scope follow-up list.

---

## Activity 4 — Integration Pass + Lock

**Format:** Quad &bull; **55 min** + Wrap &bull; Block 4

### Purpose
Read the whole PRD top-to-bottom. Fix incoherences. Lock the version that goes into Friday's review.

### Setup
Each quad needs the full Sections 1–11 draft, the eight-item integration checklist, and the AI-prose tell list. No AI.

### The integration checklist

| Check | Pass criterion |
|-------|----------------|
| **Section 1 → Section 2 flow** | Reader is motivated to keep reading |
| **Section 3 goals tied to Section 8 metrics** | Each goal references a metric; each metric references a goal |
| **Section 5 sketch consistent with Section 6 AC** | Each happy-path AC corresponds to a step in the sketch |
| **Section 6 AC vs Section 7 NFRs** | NFRs cover what AC don't (system properties vs system behavior) |
| **Section 7 NFRs reference Section 8 observability** | Observability NFR enables every Tier Sheet metric |
| **Section 4 scope-out feeds Section 11 follow-ups** | Items deliberately left out appear in the follow-ups list |
| **Section 9 risks named, owned, mitigated** | No "no risks" |
| **No AI-generic prose** | Voice is consistent quad voice; no fortune-cookie sentences |

### Quad protocol

1. **Solo read-through** (25 min). Each member reads the whole PRD top-to-bottom and marks issues in the margins.
2. **Pool issues** (10 min). What did each member catch? De-dupe.
3. **Fix in priority order** (15 min). Coherence first, then prose.
4. **Lock the version** (5 min). Mark the document **Status: In review**. Save a copy as "v0 — for Friday".

### The "no AI-generic prose" check

Specific tells of AI prose that should be eliminated:

- "It is important to note that…"
- "By leveraging X, we can unlock Y…"
- "This robust solution will empower stakeholders to…"
- "In today's fast-paced environment…"
- Three adjectives in a row when one would do
- Sentences that sound true but say nothing specific

If a section sounds like it could appear in any PRD for any product, rewrite it for *your* product.

### Deliverable

Locked **Status: In review** PRD saved as "v0 — for Friday" with the integration checklist passed and no AI-generic prose.

### Wrap (last 15 min)

Each quad shares:

- The **section they're proudest of** (1 sentence why)
- The **section they're least sure about** (1 sentence why) — this is the section reviewers should hammer tomorrow

---

## End-of-day checkpoint

Each quad ships into Friday's review:

- [x] **Status: In review** PRD with Sections 1–11 complete
- [x] Section 8 Metrics with primary, counter, secondary, validation plan
- [x] Section 9 Risks (with mitigations) + Open Questions (with owners) + Assumptions
- [x] Section 10 Dependencies table with owners
- [x] Section 11 Out-of-scope follow-ups, specific
- [x] Integration check passed; no AI-generic prose
- [x] A copy saved as "v0 — for Friday"
