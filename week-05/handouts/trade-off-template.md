# Trade-Off Template

> **Day 1 handout (carried from Week 4).** The standard shape for making a design choice explicit: Option A / Option B / Choice / Why / Accepted cost / Revisit trigger. Use it for schema choices this week — and for every architecture decision after.

Copy this block once per trade-off point in your design.

```markdown
### Trade-off — <name of the choice>

**Tension:** <the two things in tension, e.g. Normalization vs denormalization>

**Option A:** <describe>
**Option B:** <describe>

**Choice:** Option <A/B>.

**Why:** <the reasoning, grounded in access patterns / SLOs / customer facts>

**Accepted cost:** <a specific thing you deliberately can't do
        efficiently now — name the query or scenario>

**Revisit trigger:** <the concrete change that would make you
        reopen this — a frequency change, a new customer, a
        tightened SLO>
```

---

## Three trade-offs every data model encounters

| Trade-off | Tension |
|-----------|---------|
| **Normalization vs denormalization** | Clean writes vs fast reads |
| **Strong consistency vs replica reads** | Always-fresh vs scalable read load |
| **Schema flexibility vs schema integrity** | Easy migration vs caught-by-database integrity |

## What separates a trade-off from a description

- A trade-off **names an Option B**. If there's no alternative, it's a description, not a trade-off.
- "Accepted cost" is a **named query or scenario** you deliberately can't run efficiently — not a vague word like "complexity."
- "Revisit trigger" is a **concrete, observable change** — usually a query-frequency shift or a new class of customer.
- At least one of your trade-offs should reference a **TCD §4 SLO**.
