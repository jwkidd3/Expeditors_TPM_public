# Day 3 — Documenting Non-Functional Requirements · Facilitator Guide

> Companion to `labs/day-03-nfrs.md`. Facilitator-only — do not hand to participants.

## Activity 1 — NFR Triage

**Cues:**
- Boilerplate NFRs are usually the result of "we copied the template" — surface this openly.
- The "wrong category" failure is sneaky — surfaces only when you ask "what would a Performance test for this look like?"

**Answer key / watch-for:** The 10-item NFR Triage Pack maps each example to one (or more) of the five failure modes printed in the student packet — Boilerplate, Unmeasurable, No defense, No verification, Wrong category. Only a few items are clean; most carry at least one failure. When triads mark an item "clean," pressure-test it against the "what would the test look like?" question before accepting the call.

## Activity 2 — Performance + Observability NFRs

**Cues:**
- "Average" latency targets get pushed to p95 — average lies in bimodal distributions.
- If observability NFRs don't reference the Tier Sheet signals, the triad is observability-theater; redirect.

## Activity 3 — Security + Accessibility + Compliance

**Cues:**
- "Security: the system shall be secure" gets a hard "no" — push for specifics.
- If a triad has no compliance NFR — ask: "If a regulator audited this feature, what would they ask?" That answer is the NFR.
- A11y is the most-skipped. If a triad omits it, redirect to Week 2 Day 3 work.

## Activity 4 — NFR Cross-Review + Trade-Off Discussion

**Cues:**
- Triads who claim "no trade-offs" haven't read their own NFRs hard enough; surface one for them.
- The most useful trade-off is one resolved with a deferred plan, not a hand-wave; coach toward specificity.

## Facilitator reflection prompts (end of day)

- Which triad's defenses were strongest? Hold up Friday as positive example.
- Which triad has the most boilerplate? Coach privately tomorrow morning.
- Did anyone skip Compliance? Probably yes. Surface tomorrow.
- Did anyone use AI? Last day to course-correct.
