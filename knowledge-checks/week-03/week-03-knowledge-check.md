# Week 3 Knowledge Check — Requirements Engineering & Mini-Capstone

> A short retention check covering the week's core ideas: drafting technical PRDs, granular acceptance criteria, non-functional requirements, PRD assembly, and structured peer review. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used in a lab.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or triad.

---

## Questions

**1. (MC)** What is the "TPM contract" — the test that distinguishes a Technical PRD from a generic PM PRD?

- A) A PRD the executive sponsor approves without edits
- B) A PRD an engineering lead would accept as scoping input *without a clarifying call*
- C) A PRD that fits on a single page
- D) A PRD marketing can turn into launch copy

**2. (T/F)** Week 3 encourages using AI to draft the PRD faster, so triads can spend more of their time on review.

**3. (MC)** Which of the following *belongs* in the Section 5 Solution Sketch, rather than being cut as over-specification?

- A) Database schema decisions
- B) Specific API contracts
- C) The user-visible flow (4–8 steps)
- D) Class names and library picks

**4. (MC)** An acceptance criterion reads: *"Then dispatchers reconcile faster."* Which of the five AC failure modes is this?

- A) Vague
- B) Untestable
- C) Restating the goal
- D) AND-soup

**5. (T/F)** Weird-path AC coverage — network drops, race conditions, timeouts, boundary values — is described as the TPM differentiator that PMs and pure engineers each tend to miss.

**6. (MC)** In the Requirement / Defense / Verification NFR form, which field is singled out as the one that separates a real TPM NFR from boilerplate?

- A) Requirement
- B) Defense
- C) Verification
- D) Category

**7. (MC)** How should a performance NFR express its latency target?

- A) The average (mean) response time
- B) A p95 target on a representative device and connection
- C) A best-case time under ideal conditions
- D) "Fast enough that users don't complain"

**8. (T/F)** A mature NFR section includes a "Known Trade-offs" subsection that names the tensions — and their resolution or open status — rather than pretending everything is achievable at once.

**9. (MC)** In Section 10 Dependencies, what makes a dependency "owned"?

- A) It's assigned to the responsible team
- B) It's assigned to a named person
- C) Its status is marked "Confirmed"
- D) It has a "by when" date

**10. (T/F)** In Section 9, listing "no risks" is acceptable as long as the feature is genuinely low-risk.

**11. (MC)** On the Friday review rubric, which dimension carries the highest weight?

- A) Problem clarity (20%)
- B) AC testability (25%)
- C) NFR completeness (20%)
- D) Strategy linkage (15%)

**12. (MC)** Which reviewer rule is enforced during AC cross-review and again on Friday?

- A) Always give three specific strengths before any criticism
- B) If you say "this could be more specific," you also write the specific version
- C) Never score below 2.0 without facilitator sign-off
- D) Reviewers must not coordinate with each other

---

# Answer Key

**1. B** — The TPM contract: a PRD an engineering lead would accept as scoping input *without a clarifying call*. This is the single best evaluation criterion, and it's the bar used again on Friday.

**2. False** — Week 3 is deliberately non-AI. AI fills vagueness with confident, generic prose — and vagueness is exactly the bug the week is built to eliminate.

**3. C** — The user-visible flow (4–8 steps). Section 5 gives an engineer the *shape*; schema, API contracts, and class names are engineering judgment and are explicitly excluded.

**4. C** — Restating the goal. It pins to a metric, not an in-system event. Fix by anchoring to an observable system state ("could you write a test without running an A/B?").

**5. True** — Weird-path coverage is where TPMs earn their seat. PMs who don't think technically miss it; engineers who don't think about users miss it differently.

**6. B** — Defense. "p95 < 400ms because dispatchers tap this 40 times per shift" beats "should be fast." The Defense field is the most-skipped part of NFRs in the wild.

**7. B** — A p95 target on a representative device/connection. Averages lie: a bimodal 200ms/5s split averages to 2.6s but describes no real user's experience.

**8. True** — The "Known Trade-offs" subsection is the senior-author signal. "We accept this" is strong; "we will change it if X happens" is stronger.

**9. B** — A named person. "The auth team" is unowned; "Lin from auth" is owned. "TBD" as owner is the dependency that ships late.

**10. False** — "No risks" is a hard fail — it's the tell of a PRD written to avoid scrutiny. Each risk gets likelihood, impact, and a mitigation.

**11. B** — AC testability, at 25%, is the highest-weighted dimension. Scores ≥3.0 ship as-is; 2.0–2.9 ship with named gaps; <2.0 triggers facilitator intervention.

**12. B** — "If you say it could be more specific, you write the specific version." The rule eliminates lazy review feedback. (Three strengths and no reviewer coordination are also real Friday rules — but *this* is "the reviewer rule.")
