# Week 6 — Stakeholder Alignment & Negotiation

> *"Every artifact you've produced — PRD, TCD, TMD — is a starting position. This week you negotiate it into a shipping position."*

Week 6 takes the documents from Weeks 3–5 and uses them as **inputs to real conversations**. The TCD §6 stakeholder sign-off matrix becomes the negotiation list. The TMD's trade-offs become the things you have to explain. The PRD's scope becomes the thing you have to defend.

By Friday afternoon, every triad has run **three simulated negotiations** with cohort members playing stakeholders, has logged outcomes, and ships a **Stakeholder Engagement Plan (SEP)** — the fourth and final sibling artifact alongside PRD / TCD / TMD.

## What's different about Week 6

- **It's outward-facing.** Earlier weeks were authoring weeks; this week is conversation.
- **Friday is simulation-heavy** — small-group breakouts, role plays, multi-round negotiations.
- **AI returns as meeting-prep tool** (Day 4) — not as a replacement for human judgment.
- **Every artifact across Weeks 3–5 is in scope** — stakeholders may push on data, architecture, SLOs, scope, or anything else.

## Learning outcomes

By Friday afternoon, each participant can:

1. **Map** the stakeholders for a feature using a Power × Interest grid + a RACI assignment, distinguishing decision-makers from approvers from informees.
2. **Plan engagement** per stakeholder — frequency, format, what they need from us, what we need from them.
3. **Translate** a technical trade-off (from TCD or TMD) into a 1-page brief a non-technical executive can act on.
4. **Use AI** to prepare for a stakeholder meeting: summarize prior context, predict objections, draft an opening — with explicit validation.
5. **Negotiate** scope / time / quality / resources in a structured exchange and capture the outcome in a way the team can act on.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | Identifying & mapping stakeholders | SEP §1 — Stakeholder map (Power × Interest, RACI) |
| 2 | Managing engagement for outcomes | SEP §2 — Engagement plan |
| 3 | Communicating technical trade-offs | SEP §3 — One-page trade-off brief |
| 4 | AI-augmented requirement summaries | SEP §4 — Meeting prep + objection map |
| 5 | Negotiating priorities & roadmaps | SEP §5 — Negotiation outcomes log (3 simulated rounds) |

The SEP ships Friday alongside the PRD, TCD, and TMD.

## Daily cadence

| Clock | Block | Mix |
|-------|-------|-----|
| 09:00 – 09:15 | Opening & objectives | Instructor |
| 09:15 – 10:30 | Teaching Block 1 + Activity 1 | ~25 min teach / 50 min triad work |
| 10:30 – 10:45 | **Break** | |
| 10:45 – 12:00 | Teaching Block 2 + Activity 2 | ~25 min teach / 50 min triad work |
| 12:00 – 13:00 | **Lunch** | |
| 13:00 – 14:15 | Teaching Block 3 + Activity 3 | ~25 min teach / 50 min triad work |
| 14:15 – 14:30 | **Break** | |
| 14:30 – 16:00 | Teaching Block 4 + Activity 4 + Wrap | ~25 min teach / 45 min triad / 20 min wrap |

### Friday cadence (negotiation simulation)

Friday's blocks are simulation-heavy:

| Clock | Block | What happens |
|-------|-------|--------------|
| 09:00 – 09:15 | Opening; sim pairings posted | Triads + their counterpart triads (playing stakeholders) named |
| 09:15 – 10:45 | **Round 1: Architecture / SLO negotiation** | Triad negotiates one TCD §4 SLO or §5 trade-off |
| 10:45 – 11:00 | Break | |
| 11:00 – 12:00 | Round 1 debrief + Round 2 prep | Role-swap; capture outcomes |
| 12:00 – 13:00 | Lunch | |
| 13:00 – 14:30 | **Round 2: Scope negotiation** | Triad negotiates a non-goal challenge or scope-creep ask |
| 14:30 – 14:45 | Break | |
| 14:45 – 15:45 | **Round 3: Resource / timeline negotiation** | Cross-team dependency or roadmap ask |
| 15:45 – 16:00 | Wrap + sign-off | SEP §5 outcomes log finalized |

## The SEP template

```markdown
# Stakeholder Engagement Plan — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>
**Authors:** <triad>  |  **Status:** Draft / Reviewed

## 1. Stakeholder map
Power × Interest grid + RACI for the feature. Pulls from TCD §6
sign-off matrix.

## 2. Engagement plan
Per stakeholder: cadence, format, what they need from us,
what we need from them.

## 3. Trade-off translation brief
One TCD/TMD trade-off, translated to one page for a non-technical
executive. Includes: business framing, options, recommendation,
the call you need from them.

## 4. Meeting-prep + objection map
Prior context (AI-summarized + validated), predicted top objections,
opening you'd lead with, the non-negotiables.

## 5. Negotiation outcomes log
For each simulated round: the ask, the response, the agreement
(or disagreement), the next step.
```

## Triads

Same triads from Weeks 1–5. Friday's simulations pair triads as **author** + **stakeholder** — triads play each other's stakeholders, swapping roles round to round.

## Facilitator pre-flight checklist

- [ ] Confirm every triad has accessible PRD + TCD + TMD Monday morning.
- [ ] Pre-print or share digitally: **Power/Interest Grid** (Day 1), **RACI Worksheet** (Day 1), **Engagement Plan Template** (Day 2), **One-Page Brief Template** (Day 3), **Meeting Prep Template** (Day 4), **Negotiation Outcomes Log** (Day 5).
- [ ] Build **stakeholder personas** for Friday's simulation. Suggested set: Operations VP, Architect, Security Lead, Eng Director, Customer Success Lead, CFO.
- [ ] Review the **Friday simulation rubric**.
- [ ] Coach yourself on the **most common Week 6 trap**: triads who treat the stakeholder map as an org-chart exercise rather than a negotiation tool. The map is **the input** to the conversations, not the deliverable.

## Friday simulation rubric

For each negotiation round, both sides score on:

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| Listened first | 20% | Restated stakeholder's concern accurately before responding |
| Translated tech to business | 20% | No unexplained jargon; framed cost in business terms |
| Held the line where it mattered | 15% | Did not surrender constraints under social pressure without rationale |
| Found the trade space | 20% | Surfaced what could move (scope, time, quality, resources) |
| Captured the outcome | 15% | Specific, written, with owner + next step |
| Body / pacing / closure | 10% | Conversation reached a decision (or explicit deferral) |

## Bridge to Week 7

Week 7 (Agile Delivery & ADO Mastery) takes the negotiated commitments into delivery. The SEP §5 outcomes log becomes the **input to sprint planning**. Constraints that survived negotiation become the work; deferred items become the backlog; rejected asks get a documented "no" with reasoning.
