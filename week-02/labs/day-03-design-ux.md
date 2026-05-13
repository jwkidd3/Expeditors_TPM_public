# Day 3 — Product Design & UX Principles for TPMs

> **Activity packet** for facilitators and participant triads. Today's job: equip TPMs to partner credibly with design — to spot UX failures, name them in the right vocabulary, and ship 3 design principles their squad can hold the line on.

## Where we are in the week

Days 1–2 produced a Metrics Tier Sheet and a defensible North Star. Today the triads zoom into the **product surface** — the actual screens, flows, and moments where the strategy meets the user.

A TPM is not a designer. But a TPM who cannot tell a designer why a UX choice matters, in design vocabulary, will lose every trade-off conversation. That's today's muscle.

## Inputs

- The triad's NS and Tier Sheet (from Days 1–2)
- One product surface (FieldPulse mobile, FieldPulse web, or a competitor like Housecall Pro / ServiceTitan) — chosen by the triad before today
- The **UX Heuristics Card** (handout)
- The **A11y Floor Checklist** (handout)

---

## The UX Heuristics Card (today's reference)

We use Nielsen's 10 heuristics as the shared vocabulary, plus three TPM-specific lenses we add on top.

**Nielsen's 10 (abbreviated):**

1. Visibility of system status
2. Match between system and real world
3. User control and freedom (undo)
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose, recover from errors
10. Help and documentation

**TPM-specific lenses (added today):**

11. **Time-to-first-value:** can a new user produce a useful result in their first session?
12. **Failure-mode dignity:** how does the product behave when the network drops, the data is wrong, or the user is rushed?
13. **Power-user respect:** does the product reward repeat use with shortcuts, or punish it with the same friction every time?

---

## Activity 1 — Heuristic Hunt

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Calibrate the room on the Nielsen 10 by hunting violations in a live product before they audit their own.

