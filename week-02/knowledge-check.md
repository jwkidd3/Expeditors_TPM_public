# Week 2 Knowledge Check — Strategic Design & Metrics

> A short retention check covering the week's core ideas: the metrics pyramid & vanity metrics, the North Star and its counter-metric, UX heuristics & design principles, AI-assisted research, and customer journey mapping. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used in a lab.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or triad.

---

## Questions

**1. (MC)** The Metrics Pyramid has a deliberate shape. Which set of counts, top to bottom, is correct?

- A) Many North Stars, few KPIs, few operational signals
- B) 1 North Star, 2–4 KPIs, 4–10 operational signals
- C) 1 North Star, 10 KPIs, 2–3 operational signals
- D) Equal numbers at every tier

**2. (T/F)** When a candidate operational signal can't be measured in production today, it's a failure that should be hidden until the data exists.

**3. (MC)** The North Star template requires exactly three parts. Which set?

- A) Customer outcome, user segment, single number
- B) Revenue, retention, NPS
- C) Problem, solution, metric
- D) Customer outcome, counter-metric, deadline

**4. (MC)** A counter-metric is best described as:

- A) A backup North Star to use if the first one fails
- B) A second metric that, if it moves the wrong way, signals you're winning the North Star for the wrong reasons
- C) A competitor's metric you benchmark yourself against
- D) The KPI that sits directly below the North Star

**5. (T/F)** A North Star that lands with leadership but needs translation before it means anything to the customer still qualifies as a defensible North Star.

**6. (MC)** Beyond Nielsen's 10 heuristics, Day 3 adds three TPM-specific lenses. Which set?

- A) Time-to-first-value, failure-mode dignity, power-user respect
- B) Consistency, minimalism, error prevention
- C) Color contrast, focus order, alt text
- D) Severity, frequency, addressability

**7. (T/F)** The TPM's accessibility responsibility is to personally become the squad's accessibility expert.

**8. (MC)** Which request crosses the "bright line" — asking AI to do something it can't do safely?

- A) "Structure these two product-tour transcripts into a comparison matrix"
- B) "Identify 3 questions these materials don't answer"
- C) "What is ServiceTitan's market share?"
- D) "Tell me what's missing relative to my own product"

**9. (T/F)** When cross-validating an AI research summary, the AI's own confidence rating (H/M/L) is a reliable signal of which themes you can trust.

**10. (MC)** An AI summary cites "Ticket #4," but no such ticket exists in your pack. Which summarization failure mode is this?

- A) Theme inflation
- B) Citation invention
- C) Premature confidence
- D) Source bias

**11. (MC)** A feature concept earns a place off the journey map only if it passes all three tests. Which set?

- A) Friction link, metric link, principle link
- B) Cost, schedule, scope
- C) Desirability, feasibility, viability
- D) Severity, frequency, addressability

**12. (MC)** On a journey map, a friction star on 5+ of the stages most likely means:

- A) The map is thorough and honest
- B) You're not discriminating — re-rank friction by severity
- C) The product is beyond saving
- D) You sanitized the journey and should re-listen to interviews

---

# Answer Key

**1. B** — 1 North Star, 2–4 KPIs, 4–10 operational signals. Few at the top, many at the bottom. "A team that has 10 KPIs has 0 KPIs."

**2. False** — "We don't measure that today" is not a failure, it's a *finding* — an instrumentation gap. Surface it openly; it becomes a Week 4–5 conversation.

**3. A** — Customer outcome / user segment / single number. Miss any blank and the team fights about which version of the NS they meant.

**4. B** — A counter-metric is the guardrail: it catches when you move the North Star for the wrong reasons (e.g., time returned but trust broken). It's the day's most durable new tool.

**5. False** — A defensible NS lands with the CEO *and* the customer without translation. If it only lands with one audience, it's a KPI in disguise.

**6. A** — Time-to-first-value, failure-mode dignity, power-user respect. (D, Severity × Frequency × Addressability, is Week 1's pain model.)

**7. False** — The job isn't to be the a11y expert; it's to refuse to ship a feature that fails the 8-check floor — and to spot failures unsolicited.

**8. C** — AI can summarize and structure source material you provide; it *cannot* tell you what competitors actually do. Market-fact questions return confident, fabricated answers.

**9. False** — Don't trust the AI's confidence about its own output. Independent citation verification is the only reliable signal.

**10. B** — Citation invention. Fix: verify every cited source exists and demote uncited claims. (Theme inflation lumps distinct complaints; source bias over-weights the loudest source.)

**11. A** — Friction link, metric link, principle link. The recurring failure is features with no metric link — force the link or kill the feature.

**12. B** — 5+ starred stages means you're not discriminating; re-rank by severity. (2–3 stars is healthy; 0 stars means you sanitized the journey.)
