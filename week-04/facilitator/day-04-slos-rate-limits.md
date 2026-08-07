# Day 4 — Targeting Latency, Availability, and Rate Limits · Facilitator Guide

> Companion to `labs/day-04-slos-rate-limits.md`. Facilitator-only — do not hand to participants.

## Framing note

Today's job is to set realistic **SLO targets** anchored to user behavior, calculate a **per-hop latency budget**, and design a **rate-limit policy** the team will actually defend. TCD Section 4 is the output.

## Activity 1 — SLO Triage

**Cues:**
- The "average" trap is the most under-detected. Push: "if half your users see 100ms and half see 5s, the average is 2.55s — but your experience is bimodal, not 'OK on average'."
- The "99.99%" trap: ask "what's the team's on-call coverage?" 99.99% requires multi-region active-active and 24/7 on-call — usually not realistic for early features.

**Answer key / watch-for (failure mode → worked example):**
Each failure mode in the triage pack maps to a canonical example. Use these to seed the discussion and confirm quads spotted the right defect:

| Failure mode | Example statement |
|--------------|-------------------|
| **No measurement window** | "p95 < 400ms" (over what period? always? best case?) |
| **No percentile (or "average")** | "Average response time < 500ms" — averages hide bimodal distributions |
| **No defense** | "99.9% availability" with no rationale |
| **Aspirational beyond capability** | "99.99% availability" for a 2-engineer feature on shared infra |
| **Mismatched to user threshold** | "p95 < 5s" for a typing-feedback feature |
| **Confusion with SLA** | "We commit to 99.99% availability" (this is a contractual claim) |

The most subtle failure to call out in readout is usually the **average** trap (looks quantified, hides a bimodal distribution) or the **SLA-confusion** trap (looks like a fine target but is actually a contractual commitment).

## Activity 2 — Set Your Three SLOs

**Cues:**
- 99.99% availability without 24/7 on-call evidence is aspirational. Coach toward 99.5% or 99.9% as defensible defaults.
- Rate-limit policies without a named 429 / backoff response are half-finished; force the failure-mode column.

## Activity 3 — Latency Budget Walk

**Cues:**
- Many quads will under-estimate the **synchronous external call**. Push them to look up real numbers if available.
- The "Tickets module dominates" finding is the kind of insight that drives architecture conversations — celebrate it.
- If the math doesn't fit, the **wider-percentile** option is the most-overlooked. Don't go to p99 if you have no instrumentation; p95 is usually fine for B2B SaaS.

## Activity 4 — Cross-Review + AI Sanity Check

**Cues:**
- Error-budget consequences phrased as "we'll be careful" don't change behavior. Force a concrete action like a feature-freeze trigger.
- Quads that adopt every AI suggestion didn't critique; force at least one rejection with reasoning.

## Facilitator reflection prompts (end of day)

- Which quad's latency-budget walk surfaced a real architectural risk? Surface as Friday positive.
- Which quad set 99.99% without justification? Coach Friday morning before the TCD assembly.
- Did anyone confuse SLO with SLA? Common; correct it explicitly.
- Did the cohort use AI as critic or as oracle? Today is a strong signal.
