# Sprint-Review Template (DP §3)

> **Day 3 · Activity 2 handout.** Design the 2-week sprint review where outputs *and* outcomes are inspected together — not just velocity.

A typical sprint review covers six sections. The TPM-owned twist: **at least one section is about outcome**, not output. The team sees the leading indicators next to the velocity.

## The six sections

1. **What shipped** (outputs) — pull from the "Done in this sprint" query.
2. **What's still open** — pull from the "Open in current sprint" query.
3. **Velocity** — points completed.
4. **Leading indicators** — which moved? Which didn't?
5. **Anomalies** — unusual patterns from the week.
6. **Adjustments for next sprint** — what to do differently.

---

## Fill-in structure

```markdown
## Sprint Review — <feature> — Sprint <N> (<dates>)

### 1. What shipped (outputs)
<from "Done in this sprint" query>

### 2. What's still open
<from "Open in current sprint" query>

### 3. Velocity
Points completed: <X>   |   Rolling average: <Y>

### 4. Leading indicators
| Indicator | Last sprint | This sprint | Moving right? |
|-----------|-------------|-------------|---------------|
| <indicator> | <value> | <value> | 🟢 / 🟡 / 🔴 |

### 5. Anomalies
<unusual patterns from the week>

### 6. Adjustments for next sprint
<what we'll do differently>
```

---

## The leading-indicator dashboard

Build a dashboard of **3–5 charts** (more = ignored). Each chart references one or more leading indicators. For each indicator, set a **threshold** — the point at which you say "this isn't moving; what should we change next sprint?"

| Leading indicator | Chart | Threshold that triggers a conversation |
|-------------------|-------|----------------------------------------|
| <indicator> | <chart> | <threshold + the conversation it starts> |

## What "good" looks like

- The template has **a slot for outcome**, not just output.
- The dashboard has **3–5 charts** — no more.
- Each chart has a **threshold** that triggers a specific conversation.
- The review has a **cadence anchor**: a day of week, a time, recurring.
