# Day 4 — AI-Augmented Stakeholder Requirement Summaries

> **Activity packet** for facilitators and participant triads. Today's job: use AI as a **meeting-prep assistant** — to summarize prior context, predict objections, and draft openings — with the AI-validation discipline from Week 5 Day 5 firmly in place. By 16:00, every triad has SEP §4 — a meeting-prep packet for tomorrow's Friday simulation.

## Where we are in the week

The map exists (Day 1). The plan exists (Day 2). One brief exists (Day 3). Today AI helps prepare for tomorrow's negotiation. The discipline: AI summarizes; the human decides; everything gets logged.

## Inputs

- SEP §1 (stakeholder map)
- SEP §2 (engagement plan + 5 most consequential asks)
- SEP §3 (the 1-page brief from yesterday)
- TCD §6 (sign-off matrix with statuses)
- All prior artifacts (PRD, TCD, TMD)

---

## What "meeting prep with AI" actually means

A common rookie pattern: dump 50 pages into ChatGPT and say "summarize this for my meeting." Output: confident, generic, invariant-blind.

Better pattern: AI does **specific, structured tasks** under explicit constraints, and every output gets validated.

| AI does well | AI does poorly |
|--------------|----------------|
| Re-organize content you provide | Tell you what's been decided |
| Suggest predictable objections | Predict who in the room you've never met |
| Draft an opening that you edit | Decide the opening tone |
| Identify gaps in coverage | Verify facts against current production |

---

## The 4 meeting-prep deliverables (today's structure)

For tomorrow's negotiation simulation, each triad produces:

### 1. Prior-context summary
A short summary of what's already been said about this trade-off / ask:

- Prior decisions made (by whom, when, where documented)
- Open questions that remain
- Tension that surfaced in earlier conversations

### 2. Objection map
Predicted top 5 objections from the stakeholder, ranked, with:

