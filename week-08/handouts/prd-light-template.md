# PRD-Light Template (2 pages)

> **Day 2 handout.** The compressed PRD — Week-3 rigor in a fraction of the space. Compression is **selective, not lower-quality**: keep what's load-bearing, cut what's cosmetic. Every word earns its place. Target: 2 pages total, §§1–7.

---

## The compressed PRD covers

| § | Section | Budget |
|---|---|---|
| 1 | Context | ½ page |
| 2 | Problem | ½ page |
| 3 | Goals + non-goals | ½ page |
| 4 | Scope (in / out table) | — |
| 5 | Solution sketch | ½ page |
| 6 | Top 6–8 Acceptance Criteria | — |
| 7 | Top 5 NFRs (one per category) | — |

---

## Compressed persona (feeds §§1–2)

Name the persona before you draft. A compressed persona has 3 fields:

```markdown
**Persona:** <role + segment>
**Job-to-be-done:** <verb-based, in their language>
**Why it's hard today:** <specific friction; quote a real customer if possible>
```

*Example:* **Persona:** New B2B finance ops associate at a 200-person company. **Job-to-be-done:** Close the books each month without staying late on Friday. **Why it's hard today:** "I spend Thursday night chasing 4 different teams for missing accruals — by the time they respond, I've forgotten what I asked."

Rank your top 3 pains on **Severity × Frequency × Addressability.** The pain that survives all three goes in the PRD.

---

## The PRD-light structure

```markdown
# PRD-light — <feature>

## 1. Context   (½ page)
Strategic anchor + at least one customer quote or data point.

## 2. Problem   (½ page)
The persona's specific friction.

## 3. Goals + non-goals   (½ page)
3 goals (user outcomes, not feature names) + 2–3 non-goals.

## 4. Scope
| In | Out |
|----|-----|
|    |     |
Cut aggressively to fit the 4-day window; scope-out should be rich.

## 5. Solution sketch   (½ page)
User-visible flow + key surfaces + hard interactions.
Does NOT specify implementation. Passes the "engineer's first
three questions" test.

## 6. Acceptance Criteria   (6–8 total)
- 3 happy-path ACs
- 2 sad-path ACs
- 1 weird-path AC
Given / When / Then form. Compressed = fewer ACs, not weaker ACs.

## 7. NFRs   (top 5 — one per category)
- 1 Performance (latency target with defense)
- 1 Security (auth/authz approach)
- 1 Accessibility (the WCAG floor)
- 1 Observability (leading indicator from your outcome map)
- 1 Compliance (the regime that applies)
Each uses the Wk-3 template: requirement / defense / verification.
```

---

### What "good" looks like
- §1 fits ½ page and references at least one real customer quote or data point.
- Goals are **outcomes**, not features.
- Non-goals catch the most-likely scope creep.
- §5 does not specify implementation.
- §6 has happy / sad / weird coverage.
- §7 has all 5 categories represented.
- The whole document fits **2 pages**.
