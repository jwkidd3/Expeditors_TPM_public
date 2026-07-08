# Competitive Snapshot — Prompt Card

> **Day 4 · Activity 3 handout.** Two safe prompts for the most defensible part of competitive research: structuring information you already have. And the bright line you do not cross.

## The bright line

> AI can summarize and structure source material you provide.
> AI **cannot** tell you what your competitors actually do.

Feed it the two competitor product-tour notes and the public pricing pages. Do not ask it to fill gaps from its training data.

---

## Prompt 1 — "Structure what we know" (safe)

```
Role: Competitive analyst.
Context: I'm pasting in two competitor product tour transcripts (ServiceTitan, Housecall Pro) plus their public pricing pages.
Task: Structure into a comparison matrix.
Constraints:
  - Only use facts from the materials I pasted; do not pull from your training data
  - Flag any cell where the source is silent (do not infer)
Format: Markdown table — Feature / ServiceTitan / Housecall Pro / Source citation
```

## Prompt 2 — "Tell us what's missing" (also safe)

```
Continuing from above. Now: looking at the matrix you just built,
what are the THREE most important questions about these competitors
that the source materials do NOT answer? For each, suggest where a
TPM should look (analyst reports, customer interviews, public earnings calls).
```

---

## What NOT to ask

These will be confidently fabricated:

- "What is ServiceTitan's market share?"
- "Who is the leader in dispatch SaaS?"
- "Cite a study showing dispatcher productivity gains."

> Prompt 2 is the highest-leverage move of the day. Run it every time.
