# Day 5 — Technical Trade-Offs & Constraints (TCD Assembly + Review) · Facilitator Guide

> Companion to `labs/day-05-tradeoffs-tcd.md`. Facilitator-only — do not hand to participants.

## Framing note

Today's job is to name the **top 5 trade-offs** (TCD Section 5), build the **stakeholder sign-off matrix** (Section 6), assemble the integrated TCD, peer-review it, and ship it as the sibling artifact to the PRD.

## Activity 1 — Surface the Trade-Offs

**Cues:**
- Strawman alternatives ("the other option was obviously worse") signal under-thinking. Push for a real Option B.
- All-one-category lists usually missed real tensions; mix coupling, consistency, latency, speed, or generality.

## Activity 2 — Write the Top 5 Trade-Offs

**Cues:**
- A trade-off that ends "we chose A because A is better" with no actual reasoning — push back. Force the cost and trigger.
- Watch for "we accept complexity" — that's vague. What complexity? What does it cost in maintenance, debugging, on-call?
- Trade-offs that align suspiciously well with personal preference are a smell. The reasoning should come from the system, not from "I like X better."

## Activity 3 — Stakeholder Sign-Off Matrix

**Cues:**
- "TBD" stakeholders signal an unowned constraint that will slip. Force a real name even if it's the architect placeholder.
- Matrices that overstate status ("Approved" without evidence) become Week 6 surprises; coach toward honesty.

## Activity 4 — Integration + Cross-Review + Sign-Off

**Cues:**
- Watch for "Approved" without an honest gap list. The rubric should set the bar, not the quad's confidence.
- Reviewers who score generously should be calibrated against the rubric mid-block.

## Facilitator wrap (15 min, end of day)

- Read aloud one trade-off from each quad's TCD that the cohort should learn from.
- Surface the **most common pattern of trade-off avoidance** the cohort exhibited (this is a Week 5 + 6 coaching theme).
- Preview Week 5: TCD becomes the spine. Data modeling will reference Section 2; performance baselines will reference Section 4; APIs will reference Section 3 (auth) and Section 4 (rate limits).

## Facilitator reflection prompts (end of week)

- Which quad's TCD reads like an architect could pick it up? They are the Week-5 positive example.
- Which quad's stakeholder matrix is the weakest? Coach individually before Week 5.
- Did any quad over-specify and accidentally make architectural decisions? Coach toward "surface trade-offs, don't decide."
- AI use this week: was the discipline maintained? If not, surface for the cohort.
