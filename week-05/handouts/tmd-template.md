# TMD Template

> **Day 1 handout.** The 5-section Technical Modeling Document (TMD) skeleton your quad builds across Week 5 — the sibling to your PRD and TCD, one level deeper than the TCD. Print it, pin it, fill it section by section. Each section carries a `[Day X]` tag telling you when it gets written. Friday it ships, peer-reviewed.

---

```markdown
# Technical Modeling Document — <feature>
**Sibling to:** PRD <link>, TCD <link>  |  **Authors:** <quad>  |  **Status:** Draft / Reviewed

## 1. Data model                                       [Day 1]
Entity-level model: tables / collections, keys, relationships, indexes.
Storage choices and the trade-offs that drove them.

## 2. Cloud topology                                   [Day 2]
Region / AZ choice, managed services, multi-tenancy stance.
Rough-order-of-magnitude (ROM) cost note.

## 3. API contract                                     [Day 3]
Resource design, methods, versioning, idempotency, error semantics.
REST or SOAP — a defended choice.

## 4. System sequence model                            [Day 4]
End-to-end happy-path sequence diagram + 1–2 sad/weird-path sequences.
Names every hop, protocol, and failure handler. Each sequence traces
back to a PRD acceptance criterion.

## 5. Performance baselines & monitoring               [Day 5]
- Baselines: what we measure today (or expect at launch)
- Targets: pulled from TCD Section 4 SLOs
- Monitoring plan: dashboards, alerts, on-call signal
- AI-summary validation log: this week's AI-assisted summaries with
  their validation status (correct / partly correct / wrong + evidence)
```

---

## How the sections build on each other

- **§1 data model** is the vocabulary the rest of the TMD speaks in — entities named here recur in the API (§3) and the sequences (§4).
- **§3 API contract** is the surface **§4 sequences** exercise; every hop in a sequence is a call defined in §3.
- **§4 sequences** must satisfy the PRD acceptance criteria and stay inside the **§5 / TCD SLO** latency budget — if the sequence sums past the SLO, that's a finding.
- **§5 monitoring** makes the TCD's SLOs *observable* — an SLO with no alert in §5 is an unverifiable promise.

**The bar:** a TMD an engineer could start building from. It ships alongside the PRD and TCD; together they carry into Week 6's stakeholder negotiation.

*Friday review criteria are on the separate `friday-tmd-rubric` handout.*
