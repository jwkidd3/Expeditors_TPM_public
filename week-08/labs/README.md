# Week 8 — AI Spec Development & Capstone

> *"Eight weeks of muscle. Five days of proof."*

Week 8 is the capstone. Every quad works the same **capstone subject** — the **Holocron** enterprise string-management problem, supplied as a problem brief at the end of Week 7 — and produces a compressed-but-complete artifact set, anchored on the new technique introduced this week: **AI Spec Development** — using AI to draft the integrated technical spec that ties PRD / TCD / TMD outputs together, with full validation discipline.

Friday is **final artifact presentations**. The cohort + instructors score on a rubric that touches every muscle from Weeks 1–7.

## What's different about Week 8

- **The subject is fixed: Holocron.** Every quad gets the same problem brief and writes its own requirements from it — nothing is pre-specified.
- **Compression.** The 5-artifact set produced over Weeks 3–7 gets re-produced in **one week** for the new subject. This tests whether the muscles transfer.
- **AI Spec Development is new.** Day 1 introduces the technique; Day 3 applies it.
- **Friday is presentations.** Each quad has 15 minutes + 5 min Q&A.
- **The tone is summative, not introductory.** This week shows whether the academy worked.

## Learning outcomes

By Friday afternoon, each participant can:

1. Apply the **AI Spec Development pattern** — a structured prompt sequence that produces an engineering-ready integrated technical spec, with explicit validation against the PRD/TCD/TMD inputs.
2. Re-produce the artifact set (PRD-light / TCD-light / TMD-light / SEP-light / DP-light) for the capstone subject in **5 days**, applying the muscles built across Weeks 1–7 end-to-end.
3. Run **technical logic validation** — checking metric coherence, architectural consistency, data-API alignment, and trade-off honesty across the artifact set before shipping.
4. Present the integrated artifact set in a **15-minute readout** that lands with both engineering and business audiences.
5. Reflect on the **8-week arc** — what stuck, what to deepen, what habits to keep.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | AI Spec Development | AI Spec template + Holocron scope slice locked |
| 2 | Capstone discovery + compressed PRD | Capstone PRD-light |
| 3 | Capstone architecture + AI Spec drafted | TCD-light + TMD-light + AI Spec v1 |
| 4 | Technical logic validation + finalization | Validated, integrated capstone artifact set |
| 5 | Final artifact presentations + course closure | Presented capstone; course complete |

## Daily cadence (Mon–Thu — Friday differs)

| Clock | Block | Mix |
|-------|-------|-----|
| 09:00 – 09:15 | Opening & objectives | Instructor |
| 09:15 – 10:30 | Teaching Block 1 + Activity 1 | ~25 min teach / 45 min quad work |
| 10:30 – 10:45 | **Break** | |
| 10:45 – 12:00 | Teaching Block 2 + Activity 2 | ~25 min teach / 50 min quad work |
| 12:00 – 13:00 | **Lunch** | |
| 13:00 – 14:15 | Teaching Block 3 + Activity 3 | ~25 min teach / 50 min quad work |
| 14:15 – 14:30 | **Break** | |
| 14:30 – 16:00 | Teaching Block 4 + Activity 4 + Wrap | ~25 min teach / 55 min quad / 10 min wrap |

### Friday cadence (presentations)

For 4 quads, Friday is structured as (each quad: 15 min present + 5 min Q&A):

| Clock | Block | What happens |
|-------|-------|--------------|
| 09:00 – 09:30 | Opening; presentation order; rubric; final tweaks | Instructor + quads |
| 09:30 – 10:30 | **Quad 1 + Quad 2 presentations** (20 min each + ~10 min flex) | Cohort scores |
| 10:30 – 10:45 | Break | |
| 10:45 – 11:45 | **Quad 3 + Quad 4 presentations** | |
| 11:45 – 12:15 | Cohort debrief / scoring reconcile | What worked; what to deepen |
| 12:15 – 13:15 | Lunch | |
| 13:15 – 15:00 | Course closure: post-assessments (PM + Data Literacy), certificates | Instructor-led |
| 15:00 – 16:00 | Cohort retrospective + send-off | |

If the cohort is smaller, Friday compresses; if larger, the morning extends and break shifts.

## The capstone artifact set (compressed)

Each quad ships a **compressed but complete** version of the 5-week artifact set:

```
capstone/
├── PRD-light.md          (sections 1–5 + 6 AC + 7 NFR — shorter than the 11-section Week-3 version)
├── TCD-light.md          (stance + integration + threat-model summary + SLOs + top trade-offs)
├── TMD-light.md          (data + cloud + API + sequence + baselines)
├── SEP-light.md          (stakeholder map + 1 trade-off brief + simulated negotiation outcome)
├── DP-light.md           (outcome map + backlog skeleton + tracking + 1 experiment)
└── AI-Spec.md            (NEW THIS WEEK — integrated engineering-ready spec)
```

Compression is the constraint. Every artifact must fit on **2 pages** or less. The discipline is **what to cut**, not what to add.

## Quads

Same quads from Weeks 1–7. The PRD authors → TCD authors → TMD authors → SEP authors → DP authors → AI-Spec authors → presenters.

## Friday presentation rubric

Each quad's 15-min presentation is scored on:

| Dimension | Weight | Exemplary |
|-----------|--------|-----------|
| **Customer + problem clarity** | 15% | Engineer or stakeholder could understand the customer's pain in 90 seconds |
| **Integrated artifact set** | 15% | All 6 artifacts referenced; references are consistent |
| **AI Spec quality** | 20% | Engineering-ready; integrates PRD/TCD/TMD outputs; provenance log included |
| **Trade-off honesty** | 15% | At least 2 trade-offs named with cost + revisit trigger |
| **Outcome thinking** | 10% | NS / Tier-Sheet / leading indicator vocabulary used naturally |
| **Delivery readiness** | 10% | DP-light shows backlog, tracking, one bottleneck experiment |
| **Presentation craft** | 15% | All quad voices speak; time-managed; questions answered with curiosity not defensiveness |

## Bridge — what closes when the academy closes

- Post-assessments (Product Management + Data Literacy) administered after presentations
- Each participant declares **two muscles to keep deepening** in their next role
- Each participant declares **one habit to retire**
- Cohort retrospective captures patterns for the next academy cohort
