# Week 1 Knowledge Check — Customer-Centric Foundations

> A short retention check covering the week's core ideas: AI fundamentals & prompting, working backwards, personas, pain points, and problem framing. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used in a lab.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or triad.

---

## Questions

**1. (MC)** The RCCF prompting scaffold stands for:

- A) Role, Constraints, Context, Feedback
- B) Role, Context, Constraints, Format
- C) Request, Context, Criteria, Format
- D) Role, Content, Clarity, Format

**2. (MC)** You ask an AI to summarize your product's competitive landscape and it produces a confident, plausible-sounding answer that is generic and not actually about your product. Which failure mode is this most likely?

- A) Hallucination
- B) Sycophancy
- C) Context starvation
- D) Anchoring

**3. (MC)** Rank the evidence tiers from most to least trustworthy:

- A) Reported → Observed → Inferred → AI-generated
- B) Observed → Reported → Inferred → AI-generated
- C) Observed → Inferred → Reported → AI-generated
- D) AI-generated → Observed → Reported → Inferred

**4. (T/F)** A model with a good enough context window will remember facts about your product from previous, separate sessions even if you don't include them in the current prompt.

**5. (MC)** In a Working Backwards PR/FAQ, which section is described as the *single most diagnostic* — if it sounds like marketing, the idea is in trouble?

- A) The heading
- B) The problem paragraph
- C) The customer quote
- D) The summary paragraph

**6. (T/F)** The core purpose of the Working Backwards document is to plan *how* to build a product the team has already decided to build.

**7. (MC)** Which of the "Five Questions That Force Clarity" is where Day 1's evidence tiers re-enter the picture?

- A) "Who is the customer?"
- B) "What is the most important benefit?"
- C) "How do you know what they want or need?"
- D) "What does the experience look like?"

**8. (T/F)** Writing a persona trait as an adjective — e.g., "busy," "tech-savvy" — is a strength because it captures the customer succinctly.

**9. (MC)** During a validation interview, which question should you **avoid** asking?

- A) "Walk me through the last time you did X."
- B) "Would you use a product that did X?"
- C) "What did you do to work around it?"
- D) "How often does that happen?"

**10. (MC)** According to the pain-extraction sources, where does the *most reliable* signal of real pain usually show up?

- A) Support tickets
- B) Observation / ride-alongs (workarounds, side-channels)
- C) Sales/loss reviews
- D) Analytics drop-offs

**11. (MC)** In the Severity × Frequency × Addressability model, which axis do PMs most often forget — and which turns a pain into a *communication* problem rather than a product one when it's low?

- A) Severity
- B) Frequency
- C) Addressability
- D) Reliability

**12. (T/F)** The line most problem statements skip — and the one that lets you know when you're actually done — is "Success looks like…"

---

# Answer Key

**1. B** — Role, Context, Constraints, Format. The kernel prompt scaffold; heavier frameworks (CO-STAR, CRISPE) are elaborations of the same habit.

**2. C** — Context starvation: a plausible-but-generic answer. Fix by adding Role + Context and pasting in the source material. (Hallucination is *confident fabricated specifics*; this one is generic.)

**3. B** — Observed → Reported → Inferred → AI-generated. AI-generated is the lowest tier and must be upgraded before use.

**4. False** — If the model can't see it in the prompt, it's guessing. "What does this model know about my product right now? Nothing."

**5. C** — The customer quote. If you can't write a fictional-but-credible quote believably, the PR fails; if it sounds like marketing, the problem is marketing.

**6. False** — Working Backwards is used to decide *whether* to build at all, not to plan the how of an already-approved build. "Fiction you can stress-test is cheaper than code you can't unship."

**7. C** — "How do you know what they want or need?" — name the evidence and tag its tier.

**8. False** — Adjectives are the real killer because they're un-falsifiable. Working personas use observed behaviors and words, each tied to an evidence tier.

**9. B** — "Would you use a product that did X?" The answer is always yes. Ask about past behavior instead (the "Mom Test" instinct).

**10. B** — Observation / ride-alongs are highest for real pain. The best pain points are the ones customers *stopped* complaining about because they built a workaround.

**11. C** — Addressability. High severity + high frequency + low addressability = communicate, don't engineer. A red "Must fix" cell is a stakeholder-framing problem, not a JIRA ticket.

**12. True** — "Success looks like…" is the most-skipped line and the one that makes a problem statement falsifiable.
