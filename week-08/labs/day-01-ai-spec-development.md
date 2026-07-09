# Day 1 — AI Spec Development

> **Activity packet** for participant triads. Today's job: install the **AI Spec Development pattern** — a structured prompt sequence that produces an engineering-ready integrated technical spec from PRD/TCD/TMD inputs — and confirm the capstone subject.

## Where we are in the week

Week 8 opens with a new technique. AI Spec Development is the synthesis of everything learned across Weeks 2 (prompting), 4–5 (architecture and modeling), and Week 5 Day 5 (validation discipline). The pattern is what an experienced TPM uses to compress a week of spec work into hours — without losing the rigor.

By 16:00, every triad has:

- A **working AI Spec template** with the prompt sequence
- A **confirmed capstone subject** with initial inputs gathered
- **Tomorrow's plan** — what discovery they need to do for compressed PRD work

## Inputs

- The full sibling artifact set from Weeks 3–7 (the templates carry forward)
- The triad's declared Week-8 capstone candidate
- The Pattern Library accumulated across Weeks 2, 4, 5, 6, 7

---

## What "AI Spec Development" is — and isn't

| Is | Is not |
|----|--------|
| A structured sequence of validated prompts that produces an integrated spec | "Just paste everything and ask AI to summarize" |
| Anchored on the PRD/TCD/TMD/SEP/DP outputs as inputs | Replacing the artifact set |
| Disciplined: every output is validated against a source | Trust the AI's output |
| Iterative: 4–6 prompts in sequence, each refining | One mega-prompt |
| Engineering-ready output — sections an engineer can scope from | A pretty draft for stakeholders |
| Always paired with a provenance log | Untracked AI use |

A senior TPM uses this pattern to **draft** the spec; their judgment shapes every section; AI accelerates the typing, not the thinking.

---

## The AI Spec template (today's reference)

```markdown
# AI Spec — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>, SEP <link>, DP <link>
**Authors:** <triad>  |  **Status:** Draft / Reviewed
**AI Provenance:** see end-of-doc log

## 1. Headline
One sentence: what is this feature, who is it for, what outcome does it produce?

## 2. Engineering-ready summary
3–5 paragraphs that an engineer could scope from without a clarifying call.
Synthesizes: PRD §§1–5, TCD §1, TMD §3.

## 3. Data + API contract
The shape an engineer needs to start coding. Synthesizes:
TMD §1 (data) + TMD §3 (API).

## 4. Sequence + failure handling
Happy / sad / weird path summary. Synthesizes: TMD §4.

## 5. Constraints
Performance / availability / security / compliance / accessibility.
Synthesizes: TCD §3 + TCD §4 + PRD §7.

## 6. Decisions made (and not made)
Top trade-offs (TCD §5) + open questions still requiring decision.

## 7. Stakeholders + sign-off
Who must sign off on what. From SEP §1 + TCD §6.

## 8. Provenance log
Every AI prompt + validation status.
```

The AI Spec is **shorter** than the sum of its inputs. It's the synthesis an engineer would read first, with citations back to the deeper artifacts.

---

## The 5-prompt sequence (today's main pattern)

The AI Spec is generated from a **5-prompt sequence**, not a single prompt. Each prompt has a specific job + validation step.

### Prompt 1: Headline + engineering-ready summary

```
Role: Senior TPM drafting an engineering-ready spec.
Context: Below are excerpts from PRD §§1–5, TCD §1, TMD §3.
<paste excerpts>
Task: Produce:
  1. A one-sentence headline (what / who / outcome)
  2. 3–5 paragraphs that an engineer could scope from without
     a clarifying call. Synthesize the inputs; do not invent.
Constraints:
  - Use only the provided content
  - Cite sections you draw from
  - Flag anything ambiguous in the input
Format: Headline + numbered paragraphs + footnotes section.
```

**Validation:** read through; verify every claim cites a section. Cut hallucinated claims.

### Prompt 2: Data + API contract synthesis

```
Continuing. Below are TMD §1 (data) and TMD §3 (API).
<paste>
Task: Produce a 1-page synthesis that an engineer could
implement against. Include:
  - Entity-level data shape (key fields + relationships)
  - API surface (endpoints + methods + key behaviors)
  - Idempotency + versioning + error semantics
Constraints:
  - Do not invent fields or endpoints
  - Flag any inconsistency between the data model and API
Format: Markdown with sub-sections.
```

**Validation:** for every entity / endpoint, verify it exists in the source.

### Prompt 3: Sequence + failure handling

```
Continuing. Below are the 3 sequence diagrams (happy/sad/weird)
from TMD §4.
<paste descriptions>
Task: Produce:
  1. Happy-path narrative (1 paragraph)
  2. Top 2 sad-path scenarios with system response
  3. Top 1 weird-path scenario with named invariant
Constraints:
  - Reference the sequence diagrams; do not invent flows
  - Preserve the named invariant from the weird path
Format: Markdown with sub-headings.
```

**Validation:** the named invariant from TMD §4 is preserved verbatim.

### Prompt 4: Constraints synthesis

```
Continuing. Below are TCD §3 (security/compliance), TCD §4 (SLOs),
PRD §7 (NFRs).
<paste>
Task: Produce a 1-page constraints summary covering:
  - Performance + availability targets (SLOs)
  - Security + compliance non-negotiables
  - Accessibility floor
  - Observability requirements
Constraints:
  - Use the actual numbers / targets from the inputs
  - Flag any constraint that conflicts with another
Format: Markdown table; include "trade-off" column for any conflicts.
```

