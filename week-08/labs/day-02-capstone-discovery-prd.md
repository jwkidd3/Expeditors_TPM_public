# Day 2 — Capstone Discovery + Compressed PRD

> **Activity packet** for participant quads. Today's job: do compressed discovery on the Holocron problem (the Week-1 muscles in 1 day) and produce **PRD-light** — a 2-page version that captures sections 1–7 with the same discipline as Week 3 in a fraction of the time.

## Where we are in the week

Day 1 locked the Holocron scope slice and installed the AI Spec pattern. Today is **Discovery + PRD-light**. The Week-1 customer-centric work is compressed into one day; Week-3's PRD work is compressed into the afternoon.

By 16:00, every quad has a 2-page PRD-light ready to hand off as input to tomorrow's compressed architecture work.

## The compression discipline

Compressed work is not lower-quality work. It's **selective**: keep what's load-bearing, cut what's cosmetic. A compressed PRD covers:

- Section 1 Context (½ page)
- Section 2 Problem (½ page)
- Section 3 Goals + non-goals (½ page)
- Section 4 Scope (in/out table)
- Section 5 Solution sketch (½ page)
- Section 6 Top 6–8 Acceptance Criteria
- Section 7 Top 5 NFRs (one per category from Wk 3 D3)

That's 2 pages. Every word earns its place.

## Inputs

- The discovery inputs gathered overnight + this morning
- The AI Spec template from Day 1
- The Pattern Library prompts from Weeks 2, 4, 5

---

## Activity 1 — Compressed Customer Discovery

**Format:** Quad &bull; **35 min** &bull; Block 1

### Purpose
Compressed Week-1 work: ground in customer signal, name the persona, name the pain, name the journey friction.

### Quad protocol

#### Step 1 — Synthesize what you know (10 min)

Each quad member shares the inputs they gathered. Pool into:

- **Direct customer signal** — interviews, support tickets, observation, data
- **Indirect signal** — public reviews, competitor analysis, internal Slack
- **What's missing** — be honest

#### Step 2 — Name the persona (10 min)

A compressed persona has 3 fields:

```markdown
**Persona:** <role + segment>
**Job-to-be-done:** <verb-based, in their language>
**Why it's hard today:** <specific friction; quote a real customer if possible>
```

Example: "**Persona:** New B2B finance ops associate at a 200-person company. **Job-to-be-done:** Close the books each month without staying late on Friday. **Why it's hard today:** 'I spend Thursday night chasing 4 different teams for missing accruals — by the time they respond, I've forgotten what I asked.'"

#### Step 3 — Top 3 pain points + journey friction (10 min)

For the persona, list 3 specific pains. Each ranks on:

- **Severity** (how bad is it?)
- **Frequency** (how often does it happen?)
- **Addressability** (can our feature actually fix it?)

The pain that survives all three goes in the PRD.

#### Step 4 — Sanity check (5 min)

The quad reads what they have aloud. Does it sound like a real customer's life, or a generic SaaS persona?

### Output

A 1-page **discovery summary** that becomes the input to PRD-light Sections 1–2.

---

## Activity 2 — PRD-Light Sections 1–4

**Format:** Quad &bull; **40 min** &bull; Block 2

### Purpose
Draft sections 1–4 of the compressed PRD: context, problem, goals/non-goals, scope.

### Quad protocol — applied with AI assistance

The Week-3 discipline holds. AI accelerates drafting but does not replace judgment.

#### Step 1 — Context + Problem (15 min)

Each quad member solo-drafts Section 1 and Section 2 first. Then quad picks the strongest.

AI assistance pattern (after the solo drafts):

```
Role: Editor for a TPM's PRD context section.
Context: <quad's draft Section 1 + the discovery summary>
Task: Tighten this section to ½ page max. Preserve the customer
quote. Preserve the strategic anchor. Cut anything that sounds
like marketing language.
Constraints:
  - Do not invent customer signal
  - Flag any claim that needs source backing
Format: Tightened Section 1 + a "what I cut" note.
```

#### Step 2 — Goals + Non-goals (15 min)

3 goals; 2–3 non-goals. Same Week-3 discipline. Goals are user outcomes, not feature names.

#### Step 3 — Scope (in / out) (10 min)

A 2-column table. Default: cut aggressively to fit the 4-day capstone window.

### What "good" looks like

- Section 1 fits ½ page; references at least one customer quote or data point
- Section 2 names the persona's specific friction
- Goals are outcomes, not features
- Non-goals catch the most-likely scope creep
- Scope-out is rich (capstone work is naturally narrowed)

---

## Activity 3 — PRD-Light Sections 5–7

**Format:** Quad &bull; **40 min** &bull; Block 3

### Purpose
Draft Section 5 solution sketch + Section 6 Acceptance Criteria + Section 7 NFRs.

### Quad protocol

#### Step 1 — Section 5 Solution Sketch (10 min)

½ page. The user-visible flow + key surfaces + hard interactions. Does **not** specify implementation.

The "engineer's first three questions" test from Week 3 still applies.

#### Step 2 — Section 6 Acceptance Criteria (15 min)

6–8 ACs total. Coverage:

- 3 happy-path ACs
- 2 sad-path ACs
- 1 weird-path AC

Use the Given/When/Then form. Compressed = fewer ACs, not weaker ACs.

#### Step 3 — Section 7 NFRs (15 min)

Top 5 NFRs — one per category:

- 1 Performance NFR (latency target with defense)
- 1 Security NFR (auth/authz approach)
- 1 Accessibility NFR (the WCAG floor)
- 1 Observability NFR (the leading indicator from your outcome map)
- 1 Compliance NFR (the regime that applies)

Each NFR uses the Wk 3 template: requirement / defense / verification.

### What "good" looks like

- Section 5 doesn't specify implementation
- Section 6 has happy/sad/weird coverage
- Section 7 has all 5 categories represented
- The whole document fits 2 pages

---

## Activity 4 — AI Validation Pass + Day-3 Setup

**Format:** Quad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Run the validation pass on PRD-light. Set up Day 3's compressed architecture work.

### The validation pass

Use the Week 5 Day 5 discipline. For PRD-light:

```
Role: Senior PM reviewing a compressed PRD.
Context: <paste PRD-light Sections 1–7>
Task: Identify 5 issues:
  1. A claim that lacks evidence
  2. A goal that's actually an output
  3. A non-goal that's missing
  4. An AC that's untestable or vague
  5. An NFR that's boilerplate
Constraints:
  - Be specific
  - Suggest a concrete fix
Format: 5 numbered findings.
```

Adopt / defer / reject. Update PRD-light. Provenance log.

### Day-3 setup (last 20 min of block)

Tomorrow you'll produce TCD-light + TMD-light + AI Spec v1. Plan ahead:

1. **What architectural questions do you need an answer to?** List the 3 questions a senior architect would ask reading PRD-light. These become tomorrow's TCD-light Section 1 input.
2. **What systems / data / APIs are in scope?** Sketch the integration map you'll formalize tomorrow.
3. **What's the critical path?** Which of TCD-light / TMD-light / AI Spec must ship by EOD tomorrow vs Thursday?

### Wrap (last 15 min)

Each quad shares:

- Their **persona's job-to-be-done** in one sentence
- The **AC** they're proudest of
- The **NFR** that worried them most

---

## End-of-day checkpoint

Each quad ends Day 2 with:

- [x] **Discovery summary** (1 page)
- [x] **PRD-light Sections 1–7** (2 pages total)
- [x] AI validation pass run on PRD-light
- [x] Provenance log entry
- [x] **Day-3 plan**: 3 architecture questions, integration sketch, critical path
