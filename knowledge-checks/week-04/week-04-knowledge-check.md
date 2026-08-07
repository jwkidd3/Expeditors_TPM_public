# Week 4 Knowledge Check — Technical Architecture & Constraints

> A short retention check covering the week's core ideas: monolith vs microservices and the three-question frame, STRIDE threat modeling and compliance, the C4 model, SLI/SLO/SLA and error budgets, and mature architectural trade-offs. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used to build the TCD.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or quad.

---

## Questions

**1. (MC)** A multi-deploy system whose services *must* all be released together to work is best described as a:

- A) Modular monolith
- B) Service-oriented architecture (SOA)
- C) Distributed monolith
- D) Event-driven architecture

**2. (T/F)** In the architecture stance template, writing "**Revisit if:** later / when needed" is an acceptable revisit trigger.

**3. (MC)** In a STRIDE pass, which letter is called out as the *most-missed* — the least intuitive one that teams building without audit trails routinely skip?

- A) Spoofing
- B) Repudiation
- C) Information disclosure
- D) Elevation of privilege

**4. (T/F)** A strong security brief opens by telling the security team "we don't know anything yet, please tell us what to do."

**5. (MC)** In the C4 model, which two levels are the TPM's scope to draw?

- A) Context and Container
- B) Container and Component
- C) Component and Code
- D) Context and Component

**6. (MC)** When stress-testing a Container diagram with the three lenses (failure, trust boundary, evolvability), which annotation is called out as the *most-missed* — the place where compliance and security risk concentrates?

- A) The failure path
- B) The trust boundary
- C) The evolvability arrows
- D) The async/sync distinction

**7. (T/F)** Under a modular-monolith stance, the modules should be drawn inside one container as labeled sub-boxes, not promoted to separate containers.

**8. (MC)** Which of these is a *contractual commitment with consequences* — as opposed to an internal target?

- A) SLI
- B) SLO
- C) SLA
- D) Error budget

**9. (MC)** If a feature's availability SLO is 99.9% over a 30-day window, its error budget is roughly:

- A) 4 minutes
- B) 43 minutes
- C) 7 hours
- D) 22 hours

**10. (T/F)** Stating a latency SLO as "avg < 500ms" is a solid target because the average captures typical user experience.

**11. (MC)** Which of these is a *mature* trade-off statement rather than a mere description?

- A) "We considered microservices but chose a monolith."
- B) "We chose a monolith because monoliths are simpler."
- C) "Option A: modular monolith. Option B: extract a service. We chose A. Accepted cost: future extraction needs a coordinated refactor. Revisit if traffic exceeds 5× rest-of-app."
- D) "We'll start with a monolith and figure out the rest later."

**12. (MC)** When writing the top-5 architectural trade-offs, what is the recommended coverage check to confirm you surfaced real tensions?

- A) All 5 come from a single category
- B) They span at least 3 of the five trade-off categories
- C) Each names a specific competitor
- D) Each has a dollar figure attached

---

# Answer Key

**1. C** — Distributed monolith: the anti-pattern where you pay the ops cost of many deploys but still must release them together. "Microservices" in name only.

**2. False** — "Later" or "when needed" is not a trigger. The senior-author signal is a concrete metric or org change (e.g., "if traffic grows 10x" or "if a second team contributes").

**3. B** — Repudiation. The least intuitive letter; teams that ship without audit trails miss it. A threat list with zero R's should be pushed on.

**4. False** — A passive "please tell us everything" brief signals an outsourced-thinking TPM. A strong brief is short, specific (concrete open questions), and confident (decisions already made, with justification).

**5. A** — Context and Container. Stay above Component — the architect and engineers own the Component and Code layers.

**6. B** — The trust boundary: where data crosses from our control to someone else's. It's the most-missed annotation and where security/compliance risk concentrates.

**7. True** — A modular monolith is one container; draw the modules as sub-boxes inside it. Don't promote them to separate containers — that would misrepresent the stance.

**8. C** — SLA: a contractual commitment with consequences. SLI is the measurement, SLO is the internal target, and error budget is (1 − SLO) over the window. Calling an SLO an SLA casually is a common error.

**9. B** — ~43 minutes. Error budget = (1 − 0.999) = 0.1% of 30 days ≈ 43 minutes of allowed downtime.

**10. False** — Average hides bimodal distributions. Force percentiles (e.g., p95); every SLO needs a percentile, a window, and a defense.

**11. C** — The mature pattern is Option A vs Option B → choice → accepted cost → revisit trigger. A, B, and D are descriptions, not trade-offs.

**12. B** — Span at least 3 of the five categories (coupling vs independence, consistency vs availability, latency vs durability, speed vs robustness, generality vs simplicity). All in one category usually means real tensions were missed.
