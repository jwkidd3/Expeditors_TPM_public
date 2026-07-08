# SLO Triage Pack — 8 Statements

> **Day 4 · Activity 1 handout.** Eight SLO statements drawn from real (anonymized) systems. Triage each: is it clean, or does it fail one of the common checks? Then rewrite the five worst so they pass **percentile + window + defense**.

---

### The common failure modes

| Failure mode | What it looks like |
|--------------|--------------------|
| **No measurement window** | A target with no period — "always"? "best case"? |
| **No percentile (or "average")** | Averages hide bimodal distributions |
| **No defense** | A number with no rationale for *why that number* |
| **Aspirational beyond capability** | A target the team's staffing/infra can't sustain |
| **Mismatched to user threshold** | A target far looser or tighter than the user actually needs |
| **Confusion with SLA** | A *contractual* commitment stated as an internal target |

---

### The 8 statements

1. `p95 < 400ms`
2. `Average response time < 500ms`
3. `99.9% availability`
4. `99.99% availability` (for a 2-engineer feature on shared infra)
5. `p95 < 5s` (for a typing-feedback feature)
6. `We commit to 99.99% availability`
7. `p99 ≤ 800ms, 99.9% of the time over 30 days`
8. `Error rate under 1% during business hours, measured on the checkout endpoint`

---

### Your protocol

1. **Triage all 8** (15 min). Label each with its failure mode(s), or mark **"clean"** if it passes.
2. **Rewrite the 5 worst** (15 min) so each passes all three checks: **percentile + window + defense.**
3. **Identify the one with the most subtle failure** (5 min) — discuss in the readout.

### The three checks a clean SLO passes

- **Percentile** — p95 / p99, *not* "average."
- **Window** — "over 30 days," *not* "always" / unstated.
- **Defense** — a stated reason tied to user behavior or platform precedent, *not* a bare number.

### Readout (60 sec)

> "The most subtle failure was [X] because [why]. Our cleanest rewrite was [example]."

---

### Triage grid

| # | Statement | Failure mode(s) / "clean" | Rewrite (if among worst 5) |
|---|-----------|---------------------------|-----------------------------|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| 7 | | | |
| 8 | | | |
