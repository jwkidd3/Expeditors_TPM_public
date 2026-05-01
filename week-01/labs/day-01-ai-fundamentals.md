# Day 1 — AI Fundamentals & Prompting for TPMs

> **Activity packet** for facilitators and participant triads. This file is the single source of truth for the day's small-group work, character cases, and deliverable templates.

## Running case study — FieldPulse

Every day of Week 1 uses the same fictional product to keep momentum.

**FieldPulse** is a mobile-first field-service dispatch SaaS sold to HVAC, plumbing, and electrical shops with 50–200 technicians. It competes with ServiceTitan, Housecall Pro, and in-house tooling. It is mid-sized (Series B), 400 customers, $40M ARR. The academy's "TPM role" sits in the Dispatcher Workflow squad, which owns the dispatcher's primary web app and the tech's mobile app.

### What the cohort will be given as ambient context

- One-page product overview (handed out at start of Day 1)
- Three anonymized dispatcher interview transcripts (used starting Day 3)
- A pack of 14 support tickets (used on Day 4)
- A screen-time analytics export (Day 4)
- A composite customer quote from a prior PR (Day 2)

> Pre-flight: print or digitally share these handouts before Day 1 morning break.

---

## Triad formation

Form triads by 10:30 on Day 1. Composition rules:

1. Mix experience levels (at least one person with 3+ years in an engineering-adjacent role per triad where possible)
2. Mix domain backgrounds
3. No two people from the same home team if cohort is intra-company

Triads persist through the **end of Week 3** (they carry the mini-capstone). Make the formation stick.

---

## Activity 1 — "Same Question, Three Models"

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Surface that (a) different AI tools give materially different answers to the same question, and (b) "it sounded confident" is not evidence of correctness.

### Setup
Each triad picks **one** question from the list below. Each triad member runs it on a different tool (ChatGPT, Claude, Gemini/Copilot). If only one tool is available to the whole cohort, vary **phrasing** across the three triad members instead.

### The question bank (pick one)

1. What's the largest regulatory risk a dispatcher-facing SaaS should plan for when expanding into HVAC in California?
2. Give me the five most frequently stated frustrations of HVAC dispatchers, with sources.
3. What are the top 3 dispatch-tool competitors in the U.S. small-mid market, and their differentiators?
4. Summarize the dispatcher-to-tech handoff process in a 50-person HVAC company.
5. What KPIs do dispatcher teams actually report to owners?
6. Walk me through how a dispatcher typically reacts when a technician calls out sick mid-shift.
7. List integrations a small HVAC shop likely already uses.
8. How do most dispatch apps handle offline/intermittent connectivity today?
9. Who is Maria, a fictional HVAC dispatcher? (watch for hallucinated specifics)
10. What academic research supports mobile-first field service tools?

### Scoring rubric (each tool gets three 1–5 scores)

| Dimension | 1 | 5 |
|-----------|---|---|
| Usefulness | Generic/off-topic | Specific to domain & role |
| Verifiability | Claims can't be checked | Claims traceable, named sources |
| Risk if wrong | Low (opinion, easy to fix) | High (would mislead scoping or strategy) |

### Readout (60 seconds per triad)

> "We would trust [Tool X] for [kind of question]. We would never trust any of them for [kind of question]."

### Facilitator coaching cues

- If all three tools agreed, ask "did they agree *correctly*? How do you know?" — surfaces the comfortable-but-wrong trap.
- If a tool fabricated a citation, celebrate it as a finding. Take a screenshot for the week's reference.

---

## Activity 2 — Rewrite This Prompt

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Convert the Day 1 teaching (RCCF) into reflexive behavior. Participants handle three weak prompts pulled from the FieldPulse backlog and rewrite them.

### The three weak prompts

1. *"Write me an epic for improving the reconcile workflow."*
2. *"Summarize all the dispatcher interview feedback."*
3. *"Give me a competitive comparison chart."*

### Rewrite protocol

1. Identify what's missing: Role, Context, Constraints, Format
2. Add specifics from the FieldPulse handouts
3. Add a constraint that limits hallucination (e.g., "cite evidence," "flag assumptions")
4. Specify exact output format (markdown table, 3-bullet list, etc.)

### Deliverable — Prompt Pattern Library (seed)

Each triad publishes a shared document (any format) with this schema:

```markdown
## Pattern: <short name>

**When to use:** <situation>
**Template:**
```
Role: …
Context: …
Constraints: …
Format: …
```
**Why it works:** <1-2 sentences>
**Caveats:** <where it still fails>
```

Minimum four entries by end of Day 1. Entries earned in Activities 2, 3, and 4.

---

## Activity 3 — The Three Hats

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Use AI as a rapid multi-perspective critic, and practice asking a single question from each perspective.

### The FieldPulse one-paragraph problem brief

> Dispatchers at mid-sized HVAC shops spend roughly 45 minutes after their shift reconciling paper tickets, truck stock, and tech timecards. We believe a mobile-first guided reconcile flow could cut this to under 10 minutes. We are considering building this in Q3.

### The three hats

1. **Engineer hat:** "Read this as a skeptical engineer scoping the work. What three questions will you ask first?"
2. **Blocker-stakeholder hat:** "Read this as the operations VP who most often blocks dispatcher-app launches here (she's worried about training load). What objection worries you most?"
3. **Target-customer hat:** "Read this as Maria, a 12-year HVAC dispatcher at a 90-tech shop. Where does this not ring true?"

### Deliverable

For each hat: the single most uncomfortable question surfaced. One of those three questions becomes your **Day 3 research target** (the one you cannot currently answer).

---

## Activity 4 — Prompt Pattern Library (Publish)

**Format:** Triad &bull; **45 min** &bull; Block 4 + readouts

### Purpose
Ship a durable artifact. The library is referenced every remaining day of Week 1 and beyond.

### Required entries (minimum)

- [ ] One Research prompt
- [ ] One Summarization-with-evidence prompt
- [ ] One Critique-hat prompt
- [ ] One "Where could you be wrong?" prompt

### Optional extra credit

- [ ] One prompt for converting tickets → themed frustrations (will be needed on Day 4)
- [ ] One prompt for generating candidate JTBDs from a persona (Day 3)

### Readout structure (60 seconds per triad)

> "Our starred prompt is <name>. We tested it on <situation>. The reason we'd reuse it is <why>. Its known failure mode is <caveat>."

### Facilitator: collect and share

Post all triad libraries to a shared space by end of Day 1. Every triad should be able to borrow another's prompts starting Day 2.

---

## End-of-day checkpoint

Each triad leaves the day with:

- [x] Formed triad with declared norms (meet-time, tool choice, note-keeper role)
- [x] At least one person per triad who owns the Pattern Library file
- [x] A Day 3 research target question selected from Activity 3
- [x] A pre-Day-2 commitment: one product idea they want to PR/FAQ tomorrow

## Facilitator reflection prompts (end of day)

- Did any triad over-rely on AI without critique? What would I model differently tomorrow?
- Which failure mode (hallucination, starvation, sycophancy, anchoring) did the room most struggle to see?
- Who in the room was quieter than I'd like? How can I engineer tomorrow's triad interactions to pull them in?
