# Day 2 — Writing Granular Acceptance Criteria

> **Activity packet** for participant triads. Today's job: take your §§1–5 draft from Day 1 and write 8–12 testable Acceptance Criteria in Given/When/Then form. By 16:00, the AC section is shareable; tomorrow we add NFRs.

## Where we are in the week

Day 1 produced sections 1–5 of the PRD. Today produces section 6 — the Acceptance Criteria. AC are where most PRDs go from "interesting idea" to "implementable contract." A good AC section is the difference between an engineer scoping confidently and an engineer raising 30 questions in standup.

## The non-AI rule (still in force)

No generative tools today. Spell-check is fine. Last-week artifacts and Day-1 PRD draft are inputs.

---

## What an Acceptance Criterion is (and isn't)

An AC is a **testable assertion** about the system's behavior in a specific situation. It has three parts:

```
Given <a precondition / starting state>
When <an action or event happens>
Then <an observable, falsifiable result>
```

| Is | Is not |
|----|--------|
| Testable (you can write a test that passes/fails) | "The system should be intuitive" |
| Specific to one behavior | "The system handles errors well" |
| Implementation-agnostic | "Use Redis to cache the response" |
| Falsifiable (you can prove it wrong) | "Performance should be good" |

---

## The 5 AC failure modes (today's mental model)

| Failure | What it looks like | Fix |
|---------|--------------------|-----|
| **1. Vague ("intuitive", "fast", "easy")** | "Then the user has a good experience" | Replace with measurable outcome |
| **2. Untestable (no observable result)** | "Then the user feels confident" | Anchor to a system-visible action or state |
| **3. Restating the goal** | "Then dispatchers reconcile faster" | Pin to a specific in-system event, not a metric |
| **4. Multi-condition (AND-soup)** | "Then X and Y and Z and W happen" | Split into multiple ACs |
| **5. Implementation-prescriptive** | "Then a Redis cache hit returns…" | Describe behavior, not implementation |

A good triad will produce AC that fail **none** of these five failure modes.

---

## The "happy path / sad path / weird path" coverage

A complete AC section covers three categories of scenario:

| Path | Question | Typical AC count |
|------|----------|------------------|
| **Happy** | What does success look like end-to-end? | 3–5 |
| **Sad** | What happens when the user does the wrong thing or input is invalid? | 2–4 |
| **Weird** | What about network drops, partial data, race conditions, edge cases the user wouldn't think of? | 2–4 |

Triads should aim for **8–12 AC total** with this coverage shape.

The "weird path" is where TPMs earn their seat. PMs who don't think technically miss it. Engineers who don't think about users miss it differently.

---

## Activity 1 — AC Triage

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Calibrate the eye for the 5 failure modes by triaging real-world AC examples before drafting your own.

### Setup
Each triad receives the **AC Triage Pack**: 12 AC examples drawn from real (anonymized) PRDs. Some are good. Some have one of the 5 failures. A few have multiple.

### Triad protocol

1. For each AC: identify which failure mode(s) are present (or "clean")
2. For each failed AC: rewrite it
3. Pick the most common failure mode in your pack — be ready to explain why it's the most common in real PRDs

### Sample items in the triage pack

- `Given the user is logged in, When they reach the dashboard, Then it loads quickly.`
- `Given a dispatcher with 3+ open tickets, When they tap "Reconcile all", Then the modal opens with all 3 tickets pre-selected and shows the count "3 selected" in the header.`
- `Given any user, When they use the system, Then they should feel productive.`
- `Given a network drop, When the user submits the form, Then the data is queued via WebSocket retry mechanism.`
- `Given a duplicate ticket, When the API receives it, Then 409 Conflict is returned with the original ticket ID in the body.`

### Readout (60 seconds per triad)

> "The most common failure in our pack was [X]. Our cleanest rewrite was [example]."

### Deliverable

12 triaged AC with failure-mode labels, plus rewrites for each failing AC and a one-sentence note on the most common failure.

---

## Activity 2 — Happy-Path AC for Your PRD

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
Write the 3–5 happy-path AC for the triad's PRD. These are usually the easiest — get them out of the way first.

### Setup
Each triad needs their §5 solution sketch from Day 1, the AC template card, and the 5-failure-mode checklist. No AI.

### Triad protocol

