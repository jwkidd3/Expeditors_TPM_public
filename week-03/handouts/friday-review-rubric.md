# Friday Review Rubric

> **Day 5 handout.** Every reviewer scores each PRD on these six weighted dimensions. Score 0–4 per dimension (0 = absent, 4 = exemplary), multiply by weight, sum for a total out of 4.0. Used in both the AM primary review and the PM secondary review.

---

## The six dimensions

| Dimension | Weight | What "exemplary" (4) looks like |
|-----------|:---:|------------------------------|
| **Problem clarity** | 20% | Engineer could scope without a clarifying call |
| **AC testability** | 25% | Each AC implementable + falsifiable; covers happy / sad / weird |
| **NFR completeness** | 20% | All 5 categories present; each has a defended target |
| **Strategy linkage** | 15% | Goals tie to Week-2 NS / KPIs / journey friction |
| **Risk honesty** | 10% | Real risks named; "no risks" is a fail |
| **Writing discipline** | 10% | Clear, specific; no AI-generic prose |

---

## How to score

- Score each dimension **0–4**: 0 = absent, 1 = weak, 2 = partial, 3 = solid, 4 = exemplary.
- Multiply each by its weight, then sum. **Total is out of 4.0.**

**Worked example:**

| Dimension | Score | Weight | Weighted |
|-----------|:---:|:---:|:---:|
| Problem clarity | 3 | 0.20 | 0.60 |
| AC testability | 3 | 0.25 | 0.75 |
| NFR completeness | 2 | 0.20 | 0.40 |
| Strategy linkage | 4 | 0.15 | 0.60 |
| Risk honesty | 3 | 0.10 | 0.30 |
| Writing discipline | 3 | 0.10 | 0.30 |
| **Total** | | | **2.95** |

---

## Verdict bands

| Total | Verdict |
|-------|---------|
| **≥ 3.0** | Ships as-is |
| **2.0 – 2.9** | Ships with named gaps (captured in the resolution log) |
| **< 2.0** | Facilitator intervenes |

---

## Two reviewing principles

- **Score the *PRD*, not the *idea*.** A weak idea can have a strong PRD; a strong idea can have a weak PRD.
- **Specific beats general.** "Section 2 is unclear" is unhelpful; "Section 2 doesn't say *which* dispatchers — small-shop or large-shop — and that changes scope" is a real finding.
