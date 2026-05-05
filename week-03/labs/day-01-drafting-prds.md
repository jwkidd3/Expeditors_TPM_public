# Day 1 — Drafting Technical PRDs from Customer Requirements

> **Activity packet** for facilitators and participant triads. Today's job: take the triad's top Week-2 feature concept and start the PRD that they'll ship Friday — context, problem, goals, scope, and a solution sketch crisp enough for an engineer to imagine the shape.

## Where we are in the week

Week 3 is the mini-capstone. Triads carry their Week-2 strategy package and pick **one feature concept** to PRD this week. By Friday, that PRD ships, peer-reviewed.

Today produces sections 1–5 of the PRD. AC come Day 2. NFRs come Day 3. The integrated assembly happens Day 4. Reviews happen Day 5.

## The non-AI rule (reminder)

This week is the discipline of producing a defensible written artifact without a generative tool. AI is off until Week 4. What's allowed: spell-check, dictionary, transcripts, your Week-1 and Week-2 artifacts.

## The PRD template (today's reference; printed and on the wall)

```markdown
# PRD — <Feature name>
**Author triad:** <names>  |  **Date:** <date>  |  **Status:** Draft

## 1. Context
## 2. Problem
## 3. Goals & non-goals
## 4. Scope (in / out)
## 5. Solution sketch
## 6. Acceptance Criteria      [Day 2]
## 7. Non-Functional Requirements  [Day 3]
## 8. Metrics & validation     [Day 4]
## 9. Risks & open questions   [Day 4]
## 10. Dependencies            [Day 4]
## 11. Out-of-scope follow-ups [Day 4]
```

---

## Activity 1 — Pick the One Feature

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Force the triad to commit to **one** feature concept from Week 2 and articulate why that one. Many triads will want to keep all three — the discipline of choosing is the work.

### Triad protocol

1. **Re-read the 3 feature cards aloud** (5 min)
2. **Score each on 4 dimensions** (10 min). 1–5 each:
    - **Friction severity** — how big is the pain it addresses?
    - **Metric movability** — how confident are we it'll move the metric in 30 days?
    - **Build feasibility** — how achievable in one quarter?
    - **Learning value** — what do we learn even if it doesn't ship?
3. **Pick one** (10 min). Highest total score is the default; if scores tie, the triad must argue.
4. **Write the "Why this one" memo** (10 min). Two paragraphs:
    - Paragraph 1: Why this feature, in user terms
    - Paragraph 2: Why this feature, in business / strategy terms

### Output

A single feature locked in, with a "Why this one" memo. The memo seeds Section 1 (Context).

---

## Activity 2 — Section 1 (Context) and Section 2 (Problem)

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Write the two sections that give the engineer who reads the PRD enough to **care** about the work before they read what to build.

### Section 1: Context (½ page max)

What this section answers:

- Why this work? (Customer signal — pull from Week-1 interviews/tickets)
- Why now? (Strategic fit — pull from Week-2 NS / Tier Sheet)
- What changed? (If anything triggered the urgency)

What this section avoids:

- ❌ "Customers are asking for it" (vague)
- ❌ Marketing language ("delight users")
- ❌ Restating the company strategy from scratch

### Section 2: Problem (½ to ¾ page)

What this section answers:

- The user's **job-to-be-done** (verb-based, in their language)
- The **friction they hit today** (specific, observed)
- Why **today's workarounds are inadequate**

Tie explicitly to the **Week-2 journey map**. Reference the friction stars.

### Triad protocol

1. **Each member drafts §1 alone** (10 min). Three drafts.
2. **Pick the strongest** (10 min). Combine if needed.
3. **Each member drafts §2 alone** (10 min).
4. **Pick the strongest, combine, edit** (10 min).

### What "good" looks like

- Section 1 fits on half a page.
- Section 2 quotes a real customer (from Week-1 interviews) at least once.
- The reader leaves §2 knowing whose Wednesday afternoon will improve.

