# Queue-Ranking Worksheet (DP Section 4)

> **Day 4 · Activity 3 handout.** Find where the time hides. List your top 3 queues, name the cause of each, name a candidate intervention — then rank by impact, effort, and risk.

If you're spending 6 weeks total and only 2–3 days of actual work, the other 5+ weeks are in the queues. This worksheet finds and ranks them.

## Fill in your top 3 queues

For each queue, name the cause (capacity, policy, inertia, hidden dependency) and a candidate intervention (more capacity, different policy, parallel work, dependency removal). Then rank.

| Queue | Time | Cause | Candidate intervention | Impact | Effort | Risk |
|-------|------|-------|------------------------|--------|--------|------|
| | | | | | | |
| | | | | | | |
| | | | | | | |

- **Impact** — how much cycle time would shrink.
- **Effort** — how hard it is to fix (people-time, money, org change).
- **Risk** — what could go wrong.

---

## Worked example — FieldPulse

| Queue | Time | Cause | Candidate intervention |
|-------|------|-------|------------------------|
| Spec → Estimate (1 week wait) | 168 hrs | Sprint planning is bi-weekly | Mid-cycle sync to pre-load stories; OR mid-sprint pull |
| Build → Code review (1.5 days) | 36 hrs | 5 reviewers; PRs wait for them | Pair-review during dev; auto-assign reviewer |
| Discovery → Spec (varies; often weeks) | 168+ hrs | Customer interview scheduling | Async interview cycles; lighter-weight discovery for known patterns |

---

## What "good" looks like

- Top 3 queues are **specific** — not "we're slow in code review," but "PRs wait 2 days for first review because we have 8 reviewers and 40 PRs/week."
- Each has a **named cause** — not just "we're slow."
- Each has a **candidate intervention** — not "be faster."
