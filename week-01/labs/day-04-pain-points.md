# Day 4 — Identifying Pain Points

> **Activity packet** for facilitators and participant triads. Day 4 produces a scored pain-point matrix and a rank-ordered Top 3 per triad.

## Prerequisite artifacts (from Day 3)

- Persona Validation Canvas (all 6 boxes complete)
- At least 5 candidate pain points in Box 5
- Parking-lot of open validation questions

## Materials for the day

### FieldPulse Pain Extraction Packet (distributed at start of day)

Each triad receives a **shuffled subset** of the packet — no two triads get the same full set. Encourages later cross-triad learning.

Contents (total):

1. **14 support tickets** — sanitized, ranging from "app crashes mid-reconcile" to "please add dark mode"
2. **2 ride-along note pages** — one for Maria, one for Trey (observed workarounds)
3. **4 interview excerpts** — multi-paragraph selections from Day 3 interviews
4. **1 analytics screenshot** — funnel showing dispatcher drop-off on the current reconcile flow (65% abandonment at step 4 of 7)

### Pain-Point Severity Matrix

Provided as a printable 3×3 grid with color overlay. Severity (high/medium/low) × Frequency (high/medium/low). Each cell large enough to stick sticky notes or names in.

---

## Activity 1 — Extract From the Packet

**Format:** Triad &bull; **45 min** &bull; Block 1

### Purpose
Train the eye for real pain hiding in observed behavior, not just stated complaints.

### Protocol

1. **Silent pass (10 min):** Read the packet individually. Flag anything that hints at pain.
2. **Extract (25 min):** As a triad, produce at least **15 candidate pains**. Each must:
   - Be a verb + circumstance + consequence
   - Cite its source (ticket #, interview initials, observation line)
3. **Review (10 min):** Go through each entry and mark:
   - [ ] Verb-based (not a noun category)?
   - [ ] Specific circumstance named?
   - [ ] Measurable or observable consequence?

### Anti-patterns to watch for

| If you wrote… | Fix to… |
|---------------|---------|
| "Bad UX" | "Dispatchers abandon the reconcile flow at step 4 because…" |
| "Mobile issues" | "Techs retype tickets at night because the app can't submit on 3G" |
| "Confusing" | "New dispatchers bounce after screen 5 of onboarding because…" |

### Deliverable
A raw list of 15+ pain-point candidates, tagged with source.

---

## Activity 2 — Dig, Sort, Promote

**Format:** Triad &bull; **50 min** &bull; Block 2

### Step 1 — 5 Whys on 3 pains (20 min)

Pick the **three surface-most** pains from your list. Run 5 Whys on each (no more than 5 levels; usually 3–4 is enough). Capture:

```markdown
L1: <surface pain>
  Why? <answer>
L2: <new pain>
  Why? <answer>
L3: <new pain>
  Why? <answer>
  → (if reached) Root cause: <systemic or out-of-scope>
```

### Step 2 — Silent sort (20 min)

> **Enforce silence.** The facilitator should call the room silent for this block.

1. Write each pain on a sticky note (or equivalent in your tool)
2. In silence, each triad member places pains on the wall, grouping by affinity
3. When two members disagree on placement, move the note — don't discuss
4. After 10 minutes of placing, stop. Take 2 minutes of silent look.

### Step 3 — Cluster + promote (10 min)

Now speak. For each cluster:

- Name it with a **verb phrase**, not a category (e.g., "closing the day" not "operations")
- Promote 1–2 pains that best represent the cluster

### Deliverable
5–8 named clusters, each with 1–2 promoted pains.

### Facilitator note
If a triad finishes silent-sort fast, they probably skipped disagreement. Walk over and ask: "Were there any placements someone else moved? Good ones to revisit."

---

## Activity 3 — Score Your Map

**Format:** Triad &bull; **45 min** &bull; Block 3

### Instructions

1. Place each promoted pain on the Severity × Frequency matrix (20 min)
2. Color-code by Addressability: green (fully our product), amber (partial), red (out of scope) (10 min)
3. For each **red "Must fix"** pain (high sev + high freq + low addr), draft two sentences (10 min):
   - *Why we cannot solve this.*
   - *What we will do instead* (communicate, partner, accept with mitigation).
4. Identify **one pain** where AI-augmented analysis could raise addressability — e.g., AI-summarizing inbound support tickets to reduce dispatcher load (5 min)

### Scoring guidance

| Severity | Low | Medium | High |
|----------|-----|--------|------|
| Means | Annoyance | Workaround in place | Blocked — can't complete the goal |

| Frequency | Low | Medium | High |
|-----------|-----|--------|------|
| Means | Monthly or less | Weekly | Daily or more |

| Addressability | Low (red) | Medium (amber) | High (green) |
|----------------|-----------|----------------|--------------|
| Means | Org/regulatory | Partial (need other teams) | Fully within our product |

### Deliverable
A completed matrix with all promoted pains placed and color-coded. "Must live with" notes for red cells.

---

## Activity 4 — Cross-Triad Challenge

**Format:** Paired triads &bull; **60 min** &bull; Block 4

### Step 1 — Select Top 3 (within triad, 10 min)

Pick the three pains you'll carry into Friday's problem statement. Rank-order them. Be prepared to defend:

1. Why these three over the others? (matrix + evidence)
2. Are they independent, or aspects of the same root cause?
3. What's the "if we solved this, everything else is easier" pain?

### Step 2 — Cross-triad challenge (25 min each direction)

Triad A presents Top 3 + matrix. Triad B must:

- Nominate the **weakest** of the three (based on evidence tier, not feel)
- Propose one pain **not** selected that might be stronger, with reasoning
- Ask one **"so what if we're wrong?"** question per pain

### Step 3 — Revise (within triad, 15 min)

Update Top 3 based on critique. If nothing changes, re-read the critique.

### Step 4 — Readout (full room, 10 min)

Each triad: 60 seconds. Final Top 3, with one-sentence defense each.

### Scoring rubric (each critique pair peer-scores)

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| Pain specificity | Category words | Verb-based but vague | Verb + circumstance + consequence |
| Evidence strength | Unsourced | 1 source per | Multiple tiers, observed present |
| Independence | Overlapping | Related | Three distinct root causes |
| Honesty | Avoided the weakest | Named the weakest | Publicly dropped/downgraded one |

---

## End-of-day checkpoint

- [x] Scored Severity × Frequency × Addressability matrix per triad
- [x] "Must live with" notes for any red "Must fix" cells
- [x] Rank-ordered Top 3 pains, each defended against cross-triad critique
- [x] One AI-leverage candidate identified (for raising addressability)

## Bridge to Day 5

The Top 3 pain set is the direct input to the Friday problem statement. Each triad should also carry forward **the one pain they dropped that they're still wrestling with** — it's useful material for Day 5.
