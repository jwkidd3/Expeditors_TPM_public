# Week 7 — Agile Delivery & ADO Mastery

> *"A PRD without a delivery plan is a wish. A delivery plan without outcome tracking is busywork. The TPM job is to keep both honest."*

Week 7 takes the negotiated commitments from Week 6 and turns them into **deliverable work**: backlog items in Azure DevOps, sprint plans, outcome metrics, and a value stream the team can actually inspect.

By Friday afternoon, every triad ships a **Delivery Plan (DP)** — the fifth and final sibling artifact alongside PRD / TCD / TMD / SEP. The DP includes the loaded ADO backlog, the outcome-tracking plan, the value stream map, and the bottleneck-removal plan.

## What's different about Week 7

- **Hands-on tooling.** Day 2 is an ADO workshop — triads load their feature into a real (or sandboxed) ADO instance.
- **Outcome ≠ output.** Day 3 explicitly distinguishes "we shipped X" (output) from "the customer is winning" (outcome). Most teams confuse these.
- **Lean foundations.** Days 4–5 introduce value stream mapping and bottleneck-identification — practices that travel beyond software.
- **AI is restored as a delivery aid** — for instance, summarizing standup updates, drafting release notes, surfacing patterns in cycle time.

## Learning outcomes

By Friday afternoon, each participant can:

1. State the **product delivery outcomes** their feature is meant to produce, in user terms — and distinguish them from outputs.
2. Apply the **Agile Manifesto values** as a decision-making aid in real product trade-offs (not as ceremony).
3. Use **Azure DevOps** to load a feature: Epic → Feature → User Story → Task hierarchy; field discipline; basic queries; reading flow charts.
4. Build a **tracking plan** that pairs each output with an outcome metric, with leading indicators that surface failure early.
5. Construct a **value stream map** for the feature's delivery — from idea through value-realized — naming each step's lead time, process time, and flow efficiency.
6. **Identify and design experiments to remove** the top 2–3 delivery bottlenecks.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | Delivery outcomes + Agile principles | DP Section 1 — Outcome map |
| 2 | ADO Usage (hands-on workshop) | DP Section 2 — Loaded ADO backlog |
| 3 | Outcome-based vs output-based tracking | DP Section 3 — Tracking plan |
| 4 | Lean delivery + value stream mapping | DP Section 4 — Value stream map |
| 5 | Identifying & removing bottlenecks | DP Section 5 — Bottleneck removal experiments + DP integration |

## Daily cadence (applies all five days)

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

## The DP template

```markdown
# Delivery Plan — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>, SEP <link>
**Authors:** <triad>  |  **Status:** Draft / Reviewed

## 1. Outcome map
What customer-visible / business outcomes this feature is meant
to produce, tied to NS / Tier Sheet metrics.

## 2. ADO backlog (loaded)
- Epic: <link>
- Features: <links>
- User Stories: <links>
- Tasks: <links>
Hierarchy + tags + iteration paths populated.

## 3. Tracking plan
Output / Outcome / Leading indicator triples per feature.
Sprint cadence, dashboards, alerts.

## 4. Value stream map
End-to-end flow: idea → discovery → spec → build → ship → measure → iterate.
Per step: lead time, process time, flow efficiency, queue.

## 5. Bottleneck removal
Top 2–3 bottlenecks identified with evidence + experiments to test
removal. Each experiment: hypothesis, test, success criterion.
```

## Triads

Same triads from Weeks 1–6. PRD authors → TCD authors → TMD authors → SEP authors → DP authors.

## Friday review rubric (DP)

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| Outcome clarity | 20% | Outcomes are user-visible; tied to NS / Tier Sheet |
| ADO discipline | 15% | Hierarchy, fields, tags, iterations all populated; queries work |
| Output ↔ outcome pairing | 20% | Each output has an outcome AND a leading indicator |
| Value stream realism | 20% | Lead times measured (or honestly estimated); queues named |
| Bottleneck experiments | 15% | Each has hypothesis, test, success criterion |
| Integration with prior artifacts | 10% | DP references PRD/TCD/TMD/SEP appropriately |

## Bridge to Week 8

Week 8 (AI Spec Development & Capstone) is the capstone. Each triad picks a capstone subject (FieldPulse or a real project of their own) and produces an integrated artifact set. The DP from Week 7 is the **delivery template** the capstone instance will follow. Week 8's "AI Spec Development" topic gets explicit treatment — using AI to draft technical specs that integrate with the PRD/TCD/TMD/SEP/DP artifact set built across Weeks 3–7.
