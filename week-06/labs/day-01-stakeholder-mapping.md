# Day 1 — Identifying & Mapping Key Stakeholders

> **Activity packet** for participant triads. Today's job: take the TCD §6 sign-off matrix, expand it into a real stakeholder map (Power × Interest + RACI), and draft SEP §1.

## Where we are in the week

The TCD already has §6 — a sign-off matrix listing constraints and owners. That matrix is the **starting input** to today's work. Today expands it into a usable map: who has what kind of power, who cares how much, who is Responsible, Accountable, Consulted, or Informed.

By 16:00, every triad has SEP §1 — a stakeholder map ready to drive engagement planning tomorrow.

## Inputs

- TCD §6 (stakeholder sign-off matrix from Week 4 Day 5)
- PRD §10 (named dependencies + owners)
- The triad's customer interviews (Week 1) for stakeholder context

---

## Why "stakeholder mapping" is not org-chart copying

A common rookie mistake: list the team names from the org chart and call it a stakeholder map. That's not a map — it's a directory.

A real stakeholder map answers:

- **Who has the power to block this work?**
- **Who cares whether it ships?**
- **Whose buy-in do we *need*?** (vs whose buy-in is *nice-to-have*?)
- **Who must be consulted vs only informed?**
- **Who do we wish we could ignore but can't?**

Org charts answer "who reports to whom." Maps answer "whose attention do we need to manage and how?"

---

## The Power × Interest Grid (today's first frame)

A 2×2 placing every stakeholder by:

- **Power**: how much can they affect this work? (block it, fund it, redirect it, accelerate it)
- **Interest**: how much do they care about this work?

```
              High Interest
                    ▲
                    │
  Keep informed     │     Manage closely
  (engaged           │     (key partners)
   audience)        │
                    │
─────High Power◀────┼────▶Low Power
                    │
  Manage with       │     Monitor
  authority         │     (low effort)
  (block-                   │
   capability)      │
                    ▼
              Low Interest
```

Each quadrant suggests an engagement style:

| Quadrant | Engagement style |
|----------|------------------|
| **High power, high interest** | Manage closely — frequent, deep engagement |
| **High power, low interest** | Manage with authority — keep them out of weeds; surface only when needed |
| **Low power, high interest** | Keep informed — engaged audience; you'll learn from them |
| **Low power, low interest** | Monitor — low effort; check in periodically |

Most TPMs over-invest in the high-interest quadrants and under-invest in the **high-power-low-interest** quadrant. That's the quadrant that surprises you with a "no" at the worst time.

---

## The RACI assignment (today's second frame)

Once stakeholders are placed on the grid, assign their role for **specific decisions** in the project:

| Letter | Role | Definition |
|--------|------|------------|
| **R** | Responsible | Does the work. There can be many R's. |
| **A** | Accountable | Owns the outcome. **Exactly one** person per decision. |
| **C** | Consulted | Two-way conversation; opinion sought. |
| **I** | Informed | One-way notification; outcome shared. |

The discipline: **one A per decision**. If two people are A, neither is. If no one is A, the decision will rot.

For a single feature, several decisions need RACI:

- The **scope** of the feature
- The **architecture** (TCD §1 stance)
- The **SLO targets**
- The **launch date**
- Each **out-of-scope follow-up** (deferred to a backlog with an owner)

---

## Activity 1 — Build the Stakeholder List

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Build a **complete** stakeholder list before mapping. Most triads will start with 5–7 stakeholders and discover they have 12–15.

### Triad protocol

1. **Start with TCD §6** (5 min). Copy every stakeholder name from the sign-off matrix into a list.
2. **Augment with the "five circles"** (15 min). For each circle, add anyone who isn't already on the list:
    - **Customer-facing:** customer success, sales, support
    - **Engineering-adjacent:** architecture, security, platform, infra, data, QA
    - **Operating partners:** ops, IT, compliance, legal, finance
    - **Decision-makers:** PM lead, eng director, GM, executive sponsor
    - **Indirect interest:** other product teams whose work this touches
3. **Cull lightly** (5 min). Anyone who genuinely doesn't need to be on the list, drop. Default: keep.
4. **Capture context per stakeholder** (10 min). For each, one sentence:
    - What's their role on this feature?
    - What do they care about most?

### Output

A **comprehensive stakeholder list** (typically 10–18 names) with role + concern.

---

## Activity 2 — Power × Interest Mapping

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Place each stakeholder on the 2×2 grid. The discussion of *where* each one goes is most of the learning.

### Triad protocol

1. **Sketch the 2×2** on whiteboard or paper (5 min).
2. **Place each stakeholder with a sticky note** (15 min). Argue when you disagree — don't average.
3. **Highlight the four corners** (10 min). For each quadrant:
    - Who is here?
    - What does our engagement style with them need to look like?
4. **Identify the 2 "surprises"** (10 min). Usually:
    - One person you thought was high-power who actually isn't (their veto isn't real)
    - One person you thought was low-interest who actually isn't (they care more than they let on)

