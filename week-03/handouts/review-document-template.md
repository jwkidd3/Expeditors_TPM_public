# Review Document Template

> **Day 5 · Activity 1 handout.** The primary-review deliverable. Each reviewing triad fills one of these independently (two reviewing triads per PRD, no coordination). Score with the Friday rubric, then give three strengths, five specific findings, and the questions you'll ask in the clarifying conversation.

---

```markdown
# Review of PRD: <feature name>
**Reviewers:** <reviewer triad>  |  **PRD authors:** <author triad>  |  **Date:** <today>

## Scores (0–4 per dimension)

| Dimension | Score | One-line rationale |
|-----------|-------|--------------------|
| Problem clarity | | |
| AC testability | | |
| NFR completeness | | |
| Strategy linkage | | |
| Risk honesty | | |
| Writing discipline | | |

**Total:** [weighted sum, out of 4.0]

## Top 3 strengths
1. <specific>
2. <specific>
3. <specific>

## Top 5 specific findings (defects, gaps, suggestions)

For each: cite the section / line, name the problem, propose the fix.

1. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

2. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

3. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

4. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

5. **§ ___ — <short label>**
   - What we observed:
   - Why it matters:
   - Suggested fix:

## Open questions for the author triad
> Things we'd ask in the in-person clarifying conversation (Block 2).
```

---

## What good reviewing looks like

- **Specific beats general.** Cite the section. "§2 is unclear" is bad; "§2 doesn't say *which* dispatchers" is good.
- **Suggest a fix.** A reviewer who only finds problems is half-doing the job. If you'd "make it more specific," write the specific version yourself.
- **Three strengths is required** — honest praise builds the trust that lets the harder feedback land.
- **Read order:** §§1–5 first (Problem clarity, Strategy linkage), then §§6–7 (AC testability, NFR completeness), then §§8–11 (Risk honesty, metric/goal consistency, dependency owners).
