# NFR — Failure-Mode Checklist

> **Day 3 · Activity 1 handout.** The five ways NFRs go wrong. Most PRD templates ship with terrible boilerplate NFRs — this is the eye you calibrate before writing your own. Check every NFR against all five.

---

## The five NFR failure modes

| Failure mode | What it looks like | The fix |
|--------------|--------------------|---------|
| **Boilerplate** | "Performance must be acceptable" | Copy-pasted from a template — rewrite for *your* feature and users |
| **Unmeasurable** | "The system shall be highly available" | Attach a number and a condition you can observe at runtime |
| **No defense** | "p95 latency < 100ms" (no rationale — why this number?) | Add the scenario that justifies the target |
| **No verification** | "The system shall be secure" (how would we ever know?) | State how it's tested/observed in pre-prod or production |
| **Wrong category** | A "Performance" NFR that's actually a feature requirement | Ask "what would a Performance test for this look like?" — if there isn't one, recategorize |

> **The sneaky one is Wrong category.** It surfaces only when you ask what a test *in that category* would even look like.
> **The most common one is Boilerplate** — usually the result of "we copied the template." Name it openly.

---

## What a clean NFR has (the four-part shape)

```markdown
### NFR — <short name>
**Category:** Performance / Security / Accessibility / Observability / Compliance
**Requirement:** <specific, measurable target>
**Defense:** <why this number; what scenario justifies it>
**Verification:** <how we test/observe it>
```

---

## Triage pass/fail sheet

| NFR | Boilerplate | Unmeasurable | No defense | No verification | Wrong category | Clean? |
|:--:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | | | | | | |
| 2 | | | | | | |
| 3 | | | | | | |
| 4 | | | | | | |
| 5 | | | | | | |
