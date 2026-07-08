# TCD-Light Template (1.5 pages)

> **Day 3 handout.** The compressed Technical Concept Document — Week-4 architecture work in 1.5 pages. Architecture stance, integration, threat model, SLOs, trade-offs, sign-off. Compression is the discipline: if you go deeper than 1.5 pages, cut.

---

```markdown
# TCD-light — <feature>

## 1. Architecture stance
1 paragraph. Mono / micro / hybrid + the deploy/failure/scale frame.

## 2. Integration map
Table: system / owner / sync-async / R-W / failure handling.

## 3. Threat-model summary
3 highest-priority STRIDE threats + mitigations.

## 4. SLOs (3)
1 latency / 1 availability / 1 rate-limit. Target + defense + verification.

## 5. Top 3 trade-offs
Each: Option A / B / Choice / Cost / Revisit trigger.

## 6. Stakeholder sign-off
3–5 stakeholders + status.
```

---

### Integration map — row shape (§2)

| System | Owner | Sync / Async | R / W | Failure handling |
|---|---|---|---|---|
|   |   |   |   |   |

### Trade-off — row shape (§5)

| Option A | Option B | Choice | Accepted cost | Revisit trigger |
|---|---|---|---|---|
|   |   |   |   |   |

---

### What "good" looks like
- Architecture stance defended in **business terms**, not framework hype. Not "we'll figure it out" — name the starting position.
- Integration map has a **failure-handling stance per row**.
- Threats are specific, each with a mitigation.
- SLOs have defenses tied to **user behavior**.
- Trade-offs have **revisit triggers**.
