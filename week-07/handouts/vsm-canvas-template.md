# Value Stream Map Canvas (DP §4)

> **Day 4 · Activities 1–4 handout.** The one-page canvas for mapping your feature's delivery stream: steps, process time, lead time, queues, and total flow efficiency.

Draw this on a whiteboard or large paper. The visual makes the queues hit emotionally. Aim for **7–10 steps** (more = over-decomposed; fewer = lumping).

## The canvas

```
[Step 1]──→[Step 2]──→[Step 3]──→...
   │           │           │
   PT: __      PT: __      PT: __
   LT: __      LT: __      LT: __

   QUEUE       QUEUE       QUEUE
   __ items    __ items    __ items
   __ days     __ days     __ days

═════════════════════════════════════
Total cycle time: __ days
Total process time: __ days
Total flow efficiency: __%
```

---

## Per-step worksheet

Fill one row per step. Use real data where available (ADO data; team retros). Otherwise estimate honestly — and label it an estimate.

| Step | What happens | Owner (role) | PT | LT | Flow eff (PT/LT) | Notes |
|------|--------------|--------------|-----|-----|------------------|-------|
| | | | | | | |
| | | | | | | |
| | | | | | | |

## Worked sample — FieldPulse reconcile

| Step | PT | LT | Flow eff | Notes |
|------|------|------|----------|-------|
| Idea | 1 hour (signal review) | 3 days (queue at TPM's calendar) | 5% | Signal sometimes lost in inbox |
| Discovery | 4 hours | 2 days | 25% | Often blocked on customer-interview scheduling |
| Spec | 16 hours | 2 weeks | 22% | Multiple stakeholder review cycles |
| Estimate + accept | 1 hour | 1 week (queue for sprint planning) | 3% | One sprint planning per 2 weeks |
| Build | 8 hours per story | 1 week per story (mid-sprint) | 14% | Multi-tasking; dependency wait |
| Code review | 30 min review | 1.5 days waiting for reviewer | 4% | Reviewer queue |
| QA + integration | 4 hours | 2 days | 12% | QA staffing constraint |
| Deploy | 30 min ship | 6 hours (deploy windows) | 8% | Daily deploy schedule |
| Measure | 1 hour per check | 30 days for outcome | n/a | Inherent waiting (data accrual) |

**Total cycle time idea-to-deploy:** ~6–8 weeks. Total flow efficiency for the whole stream: typically **5–15%**.

---

## Optional: AI critique of your VSM

```
Role: Lean coach reviewing a software value stream.
Context: <description of the VSM with PT/LT/flow eff numbers
         and identified queues>
Task: Identify 3 queues likely missing or under-counted:
  1. A queue between two steps not yet shown
  2. A step where PT and LT seem out of line with team reality
  3. An invisible queue (e.g., approvals, "ping someone")
Constraints:
  - Use only the data given
  - Be specific
Format: 3 numbered findings — what's missing / why suspect / how to verify.
```

## What "good" looks like

- Numbers are **honest**, even if estimated (and estimates are flagged as estimates).
- Flow efficiency is **computed** (a single-digit number is typical and informative).
- Distinguish a **systemic queue** (waste) from a **necessary delay** (e.g., 30 days for outcome data is not a bug).
