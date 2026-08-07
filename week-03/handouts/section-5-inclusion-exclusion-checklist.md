# Section 5 Solution Sketch — Inclusion / Exclusion Checklist

> **Day 1 · Activity 4 handout.** Section 5 is the most-mis-written PRD section. Describe the solution *just enough* for an engineer to imagine its shape — not so much that you've designed it for them. Use this checklist while drafting, then run the "engineer's first three questions" test.

---

## ✅ What goes IN Section 5

- [ ] The **user-visible flow** — 4–8 steps from the user's perspective.
- [ ] The **key surfaces** affected (which screens, which surfaces).
- [ ] The **hard interactions** with other systems (other products, APIs, third parties — name them).
- [ ] A **happy-path narrative** — one paragraph describing what a successful run looks like.
- [ ] *(Optional, encouraged)* 1–2 simple sketches or wireframes.

## ❌ What stays OUT of Section 5

- [ ] Database schema decisions
- [ ] Specific API contracts
- [ ] Class names, framework choices, library picks
- [ ] Pixel-level layout

---

## The "engineer's first three questions" test

After writing Section 5, each quad member proposes the **first three questions** an engineer would ask after reading it. Then diagnose:

| If the questions are about… | Your Section 5 is… | Do this |
|-----------------------------|-------------|---------|
| Implementation choice (which DB? which framework?) | **Over-specified** — you've designed it for them | Pull back; leave room for engineering judgment |
| User behavior or scope (what if the user does X? is Y in scope?) | Correctly specified | Good — those are the right questions |
| Basic mechanics ("what does this even do?") | **Under-specified** | Add the missing flow step or surface |

> **Common failure mode:** most over-specifications come from PMs who used to be engineers. If your three questions are all implementation questions, you've over-specified — cut back.

---

## Quad three-questions capture

| Member | Q1 | Q2 | Q3 | Over / under / OK? |
|--------|----|----|----|--------------------|
| | | | | |
| | | | | |
| | | | | |
