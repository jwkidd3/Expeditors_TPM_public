# VSM Vocabulary Card

> **Day 4 handout.** The value-stream-mapping terms to keep straight while you map the feature's delivery flow and draft DP §4 — with an example for each.

Use this as your reference while you walk the stream, measure each step, and compute flow efficiency. The most-startling number is usually **flow efficiency** — single-digit percentages are typical.

| Term | What it means | Example |
|------|---------------|---------|
| **Value stream** | The whole flow from idea to value-realized | Idea → discovery → spec → build → ship → measure → iterate |
| **Process time (PT)** | Hands-on-work time at a step | "2 hours of actual coding" |
| **Lead time (LT)** | Total time at a step including waiting | "3 days from PR opened to merged" |
| **Flow efficiency** | PT / LT × 100% | 2 hrs / (3 days = 24 hrs) = 8% |
| **Queue** | Work waiting between steps | "5 PRs waiting for review" |
| **Cycle time** | Lead time across the whole stream | "Idea to production: 6 weeks" |
| **Throughput** | Completed items per unit time | "3 stories per sprint" |
| **WIP (Work In Progress)** | Items currently being worked | "12 stories started, 4 done" |
| **Little's Law** | Cycle time = WIP / throughput | More WIP = longer cycle time |

---

**The one insight to remember:** most of the time work spends in a system is *waiting*, not being worked on. A story might take 2 hours of coding but spend 3 weeks in the system. A TPM who optimizes coding time saves minutes; a TPM who reduces the waiting saves weeks.
