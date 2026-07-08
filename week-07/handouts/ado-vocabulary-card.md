# ADO Vocabulary Card

> **Day 2 handout.** The Azure DevOps terms to keep straight while you load the feature and draft DP §2 — with the TPM-relevant signal each one carries.

Use this as your reference while you build the hierarchy, populate fields, and write queries. You don't have to *administer* ADO — you have to name these clearly enough that an engineering team could pick up your backlog Monday.

| Term | What it is | TPM-relevant |
|------|-----------|--------------|
| **Work item** | The atomic unit (Epic, Feature, User Story, Task, Bug) | Everything tracked is one of these |
| **Hierarchy** | Epic → Feature → User Story → Task | The default in the Agile process; configurable |
| **Area path** | Logical product area (`Reconcile / Mobile`) | Filters reports |
| **Iteration path** | Sprint number / time window | When the work is scheduled |
| **State** | New / Active / Resolved / Closed (varies by template) | Workflow status |
| **Tags** | Free-form labels | Cross-cutting filters (`security-review`, `customer-XYZ`) |
| **Story points** | Effort estimate (typically Fibonacci: 1, 2, 3, 5, 8, 13) | Velocity input |
| **Acceptance Criteria** | The criteria from PRD §6, attached to the work item | Definition of done |
| **Query (WIQL)** | A saved filter | "Show me everything in this state / iteration / tag" |
| **Board** | Kanban view of work items | Visual flow |
| **Backlog** | Prioritized list view | Planning view |
| **Sprint board** | Filtered Kanban for the current iteration | Daily-standup view |

---

**The one discipline to remember:** most teams populate the title and skip every other field. The cost of skipping shows up at sprint review when nobody can find anything. The cost of populating them is ~5 minutes per item.