1. **Identify the happy path** (5 min). Re-read §5 from yesterday. The 4–8 step flow becomes the basis for AC.
2. **Solo drafts** (15 min). Each member writes 3 happy-path AC alone.
3. **Pool, de-dupe, refine** (15 min). The triad converges on 3–5 final happy-path AC.
4. **Failure-mode check** (5 min). Run each AC through the 5-failure list.

### What "good" looks like

- Each AC is one Given/When/Then with no ANDs in the Then
- Each AC names the exact system state, screen, or event
- A junior engineer could read the AC and write a test against it

### Deliverable

3–5 happy-path AC in Given/When/Then form, each passing the 5-failure-mode check, appended to PRD §6.

### Worked FieldPulse example (happy path)

```
Given a dispatcher viewing the end-of-shift summary
When they tap "Reconcile all"
Then the reconcile modal opens within 1 second
  and shows all open tickets pre-selected
  and the header shows the count of tickets selected
```

(The "and"s here are part of one observable state, not separate behaviors. This is a judgment call — split if the "ands" represent different system actions.)

---

## Activity 3 — Sad-Path and Weird-Path AC

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Cover the failure modes — what goes wrong when the user, the network, or the data does something unexpected.

### Setup
Each triad needs the happy-path AC from Activity 2 and the sad/weird-path generator prompts. No AI.

### The sad-path generator

For each happy-path AC, ask:

- What if the **input is invalid**?
- What if the **user lacks permission**?
- What if the **user cancels mid-flow**?
- What if the **data is missing or stale**?

### The weird-path generator

For each happy-path AC, ask:

- What if the **network drops** mid-action?
- What if **two users do the same thing simultaneously** (race)?
- What if the **action takes longer than expected** (timeout)?
- What if the **upstream system is down**?
- What if the **user is at the boundary** (max characters, max items, empty)?

### Triad protocol

1. **Solo sad-path drafts** (10 min). Each member produces 2 sad-path AC for the triad's PRD.
2. **Solo weird-path drafts** (10 min). Each member produces 2 weird-path AC.
3. **Pool and cull to 4–6** (10 min). 2–4 sad, 2–4 weird.
4. **Failure-mode check** (10 min). The 5 failure modes again.

### Worked FieldPulse examples

**Sad path:**
```
Given a dispatcher with 0 open tickets
When they tap "Reconcile all"
Then a non-modal toast appears with text "No tickets to reconcile"
  and the dispatcher remains on the summary screen
```

**Weird path:**
```
Given a dispatcher with 47 open tickets (more than the modal can list)
When they tap "Reconcile all"
Then the modal opens with the first 25 tickets pre-selected
  and a banner reads "22 more tickets — load more"
  and a tap on the banner appends the next 25 below
```

### Deliverable

2–4 sad-path AC and 2–4 weird-path AC appended to PRD §6, each passing the 5-failure-mode check.

---

## Activity 4 — AC Cross-Review

**Format:** Triad-pair &bull; **45 min** + Wrap &bull; Block 4

### Purpose
Apply the calibrated eye to *another triad's* AC. Cross-review surfaces failure modes the author triad has gone blind to.

### Setup
Instructor pre-assigns triad pairs. Each triad needs their own §§1–6 (incl. AC) and a printed review template. No AI.

### The protocol

1. **Pair triads** (instructor assigns).
2. **Swap AC sections** (5 min). Read the other's PRD §§1–5 first for context, then their AC.
3. **Review pass — identify failures** (15 min). For each AC:
    - Which failure mode (if any)?
    - Which path (happy / sad / weird) is *missing*?
    - Is there an implicit AC the author triad didn't write?
4. **Author triad responds** (10 min). For each finding: adopt / defer / push back.
5. **Authors revise** (15 min). Update the AC section.

### Output

- A revised AC section (8–12 ACs)
- A short **review-resolution note** at the bottom of §6 listing what was adopted, deferred, or rejected (and why)

### Wrap (last 15 min)

Each triad shares **one AC** they're proudest of and **one** they're least sure about. The "least sure" share is the calibration — what does the room think about it?

---

## End-of-day checkpoint

Each triad leaves the day with their PRD updated to include:

- [x] Section 6 with **8–12 testable AC** in Given/When/Then form
- [x] Coverage spans happy / sad / weird paths
- [x] All AC pass the 5-failure-mode check
- [x] A review-resolution note documenting changes from peer review
