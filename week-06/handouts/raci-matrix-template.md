# RACI Definitions + Matrix Template

> **Day 1 · Activity 3 handout.** Assign each stakeholder a role for the five most consequential decisions on your feature. The discipline: exactly one **A** per decision.

---

## The four letters

| Letter | Role | Definition |
|--------|------|------------|
| **R** | Responsible | Does the work. There can be many R's. |
| **A** | Accountable | Owns the outcome. **Exactly one** person per decision. |
| **C** | Consulted | Two-way conversation; opinion sought before the call. |
| **I** | Informed | One-way notification; outcome shared after the call. |

**The core discipline: one A per decision.** If two people are A, neither is. If no one is A, the decision will rot.

## The five decisions to assign

For most features, RACI these five:

1. **Scope** — what's in vs out
2. **Architecture** — TCD §1 stance + key trade-offs
3. **SLO targets** — TCD §4
4. **Launch date** — when it ships
5. **Out-of-scope follow-up backlog** — deferred items + owners

## Matrix template

Fill one row per decision. Multiple R / C / I are fine; **one A only**.

```markdown
| Decision                | R | A | C | I |
|-------------------------|---|---|---|---|
| Scope                   |   |   |   |   |
| Architecture            |   |   |   |   |
| SLO targets             |   |   |   |   |
| Launch date             |   |   |   |   |
| OOS backlog ownership   |   |   |   |   |
```

## Worked example — FieldPulse "End-of-Day Reconcile"

```markdown
| Decision              | R          | A           | C                                    | I                  |
|-----------------------|------------|-------------|--------------------------------------|--------------------|
| Scope                 | TPM (you)  | PM Director | Eng Lead, Architect, Customer Success | Sales, Support     |
| Architecture          | Architect  | Eng Director| TPM, Security, Platform              | All eng            |
| SLO targets           | Eng Lead   | TPM         | SREs, Customer Success               | Eng Director       |
| Launch date           | TPM        | PM Director | Eng Lead, Customer Success, Marketing | All eng, Sales     |
| OOS backlog ownership | TPM        | TPM         | Eng Lead                             | Backlog readers    |
```

## Four checks before you're done

1. **No two A's** — walk every column; verify exactly one A per decision.
2. **Is the A actually empowered?** — for each A, confirm they have the authority (formal + informal) to make the call. Many nominal A's are rubber stamps; the real A is upstream.
3. **Anyone surprised to be an I?** — a stakeholder often gets I when they think they're C. Surface it and decide.
4. **"We're all R" is a smell** — it usually means responsibility is unclear. Push for specificity.

> **Common error:** the TPM writing "I'll be A" on architecture. TPMs are usually **C** on architecture, with the Architect as **R** and the Eng Director as **A**.
