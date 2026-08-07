# Cumulative Knowledge Check — The Artifact Chain (End-to-End)

> A capstone-week check that tests the course as a *system*, not week by week. Every question is about how the artifacts connect — what feeds what, what must stay consistent across documents, and what each artifact is *for*. If you can answer these, you understand why the eight weeks are one arc, not eight topics.

**Format:** 16 questions (multiple choice + true/false). ~25 minutes. Individual or quad. Aim for the *relationships between* artifacts, not trivia inside one.

---

## The chain, for reference

**Discovery** (persona → pain → problem statement, W1) + **metrics** (North Star, W2) → **PRD** (W3) → **TCD** (W4) → **TMD** (W5) → **SEP** (W6) → **DP** (W7) → **AI Spec** (W8, integrates them all).

---

## Questions

**1. (MC)** Which sequence correctly orders the core artifacts by when they're built?

- A) PRD → TMD → TCD → DP → SEP → AI Spec
- B) PRD → TCD → TMD → SEP → DP → AI Spec
- C) TCD → PRD → TMD → DP → SEP → AI Spec
- D) PRD → TCD → SEP → TMD → DP → AI Spec

**2. (MC)** Each artifact answers a different question. Which pairing is **wrong**?

- A) PRD — "What are we building, and why?"
- B) TCD — "Is it technically sound, and what are the trade-offs?"
- C) TMD — "Who do we need to align, and how?"
- D) DP — "How do we deliver it, and how do we know it's working?"

**3. (T/F)** The Week-1 persona and problem statement are just warm-up exercises — once the PRD exists, they stop mattering.

**4. (MC)** The North Star metric (Week 2) reappears later in the chain as:

- A) An acceptance criterion in the PRD
- B) An SLO in the TCD
- C) The outcome the Delivery Plan is trying to move
- D) A sequence diagram in the TMD

**5. (MC)** A PRD **acceptance criterion** most directly drives the content of which later artifact?

- A) The SEP stakeholder map
- B) The TMD sequence diagrams (happy / sad / weird paths)
- C) The TCD compliance frame
- D) The DP value-stream map

**6. (T/F)** An SLO defined in the TCD but with no corresponding monitoring/alert plan in the TMD is an unverifiable target — you've promised something you can't observe.

**7. (MC)** In the Week-8 cross-artifact validation, a quad finds their TMD reconcile sequence sums to ~800 ms but the TCD SLO says p95 ≤ 500 ms. This is:

- A) Fine — the SLO and the sequence are different documents
- B) A real inconsistency: the design can't meet its own stated target, and one has to change
- C) Only a problem if a customer complains
- D) Expected; sequences are always slower than SLOs

**8. (T/F)** Evidence tiers (Observed / Reported / Inferred / AI-generated) are a Week-1 discovery tool only; by the time you're writing the TCD and TMD, everything is just "technical fact."

**9. (MC)** A claim in the AI Spec reads "see the TCD for the rate-limit design." Why does this fail the validation discipline?

- A) The AI Spec shouldn't reference other artifacts
- B) Cross-references must be **specific** (cite the Section) and verified — a vague pointer means the writer didn't actually check
- C) Rate limits belong in the TMD, not the TCD
- D) It doesn't fail — that's a valid reference

**10. (MC)** What is the SEP's main job in protecting the artifact set?

- A) To make the architecture faster
- B) To keep a technically-sound spec from being blocked by unaligned stakeholders
- C) To replace the PRD's scope section
- D) To define the data model

**11. (MC)** "Outcome vs output" — which item is an **outcome** the DP would track (not an output)?

- A) Shipped the reconcile flow on July 15
- B) Closed all 23 stories in the sprint
- C) Median nightly close time dropped from 45 min to under 10
- D) Hired three engineers

**12. (T/F)** "Compression" in the Week-8 `-light` artifacts means dropping whole sections to save time.

**13. (MC)** A TCD Section 5 trade-off reads "We chose Postgres because Postgres is better." Why is this not yet a real trade-off?

