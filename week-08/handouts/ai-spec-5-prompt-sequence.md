# AI Spec — The 5-Prompt Sequence

> **Day 1 handout.** The AI Spec is generated from a *sequence* of 5 prompts, not one mega-prompt. Each prompt has a specific job and a specific validation step. Run them in order — each builds on the prior prompt's validated output. Do not run them in parallel.

---

## Prompt 1 — Headline + engineering-ready summary

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

---

## Prompt 2 — Data + API contract synthesis

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

---

## Prompt 3 — Sequence + failure handling

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

---

## Prompt 4 — Constraints synthesis

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

---

## Prompt 5 — Decisions + stakeholders

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

### Between every prompt — the validation discipline

- **Read** the output against the source.
- Mark each claim: cross-checked / spot-checked / pending / rejected.
- Cut hallucinated claims.
- Preserve **verbatim**: trade-off costs, revisit triggers, named invariants, customer quotes.

Then assemble the 5 validated outputs into the AI Spec §1–§7 structure and add the §8 provenance log.
