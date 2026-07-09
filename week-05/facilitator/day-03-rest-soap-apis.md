# Day 3 — REST & SOAP API Fundamentals · Facilitator Guide

> Companion to `labs/day-03-rest-soap-apis.md`. Facilitator-only — do not hand to participants.

## Activity 1 — Resource Modeling Calibration

**Cues:**

- Another common error: putting query parameters where path parameters belong (or vice versa). Push: "filtering or identifying?"

**Answer key / watch-for:**

- The "share" question is the calibration point. **POST /lists/{id}/shares** (resource) beats **POST /lists/{id}/share** (verb). REST nudges toward nouns, even when actions are involved. Triads will land differently in Step 4 — hold the answer until after they argue; the discussion is the point.

## Activity 2 — Design Your Feature's API

**Cues:**

- Verbs in URLs are the most common rookie error; redirect to noun resources.
- Status codes lumped at 400/500 hide actionable distinctions; push for 409/422/429 where they apply.

## Activity 3 — Idempotency, Versioning, Error Semantics

**Cues:**

- "We don't need versioning yet" defers a cost rather than removing one. Force the strategy choice now.
- Idempotency without a window definition is half-decided; coach toward a stated 24-hour or 7-day key retention.

## Activity 4 — REST vs SOAP + AI Critique

**Cues:**

- "Just in case" SOAP support is gold-plating; force a named partner requirement.
- AI critiques that miss the idempotency conversation suggest the prompt didn't load the contract details; tighten the context.

## End-of-day reflection prompts

- Which triad's resource design was cleanest? Hold up Friday.
- Did anyone use verbs in URLs? Coach back.
- Did anyone skip idempotency? Push — most rookie APIs are accidentally non-idempotent.
- Did the cohort engage with REST principles or just memorize forms? The deeper engagement is the goal.