- The objection (in the stakeholder's likely words)
- The honest response — what's true
- The pivot — where to redirect if pushback continues

### 3. Opening
The 60-second opening you'd use to start the conversation:

- Why we're meeting
- What's at stake for them
- What you're asking for
- Any acknowledgment of past tension

### 4. Non-negotiables
The 1–3 things you cannot give up. Knowing these in advance is the defense against folding under pressure.

---

## Activity 1 — Prior-Context Summary (with Validation)

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Use AI to assemble a prior-context summary, then validate it.

### The two-prompt approach

#### Prompt A — Assemble the context

```
Role: Project archivist for a TPM.
Context: Below is the relevant content from PRD, TCD, TMD, and SEP
on the topic of <trade-off / ask>.
<paste relevant excerpts — sections that touch this topic>
Task: Produce a prior-context summary covering:
  1. Prior decisions made (with section reference)
  2. Open questions that remain
  3. Tension that surfaced (if any) — with section reference
Constraints:
  - Use only the provided content; do not extrapolate
  - Cite specific sections for every claim
  - If a category has nothing to report, say "none documented"
Format: 3 numbered sections; bulleted entries with citations.
```

#### Prompt B — Find the gaps

```
Continuing from above. What's likely to come up in the negotiation
that the documented context does NOT cover? List 3 gaps the
stakeholder might raise that we don't have a documented answer to.
Constraints:
  - Be specific to the topic and stakeholder
  - Do not invent stakeholders or scenarios
Format: 3 gaps, each with: gap / scenario / suggested research.
```

### Triad protocol

1. **Identify the topic** (5 min). What's the negotiation about? (Pull from "5 most consequential asks" — Day 2.)
2. **Run Prompt A** (10 min). Generate the prior-context summary.
3. **Validate** (15 min). For each cited section: does it actually say what the AI claims? Same Wk 5 D5 discipline. Mark each: cross-checked / spot-checked / wrong → cut.
4. **Run Prompt B** (5 min). Capture the 3 gaps.

### Output

A validated prior-context summary + a gap list. Add to AI-validation log.

### Facilitator coaching cues

- The validation step is the muscle. Don't let triads skip it. If they say "looks fine" — push them: "did you actually open §3 of TCD and verify?"
- The gap list is high-leverage — it's what you'll research before the meeting (or admit during it).

---

## Activity 2 — Objection Map

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Predict the top 5 objections the stakeholder will raise, with honest response + pivot.

### The objection-map prompt

```
Role: <stakeholder type — e.g., Compliance Lead, Architect>
Context: <paste the 1-page brief from Day 3 + relevant TCD/TMD excerpts>
Task: Read as the named stakeholder. List your top 5 objections to
the proposal, ranked by intensity.
Constraints:
  - Be specific to the brief, not generic
  - Voice the stakeholder honestly — not a strawman
  - At least 1 objection should be hostile (the one you'd push hardest)
Format: 5 numbered objections; each one short, in the stakeholder's
likely tone.
```

### The triad's response template

For each predicted objection:

```markdown
### Objection N: <short name>
**The stakeholder says:** <quoted, in their voice>

**The honest response:** <what's actually true; do not over-promise>

**The pivot (if pushback continues):** <where to redirect — usually
to a deeper "why" or to a documented trade-off>

**The line we hold:** <if this objection wins, what's the smallest
ground we give up?>
```

### Triad protocol

1. **Run the AI prompt** (10 min). Capture 5 objections.
2. **Validate** (10 min). Are these realistic for this stakeholder? Edit; some AI predictions will be wrong tonally or factually.
3. **Write the response template** (15 min). Each objection gets honest response + pivot + line we hold.
4. **Identify the highest-stakes objection** (5 min). Which is most likely to derail tomorrow?

### What "good" looks like

- Objections sound **like the stakeholder would actually say them**, not strawmen
- "The honest response" includes what's actually true, not just persuasion
- "The line we hold" is **specific** — not "compromise"
- The highest-stakes objection has a **rehearsed response** by the end of the activity

---

## Activity 3 — The Opening + Non-Negotiables

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Write the 60-second opening for tomorrow's negotiation. Identify the 1–3 non-negotiables.

### The opening — 4 essential parts

```markdown
### Opening (target: 60 seconds)

1. **Why we're meeting** (1 sentence)
   "I want to walk you through our proposed approach to <trade-off>
   and confirm that you can support it."

2. **What's at stake for them** (1 sentence in their currency)
   "This affects <currency>: <one specific thing they care about>."

3. **What you're asking for** (1 sentence — concrete decision)
   "I'm asking for <approval / specific information / specific action>."

4. **Acknowledgment of any past tension** (1 sentence; only if needed)
   "I know last quarter's <X> didn't go the way we planned; I want
   to be sure we don't repeat that here."
```

A good opening is **practiced**, not improvised. Triads literally rehearse the opening aloud — twice — before tomorrow.

### Non-negotiables

The 1–3 things you cannot give up. Examples:

- "We will not compromise on the audit-trail retention requirement"
- "We will not slip the launch date past July 1; we'll cut scope first"
- "We will not break the SSO scope contract with Identity"

The discipline:

- Each non-negotiable is **specific** (not "quality" or "the user")
- Each has a **fallback** if pushed — what we'd cut to preserve it
- The list is **short**: 3 non-negotiables max

### Triad protocol

1. **Draft the opening** (15 min). Use the 4-part template.
2. **Rehearse** (10 min). Read it aloud in the triad twice. Time it. If > 75 seconds, cut.
3. **Identify non-negotiables** (10 min). 1–3 specific items.
4. **Pick fallback for each** (5 min). What scope / time / approach would you give up to protect each non-negotiable?

### What "good" looks like

- Opening is **under 75 seconds** when read aloud
- Opening **invites the stakeholder in** (not a lecture)
- Non-negotiables are **specific and few**
- Fallbacks are named — not just "we'd find another way"

---

## Activity 4 — Cross-Review + Mock Meeting

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Pair triads. Each triad runs a 5-minute mock meeting opening with the other triad in role. Surface what works and what doesn't before tomorrow.

### The mock-meeting protocol

1. **Pair triads** (instructor assigns; same pair as Day 3).
2. **First triad opens** (5 min). They give their 60-second opening; the reviewer triad asks 1–2 of their predicted objections.
3. **Pause + capture** (5 min). What worked? What threw the author triad?
4. **Switch roles** (5 min for opening).
5. **Pause + capture** (5 min).

### After both rounds (25 min)

Each triad updates their §4 with:

- The opening tweak that came from rehearsal
- The objection that was harder than expected
- A "I wish I'd said" — the line that came after, not in the moment

### AI cross-check (10 min)

```
Role: Negotiation coach reviewing a meeting-prep packet.
Context: <paste the §4 packet — opening, objection map,
        non-negotiables>
Task: Identify 3 gaps in the prep:
  1. An objection probably under-prepared
  2. A non-negotiable that's actually negotiable (or absent)
  3. A part of the opening likely to sound rehearsed in a bad way
Constraints:
  - Be specific
  - Suggest a concrete fix
Format: 3 numbered findings.
```

### Wrap (last 15 min)

Each triad shares:

- Their **non-negotiable** that they're most worried about defending
- The **opening sentence** they're proudest of
- The **objection** they want to rehearse one more time before tomorrow

---

## End-of-day checkpoint

Each triad ends Day 4 with:

- [x] Prior-context summary (validated)
- [x] **5-objection map** with response + pivot + line-we-hold
- [x] **Opening** under 75 seconds, rehearsed
- [x] **1–3 non-negotiables** with fallbacks
- [x] Mock-meeting feedback captured
- [x] AI provenance log entry (continuing the cumulative log from Wk 5 D5)
- [x] SEP §4 drafted

## Facilitator reflection prompts (end of day)

- Which triad's objection map is most realistic? Hold up Friday morning.
- Which triad's opening was sharpest? Hold up.
- Did anyone skip the validation step on AI outputs? Coach Friday morning before the simulation.
- Did any triad list 6+ non-negotiables? Coach to cut to 3 — they'll fold tomorrow if they have too many.