- A) Postgres is the wrong choice
- B) A trade-off needs the rejected option, the accepted cost, and a revisit trigger — not just a justified pick
- C) Trade-offs belong in the TMD
- D) It's fine as written

**14. (T/F)** The single evaluation bar for the PRD — "an engineering lead could scope from it without a clarifying call" — is the same standard, in spirit, that every downstream artifact is held to: self-sufficient and unambiguous.

**15. (MC)** What is the AI Spec's role in the chain (Week 8)?

- A) To replace the PRD/TCD/TMD with a single AI-written document
- B) To integrate the artifact set into one engineering-ready spec, drafted with AI and **validated section by section**
- C) To let AI make the product decisions the quad couldn't
- D) To summarize the artifacts for executives

**16. (T/F)** The reason the eight weeks form one chain is traceability: a line in the AI Spec should trace back — through the TMD, TCD, and PRD — to a real customer problem tagged with real evidence.

---

# Answer Key

**1. B** — PRD → TCD → TMD → SEP → DP → AI Spec. Requirements first, then how it's built soundly (TCD), then data/API/sequences (TMD), then who to align (SEP), then how to deliver (DP), then the integrated spec (AI Spec).

**2. C** — TMD is the **Technical Modeling Document** (data model, cloud, APIs, sequences, monitoring). "Who do we align, and how?" is the **SEP**. The other three pairings are correct.

**3. False** — The persona and problem statement are the *root* of the chain. Every downstream artifact traces back to them; if they're wrong, the whole spec is confidently building the wrong thing.

**4. C** — The North Star is the **outcome** the Delivery Plan tracks. Outputs (shipped, stories closed) are not the North Star; the DP watches whether the customer outcome actually moved.

**5. B** — Acceptance criteria define the behaviors the system must exhibit, which the **TMD sequence diagrams** (happy / sad / weird paths) model. The Week-8 validation explicitly checks that every AC has a corresponding sequence.

**6. True** — An SLO you can't measure isn't an objective, it's a wish. The TCD sets the target; the TMD's monitoring plan makes it observable. No monitoring = unverifiable.

**7. B** — This is exactly what the cross-artifact validation exists to catch: the design (TMD) can't meet the target it set for itself (TCD). One must change — tighten the sequence or relax/revise the SLO — before it ships.

**8. False** — Evidence tiers run through the **whole** chain. A TCD trade-off, a TMD cost estimate, an AI-Spec claim — each still carries a tier. "We think" vs "we measured" matters just as much in the technical artifacts.

**9. B** — Cross-references must cite the specific section and be verified. "See the TCD" without a Section is the tell that the writer never actually checked the two documents agree — the opposite of integration.

**10. B** — A spec can be technically flawless and still die if the Ops VP, Compliance, or Eng lead block it. The SEP de-risks *alignment*, which is a different failure mode from *soundness*.

**11. C** — Close time dropping is a **change for the user** (outcome). Shipping, closing stories, and hiring are all things the team *did* (outputs). The DP tracks the former and guards against gaming it.

**12. False** — Compression is **selective**, not lossy: keep what's load-bearing, cut what's cosmetic. A `-light` artifact is shorter, not weaker — the discipline is knowing *what* to cut.

**13. B** — A justified pick isn't a trade-off. The mature form names the rejected option, the cost you're accepting, and the trigger that would make you revisit — otherwise there's no real tension being managed.

**14. True** — "Self-sufficient enough that the reader can act without a clarifying call" is the through-line standard: the PRD for an engineer, the SEP for a stakeholder, the AI Spec for the whole build.

**15. B** — The AI Spec **integrates** the set into one engineering-ready spec, drafted fast with AI but validated section by section. AI accelerates the typing; the quad's judgment (and the validation chain) keeps it honest.

**16. True** — Traceability is the point. If a line in the AI Spec can't be walked back to a real, evidence-tagged customer problem, it's ungrounded — the same failure the whole course is built to prevent, just at the end of the chain instead of the start.
