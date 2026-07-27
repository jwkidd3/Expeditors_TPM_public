# Week 5 — Technical Infrastructure & Modeling

> *"The TCD says what the system must respect. The TMD shows what the system actually looks like at a level an engineer can build from."*

Week 5 takes the **Technical Concept Document (TCD)** from Week 4 and goes one level deeper. Each triad produces a **Technical Modeling Document (TMD)** — a sibling artifact that documents:

- The **data model** the feature reads, writes, and indexes
- The **cloud topology** it deploys to
- The **API contract** it presents to callers
- A **system-level technical model** (sequence diagrams) tying it all together
- A **performance baseline + monitoring plan** that lets the team know whether the SLOs from Week 4 are actually being met
- An **AI-summary validation log** — the discipline of checking AI-generated data summaries against the source

By Friday afternoon, every triad has a TMD that an engineering lead would accept as scoping input for sprint planning.

## What's different about Week 5

- **The TCD becomes the spine.** Every section of the TMD references a corresponding TCD section.
- **Technical depth increases.** This is the most engineering-adjacent week. TPMs aren't expected to *make* the choices, but they should be able to read engineering proposals and ask sharp questions.
- **AI use is mature.** The Week-2 prompt patterns and Week-4 AI norms apply. New today: explicit **AI-summary validation** discipline (validating AI's read of *real* data, not just text).

## Learning outcomes

By Friday afternoon, each participant can:

1. Read and reason about a **data model** at the entity level — primary keys, foreign keys, indexes, normalization vs denormalization trade-offs.
2. Frame **cloud topology** decisions (region, availability zones, managed services, multi-tenancy) in customer and cost terms.
3. Author or review a **REST API contract** with sharp resource modeling, idempotency, versioning, and error semantics — and explain when **SOAP** is still the right call.
4. Produce a **sequence diagram** for a feature's happy path that names every hop, every protocol, and every failure handler.
5. Set realistic **performance baselines** anchored to the SLOs from Week 4 and design a **monitoring plan** that surfaces breaches before users do.
6. Validate an AI-generated data summary against source data and produce a **validation log** that documents what was correct, partly correct, and wrong.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | Database structures & data logic | TMD Section 1 — Data model |
| 2 | Cloud architecture & infrastructure | TMD Section 2 — Cloud topology |
| 3 | REST & SOAP API fundamentals | TMD Section 3 — API contract |
| 4 | High-level technical modeling | TMD Section 4 — System sequence + integration model |
| 5 | Performance baselines, monitoring, AI-summary validation | TMD Section 5 + final TMD assembly |

Each day adds a section. Friday assembles the whole document and runs an integration pass — same discipline as the Week-3 PRD assembly and Week-4 TCD assembly.

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

## The TMD template (Friday's deliverable)

```markdown
# Technical Modeling Document — <feature>
**Sibling to:** PRD <link>, TCD <link>
**Authors:** <triad>  |  **Status:** Draft / Reviewed

## 1. Data model
Entity-level model: tables / collections, keys, relationships, indexes.
Storage choices and the trade-offs that drove them. (Day 1)

## 2. Cloud topology
Region / AZ choice, managed services, multi-tenancy stance. (Day 2)

## 3. API contract
Resource design, methods, versioning, idempotency, error semantics.
REST or SOAP — defended choice. (Day 3)

## 4. System sequence model
End-to-end happy-path sequence diagram + 1–2 sad/weird-path
sequences. Names every hop, protocol, and failure handler. (Day 4)

## 5. Performance baselines & monitoring
- Baselines: what we measure today (or expect at launch)
- Targets: from TCD Section 4 SLOs
- Monitoring plan: dashboards, alerts, on-call signal
- AI-summary validation log (this week's AI-assisted summaries
  with their validation status) (Day 5)
```

## Triads

Same triads from Weeks 1–4. PRD authors → TCD authors → TMD authors. By Week 6 these triads will negotiate this work with stakeholders.

## Friday review rubric (TMD)

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| Data model clarity | 20% | Entities, keys, indexes, and trade-offs all named; storage choice defended |
| Cloud topology realism | 15% | Region/AZ stance fits the SLOs; multi-tenancy stance honest |
| API contract sharpness | 20% | Resources are nouns; idempotency, errors, versioning explicit |
| Sequence model completeness | 20% | Happy + sad/weird paths covered; protocols named; failure handlers shown |
| Baselines + monitoring | 15% | Baselines real; monitoring fires before users notice |
| AI-validation discipline | 10% | Validation log distinguishes correct / partly correct / wrong with evidence |

## Bridge to Week 6

Week 6 (Stakeholder Alignment & Negotiation) takes the TCD's Stakeholder Sign-Off Matrix (Section 6) and the TMD's technical decisions and **negotiates** them. Each triad picks one or two constraints to actively negotiate with simulated stakeholders. The TMD's specificity is what makes those negotiations productive — vague briefs produce vague conversations.
