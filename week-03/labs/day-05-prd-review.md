# Day 5 — PRD Review (Morning Reviews, Afternoon Revisions + Secondary)

> **Activity packet** for facilitators and participant triads. Today's job: subject every PRD to a structured peer review, revise it in response, and submit a final version with a complete review-resolution log. By 16:00 every triad has shipped a reviewed, revised PRD — the mini-capstone deliverable.

## Where we are in the week

Days 1–4 produced one **locked v0 PRD per triad** (sections 1–11, status "In review"). Today is the **structured review cycle**. The cadence is intentionally split per the outline: **morning in reviews, afternoon in revisions and secondary reviews**.

## Today's cadence (different from Mon–Thu)

| Clock | Block | What happens |
|-------|-------|--------------|
| 09:00 – 09:15 | Opening; review pairings posted | Instructor explains rubric; pairings revealed |
| 09:15 – 10:45 | **Primary review round 1** | Two reviewing triads on each PRD |
| 10:45 – 11:00 | **Break** | |
| 11:00 – 12:00 | Author response + clarifying conversations | Author triads receive feedback in person |
| 12:00 – 13:00 | **Lunch** | |
| 13:00 – 14:30 | **Revisions** | Authors revise based on review |
| 14:30 – 14:45 | **Break** | |
| 14:45 – 15:45 | **Secondary review** | A different reviewer reads the revision |
| 15:45 – 16:00 | Wrap + sign-off | Final PRDs + resolution logs delivered |

## The non-AI rule

Today is still non-AI. Reviews are by hand; revisions are by hand. AI restored Monday Week 4.

---

## The review pairing structure

Each triad's PRD is read by **two different primary-reviewing triads** (for the morning round) and one **different secondary-reviewing triad** (for the afternoon round). The instructor posts pairings at 09:00.

Example for 6 triads (A–F):

| PRD author | Primary reviewers (AM) | Secondary reviewer (PM) |
|------------|------------------------|--------------------------|
| A | B, C | D |
| B | C, D | E |
| C | D, E | F |
| D | E, F | A |
| E | F, A | B |
| F | A, B | C |

Each triad has **3 reading roles** during the day: primary (×2 PRDs in AM), then secondary (×1 PRD in PM). Plus they own their own PRD throughout. Time it carefully.

---

## The Friday review rubric

Every reviewer scores each PRD on:

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| **Problem clarity** | 20% | Engineer could scope without a clarifying call |
| **AC testability** | 25% | Each AC implementable + falsifiable; covers happy/sad/weird |
| **NFR completeness** | 20% | 5 categories present; each has a defended target |
| **Strategy linkage** | 15% | Goals tie to Week-2 NS / KPIs / journey friction |
| **Risk honesty** | 10% | Real risks named; "no risks" is fail |
| **Writing discipline** | 10% | Clear, specific; no AI-generic prose |

Score on 0–4 per dimension (0 = absent, 4 = exemplary). Multiply by weight; sum for total out of 4.0.

A score of **3.0+ ships as-is**. A score of **2.0–2.9 ships with named gaps** (resolution log captures them). Below 2.0 — facilitator intervenes.

---

## Activity 1 — Primary Review (Morning)

**Format:** Two-triad reviewer team &bull; **90 min total** &bull; Block 1 + Block 2

### The reviewer protocol

Each reviewing triad is paired with one PRD. Two reviewing triads independently review the same PRD (no sharing during review).

**0–10 min: read §§1–5** (Context, Problem, Goals, Scope, Sketch)

- Score Problem clarity and Strategy linkage as you read.
- Mark any **specific** confusion (not "this is unclear" — "I don't understand why dispatchers care about X").

**10–35 min: read §§6–7** (AC, NFRs)

- Score AC testability — does each AC pass the 5-failure-mode check?
- Score NFR completeness — all 5 categories? Defenses real?
- Mark **specific gaps**: missing weird-path AC, boilerplate NFR, etc.

**35–55 min: read §§8–11** (Metrics, Risks, Dependencies, Out-of-scope)

- Score Risk honesty.
- Cross-check §8 metrics against §3 goals (consistency).
- Mark dependencies that don't have named owners.

**55–75 min: write the review document**

Use the **Review Document template** (below).

**75–90 min: refine + submit to author triad**

The two reviewing triads do *not* coordinate — the author triad receives **two independent reviews**.

### The Review Document template

```markdown
# Review of PRD: <feature name>
**Reviewers:** <reviewer triad>  |  **PRD authors:** <author triad>  |  **Date:** <today>

## Scores (0–4 per dimension)

| Dimension | Score | One-line rationale |
|-----------|-------|--------------------|
| Problem clarity | | |
| AC testability | | |
| NFR completeness | | |
| Strategy linkage | | |
| Risk honesty | | |
| Writing discipline | | |

**Total:** [weighted sum, out of 4.0]

## Top 3 strengths
1. <specific>
2. <specific>
3. <specific>

## Top 5 specific findings (defects, gaps, suggestions)

For each: cite the section / line, name the problem, propose the fix.

1. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

(Repeat 5 times)

## Open questions for the author triad
> Things we'd ask in the in-person clarifying conversation (Block 2).
```

### What "good" reviewing looks like

- **Specific** beats general. "§2 is unclear" is bad; "§2 doesn't say *which* dispatchers — small-shop or large-shop — and that changes scope" is good.
- **Cite the section.** Reviewer must point to where in the document the issue lives.
- **Suggest a fix.** A reviewer who only finds problems is half-doing the job.
- **Three strengths is required.** Honest praise builds the trust that lets the harder feedback land.

### Facilitator coaching cues

