# NFR Cross-Review Template

> **Day 3 · Activity 4 handout.** Cross-review another triad's §7, then surface the trade-offs. NFRs interact — several usually pull in opposite directions. A mature NFR section *names* its trade-offs and says how each was resolved. Two halves: the **reviewer worksheet** and the **"Known trade-offs" subsection** the author triad appends.

---

## The four classic NFR trade-offs

| Trade-off | The tension |
|-----------|-------------|
| **Performance vs Observability** | Heavy logging slows the hot path; light logging blinds you when it breaks |
| **Security vs Time-to-first-value** | Strict authZ blocks the new-user happy path |
| **Compliance vs Latency** | EU data-residency requirements add cross-region hops |
| **Accessibility vs Visual polish** | Some animation patterns conflict with reduced-motion / screen readers |

---

## Part 1 — Reviewer worksheet (you review THEIR §7)

For each NFR, judge:

| Their NFR | Defense: specific or boilerplate? | Verification: real or aspirational? | Trades off with which other NFR? |
|-----------|-----------------------------------|-------------------------------------|----------------------------------|
| | | | |
| | | | |
| | | | |

**At least one place where two of their NFRs pull in opposite directions:**

```
NFR ___ (____________) vs NFR ___ (____________):
the tension is ____________________________________
```

---

## Part 2 — "Known trade-offs" subsection (AUTHOR triad appends to §7)

Name at least one explicit tension and how you resolved it — a deferred plan beats a hand-wave.

```markdown
### Known trade-offs (in this section)

- **Audit logging vs latency:** NFR-7 (full event logging) adds ~30ms to the
  hot path tested in NFR-1. We accept this; if hot-path latency becomes the
  bottleneck, we will move logging to async dispatch.
- **Strict RBAC vs onboarding:** NFR-10 (managers cannot view dispatcher
  reconciles in their first week) blocks an onboarding scenario. Resolved:
  managers see a read-only view in week 1; full view in week 2.
```

---

### Also update the review-resolution note

Extend §7's resolution note (adopt / defer / push back) to cover this Day-3 review, same format as the Day-2 note.
