# Day 5 — Data-Driven Problem Framing

> **Activity packet** for facilitators and participant triads. Day 5 is the integration day: every prior artifact of Week 1 funnels into a problem statement + evidence brief + 10-minute cohort readout.

## Prerequisite artifacts (must be brought in)

Each triad arrives with:

- **Prompt Pattern Library** (Day 1)
- **PR/FAQ** (Day 2)
- **Validated Persona Canvas** (Day 3)
- **Scored Pain-Point Matrix + Top 3** (Day 4)
- **Parking lot** of open validation questions (accumulated)

## Materials

### Problem Statement Template (printable)

```markdown
# Problem statement — [short handle]

**Who** — [persona role + context]

**Currently** — [observed behavior, with frequency]

**Which causes** — [measurable consequence]

**Because** — [root cause, from 5 Whys]

**We know this because** — [evidence, tagged by tier]

**Success looks like** — [the change we'd see if the problem is solved]
```

### Evidence Brief Template

```markdown
# Evidence brief — [short handle]

## Persona (one paragraph)
[From Day 3]

## Pain map
[Screenshot or rendering of Day 4 matrix, Top 3 highlighted]

## Problem statement
[From Activity 1]

## Evidence log
| Claim | Source | Date | Tier | Captured by |
|-------|--------|------|------|-------------|
| …     | …      | …    | …    | …           |

## Open questions
- … (ranked; most impactful first)
```

### Scoring rubric (used by cohort during readouts)

| Dimension | Weight | 1 | 3 | 5 |
|-----------|--------|---|---|---|
| Customer authenticity | 25% | Generic | Persona present, mix of claims | Observed-heavy, evidence named |
| Pain specificity | 25% | Categories | Mixed | Verb + circumstance + consequence |
| Evidence quality | 20% | Unsourced | Sources named | Tiered, auditable |
| Problem statement clarity | 20% | Vague or solution-y | Mostly clear | Engineer could scope |
| AI-use transparency | 10% | Unstated | Mentioned | Prompt + validation step disclosed |

---

## Activity 1 — Draft Your Statement

**Format:** Triad &bull; **45 min** &bull; Block 1

### Protocol

1. **Pick your anchor pain (5 min).** Usually #1 from Day 4 Top 3. If you're torn between two, draft both in parallel.
2. **Fill the template (20 min).** One line at a time. Do not skip "Success looks like."
3. **Failure-mode audit (15 min).** Check each line against:
   - Solution in disguise? (If your "Currently" or "Because" implies a specific feature, pull it)
   - Consequence-free? (Add a measurable outcome)
   - No root cause? (Run the 5 Whys again — briefly)
   - Ungrounded? (Tag the evidence)
   - Success-agnostic? (Quantify or time-bound the target)
4. **Within-triad peer read (5 min).** One member reads aloud. Others listen for what's still weak.

### Common mistakes to watch for

- **"Because" line restates the problem** — it should name the *mechanism* (why the current state exists at all)
- **"Success looks like" is a feature** — it should be a measurable change in behavior or outcome
- **Persona inflation** — "all dispatchers at all HVAC companies" when your evidence is 3 shops

---

## Activity 2 — Pressure Test

**Format:** Triad &bull; **45 min** &bull; Block 2

### The prompt (from Day 1 library)

```
Role: Senior engineering lead reading a problem statement I intend to scope against.
Context: [paste problem statement + evidence log]
Constraints:
  - Do not rewrite. Ask the questions you would ask me in a scoping meeting.
  - Rank your questions by how much they'd change your estimate if unanswered.
  - Flag any claim that is inferred or AI-generated that you'd want upgraded first.
Format: Numbered list of questions, ranked.
```

### Protocol

1. **Run the prompt (10 min).**
2. **Answer what you can (25 min).** Go question by question.
   - Green: answered from existing evidence (note the source)
   - Yellow: answerable if we do X (add to Open questions)
   - Red: unknowable from current evidence; flag the assumption we're carrying
3. **Revise (10 min).** Update the problem statement and Evidence log based on answers. Move failed claims to Open questions or drop.

### Guardrail
**AI does not get to rewrite the statement.** Ownership stays with the triad. The prompt's job is to surface weakness, not to patch it.

---

## Activity 3 — Paired Dry-Run

**Format:** Paired triads &bull; **45 min** &bull; Block 3

### Protocol

1. Triads pair up.
2. Triad A delivers a **full timed 10-minute readout** to Triad B. Partner uses a stopwatch.
3. During the readout, Partner writes down:
   - The **3 questions** they would ask in real Q&A
   - **One sentence**: "I heard the problem to be…"
4. Compare that one-sentence summary to what Triad A intended to convey.
5. Swap directions.
6. **Joint debrief (15 min):** Where did the heard-summary differ from intent? Why? What slide/paragraph caused the gap?

### The "what I heard" test

If the listener's one-sentence summary doesn't match your intent, the readout needs work — usually one of:

- The problem was buried under too much persona setup
- Success criteria were missing or abstract
- The evidence overwhelmed the narrative

Revise accordingly before Block 4.

---

## Week 1 Cohort Readouts

**Format:** Full cohort &bull; **~90 min** &bull; Block 4

### Structure per triad (10 minutes)

| Clock | Content |
|-------|---------|
| 0:00 – 1:30 | Persona (one quote, observed behavior) |
| 1:30 – 3:30 | Top 3 pains (matrix visual) |
| 3:30 – 5:30 | Problem statement (read each line) |
| 5:30 – 7:30 | Evidence sample + open questions |
| 7:30 – 10:00 | Q&A — **questions only**, no defending |

### Between triads (3 min)

Silent. Every audience member fills out a score sheet: rubric scores + 1 strength + 1 suggestion.

### Facilitator timing

- 6 triads = ~80 min readouts + 18 min between = **~98 min**. Budget 90 min and stay disciplined.
- Random draw order (pull triad names from a hat or randomizer)
- If running short, compress Q&A to 2 minutes — never the readout itself

### Score sheet template

```markdown
## Triad: [name]

### Scores (1–5)
- Customer authenticity: __
- Pain specificity: __
- Evidence quality: __
- Problem statement clarity: __
- AI-use transparency: __

### One strength
…

### One suggestion
…
```

---

## End-of-Week-1 checkpoint

Each triad leaves the week with:

- [x] Problem statement + Evidence brief, reviewed by peers and scored
- [x] Readout deck/visuals reusable on demand
- [x] A ranked list of Open questions (input to Week 2 research)
- [x] A clear sense of which evidence tiers need upgrading before Week 3 mini-capstone

## Facilitator debrief (end of Friday, instructor only)

Before you log off:

1. Which triads seem **PRD-ready** for Week 3? Which need extra coaching during Week 2?
2. Who was over-relying on AI by the end of the week vs. using it judiciously?
3. Which triad surprised you — in either direction — and why?
4. Three adjustments for Week 2 pacing based on what you saw today.

## Bridge to Week 2

Monday opens with: *"Review the problem statements from Friday. Choose your triad's candidate North Star metric. Bring three candidates, come ready to defend one."*
