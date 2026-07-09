# Day 2 — Cloud Architecture & Infrastructure · Facilitator Guide

> Companion to `labs/day-02-cloud-infrastructure.md`. Facilitator-only — do not hand to participants.

## Activity 1 — Region & Availability Zone Choice

**Cues:**

- Multi-region active-active without an outage-cost defense is the expensive rookie call. Coach toward warm-DR as a starting point.
- Single-AZ for production isn't a stance; it's a future incident. Push to at least multi-AZ.

## Activity 2 — Managed vs Self-Managed for Each Component

**Cues:**

- "We want full control" is a smell. Push: "what specific decision do you need to make that the managed service forecloses?"
- If a triad picks self-managed for everything, they're carrying a heavy ops bill. Surface it.

## Activity 3 — Multi-Tenancy + Network Boundary

**Cues:**

- Single-tenant without contractual customer evidence is the classic over-promise; push back.
- Public-internet APIs without a TLS / WAF stance hidden somewhere are incomplete. Coach toward naming the security layer.

## Activity 4 — Cost Awareness + AI Sanity Check

**Cues:**

- Cost numbers more precise than ROM bands are a trap; the goal is surfacing 2x surprises, not finance modeling.
- Egress costs are the surprise that hides; coach triads to name outbound bandwidth as a line item.

## End-of-day reflection prompts

- Which triad's ROM cost was most realistic? Hold up Friday.
- Did anyone pick multi-region active-active without justification? Most rookie expensive choice.
- Did any triad pick self-managed for components that have clear managed equivalents? Coach toward defaults.
- Did anyone treat tenancy as a tech decision rather than a customer-and-cost decision?
