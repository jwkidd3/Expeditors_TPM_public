# TPM Academy — Capstones

The academy has **two capstone moments**: a mid-arc PRD discipline check in Week 3, and a full-arc artifact-set delivery in Week 8.

| | **Week 3 — Mini-Capstone** | **Week 8 — Final Capstone** |
|---|---|---|
| Position | End of the requirements arc | End of the academy |
| Subject | **FieldPulse** (the shared HVAC dispatch SaaS case) | **Triad's choice** — FieldPulse or a project from their actual work / school / hobby |
| Duration | 1 week (Mon–Fri) | 1 week (Mon–Thu build, Fri present) |
| AI tools | **Off** — honor system | **On** with validation discipline; new AI Spec Development pattern introduced Day 1 |
| Deliverable | One Technical PRD + review-resolution log | 6-artifact set (PRD/TCD/TMD/SEP/DP + AI Spec) |
| Compression rule | None — full 11-section PRD | **2 pages per artifact** — discipline is what to cut |
| Triads | Same triads since Week 1 | Same triads since Week 1 |
| Friday | Cross-triad peer review (2 primary reviewers + 1 secondary, then revise) | 15-min triad presentations + 5 min Q&A; cohort + instructors score |
| Output proves | Cohort can write a defensible PRD without AI | Muscles from Weeks 1–7 applied end-to-end on the capstone subject |

---

## Week 3 — Mini-Capstone: PRD Discipline

The first capstone is **focused and narrow**: produce one Technical PRD against the shared FieldPulse case, by hand, under peer review. AI is intentionally off all week so the **structured-thinking-expressed-as-written-words** muscle gets isolated and built.

### What ships Friday

- A revised PRD (template below)
- A **review-resolution log** showing which feedback was adopted, deferred, or rejected, with reasoning

### PRD template (sections used all week, cumulative)

```
1. Context
2. Problem
3. Goals & non-goals
4. Scope (in / out)
5. Solution sketch
6. Acceptance Criteria (Given/When/Then — granular, falsifiable)
7. Non-Functional Requirements (5 categories)
8. Metrics & validation (tied to Week 2 Tier Sheet)
9. Risks & open questions
10. Dependencies
11. Out-of-scope follow-ups
```

### Daily map

| Day | Topic | PRD section produced |
|---|---|---|
| Mon | Drafting Technical PRDs | Sections 1–3 (context, problem, goals, scope) |
| Tue | Granular Acceptance Criteria | 8–12 testable ACs |
| Wed | Non-Functional Requirements | NFR across performance / security / accessibility / observability / compliance |
| Thu | Mini-capstone PRD assembly | **Complete PRD** ready for review |
| Fri | Peer review → revisions → secondary review → sign-off | **Revised PRD + resolution log** |

### Review rubric (Friday)

| Dimension | Weight |
|---|---|
| Problem clarity | 20% |
| AC testability | 25% |
| NFR completeness | 20% |
| Strategy linkage (to Week 2 Tier Sheet / journey friction) | 15% |
| Risk honesty | 10% |
| Writing discipline (no AI-generic prose) | 10% |

### The non-AI rule

Allowed: spell-check, dictionary, customer-interview transcripts, Week 1–2 artifacts. Not allowed: any generative AI for drafting, summarizing, or critiquing any part of the PRD. The reasoning: AI fills vagueness with confident generic prose, and vagueness is the bug Week 3 is trying to eliminate.

**Full details:** [`../../../week-03/markdown/labs/README.md`](../../../week-03/markdown/labs/README.md). Day-by-day lab briefs: [`../../../week-03/markdown/labs/day-01..05-*.md`](../../../week-03/markdown/labs/). Decks: [`../../../week-03/markdown/presentations/day-01..05-*.md`](../../../week-03/markdown/presentations/).

---

## Week 8 — Final Capstone: Integrated Artifact Set

The final capstone is **wide and integrative**. Triads pick a capstone subject (declared end of Week 7 — FieldPulse or a project of their own) and produce a compressed-but-complete version of the 5-week artifact set, plus a new AI-generated integrated technical spec.

### What ships Friday

```
capstone/
├── PRD-light.md       ← compressed from Week 3 muscle
├── TCD-light.md       ← compressed from Week 4 muscle
├── TMD-light.md       ← compressed from Week 5 muscle
├── SEP-light.md       ← compressed from Week 6 muscle
├── DP-light.md        ← compressed from Week 7 muscle
└── AI-Spec.md         ← NEW THIS WEEK — integrated engineering-ready spec
```

**Compression constraint:** every artifact fits on **2 pages or less**. The discipline is what to cut, not what to add.

### Daily map

| Day | Topic | Artifact produced |
|---|---|---|
| Mon | AI Spec Development technique introduced | AI Spec template + capstone subject confirmed |
| Tue | Capstone discovery + compressed PRD | PRD-light |
| Wed | Capstone architecture + AI Spec drafted | TCD-light + TMD-light + AI Spec v1 |
| Thu | Technical logic validation + finalization | Validated, integrated capstone set |
| Fri | **Final presentations** + course closure | Presented capstone; course complete |

### Friday — presentation day

For ~6 triads: 15 min present + 5 min Q&A each, two morning blocks + two afternoon blocks, then cohort retrospective and post-assessments + course closure.

### Presentation rubric

| Dimension | Weight |
|---|---|
| Customer + problem clarity | 15% |
| Integrated artifact set (consistent cross-references) | 15% |
| **AI Spec quality** (engineering-ready; provenance log) | 20% |
| Trade-off honesty (≥2 named with cost + revisit trigger) | 15% |
| Outcome thinking (NS / Tier-Sheet / leading-indicator vocabulary) | 10% |
| Delivery readiness (DP-light: backlog + tracking + one experiment) | 10% |
| Presentation craft (all triad voices; time-managed; curious Q&A) | 15% |

### AI Spec Development (the new technique)

Day 1 introduces a structured prompt sequence that produces an engineering-ready integrated technical spec from PRD/TCD/TMD outputs, with explicit validation discipline. Day 3 applies it. The provenance log — prompts used, what was kept, what was discarded — is required and graded.

**Full details:** [`../../../week-08/markdown/labs/README.md`](../../../week-08/markdown/labs/README.md). Day-by-day lab briefs: [`../../../week-08/markdown/labs/day-01..05-*.md`](../../../week-08/markdown/labs/). Decks: [`../../../week-08/markdown/presentations/day-01..05-*.md`](../../../week-08/markdown/presentations/).

---

## How the two capstones relate

Week 3 proves the cohort can write **one well-formed PRD without AI**. Week 8 proves the cohort can produce the **full artifact set on their capstone subject in five days, with AI used as a force multiplier instead of a crutch**. The Week 3 PRD muscle is the load-bearing input for the Week 8 PRD-light; every other compressed artifact rests on it.

Failing Week 3 makes Week 8 fragile. Passing Week 3 makes Week 8 an integration test rather than a relearning exercise.
