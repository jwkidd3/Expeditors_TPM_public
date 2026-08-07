# Day 3 — Mapping High-Level System Components · Facilitator Guide

> Companion to `labs/day-03-system-components.md`. Facilitator-only — do not hand to participants.

## Framing note

Today's job is to draw a **C4-style component diagram** (Context + Container) for each quad's feature — replacing hand-waving with a shared visual vocabulary. By 16:00 every quad should have two diagrams ready to walk through with an architect.

## Activity 1 — Context Diagram

**Cues:**
- If a quad's diagram is just "User → System → Database", they've drawn a Container diagram badly. Push them to surface real external systems.
- If a quad lists 25 boxes, they're drafting a Container diagram inside the Context. Cap them and lift detail to Activity 2.
- The "indirect roles" check is a strong differentiator — Ops VP, compliance, customer success often appear on the Context diagram as readers of audit data.

## Activity 2 — Container Diagram

**Cues:**
- If modular monolith modules get promoted to standalone containers without justification, that contradicts the Day-1 stance. Push back.
- Sync vs async should appear on every arrow. Unlabeled protocol arrows hide consistency and failure-mode bugs.

## Activity 3 — Stress-Test the Diagram

**Cues:**
- A reviewer who just nods isn't engaging the failure lens. Force a named scenario and walk it.
- Trust boundaries that follow team org charts rather than data flow are usually wrong — challenge.

## Activity 4 — AI-Assisted Diagram Critique + Final Polish

**Cues:**
- Generic AI suggestions ("consider scalability") signal weak prompts; coach toward the Role/Context/Constraints/Format pattern.
- Absorbing every AI suggestion is the tell of unexamined use. Force at least one rejection with reasoning.

## Facilitator reflection prompts (end of day)

- Which quad's diagram has the cleanest legend? Hold up Friday.
- Which quad over-detailed the Context (sneaking Container concerns in)? Coach tomorrow.
- Did anyone produce a "Database is part of our system" arrow when the database is actually shared platform infra? That's a trust-boundary error worth surfacing.
- Did the cohort handle AI critique with discipline, or absorb every suggestion?