---

## Activity 3 — Section 3 (Goals & Non-goals) and Section 4 (Scope)

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Define what success means **in user terms** and bound what will and won't ship in this iteration. Non-goals and out-of-scope items are the most under-valued sections of any PRD.

### Section 3: Goals & non-goals

**Goals** (3–5 max):
- Each goal is a **user outcome**, not a feature
- Each goal is **observable** within 30 days of ship
- ❌ "Ship the dashboard" → ✅ "Dispatchers see open work without hunting"

**Non-goals** (2–4):
- What you explicitly will *not* do
- Often the most valuable section — pre-empts scope creep
- ❌ Skip this section → ✅ "We will not redesign the navigation bar"

### Section 4: Scope (in / out)

A two-column table:

| In scope | Out of scope (this iteration) |
|----------|-------------------------------|
| Mobile flow | Tablet layout |
| Online + offline draft | Offline-first sync |
| English only | Spanish localization |

Out-of-scope is the **negotiation tool** — it tells stakeholders "I see what you might also want; here's why this iteration doesn't include it."

### Triad protocol

1. **Draft 5 candidate goals** (10 min). Cull to 3.
2. **Draft 3 candidate non-goals** (10 min). Cull to 2.
3. **Draft scope table** (15 min). Force the right column.
4. **Sanity check** (5 min). Does each goal tie to a friction star or metric?

### Facilitator coaching cues

- If a triad's goals are feature names ("Ship X"), redirect to user outcomes.
- If non-goals is empty, ask: "What's the most ambitious thing a stakeholder might think this includes?" Put that in non-goals.
- If scope's "Out" column is empty, ask: "What's the version-2 of this feature?" Put it in Out.

---

## Activity 4 — Section 5 (Solution Sketch)

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Describe the solution **just enough** for an engineer to imagine its shape — not so much that you've designed it for them. This is the most-mis-written section in real-world PRDs.

### What goes in §5

- The **user-visible flow**: 4–8 steps from the user's perspective
- The **key surfaces** affected (which screens, which surfaces)
- The **hard interactions** with other systems (other products, APIs, third parties — name them)
- A **happy path** narrative (one paragraph; what a successful run looks like)
- Optional: 1–2 simple sketches or wireframes (allowed; encouraged for clarity)

### What does NOT go in §5

- Database schema decisions
- Specific API contracts
- Class names, framework choices, library picks
- Pixel-level layout

### The "engineer's first three questions" test

After writing §5, ask: what are the **first three questions** an engineer would ask after reading this? If those questions are about implementation choice, you've over-specified. If they're about user behavior or scope, you've under-specified.

### Triad protocol

1. **Sketch the flow** (15 min). On paper. 4–8 steps.
2. **Write the happy-path paragraph** (10 min).
3. **List the hard interactions** (10 min).
4. **The three-questions test** (10 min). Each member proposes 3 engineer questions; flag any that signal over- or under-specification.

### Wrap (last 15 min)

Each triad shares with the room:

- The feature name
- One sentence of context
- One sentence of problem
- The top goal
- The top non-goal

This **two-minute share** is intentional. It catches generic feature concepts before the triad invests another 3 days drafting.

---

## End-of-day checkpoint

Each triad leaves the day with a draft PRD containing:

- [x] Title + author + date + status
- [x] Section 1 (Context)
- [x] Section 2 (Problem)
- [x] Section 3 (Goals & non-goals)
- [x] Section 4 (Scope in / out)
- [x] Section 5 (Solution sketch)
- [x] "Why this one" memo (informal — feeds §1 if useful)

## Facilitator reflection prompts (end of day)

- Which triad picked a feature with the weakest metric link? Coach them tomorrow before AC drafting.
- Which §2 quotes the customer's actual words? Hold up as a positive example.
- Did anyone over-specify §5 (e.g., propose a database)? That's the most common failure mode — surface tomorrow morning.
- Anyone using AI? Course-correct directly and privately.