### Setup
Each triad uses the **same** product (we recommend a B2B SaaS the cohort doesn't already use — e.g., a niche CRM trial). The triad walks through one core flow (signup → first action → return).

### The protocol

1. Each triad member silently captures **3 heuristic violations** (5 min)
2. Triad pools and de-dupes (10 min)
3. Triad picks the **single most painful** violation and the **single most subtle** one (10 min)
4. Prepare a 60-second readout (5 min)

### Readout (60 sec per triad)

> "The most painful violation we found was [X]. The most subtle was [Y] — we almost missed it because [reason]."

### Deliverable

A short list per triad: 3+ heuristic violations with the heuristic number named, plus one "most painful" and one "most subtle" call.

### Facilitation cues

- If two triads pick the same violation, ask the second one: "What did you see that the first triad missed?" — sharpens observation.
- If a triad picks "the colors are ugly" — redirect to a heuristic. "Aesthetic" is in the list, but "I don't like the colors" is not the same.

---

## Activity 2 — A11y Floor Audit

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
TPMs at most companies inherit accessibility debt. Today we install the **non-negotiable floor** — the small set of checks a TPM should run before *any* PRD ships.

### The A11y Floor Checklist (8 items)

| Check | Tool | What "fail" looks like |
|-------|------|------------------------|
| All interactive elements keyboard-focusable | Tab through the page | Focus disappears or skips elements |
| Visible focus indicator | Tab through the page | No outline or visible state when focused |
| Color contrast 4.5:1 (text), 3:1 (large text) | Browser devtools / WebAIM | Light gray on white, blue-on-blue |
| Form fields have associated labels | Screen reader / inspect | "Edit text, blank" announced |
| Images have alt text | View source | `<img alt="">` on meaningful images |
| Page has a logical heading hierarchy | Outline tool | Jumps from `<h1>` to `<h4>` |
| Error messages identify the field | Submit a broken form | "Error" with no field reference |
| Touch targets &ge; 44px on mobile | DevTools mobile view | Buttons too small to tap reliably |

### Triad protocol

1. Open the FieldPulse mobile (or chosen surface) on each member's device
2. Each member runs **3 of the 8 checks** (assign so all 8 are covered, plus one overlap)
3. Pool findings; for each fail, identify which UX heuristic is also being violated
4. Output: a one-page **A11y Floor Audit** for the chosen surface

### Why TPMs care

Accessibility is a regulatory floor (ADA / Section 508 / EAA), an SEO floor, and a usability ceiling — fixes for keyboard-focus often fix mouse-user errors too. This audit is the kind of artifact TPMs are expected to surface unsolicited.

### Deliverable

A one-page A11y Floor Audit per triad: each of the 8 checks rated pass/partial/fail with a heuristic cross-link for every fail.

### Facilitation cues

- Most cohorts under-rate a11y findings on first pass. If a triad reports "all pass," ask them to try the keyboard-only flow themselves.
- Push the triad that finishes early to convert fails into severity scores — that's the bridge to Activity 3.

---

## Activity 3 — Heuristic Audit of Your Triad's Surface

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Apply the calibrated eye from Activity 1 + the floor from Activity 2 to the triad's chosen product surface.

### Setup
Each triad opens its chosen flow (FieldPulse mobile, web, or competitor). All three triad members need access.

### Steps

1. **Solo walk-through (10 min).** Each member captures 3+ findings independently.
2. **Pool + score severity (15 min).** Consolidate findings; assign 1–5 severity per the guide.
3. **Write up (10 min).** Fill the template — top 3 violations, top 3 strengths, A11y result, TPM lenses.
4. **Question for design (5 min).** Name the one question that only the design team can answer.

### The audit template

```markdown
# UX Audit: <Product surface>
**Auditor triad:** <names>
**Flow audited:** <e.g., "Dispatcher first-time reconcile flow">

## Top 3 violations
| # | Heuristic | What we observed | Why it matters | Severity (1–5) |
|---|-----------|-------------------|----------------|----------------|
| 1 | … | … | … | … |
| 2 | … | … | … | … |
| 3 | … | … | … | … |

## Top 3 strengths
> Things this product does *better than the average B2B SaaS*. Name and praise.

## A11y floor result
> Pass / Partial / Fail (per A11y Floor Checklist). List failed checks.

## TPM lens findings (Heuristics 11–13)
- **Time-to-first-value:** …
- **Failure-mode dignity:** …
- **Power-user respect:** …

## One question we cannot answer without the design team
> …
```

### Severity scoring guide

| Score | Meaning |
|-------|---------|
| 5 | Causes user task failure or data loss |
| 4 | Causes recurring frustration that users work around |
| 3 | Slows users down; they don't notice but a stopwatch would |
| 2 | Cosmetic; affects trust |
| 1 | Edge case |

### Deliverable

A completed UX Audit per triad covering top 3 violations (severity-scored), top 3 strengths, A11y result, TPM lens findings, and one design-only question.

### Facilitation cues

- Force the strengths column. Most triads default to a kill list and lose designer trust before they've earned it.
- Watch severity scoring drift. A "5" should be rare; if a triad scores three things at 5, push them to differentiate.

---

## Activity 4 — From Audit to Design Principles

**Format:** Triad &bull; **45 min** + Readouts &bull; Block 4

### Purpose
Convert the audit findings into **3 design principles** the squad can hold the line on across PRDs. This is the day's keeper artifact.

### Setup
Each triad has its completed UX Audit from Activity 3 and a way to write the principle cards (paper or digital).

### Steps

### What a design principle looks like

A good design principle is:

- A **statement**, not a feature
- **Decision-making** — it tells you what to choose when two options compete
- Phrased in the **product's voice**, not the framework's
- **Memorable** — short enough that an engineer would quote it back

### Examples (good and bad)

| Good | Why | Bad | Why |
|------|-----|-----|-----|
| "If a dispatcher can't recover from a mis-tap in 1 second, we built it wrong." | Decision-making, specific, memorable | "Be user-friendly" | Vacuous |
| "Show the network state on every screen — assume connectivity is broken." | Drives concrete choices | "Use Material Design" | A toolkit, not a principle |
| "Power users get keyboard shortcuts. New users get them visible too." | Tension named and resolved | "Be consistent" | True but not actionable |

### Triad protocol

1. **Cluster audit findings** (10 min). Group your findings into themes — each theme suggests a principle.
2. **Draft 5 candidate principles** (15 min). Some will be bad. That's fine.
3. **Cull to 3** (10 min). Test each: does it tell us what to choose when two options compete?
4. **Write the principle card** (10 min). Each principle gets one line + one example of a decision it would force.

### Readout structure (90 seconds per triad)

> 1. "Our top audit finding was [X], severity [N]."
> 2. "The 3 principles we'd hold the squad to are: [P1], [P2], [P3]."
> 3. "The principle that would cause the most disagreement with our designers is [P_x] because [why]."

### Deliverable

A 3-Principle Card per triad: each principle as one line + one decision it would force.

### Facilitation cues

- Pin the **3-Principle Cards** alongside the NS Defense Cards. Tomorrow's AI strategy work and Friday's journey map both reference them.
- Refuse "be consistent" or "be user-friendly" — they fail the decision test. The triad must rewrite before locking.

---

## End-of-day checkpoint

Each triad leaves the day with:

- [x] A heuristic-violation finding from Activity 1 (live calibration)
- [x] An A11y Floor Audit for one surface
- [x] A UX Audit (top 3 violations + 3 strengths + TPM lenses)
- [x] **Three design principles** the squad would hold the line on
- [x] At least one open question for the design team

## Facilitator reflection prompts (end of day)

- Which triad fell into the "I just don't like it" trap? They need help converting reaction to vocabulary tomorrow.
- Which triad's principles are the sharpest? Pull one as a positive example for Friday.
- Did anyone treat A11y as optional? That's a Week 4 risk to head off now.
