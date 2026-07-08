# Sequence-Diagram Elements Card

> **Day 4 handout.** What each element of a sequence diagram represents, and when a sequence diagram is the right (and wrong) tool. Keep it beside you while you draw the happy / sad / weird paths for TMD §4.

A sequence diagram shows **time flowing top to bottom** and **actors as vertical lifelines**. Messages between lifelines are arrows, ordered by time.

## The elements

| Element | What it represents |
|---------|---------------------|
| **Lifeline (vertical line)** | An actor — user, mobile app, service, datastore, queue |
| **Arrow** | A message — usually labeled with the operation + protocol |
| **Solid arrow** | Synchronous call (caller waits) |
| **Dashed arrow** | Async / fire-and-forget |
| **Return arrow** | Response (often dotted) |
| **Note** | Latency budget, condition, or important annotation |
| **Alt / opt block** | Conditional branch ("if 4xx", "if cache hit") |

A good sequence diagram has **5–12 lifelines** (more becomes unreadable) and 10–25 arrows.

---

## Right tool for the job

**Use a sequence diagram for:**
- A specific user action's journey through the system
- The interaction between services / modules during a transaction
- The order in which things happen — and where they could go wrong

**Use a different diagram for:**
- All possible interactions → Container or Component diagram
- Data structure → entity-relationship diagram
- Deployment topology → the cloud topology from §2

## The three sequences every TMD §4 needs

1. **Happy path** — the central success case
2. **One sad path** — the most common user or system error you must handle gracefully
3. **One weird path** — an edge case from your AC's "weird" coverage (network drop, race, timeout, boundary)

Sad and weird paths can be **more abbreviated** than the happy path — they usually diverge from it at a single arrow. Draw from the divergence point.