**Validation:** every number is traceable to a source.

### Prompt 5: Decisions + stakeholders

```
Continuing. Below are TCD §5 (top trade-offs), TCD §6 (sign-off
matrix), SEP §1 (stakeholder map).
<paste>
Task: Produce:
  1. The top 5 trade-offs (Option A / B / Choice / Cost / Revisit)
  2. Open decisions still required (with named owner)
  3. The sign-off matrix linking constraints to stakeholders
Constraints:
  - Preserve the trade-off structure exactly
  - Do not soften "accepted cost" or "revisit trigger"
Format: 3 sub-sections.
```

**Validation:** the trade-off costs and revisit triggers are preserved verbatim — these are the senior-author signals.

---

## Activity 1 — Capstone Subject Confirmation

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Confirm the capstone subject. Some declared candidates won't survive contact with the constraint of doing it in 4 days.

### Triad protocol

1. **Re-read your declared candidate** (5 min). What did you say end of Week 7?
2. **The 5 capstone-fit questions** (15 min):
    - Do we have a **real customer**? (interviews / observation / data — not just a guess)
    - Is the scope **substantive enough** that compressed PRD work has substance?
    - **Clear problem?** Can you state the core problem in one sentence an engineer could scope from?
    - Can we **discuss it publicly** (no NDA / IP issues)?
    - Can we **ship the artifact set in 4 days** (Day 2-4 build + Day 5 present)?
3. **Adjust or commit** (10 min). If 1+ question is "no", refine or pick a backup.
4. **List inputs you'll need** (5 min). Customer interviews / data / docs / system access.

### Output

A confirmed capstone subject + a list of inputs to gather before tomorrow's discovery work.

---

## Activity 2 — Walk Through the AI Spec Template

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Internalize the AI Spec template by walking through it section-by-section using a **previously-completed FieldPulse artifact set** as the source.

### Triad protocol

1. **Read the AI Spec template** (5 min).
2. **Walk each section** (30 min). For each of the 8 sections, identify:
    - What input artifact does this synthesize?
    - What's likely to be missing if the input is thin?
    - What would an engineer expect here that we should make sure to include?
3. **Identify the section your team will struggle with most** (5 min). Plan a counter-measure.

### What "good" looks like

- Every section is mapped back to **specific input artifacts**
- The "missing-if-thin" awareness is **specific** ("if the data model has no relationships diagrammed, §3 will be hard to draft")
- The "section we'll struggle with" is **named** with a counter-measure

---

## Activity 3 — Run the 5-Prompt Sequence on FieldPulse

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Practice the sequence on the FieldPulse artifact set (where the inputs are complete and validated) before applying it to the capstone tomorrow.

### Triad protocol

1. **Run Prompts 1–5 in sequence** (30 min). For each:
    - Paste the relevant input
    - Capture the output
    - Validate (cross-check / spot-check / mark)
2. **Assemble the AI Spec** (10 min). Combine the 5 outputs into the §1–§7 structure. Add the provenance log.
3. **Cross-check the result against the original artifacts** (no extra time block — done as you go). Anything in the AI Spec that contradicts a source: flag and fix.

### Output

A first AI Spec for FieldPulse — produced via the 5-prompt sequence — that the triad can use as a template for tomorrow's compressed work.

---

## Activity 4 — Capstone Discovery Plan

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Plan the discovery work needed for tomorrow's compressed PRD. Distribute the work across triad members.

### Triad protocol

1. **List discovery inputs needed** (10 min). For your capstone:
    - Customer signal — interviews, support data, public reviews
    - Strategic context — why this matters, what's been tried
    - System inputs — existing docs, codebase access, related artifacts
    - Stakeholder signal — who has opinions; what are they
2. **Distribute work** (10 min). Each triad member takes 1–2 categories.
3. **Set the deadline for inputs gathered** (5 min). Typically: 8 PM tonight or first hour tomorrow morning.
4. **Identify the "we don't have this and can't get it"** (10 min). Be honest. Document what you're proceeding without; mark it for AI-augmented hypothesis tomorrow (with extra validation).
5. **Run the AI prompt** (10 min):

```
Role: Capstone advisor for a TPM cohort.
Context: <capstone subject + 5-question fit assessment +
         declared inputs needed>
Task: Identify 3 risks in the capstone plan:
  1. A customer signal source likely insufficient
  2. A scope dimension likely too ambitious for 4 days
  3. A stakeholder whose buy-in we'll need but didn't list
Constraints:
  - Be specific to the subject given
  - Suggest a concrete adjustment per risk
Format: 3 numbered findings.
```

### Wrap (last 15 min)

Each triad shares:

- Their **confirmed capstone subject** in one sentence
- The **section of the AI Spec they think they'll struggle with most**
- One **risk** the AI surfaced about their plan

---

## End-of-day checkpoint

Each triad ends Day 1 with:

- [x] **Capstone subject confirmed** through 5-question fit assessment
- [x] **AI Spec template** internalized; FieldPulse practice run completed
- [x] **5-prompt sequence** rehearsed
- [x] **Discovery inputs list** + distributed assignments
- [x] **Risks** acknowledged with mitigations
- [x] AI provenance log entry
