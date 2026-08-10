# Day 1 — AI Fundamentals & Prompting for TPMs

> **Activity packet for participant quads.** This file is your source of truth for the day's small-group work, character cases, and deliverable templates.

## Running case study — FieldPulse

Every day of Week 1 uses the same fictional product to keep momentum.

**FieldPulse** is a mobile-first field-service dispatch SaaS sold to HVAC, plumbing, and electrical shops with 50–200 technicians. It competes with ServiceTitan, Housecall Pro, and in-house tooling. It is mid-sized (Series B), 400 customers, $40M ARR. The academy's "TPM role" sits in the Dispatcher Workflow squad, which owns the dispatcher's primary web app and the tech's mobile app.

### Ambient context you'll be given

- One-page product overview (handed out at start of Day 1)
- Three anonymized dispatcher interview transcripts (used starting Day 3)
- A pack of 14 support tickets (used on Day 4)
- A screen-time analytics export (Day 4)
- A composite customer quote from a prior PR (Day 2)

---

## Quad formation

Form quads by 10:30 on Day 1. Composition rules:

1. Mix experience levels (at least one person with 3+ years in an engineering-adjacent role per quad where possible)
2. Mix domain backgrounds
3. No two people from the same home team if cohort is intra-company

Quads persist through the **end of Week 3** (they carry the mini-capstone). Make the formation stick.

---

## Activity 1 — "Same Question, Three Models"

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Surface that (a) different AI tools give materially different answers to the same question, and (b) "it sounded confident" is not evidence of correctness.

### Setup
Each quad picks **one** question from the list below. Each quad member runs it on a different tool (ChatGPT, Claude, Gemini/Copilot). If only one tool is available to the whole cohort, vary **phrasing** across the three quad members instead.

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

### Steps

1. **Pick (5 min).** Quad selects one question from the bank above.
2. **Run (10 min).** Each quad member runs the same question on a different tool.
3. **Score (15 min).** Compare outputs across usefulness, verifiability, and risk-if-wrong using the rubric below.
4. **Prepare readout (5 min).** Draft a one-line trust statement.

### Scoring rubric (each tool gets three 1–5 scores)

| Dimension | 1 | 5 |
|-----------|---|---|
| Usefulness | Generic/off-topic | Specific to domain & role |
| Verifiability | Claims can't be checked | Claims traceable, named sources |
| Risk if wrong | Low (opinion, easy to fix) | High (would mislead scoping or strategy) |

### Deliverable

A scored comparison across three tools plus a one-line readout: "We would trust [Tool X] for [kind of question]. We would never trust any of them for [kind of question]."

---

## Activity 2 — Rewrite This Prompt

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Convert the Day 1 teaching (RCCF) into reflexive behavior. Handle three weak prompts pulled from the FieldPulse backlog and rewrite them.

### Setup
Your quad has the three weak prompts below, access to one AI assistant, and the FieldPulse handouts from the morning.

### The three weak prompts

1. *"Write me an epic for improving the reconcile workflow."*
2. *"Summarize all the dispatcher interview feedback."*
3. *"Give me a competitive comparison chart."*

### Steps

1. Identify what's missing: Role, Context, Constraints, Format
2. Add specifics from the FieldPulse handouts
3. Add a constraint that limits hallucination (e.g., "cite evidence," "flag assumptions")
4. Specify exact output format (markdown table, 3-bullet list, etc.)

### Deliverable — Prompt Pattern Library (seed)

Each quad publishes a shared document (any format) with this schema:

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

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Use AI as a rapid multi-perspective critic, and practice asking a single question from each perspective.

### Setup
Your quad has a working AI assistant and the FieldPulse one-paragraph problem brief below. The brief is the shared input for all three hats.

### The FieldPulse one-paragraph problem brief

> Dispatchers at mid-sized HVAC shops spend roughly 45 minutes after their shift reconciling paper tickets, truck stock, and tech timecards. We believe a mobile-first guided reconcile flow could cut this to under 10 minutes. We are considering building this in Q3.

### Steps

1. **Engineer hat (10 min).** Prompt: "Read this as a skeptical engineer scoping the work. What three questions will you ask first?"
2. **Blocker-stakeholder hat (10 min).** Prompt: "Read this as the operations VP who most often blocks dispatcher-app launches here (she's worried about training load). What objection worries you most?"
3. **Target-customer hat (10 min).** Prompt: "Read this as Maria, a 12-year HVAC dispatcher at a 90-tech shop. Where does this not ring true?"
4. **Synthesize (10 min).** Pick one question per hat that is most uncomfortable; pick one that becomes the Day 3 research target.

### Deliverable

For each hat: the single most uncomfortable question surfaced. One of those three questions becomes your **Day 3 research target** (the one you cannot currently answer).

---

## Activity 4 — Prompt Pattern Library (Publish)

**Format:** Quad &bull; **55 min** &bull; Block 4 + readouts

### Purpose
Ship a durable artifact. The library is referenced every remaining day of Week 1 and beyond.

### Setup
Your quad has been collecting candidate prompts through Activities 2 and 3. You now formalize a shared document — any tool the quad will reliably use (markdown file, shared doc, wiki page).

### Steps

1. **Inventory (10 min).** Pull every candidate prompt the quad has used today.
2. **Cull (15 min).** Keep the ones with a clear "when to use" and a known failure mode.
3. **Format (15 min).** Convert each to the schema below. Minimum four entries.
4. **Star (5 min).** Pick the prompt the quad would actually reuse on Monday morning.

### Required entries (minimum)

- [ ] One Research prompt
- [ ] One Summarization-with-evidence prompt
- [ ] One Critique-hat prompt
- [ ] One "Where could you be wrong?" prompt

### Optional extra credit

- [ ] One prompt for converting tickets → themed frustrations (will be needed on Day 4)
- [ ] One prompt for generating candidate JTBDs from a persona (Day 3)

### Deliverable

A shared Prompt Pattern Library with at least four entries, each tagged with when-to-use, the template, why it works, and known caveats. One entry is starred as the quad's go-to.

### Readout structure (60 seconds per quad)

> "Our starred prompt is <name>. We tested it on <situation>. The reason we'd reuse it is <why>. Its known failure mode is <caveat>."

---

## End-of-day checkpoint

Each quad leaves the day with:

- [x] Formed quad with declared norms (meet-time, tool choice, note-keeper role)
- [x] At least one person per quad who owns the Pattern Library file
- [x] A Day 3 research target question selected from Activity 3
- [x] A pre-Day-2 commitment: one product idea they want to PR/FAQ tomorrow
