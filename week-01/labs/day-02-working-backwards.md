# Day 2 — Working Backwards

> **Activity packet for participant quads.** Day 2 produces a one-page PR/FAQ per quad and runs the first cross-quad critique of the academy.

## Prerequisite artifacts (from Day 1)

- Quad **Prompt Pattern Library** (at minimum: Research, Summarization, Critique-hat, Where-could-you-be-wrong)
- Day 3 research target question per quad
- Optional: a chosen product idea per quad (from the FieldPulse backlog list below)

## FieldPulse backlog — eligible product ideas

Pick any one per quad. Quads may also propose their own subject to facilitator approval.

1. **End-of-Day Reconcile** — guided flow for dispatchers to close out the day in 5 min
2. **Mid-Day Re-Route** — AI-assisted tech re-routing when someone calls out sick
3. **Tech-First Messaging** — replace dispatcher-tech phone/text with in-app async
4. **Offline Ticket Capture** — tech mobile app works on zero connectivity, syncs on reconnect
5. **Inventory True-Up** — automatically reconciles truck stock vs. parts used per job
6. **Customer Follow-Up** — post-visit check-in that routes dissatisfaction to a dispatcher
7. **Tech Onboarding Fast Lane** — 20-min-or-less onboarding for a new hire

---

## Activity 1 — Forward or Backward?

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Before drafting, calibrate what the difference feels like in practice by analyzing 4 short vignettes.

### Setup
Your quad has the four vignettes below (also available as the handout `week-01/handouts/working-backwards-vignettes.md`). Have a way to take quick notes — paper or shared doc is fine.

### Steps

1. **Read (10 min).** Each quad member reads all four vignettes silently.
2. **Sort (5 min).** Tag each vignette: forward, backward, or ambiguous.
3. **Discuss (10 min).** For each: what's the one question that, if asked earlier, would have changed the outcome?
4. **Full-room debrief (5 min).** Cohort-wide discussion of vignettes C and D.

### Vignettes

1. **Vignette A** — A dispatch-tool founder, after hearing customers complain about mobile app speed, built a native iOS rewrite over two quarters. At launch, 40% of techs still used the web view because they'd switched Android mid-project.

2. **Vignette B** — A PM wrote a one-page mock press release for "OfflineFirst Ticket Capture" and circulated it to five techs for reaction. Three said they'd already built paper workarounds; two said the app's login flow was the real blocker. The PR was re-scoped to login before offline.

3. **Vignette C** — Engineering discovered a faster map-tile rendering library and shipped it as a mid-sprint improvement. Dispatcher satisfaction bumped 12 points in next-survey.

4. **Vignette D** — A PM drafted a PR/FAQ for "Tech-First Messaging" and had AI generate three customer quotes. The quotes all used marketing language no tech would say. The PM skipped persona research and shipped anyway.

### Debrief questions (full room, 15 min)

- Which vignettes are clearly forward? Clearly backward?
- C and D are designed to be ambiguous. Why does each matter?
- For each, what's the **one question that, if asked earlier, would have changed the outcome**?

### Deliverable

A one-sentence "earlier question" per vignette, recorded by the quad and surfaced in the cohort debrief.

---

## Activity 2 — Headline + Sub-headline

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Produce three candidate headlines, then use AI to critique them on three axes. Pick one.

### Setup
Your quad has chosen (or will pick now) one product idea from the backlog above. Confirm AI assistant access.

### Steps

1. Pick a product idea from the backlog (or a quad's own)
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

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Complete a draft PR paragraph + customer quote + 6 FAQ entries.

### Setup
Your quad has its chosen heading/sub-headline from Activity 2. Use the PR template below.

### Steps

1. **Plan (10 min).** Map the heading/sub-heading to the rest of the template; identify the riskiest section.
2. **Draft (25 min).** Fill the template — Summary, Problem, Solution, Customer quote, both FAQs.
3. **Self-review (10 min).** Read aloud within the quad; tag every claim with an evidence tier.

### Template

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

### Deliverable

A complete one-page PR/FAQ per quad: heading, sub-headline, three paragraphs, customer quote, 3 customer FAQs, 3 internal FAQs, and an Evidence log.

---

## Activity 4 — Cross-Quad PR/FAQ Review

**Format:** Paired quads &bull; **60 min** &bull; Block 4

### Purpose
Two quads exchange PR/FAQs and run the academy's first cross-quad critique. The critique protocol is what makes it productive instead of defensive.

### Setup
Pair with another quad. Both quads have a completed PR/FAQ from Activity 3 and a stopwatch (phone is fine).

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

### Readout (60 seconds per quad)

> "We changed X because the reviewer helped us see Y. We left Z because we disagreed for this reason."

### Failure-mode rubric (reviewers use this as their check)

| Failure | If present… |
|---------|-------------|
| Generic customer | Push the author for role + context + evidence |
| Category problem | Replace noun with verb; give an example |
| Benefit bouquet | Make them choose one; defend it |
| Handwave evidence | Ask for the tier; push for the source |
| Feature description | Ask them to describe the moment of use, not the tool |

### Deliverable

A revised PR/FAQ per quad with documented changes (what changed, what was left, and why) plus a 60-second readout.

---

## End-of-day checkpoint

- [x] Each quad has a completed one-page PR/FAQ + FAQ entries + Evidence log
- [x] Each quad has been critiqued by one other quad and has documented what they changed/left
- [x] Each quad has identified their **most worrying unvalidated assumption** (the one that keeps their PR from being fully defensible)

## Bridge to Day 3

The PR customer quote is Day 3 persona input. The "most worrying unvalidated assumption" is the first thing to interrogate with the Day 3 validation protocol.
