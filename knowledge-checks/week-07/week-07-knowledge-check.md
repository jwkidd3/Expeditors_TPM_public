# Week 7 Knowledge Check — Agile Delivery & ADO Mastery

> A short retention check covering the week's core ideas: outputs vs outcomes and the Agile Manifesto, ADO hierarchy and field discipline, outcome/leading-indicator tracking, Lean value stream mapping, and removing delivery bottlenecks. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used in a lab.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or quad.

---

## Questions

**1. (MC)** Which of the following is a true *outcome* rather than an output?

- A) "Reconcile flow shipped July 15"
- B) "We delivered all 23 user stories in the sprint"
- C) "Dispatchers spend 30 minutes less per shift"
- D) "The outcome is shipping the feature"

**2. (MC)** The Agile Manifesto value "working software over comprehensive documentation" most accurately means:

- A) PRDs, TCDs, and TMDs are waste and should be dropped
- B) Documentation is valuable, but subordinate to working software
- C) Teams should stop writing plans
- D) Daily stand-ups replace written docs

**3. (T/F)** A counter-outcome names a result you *don't* want — a guardrail signaling you may have won the primary outcome for the wrong reasons.

**4. (MC)** The correct ADO 4-level hierarchy, top to bottom, is:

- A) Feature → Epic → User Story → Task
- B) Epic → Feature → User Story → Task
- C) Epic → User Story → Feature → Task
- D) Epic → Feature → Task → User Story

**5. (T/F)** A user story estimated at more than 13 story points should be split before it enters a sprint.

**6. (MC)** Which of the 5 essential queries is called out as high-leverage because it catches forgotten work?

- A) Open in current sprint
- B) Blocked
- C) Stale (no movement > N days)
- D) Done in this sprint

**7. (MC)** In the output / outcome / leading-indicator "triple," the *leading indicator* is:

- A) The feature that shipped
- B) The final business result measured at 30–90 days
- C) The early signal you can watch before the outcome lands
- D) The number of stories completed this sprint

**8. (T/F)** "If a metric has no cadence, it has no audience."

**9. (MC)** Flow efficiency is calculated as:

- A) Lead time / process time × 100%
- B) Process time / lead time × 100%
- C) WIP / throughput
- D) Throughput / cycle time

**10. (T/F)** Lean's foundational claim is that most of the time work spends in a system is spent being actively worked on, not waiting.

**11. (MC)** According to the Theory of Constraints (Goldratt), a system's throughput is limited by:

- A) The sum of all the slow steps
- B) Exactly one bottleneck at a time
- C) The team's average velocity
- D) The number of code reviewers

**12. (MC)** What separates a real bottleneck-removal experiment from a wish?

- A) A named owner plus a team-wide announcement
- B) A hypothesis with a measurable success criterion (baseline → target → window)
- C) Broad agreement that the change "feels better"
- D) A longer sprint to give it room

---

# Answer Key

**1. C** — "Dispatchers spend 30 min less per shift" is what *changed for the user*. A and B are outputs; D is an output dressed in outcome's clothes ("the outcome is shipping" is the trap language to catch).

**2. B** — The Manifesto values documentation *less* than working software, not zero. PRDs/TCDs/TMDs/SEPs are valuable and support working software; "no docs" is the most common rookie misreading.

**3. True** — Counter-outcomes are the guardrails (inherited from the NS Defense Card). Example: reconcile time drops but support tickets rise > 20% — you won the primary by adding new pain.

**4. B** — Epic → Feature → User Story → Task. Don't go deeper than 4 levels, and don't promote a Task to a User Story just to "make it visible."

**5. True** — Stories over 13 points are too vague to estimate. Split them. Story points are a learning/calibration tool even when imperfect.

**6. C** — The "stale" query (no movement > N days) catches forgotten work — the highest-leverage query for TPMs.

**7. C** — The leading indicator is the *early* signal (e.g., first-attempt completion ≥ 80% by week 2). Without it you wait 30 days to learn the outcome failed.

**8. True** — Every metric needs a cadence (daily / sprint / monthly / quarterly) tied to a real audience. No cadence means nobody owns looking at it.

**9. B** — Flow efficiency = process time / lead time × 100%. Single-digit percentages are typical. (WIP / throughput is Little's Law for cycle time — the distractor.)

**10. False** — The opposite: most time is *waiting*, not being worked on. A story with 2 hours of coding may sit 3 weeks. Reduce the waiting and you save weeks.

**11. B** — Exactly one bottleneck at a time. Optimizing anything else just piles inventory in front of the constraint. Find it, move it, then find the next one.

**12. B** — A measurable success criterion (baseline → target → window). "We'll see if it feels better" is not an experiment; vibes don't decide.
