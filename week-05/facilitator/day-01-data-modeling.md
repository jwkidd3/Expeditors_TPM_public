# Day 1 — Database Structures & Data Logic · Facilitator Guide

> Companion to `labs/day-01-data-modeling.md`. Facilitator-only — do not hand to participants.

## Activity 1 — Read Patterns + Write Patterns

**Cues:**

- "Freshness req. = real-time" is rare. Most B2B features tolerate last-minute. Force quads to defend "real-time" claims.
- If a quad lists writes without invariants, push them: "what would you never want to allow?" That's the invariant.

## Activity 2 — Draft the Entity Model

**Cues:**

- Indexes without an access-pattern reference are speculative. Force the link.
- Watch for entity bloat — fields nobody queries. Ask "which pattern uses this column?" and drop fields that fail.

## Activity 3 — Storage Trade-Offs

**Cues:**

- Trade-offs that don't name an option B are descriptions, not trade-offs. Push for the alternative.
- Vague accepted costs ("complexity") are not load-bearing; force a named query that's intentionally slower.

## Activity 4 — AI-Assisted Schema Critique + Polish

**Cues:**

- Generic AI suggestions ("add a created_at column") usually indicate weak prompts. Coach the Critique-hat pattern with access patterns loaded.
- Adopt-everything signals oracle thinking. Force at least one rejection with reasoning.

## End-of-day reflection prompts

- Which quad's access patterns drove the model most cleanly? Surface as Friday positive example.
- Did anyone design the schema before writing queries? Coach back.
- Did anyone propose a "real-time" freshness requirement without defending it? Most rookie mistake.
- Did the cohort use AI as critic, not oracle?