### What "good" looks like

- **All four quadrants populated** (if your "low power / low interest" is empty, you've over-prioritized)
- **Discussion happened** — triads converged on placements through argument, not by the loudest voice
- **Engagement style** is named per quadrant
- **The two surprises** are flagged — these are your high-leverage discoveries

### Worked example — FieldPulse reconcile

```
                            High Interest
                                  ▲
                                  │
    [Operations VP] ←──────────── │ ──── [Reconcile triad's eng lead]
                                  │ ───── [Customer success lead]
    Keep informed                 │      [QA lead]
                                  │      Manage closely
                                  │
─────High Power ─────────────────┼─────────────────── Low Power
                                  │
    [Architect]                   │      [Compliance lead]
    [Eng Director]                │      [Other product team owners]
    [Security Lead]               │      Monitor
    Manage with authority         │
                                  │
                                  ▼
                            Low Interest
```

The "surprise" for FieldPulse: **Compliance** is low-interest in the abstract but **high-power in specific moments** (audit deadlines). Its position can shift; flag it.

---

## Activity 3 — RACI Assignment for Five Decisions

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Assign RACI to the five most consequential decisions for the feature.

### The five decisions

For most features:

1. **Scope** — what's in vs out
2. **Architecture** — TCD §1 stance + key trade-offs
3. **SLO targets** — TCD §4
4. **Launch date** — when it ships
5. **Out-of-scope follow-up backlog** — deferred items + owners

### The matrix template

```markdown
| Decision | R | A | C | I |
|----------|---|---|---|---|
| Scope | TPM (you) | PM Director | Eng Lead, Architect, Customer Success | Sales, Support |
| Architecture | Architect | Eng Director | TPM, Security, Platform | All eng |
| SLO targets | Eng Lead | TPM | SREs, Customer Success | Eng Director |
| Launch date | TPM | PM Director | Eng Lead, Customer Success, Marketing | All eng, Sales |
| OOS backlog ownership | TPM | TPM | Eng Lead | Backlog readers |
```

### Triad protocol

1. **Draft the matrix** (20 min). One A per decision. Multiple R/C/I OK.
2. **The "no two A's" check** (5 min). Walk the columns; verify exactly one A per decision.
3. **The "is the A actually empowered?"** (10 min). For each A, check: do they have the authority (formal + informal) to make the call? If not, reassign.
4. **The "anyone surprised by being I?"** (5 min). Often a stakeholder gets I when they think they're C. Surface that and decide.

---

## Activity 4 — SEP §1 Polish + Stakeholder Watch List

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Polish §1 of the SEP, plus identify a **watch list** of stakeholders whose status could change in the next month.

### The watch list

For each stakeholder in the **high-power-low-interest** quadrant, ask:

- What event would move them to **high-interest**?
- What's our trigger to escalate engagement?

Examples:

- **CFO** — currently low-interest. Would move to high-interest if quarterly cost forecasts change. Trigger: cost projection > $X.
- **General Counsel** — currently low-interest. Would move to high-interest if a regulator inquires. Trigger: any regulator email.
- **Chief Customer Officer** — currently low-interest. Would move to high-interest if a top-10 account complains. Trigger: top-10 escalation.

A watch list is the early-warning system. It's the section that distinguishes a TPM who manages stakeholders from one who reacts to them.

### Triad protocol

1. **Polish §1** (15 min). Combine list + Power×Interest grid + RACI into one section. Add the "two surprises" callouts.
2. **Build the watch list** (20 min). 3–5 stakeholders with their triggers.
3. **Cross-check against the TCD §6 sign-off matrix** (5 min). Anyone in §1 not on §6? Add to §6. Anyone on §6 not in §1? Add to §1.
4. **AI cross-check** (5 min). Run the prompt below.

### AI prompt

```
Role: Senior PM coaching a junior TPM on stakeholder management.
Context: <paste the stakeholder list with quadrants and RACI>
Task: Identify 3 likely blind spots:
  1. A stakeholder who probably has more power than the map shows
  2. A decision where the A is wrong or absent
  3. A high-power-low-interest stakeholder whose trigger isn't named
Constraints:
  - Be specific to the names and roles given
  - Do not invent stakeholders
Format: 3 numbered findings, each with a one-sentence rationale.
```

### Wrap (last 15 min)

Each triad shares:

- One stakeholder whose quadrant placement was the most contested
- One RACI-A that was reassigned during discussion
- One trigger from the watch list

---

## End-of-day checkpoint

Each triad ends Day 1 with:

- [x] Comprehensive stakeholder list with role + concern
- [x] **Power × Interest grid** populated
- [x] **RACI matrix** for 5 decisions, with one A per decision
- [x] **Watch list** of high-power-low-interest stakeholders + triggers
- [x] AI provenance log entry
- [x] SEP §1 drafted
