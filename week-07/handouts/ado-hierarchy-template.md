# ADO Hierarchy Template (DP §2)

> **Day 2 · Activity 1 handout.** The four-level spine for loading your feature into Azure DevOps, plus the per-level field stubs to fill in.

## The four-level hierarchy

```
Epic — strategic theme; usually 1 per quarterly initiative
├── Feature — a deliverable slice; usually 1–3 per Epic
│   ├── User Story — a unit of user-visible value
│   │   └── Task — engineering / design / TPM work to deliver
│   └── User Story
│       └── Task
└── Feature
```

For a single feature in the academy's scope:

- **1 Epic** for the broader theme it sits in (e.g., "Reduce dispatcher after-shift admin load")
- **1 Feature** for this PRD (e.g., "Reconcile flow (mobile)")
- **5–10 User Stories** (each Acceptance Criterion roughly maps to one)
- **2–4 Tasks per User Story**

**Discipline:** don't go deeper than 4 levels (no sub-tasks of sub-tasks). Don't promote a Task to a User Story to "make it visible." User Stories have user-visible value; Tasks don't.

---

## Level stubs (fill these in)

### Epic
```
Title: <strategic theme — usually 1 per quarter>
Description: <2-paragraph context: business goal + customer outcome>
Tags: <area, OKR identifier>
```
> FieldPulse example: "Reduce dispatcher after-shift admin load" — the umbrella for all reconcile work, manager-view, etc.

### Feature
```
Title: <the PRD's feature name>
Description: <1-paragraph from PRD §1>
Parent: <link to the Epic>
Tags: <release tag, persona tag>
```
> FieldPulse example: "Reconcile flow (mobile)".

### User Story (5–10 per Feature)
```
Title: As a <persona>, I want <capability> so that <outcome>
Description: <1-paragraph from PRD §5 sketch>
Acceptance Criteria: <copy from PRD §6, possibly grouped>
Story Points: <Fibonacci estimate>
Parent: <link to the Feature>
Tags: <happy-path / sad-path / weird-path / non-functional>
```

### Task (2–4 per User Story)
```
Title: <verb-first: "Build", "Test", "Document", "Review">
Description: <1 line>
State: New
Parent: <link to User Story>
Assignee: <if known, otherwise empty>
```
> Typical Task set: **Build** (implementation), **Test** (automated coverage), **Document** (release notes / internal docs), **Review** (security, peer, or stakeholder sign-off).

---

## NFRs are work

NFRs from PRD §7 / TCD §3 / §4 don't fit cleanly as user stories. Common treatments:

- **Performance NFR** → its own User Story tagged `non-functional` ("As a dispatcher, I want the modal to open in <1s…").
- **Security NFR** → a Task on the relevant User Story OR its own `security` story.
- **Compliance NFR** → its own `compliance` story.

They go in the backlog or they don't get done.

## Field checklist (every Epic / Feature / User Story)

- [ ] Title is action-oriented and specific
- [ ] Description has 1 paragraph of context
- [ ] Acceptance Criteria populated (User Stories) or empty (Epic / Feature)
- [ ] Area path set (e.g., `Dispatcher Workflow / Mobile`)
- [ ] Iteration path set (assign to a sprint, even if estimated)
- [ ] State set (`New` for everything until work begins)
- [ ] Tags appropriate
- [ ] Story points assigned (User Stories only; split anything >13)
