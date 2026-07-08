# Entity-Model Template

> **Day 1 handout.** One block per entity. Capture fields, keys, indexes, relationships, and invariants — an engineer should be able to start coding against what you write here.

Copy the block below once per entity. Include both **new** entities you're creating and **existing** entities you read from.

```markdown
## Entity: <Name>

| Field | Type | Notes |
|-------|------|-------|
| id    | UUID | Primary key |
| ...   | ...  | NOT NULL? UNIQUE? FK to ...? |

**Indexes:**
- (field, field) — purpose: query #N from access patterns

**Relationships:**
- belongs_to <Entity> via <fk_field>
- has_many <Entity> via <fk_field>

**Notes / invariants:**
- <invariant, e.g. "A reconcile_event is immutable once created.">
- <enumerated value, e.g. "ticket.status is one of {open, reconciled, voided}.">
```

---

## What "good" looks like

- Each new entity has a **primary key** stated.
- Every index references a **specific access pattern by number** — no speculative indexes.
- **Cardinalities are explicit** — "a Dispatcher has many ReconcileEvents; a ReconcileEvent has one Dispatcher."
- **No surprise columns** — every field has a query that uses it. If you can't name the pattern that reads a column, drop the column.
