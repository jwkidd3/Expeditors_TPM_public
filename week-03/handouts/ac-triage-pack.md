# AC Triage Pack

> **Day 2 · Activity 1 handout.** Twelve Acceptance Criteria drawn from real (anonymized) FieldPulse PRDs. Some are clean. Some carry one of the 5 failure modes. A few carry more than one. **Your job:** for each, decide which failure mode(s) are present (or mark it clean), then rewrite every failing one. No labels are provided — the judging is the work.

The 5 failure modes to check against: **① Vague · ② Untestable · ③ Restating the goal · ④ Multi-condition (AND-soup) · ⑤ Implementation-prescriptive.**

---

### AC-1
```
Given a dispatcher on the End-of-Day Reconcile summary
When they tap "Reconcile all"
Then the reconcile modal opens quickly with everything ready to go
```

### AC-2
```
Given a dispatcher with 3 open tickets on the summary screen
When they tap "Reconcile all"
Then the modal opens with all 3 tickets pre-selected
  and the header shows the count "3 selected"
```

### AC-3
```
Given any dispatcher using the reconcile flow
When they complete their end-of-day work
Then they feel confident payroll will run clean on Wednesday
```

### AC-4
```
Given a dispatcher submits a reconcile batch during a network drop
When the submit request fails to reach the server
Then the payload is queued using an IndexedDB write-behind buffer
  and replayed over a WebSocket once connectivity returns
```

### AC-5
```
Given a dispatcher with 0 open tickets on the summary screen
When they tap "Reconcile all"
Then a non-modal toast appears reading "No tickets to reconcile"
  and the dispatcher remains on the summary screen
```

### AC-6
```
Given a tech's truck-stock quick view
When the dispatcher opens it during job assignment
Then the reconcile process becomes faster and re-routes go down
```

### AC-7
```
Given a reconcile ticket missing its labor-time entry
When the dispatcher opens the pre-submit confidence banner
Then the banner lists that ticket under "Incomplete"
  and a "Jump to fix" action focuses the missing labor-time field
```

### AC-8
```
Given a dispatcher and a shop manager both editing the same re-route
When the dispatcher saves first and the manager saves 200ms later
Then the manager's save is rejected with a "This re-route changed — reload" message
  and the manager's board refreshes to the dispatcher's version
```

### AC-9
```
Given the reconcile feature is live
When a dispatcher uses it
Then the experience should be intuitive and error handling should be robust
  and the flow should be accessible
  and performance should be good
```

### AC-10
```
Given a re-route was performed 45 seconds ago
When the dispatcher taps "Undo"
Then the re-route is reversed
  and the tech's original assignment is restored on the board
  and an entry "re-route undone" is appended to the visible re-route log
```

### AC-11
```
Given a dispatcher whose role lacks the reconcile.write scope
When they tap "Reconcile all"
Then the action is blocked and a message explains they lack permission to submit reconciles
```

### AC-12
```
Given a reconcile batch of 47 tickets (more than the modal lists at once)
When the dispatcher taps "Reconcile all"
Then the modal opens with the first 25 tickets pre-selected
  and a banner reads "22 more tickets — load more"
  and tapping the banner appends the next 25 below
```

---

## Triage worksheet

| AC | Failure mode(s) or "clean" | If failing: your rewrite |
|:--:|----------------------------|--------------------------|
| 1 | | |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |
| 6 | | |
| 7 | | |
| 8 | | |
| 9 | | |
| 10 | | |
| 11 | | |
| 12 | | |

**Most common failure mode in this pack:** ______________________
**Why it's the most common failure in real PRDs (one sentence):** ______________________
