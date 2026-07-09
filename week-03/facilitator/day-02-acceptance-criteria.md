# Day 2 — Writing Granular Acceptance Criteria · Facilitator Guide

> Companion to `labs/day-02-acceptance-criteria.md`. Facilitator-only — do not hand to participants.

## Activity 1 — AC Triage

**Cues:**
- The "Restating the goal" failure is the trickiest — surfaces only when you ask "could this be tested without running A/B against the metric?"
- Every triad will have at least one over-confident "this is clean" call. Use that for shared learning.

**Answer key / watch-for (the 5 sample triage items in the student pack):**

1. `Given the user is logged in, When they reach the dashboard, Then it loads quickly.` — **Vague** ("quickly").
2. `Given a dispatcher with 3+ open tickets, When they tap "Reconcile all", Then the modal opens with all 3 tickets pre-selected and shows the count "3 selected" in the header.` — **Clean** — happy path.
3. `Given any user, When they use the system, Then they should feel productive.` — **Untestable**.
4. `Given a network drop, When the user submits the form, Then the data is queued via WebSocket retry mechanism.` — **Implementation-prescriptive**.
5. `Given a duplicate ticket, When the API receives it, Then 409 Conflict is returned with the original ticket ID in the body.` — **Clean** — weird path.

(The full instructor AC Triage Pack has 12 items; the above are the five printed in the student packet. Some pack items carry multiple failures.)

## Activity 2 — Happy-Path AC for Your PRD

**Cues:**
- If a triad pools drafts before doing solo work, push them back to solo. Solo first produces specificity.
- AND-soup in the Then clause is the most common drift; coach toward splitting into multiple AC.

## Activity 3 — Sad-Path and Weird-Path AC

**Cues:**
- Triads who can't generate weird-path AC haven't engaged with the system reality. Push with named scenarios — network drop, race, timeout.
- Watch for sad-path AC that are happy-path in disguise (the "successful error" pattern); the recovery must be observable.

## Activity 4 — AC Cross-Review

**Cues:**
- A reviewer who writes "this could be more specific" is unhelpful. Push them to write the rewritten AC themselves.
- A reviewer who finds a missing weird-path AC is gold. Surface that pair publicly.
- Watch for "we already considered that" pushback from authors — it should be in the resolution note, with a reason.

## Facilitator reflection prompts (end of day)

- Which triad over-indexed on happy path? They need a weird-path push tomorrow.
- Which triad's AC are most implementation-prescriptive? Coach them privately — old habits.
- Did anyone use AI? Privately and directly intercept; restate the rule.
