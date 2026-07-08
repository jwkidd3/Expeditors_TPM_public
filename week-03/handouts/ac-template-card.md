# AC Template Card

> **Day 2 · Activity 2 handout.** The pocket card for drafting one Acceptance Criterion. One Given/When/Then per AC, no ANDs in the Then that represent separate behaviors. Copy the block per AC into PRD §6.

---

## The shape

```
Given <a precondition / starting state>
When  <a single action or event>
Then  <one observable, falsifiable result>
```

## The rules

- **One behavior per AC.** If your Then has ANDs that describe *different system actions*, split into multiple AC. (ANDs that describe one observable state are OK — that's a judgment call.)
- **Name the exact** system state, screen, or event — no "the dashboard", say *which* screen and *what* it shows.
- **A junior engineer** should be able to read it and write a passing/failing test without asking you a question.
- **No implementation.** Describe behavior, not caches, queues, or frameworks.

---

## Worked FieldPulse example (happy path)

```
Given a dispatcher viewing the end-of-shift summary
When they tap "Reconcile all"
Then the reconcile modal opens within 1 second
  and shows all open tickets pre-selected
  and the header shows the count of tickets selected
```

*(The "and"s here are parts of one observable state, not separate behaviors — so this stays one AC.)*

---

## Blank cards to fill

```
Given
When
Then
```

```
Given
When
Then
```

```
Given
When
Then
```

> Run each finished AC through the **5-failure-mode check** (Vague / Untestable / Restating the goal / AND-soup / Implementation-prescriptive) before appending to §6.
