# TMD-Light Template (1.5 pages)

> **Day 3 handout.** The compressed Technical Modeling Document — Week-5 modeling work in 1.5 pages. Data model, cloud topology, API contract, sequence, monitoring. Behavior over implementation; a named invariant on the weird path is the senior signal.

---

```markdown
# TMD-light — <feature>

## 1. Data model
3–5 entities with PK + indexes + relationships. 1 storage trade-off.

## 2. Cloud topology
Region / managed vs self / tenancy / network boundary. ROM cost.

## 3. API contract
3–5 endpoints with method / path / status codes / idempotency.

## 4. Sequence
Happy path; 1 sad path; 1 weird path with named invariant.

## 5. Performance baseline + monitoring
3 baselines + 3 alerts + 1 leading indicator.
```

---

### API contract — row shape (Section 3)

| Method | Path | Status codes | Idempotency approach |
|---|---|---|---|
|   |   |   |   |

---

### What "good" looks like
- Data model entities have the **access patterns that drove them** (1 storage trade-off named — often normalize vs denormalize).
- Cloud topology has a **ROM cost number**, even if rough.
- API endpoints have status codes and an idempotency approach.
- The weird path has a **named invariant** (don't skip it).
- Section 3 describes **behavior, not implementation** (no "use Redis" — say what the behavior guarantees).
- The leading indicator is **measurable within 7 days**.
