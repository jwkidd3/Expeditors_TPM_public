# Day 2 — Working Backwards

> **Activity packet** for facilitators and participant triads. Day 2 produces a one-page PR/FAQ per triad and runs the first cross-triad critique of the academy.

## Prerequisite artifacts (from Day 1)

- Triad **Prompt Pattern Library** (at minimum: Research, Summarization, Critique-hat, Where-could-you-be-wrong)
- Day 3 research target question per triad
- Optional: a chosen product idea per triad (from the FieldPulse backlog list below)

## FieldPulse backlog — eligible product ideas

Pick any one per triad. Triads may also propose their own subject to facilitator approval.

1. **End-of-Day Reconcile** — guided flow for dispatchers to close out the day in 5 min
2. **Mid-Day Re-Route** — AI-assisted tech re-routing when someone calls out sick
3. **Tech-First Messaging** — replace dispatcher-tech phone/text with in-app async
4. **Offline Ticket Capture** — tech mobile app works on zero connectivity, syncs on reconnect
5. **Inventory True-Up** — automatically reconciles truck stock vs. parts used per job
6. **Customer Follow-Up** — post-visit check-in that routes dissatisfaction to a dispatcher
7. **Tech Onboarding Fast Lane** — 20-min-or-less onboarding for a new hire

---

## Activity 1 — Forward or Backward?

**Format:** Triad &bull; **30 min** &bull; Block 1

### Purpose
Before drafting, calibrate what the difference feels like in practice by analyzing 4 short vignettes.

### Vignettes

> *(Hand out as a printed or shared document. Each vignette is 3–5 sentences.)*

1. **Vignette A** — A dispatch-tool founder, after hearing customers complain about mobile app speed, built a native iOS rewrite over two quarters. At launch, 40% of techs still used the web view because they'd switched Android mid-project. *(Forward — tool-first.)*

2. **Vignette B** — A PM wrote a one-page mock press release for "OfflineFirst Ticket Capture" and circulated it to five techs for reaction. Three said they'd already built paper workarounds; two said the app's login flow was the real blocker. The PR was re-scoped to login before offline. *(Backward — validated PR.)*

3. **Vignette C** — Engineering discovered a faster map-tile rendering library and shipped it as a mid-sprint improvement. Dispatcher satisfaction bumped 12 points in next-survey. *(Backward by accident — or forward but lucky? Force the debate.)*

4. **Vignette D** — A PM drafted a PR/FAQ for "Tech-First Messaging" and had AI generate three customer quotes. The quotes all used marketing language no tech would say. The PM skipped persona research and shipped anyway. *(Forward disguised as backward — the PR was fiction, not grounded fiction.)*

### Debrief questions (full room, 15 min)

- Which vignettes are clearly forward? Clearly backward?
- C and D are designed to be ambiguous. Why does each matter?
- For each, what's the **one question that, if asked earlier, would have changed the outcome**?

### Facilitator note

Protect Vignette D's discussion. The "fictional customer quote" is the most common PR/FAQ failure in practice — make sure the room names it.

---

## Activity 2 — Headline + Sub-headline

**Format:** Triad &bull; **45 min** &bull; Block 2

### Purpose
Produce three candidate hedlines, then use AI to critique them on three axes. Pick one.

### Instructions

1. Pick a product idea from the backlog (or a triad's own)
2. Draft **three** candidate PR heading + sub-headings (5 min per candidate)
3. Use the following prompt (adapted from your Pattern Library):

```
Role: A skeptical HVAC dispatcher reading the following three product announcement headlines.
Context:
  - You have been a dispatcher for 12 years.
  - You are cynical about new tools because you've been burned by three migrations.
  - You care about: time saved, trust from your shop owner, and not looking stupid in front of techs.
Task: For each of the three, answer:
  1. Would I actually click this email?
  2. What does this promise that might not deliver?
  3. Is this interchangeable with a competitor's marketing?
Format: Markdown table. Be direct.
```

4. Pick one candidate. Write **two sentences** defending the choice.

### Deliverable

The single chosen heading + sub-headline, pinned for use in Activity 3.

---

## Activity 3 — Answer the Five, Concretely

**Format:** Triad &bull; **45 min** &bull; Block 3

### Purpose
Complete a draft PR paragraph + customer quote + 6 FAQ entries.

### Template (provide to each triad)

```markdown
# [Heading from Activity 2]

## Sub-headline
[From Activity 2]

## Summary paragraph (3–4 sentences, as-if-launched)
…

## Problem paragraph (2–3 sentences; name the pain specifically)
…

## Solution paragraph (2–3 sentences; mechanism must be explicit)
…

## Customer quote
"…" — [Name], [Role], [Company]

## Customer FAQ (3 entries)
**Q:** …  
**A:** …

## Internal FAQ (3 entries)
**Q:** …  
**A:** …

## Evidence log (every claim gets a tier)
- Claim: … — Tier: [Observed | Reported | Inferred | AI-generated] — Source: …
```

### Rules

- Every factual claim in Summary/Problem/Solution gets a row in the Evidence log.
- Customer quote must be believably in-character — no marketing speak, no adjective-salad.
- Internal FAQ must include: riskiest assumption, build-estimate-and-evidence, 30%-adoption scenario.

---

## Activity 4 — Cross-Triad PR/FAQ Review

**Format:** Paired triads &bull; **60 min** &bull; Block 4

### The critique protocol (enforce)

| Minutes | Activity |
|---------|----------|
| 0–2 | Silent read. Reviewer marks 1 line they love, 1 they question. |
| 2–5 | "What I heard." Reviewer restates the product in one sentence. |
| 5–10 | Questions only. Reviewer asks, author listens and takes notes. **No defending.** |
| 10–15 | Author response. Author says what they'll change and what they'll leave (with reason). |

### Post-critique revision (15 min)

- Revise the PR/FAQ to address the highest-priority concern
- Update the Evidence log for any claim that changed tier

### Readout (60 seconds per triad)

> "We changed X because the reviewer helped us see Y. We left Z because we disagreed for this reason."

### Failure-mode rubric (reviewers use this as their check)

| Failure | If present… |
|---------|-------------|
| Generic customer | Push the author for role + context + evidence |
| Category problem | Replace noun with verb; give an example |
| Benefit bouquet | Make them choose one; defend it |
| Handwave evidence | Ask for the tier; push for the source |
| Feature description | Ask them to describe the moment of use, not the tool |

---

## End-of-day checkpoint

- [x] Each triad has a completed one-page PR/FAQ + FAQ entries + Evidence log
- [x] Each triad has been critiqued by one other triad and has documented what they changed/left
- [x] Each triad has identified their **most worrying unvalidated assumption** (the one that keeps their PR from being fully defensible)

## Bridge to Day 3

The PR customer quote is Day 3 persona input. The "most worrying unvalidated assumption" is the first thing to interrogate with the Day 3 validation protocol.
