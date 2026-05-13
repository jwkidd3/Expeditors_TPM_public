# Week 4 — Technical Architecture & Constraints

> *"A TPM doesn't choose the architecture. A TPM names the constraints — clearly, in business terms — that the architecture must respect."*

Week 4 is the technical-thinking week. Each triad takes the **PRD they shipped Friday of Week 3** and treats it as the input to an architectural conversation: monolith vs microservices, security & compliance, system components, latency / availability / rate limits, and the trade-offs that fall out of those decisions.

By Friday, every triad produces a **Technical Constraints Document (TCD)** — a one- to two-page artifact that an architect or engineering lead would accept as scoping input. The TCD is a sibling to the PRD; together they go into Week 5.

## What's different about Week 4

- **AI is restored.** After last week's discipline, AI returns as a research and structuring assistant. The Week 1 / Week 2 prompt patterns are reused; the Week 3 review discipline applies to AI-assisted output.
- **You are not pretending to be an engineer.** The job is to make trade-offs visible and defensible to non-technical stakeholders. The architect makes the call; the TPM ensures the call is made on the right inputs.
- **The PRD's NFR section is a first draft.** Every architectural decision this week tightens, rewrites, or relocates an NFR.

## Learning outcomes

By Friday afternoon, each participant can:

1. Frame a **monolith-vs-microservices** decision in business and operational terms — not in framework hype.
2. Conduct an architecture-level **STRIDE threat-model pass** and translate the results into PRD security NFRs an engineer can scope against.
3. Draw a **C4-style component diagram** (Context + Container) for a feature, naming external dependencies and integration points.
4. Set realistic **SLO targets** (latency, availability, rate limits) anchored to user behavior and business cost, with an **error budget** the team will actually respect.
5. Author a **Technical Constraints Document** that surfaces the top five constraints, names trade-offs explicitly, and ties each to a stakeholder who must approve.

## Daily map

| Day | Topic | Key artifact produced |
|-----|-------|----------------------|
| 1 | Monolith vs Microservices | Architecture stance + integration choice |
| 2 | System security & compliance | STRIDE threat model + revised security NFRs |
| 3 | Mapping high-level system components | C4 Context + Container diagram |
| 4 | Latency, availability, rate limits | SLO sheet + latency budget + rate-limit policy |
| 5 | Technical trade-offs and constraints | **Technical Constraints Document (TCD)** |

Each day's output is a section of the TCD. Friday assembles, peer-reviews, and ships the TCD alongside the PRD.

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

## The TCD template (Friday's deliverable)

```markdown
# Technical Constraints Document — <feature name>
**Sibling to:** PRD <link>  |  **Authors:** <triad>  |  **Status:** Draft / Reviewed

## 1. Architecture stance
Monolith / microservice / hybrid; one paragraph defending the call from
business + operational angles (not framework hype).

## 2. Integration map
Which existing systems / services this feature depends on, calls, or extends.
References the C4 Container diagram (Day 3 artifact).

## 3. Security & compliance constraints
STRIDE pass summary; the 3–5 highest-priority threats and their mitigations.
Updated security and compliance NFRs (replaces the Week-3 first draft).

## 4. SLO + rate-limit policy
- Latency: p50 / p95 / p99 targets, with defenses
- Availability: monthly target + error budget
- Rate limits: per-user / per-tenant / global; what each protects

## 5. Top 5 trade-offs
Each trade-off names: option A, option B, the call we made, the cost we accept,
the trigger that would cause us to revisit.

## 6. Stakeholders + sign-off matrix
| Constraint | Stakeholder | Status (proposed / discussed / approved) |
```

## Triads

Same triads from Weeks 1–3. They authored the PRD; they author the TCD.

## Facilitator pre-flight checklist

- [ ] Confirm every triad's locked Week-3 PRD is accessible Monday morning.
- [ ] Pre-print or share digitally: the **STRIDE Card**, the **C4 Container Skeleton**, the **SLO Worksheet**, the **TCD Template**.
- [ ] **Re-establish AI norms.** Prompt patterns from Week 1 + the provenance-log discipline from Week 2 Day 4 both apply to all AI use this week.
- [ ] Coach yourself on the **most common Week 4 trap**: triads making architecture decisions instead of surfacing trade-offs. Hold the line: the architect decides; the TPM clarifies.

## Friday review rubric (TCD)

| Dimension | Weight | What "exemplary" looks like |
|-----------|--------|------------------------------|
| Stance defensibility | 20% | Architecture call defended in business terms; framework hype absent |
| Threat-model rigor | 20% | 3–5 named threats with concrete mitigations; not boilerplate |
| Component clarity | 15% | C4 diagram is readable; external dependencies named |
| SLO realism | 20% | Targets anchored to user behavior; error budget the team will actually keep |
| Trade-off honesty | 15% | Both sides named; trigger to revisit specified |
| Stakeholder map | 10% | Each constraint has an owner; sign-off status is honest |

## Bridge to Week 5

Week 5 (Technical Infrastructure & Modeling) goes one level deeper: databases, cloud architecture, REST/SOAP APIs, performance baselines, monitoring. The **TCD is the input** — its component map drives Week 5's data-modeling work; its SLOs drive performance-baseline conversations; its threat model drives encryption and key-management decisions.
