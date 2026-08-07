# The 5 Saved Queries Every Team Needs (WIQL)

> **Day 2 · Activity 3 handout.** Build and save these five queries in ADO. Fill the `<our area>` placeholders with your quad's area path. Save them all in a shared folder with clear names.

## 1. What's open in the current sprint?

```
Type: User Story or Task
State: New / Active
Iteration Path: Current
Area Path: Under <our area>
```
**Used:** every standup.

## 2. What's blocked?

```
Type: User Story or Task
State: Active
Tags: Contains "blocked"
```
**Used:** daily; surfaces dependencies that are stuck.

## 3. What's done in this sprint?

```
Type: User Story
State: Closed
Iteration Path: Current
Area Path: Under <our area>
```
**Used:** end-of-sprint review; outcome verification.

## 4. What hasn't been touched in N days?

```
Type: User Story or Task
State: Active
Changed Date: < (Today - 7 days)
```
**Used:** weekly; catches forgotten work.

## 5. What's in this NFR / quality category?

```
Type: User Story
Tags: Contains "non-functional" OR "security" OR "compliance"
State: Not Closed
```
**Used:** monthly; ensures NFRs aren't being deferred indefinitely.

---

## After you build them

- All 5 queries are **saved and named clearly** in a shared folder.
- Set up the **sprint board**: columns To Do / In Progress / In Review / Done, with WIP limits where appropriate (e.g., max 3 In Progress per developer).
- Set up the **Kanban board** for the whole Feature (same columns; this view spans the feature, not just one sprint).
- Each quad member: pick the **one query you'd run every morning**. Discuss and converge.