- Catch reviewers writing "this could be more specific" — push them to write the specific version themselves.
- Coach against scoring the *idea* instead of the *PRD*. Even a weak idea can have a strong PRD; even a strong idea can have a weak PRD.
- Some reviewers will be too generous on first pass. Calibrate by sharing the rubric definition mid-block.

---

## Activity 2 — Author Response + Clarifying Conversation

**Format:** Triad-of-three (author + 2 primary reviewers) &bull; **60 min** &bull; Block 3 morning

### Purpose
The author triad meets both primary reviewer triads in person. The conversation is **not** about negotiating scores; it's about **clarifying findings** and surfacing implicit feedback that didn't make it into the written review.

### The conversation protocol

**0–5 min: review summary (each reviewing triad)**

Each reviewer triad gives a 2-minute spoken summary of their main findings.

**5–25 min: the author triad asks**

The author triad runs the conversation. They ask:

- "Finding #3 — can you walk us through what specifically tripped you?"
- "You scored AC testability at 2 — which AC was the worst, and what would you have written instead?"
- "What did you *almost* write down but decided not to?"

**25–50 min: the reviewers ask**

Reviewers may surface things they didn't write:

- "We assumed X. Was that right?"
- "We disagreed internally about Y. What's your take?"

**50–60 min: capture**

The author triad closes by **summarizing what they heard**:

- Findings they will adopt → action item per finding
- Findings they will defer → with reasoning (and where it gets tracked)
- Findings they will push back on → with reasoning

This becomes the input to the afternoon revision block.

### Facilitator role

Sit in on at least one conversation. Watch for:

- Authors getting defensive — coach toward curiosity
- Reviewers softening at the table — call out: "What did you write down? Stand by it or revise."
- Conversations that drift to "the *idea*" instead of "the *PRD*" — redirect

---

## Activity 3 — Revisions

**Format:** Triad &bull; **90 min** &bull; Block afternoon 1

### Purpose
Revise the PRD based on the morning's reviews and conversations. Update the **review-resolution log**.

### The triad protocol

1. **Sort findings by category** (15 min):
    - Adopt — change the PRD
    - Defer — track elsewhere (issue/ticket/Week-4 backlog)
    - Push back — write the reasoning
2. **Revise in priority order** (60 min):
    - Coherence fixes first (across-section issues)
    - Specificity fixes second (within-section vagueness)
    - Prose fixes last (sentence-level)
3. **Update the resolution log** (15 min):

```markdown
## Friday review-resolution log

**Reviewers (AM):** Triad B, Triad C
**Total scores:** B = 3.1 / C = 2.8 → addressed below

### Adopted (changes made)
- B/Finding 2: §6 AC #4 was untestable. Rewrote with explicit observable.
- C/Finding 1: §7 missing Compliance NFR. Added retention + audit-trail NFRs.
- B/Finding 5: §9 risk "tech adoption" had no mitigation. Added optional toggle.
- (etc.)

### Deferred
- C/Finding 3: Multi-shop manager view scope. DEFERRED to §11 follow-up + ticket.

### Pushed back
- B/Finding 4: Reviewer suggested splitting AC #2; we declined because the
  "ands" describe one observable state. Reasoning preserved here.
```

### Status flip

After the revision pass, flip the PRD's status from "In review" to "Revised — secondary pending."

---

## Activity 4 — Secondary Review

**Format:** Single-triad reviewer &bull; **60 min** &bull; Block afternoon 2

### Purpose
A **different** reviewer reads only the **revised** PRD (not the originals). They look at:

- Did the resolution log line up with the actual changes? (Honesty check)
- Did the revisions introduce new problems?
- Are the deferrals reasonable?
- Final score using the rubric

### The secondary reviewer protocol

**0–35 min: read the revised PRD + resolution log**

Score with the rubric. Compare to the AM scores in the log — has the PRD genuinely improved?

**35–50 min: write the Secondary Review Note**

```markdown
# Secondary Review of PRD: <feature name>
**Reviewer:** <triad>  |  **Authors:** <triad>

## Final score: [weighted total]

## What improved (vs. AM scores)
- …

## What still needs work (gaps in the revision)
- …

## Verdict
- [ ] Ships as-is (score ≥ 3.0)
- [ ] Ships with named gaps (score 2.0–2.9, gaps captured in resolution log)
- [ ] Needs further revision (score < 2.0; facilitator review)
```

**50–60 min: deliver to authors + sign off**

The secondary reviewer hands the note to the authors. The authors sign off (or escalate to facilitator).

---

## End-of-day (and end-of-week) checkpoint

Each triad ships:

- [x] **Final PRD** — Status: "Approved" (or "Approved with gaps")
- [x] **Resolution log** showing all morning findings handled
- [x] **Secondary review note** with final score
- [x] At least 6 reviews authored (2 primary in AM + ≥1 secondary in PM)
- [x] At least 3 reviews received (2 primary + 1 secondary)

This is the **mini-capstone deliverable**. The PRD itself is the artifact; the review trail is the evidence of the process.

## Facilitator wrap (15 min, end of day)

- Read aloud one strength of each triad's PRD (named publicly).
- Surface the **most common review finding** across the cohort (this is the cohort's growth edge for Week 4).
- Preview Week 4: the PRDs become input to the **technical architecture** conversation. NFRs become first-draft architectural constraints.

## Facilitator reflection prompts (end of week)

- Which triad's PRD shipped highest? They are the positive example for Week 4 PRDs.
- Which triad's review *quality* (not their PRD) was strongest? Hold up — review skill is a TPM superpower.
- Did any author triad respond defensively? Coach individually before Week 4.
- Did the cohort find the non-AI discipline harder or easier than expected? Tap that next week — Week 4 reintroduces AI for technical-architecture work.
