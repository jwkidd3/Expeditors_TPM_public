# Sad-Path & Weird-Path Generator Prompts

> **Day 2 · Activity 3 handout.** For each happy-path AC you wrote, run these prompts to generate the sad-path and weird-path AC that complete your coverage. Aim for 2–4 sad and 2–4 weird. The weird path is where TPMs earn their seat.

---

## The sad-path generator

For each happy-path AC, ask:

- What if the **input is invalid**?
- What if the **user lacks permission**?
- What if the **user cancels mid-flow**?
- What if the **data is missing or stale**?

> **Watch out:** a sad-path AC must show an *observable recovery*. A "successful error" that's really the happy path in disguise doesn't count.

### Worked FieldPulse sad-path AC

```
Given a dispatcher with 0 open tickets
When they tap "Reconcile all"
Then a non-modal toast appears with text "No tickets to reconcile"
  and the dispatcher remains on the summary screen
```

---

## The weird-path generator

For each happy-path AC, ask:

- What if the **network drops** mid-action?
- What if **two users do the same thing simultaneously** (race)?
- What if the **action takes longer than expected** (timeout)?
- What if the **upstream system is down**?
- What if the **user is at the boundary** (max characters, max items, empty)?

### Worked FieldPulse weird-path AC

```
Given a dispatcher with 47 open tickets (more than the modal can list)
When they tap "Reconcile all"
Then the modal opens with the first 25 tickets pre-selected
  and a banner reads "22 more tickets — load more"
  and a tap on the banner appends the next 25 below
```

---

## Generator worksheet

| Happy-path AC | Prompt applied | New sad/weird AC (Given/When/Then) |
|---------------|----------------|-------------------------------------|
| | | |
| | | |
| | | |
| | | |

> Run every generated AC through the **5-failure-mode check** before appending to Section 6.
