# Day 4 — High-Level Technical Modeling · Facilitator Guide

> Companion to `labs/day-04-technical-modeling.md`. Facilitator-only — do not hand to participants.

## Activity 1 — Happy-Path Sequence

**Cues:**

- If a quad's diagram has more than 12 lifelines, push them: "is anything here repeating? can two be merged?"
- If a quad omits the audit publish, surface it — that's a typical compliance miss.
- The total-latency annotation at the bottom is the consistency check with TCD Section 4.

## Activity 2 — Sad-Path Sequence

**Cues:**

- Sad paths that end in a generic 500 hide error semantics. Push to the specific 4xx code from TMD Section 3.
- Recovery paths that read "user gets frustrated" are dead-ends; force a recoverable action.

## Activity 2B — Solo Sequence Drill *(ad hoc)*

**Cues:**

- This is a **fluency + coverage** block — the goal is that *everyone* can draw one, not a quad deliverable. Walk the room during the drill.
- The tell that someone can't yet draw a sequence is a **flowchart** (boxes + decision diamonds) instead of lifelines + time flowing down. Redirect to lifelines.
- Enforce **distinct flows** — if multiple members draw the same sad path, you've lost the coverage benefit. Assign if needed.
- No answer key (flows vary). Check for: named protocols, a failure handler on every external/async call, and a latency sum checked against the SLO.
- **Timing / lunch tie-in:** run this as the last block before lunch. Because it's solo, it flexes across the break — start ~40 min before lunch and let people carry it over at their own pace, then reconvene after. If the day runs tight, take the 40 min from Activity 4's AI critique rather than the quad sequence work. Flag the choice at the opening.

## Activity 3 — Weird-Path Sequence

**Cues:**

- Quads who cannot state the invariant haven't designed the weird path. Push for the explicit promise.
- Diagrams that grow longer than the happy path usually re-state shared steps; coach toward the divergence.

## Activity 4 — Cross-Review + AI Sequence Critique

**Cues:**

- Generic AI findings ("add error handling") signal weak prompts. Coach the Critique-hat pattern with diagram text loaded.
- Reviews that pass everything are calibrated low. Force at least one named gap per pair.

## End-of-day reflection prompts

- Which quad's invariant was the most useful? Surface as Friday positive.
- Did anyone forget the audit publish in the happy path? Common compliance miss.
- Did anyone produce 25-lifeline mega-diagrams? Coach toward simplification.
- Did the AI surface a weird path the cohort hadn't considered? That's the most useful kind of finding.
