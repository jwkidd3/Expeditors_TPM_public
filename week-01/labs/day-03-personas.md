# Day 3 — Building & Validating Personas

> **Activity packet for participant quads.** Day 3 produces a validated persona per quad and trains the core validation-interview muscle.

## Prerequisite artifacts (from Day 2)

- Completed quad PR/FAQ (including customer quote, FAQs, Evidence log)
- "Most worrying unvalidated assumption" sentence from end of Day 2

## Materials for the day

### FieldPulse Research Packet (distributed at start of day)

Each quad receives:

1. **Dispatcher Interview A** — "Maria R., 12yr dispatcher, 90-tech shop" (1 page, 8 excerpted quotes, 3 behaviors observed)
2. **Dispatcher Interview B** — "Trey W., 3yr dispatcher, former tech, 60-tech shop" (1 page, 6 quotes, 2 behaviors)
3. **Dispatcher Interview C** — "Susana O., 18yr dispatcher, 160-tech shop, owner's daughter" (1 page, 7 quotes, 3 behaviors)
4. **Ride-along field note** — 1-page observation of Maria for a Tuesday shift
5. **Screen-time analytics excerpt** — 1 chart showing average time-in-app per section, aggregated across 90 dispatchers

### Persona Validation Canvas

Provided as a printable participant handout (one per quad, A3 recommended): `week-01/handouts/persona-validation-canvas.md` (also built to `.pdf`). The canvas has six boxes:

1. Role & context
2. Goals (in their words)
3. Current behavior (observed)
4. Constraints
5. Pain points (verb + circumstance + consequence)
6. Assumptions to validate

Each box has a column on the right for evidence tier tags.

---

## Activity 1 — Persona Triage

**Format:** Quad &bull; **30 min** &bull; Block 1

### Purpose
Calibrate the quad's eye for behavioral vs demographic vs adjectival persona claims before they build their own.

### Setup
Your quad has the three provided personas below (also available as the handout `week-01/handouts/sample-personas.md`, one page each). You'll need colored pens or a digital equivalent for marking up claims.

### Steps

1. **Mark up (15 min).** For each persona, highlight every claim as behavioral, demographic, or adjectival; circle the ones that would change a product decision.
2. **Rewrite (10 min).** Rewrite the weakest persona using the strongest one's evidence-tagged form.
3. **Debrief (5 min).** Full-room: which persona changes the most decisions, and why?

### The three provided personas

1. **Persona 1 — "Dispatcher Diana"**
   - 35 years old, married, two kids
   - Drives a Honda CR-V
   - Busy, tech-savvy, loves efficiency tools
   - Wants to feel appreciated at work

2. **Persona 2 — "Reliable Rita"**
   - Lead dispatcher, 50–120 tech HVAC
   - Observed: retypes paper tickets into system after shift (6/8 ride-alongs)
   - Reported: "mid-day re-routes are my worst hour" (7/10 interviews)
   - Workaround: keeps a paper map next to the monitor
   - Assumption: distrusts software that hides inventory (inferred from 3 observations)

3. **Persona 3 — "Tech-lead Tom"**
   - Junior technician, 2 years in trade
   - Observed: checks in at job sites via app 60% of the time
   - Reported: "my dispatcher doesn't know where my truck is half the time"
   - "Young, digital native, eager to learn new tools"
   - "Loves to be efficient"

### Quad task (20 min)

For each persona:

1. Highlight every claim as **behavioral** / **demographic** / **adjectival**
2. Mark which claims would change a product decision
3. Rewrite the weakest persona in 10 minutes using the strongest one's form

### Full-room debrief (10 min)

- Which persona changes the most decisions?
- Where does a mixed-form persona do harm?
- What's one element you'd add to any of them?

### Deliverable

A marked-up handout per quad plus a one-paragraph rewrite of the weakest persona in the strongest one's behavioral-evidence form.

---

## Activity 2 — Build Your Persona

**Format:** Quad &bull; **45 min** &bull; Block 2

### Purpose
Take the FieldPulse Research Packet and produce a canvas-format persona that is evidence-tagged box by box.

### Setup
Your quad has the FieldPulse Research Packet (interviews A/B/C + ride-along + analytics) and the Persona Validation Canvas template. AI assistant access required for Boxes 5 and 6 only.

### Steps

1. Review the FieldPulse Research Packet as a quad (10 min)
2. Start with what you know (Boxes 1–4). Tag every claim.
3. Pull candidate pain points (Box 5) from interviews + ride-along
4. For Box 6, brainstorm assumptions you're carrying that need validating
5. Use AI **only for Box 5 and 6**, with the grounding prompt below
6. Circle the **3 claims you'd most want to validate with a real dispatcher**

### Grounding prompt (from Day 1 library, apply verbatim)

```
Role: Research assistant helping a TPM build an evidence-grounded persona.
Context:
  - The user role is Lead Dispatcher at a 50–200 tech HVAC company.
  - Observed behaviors: [paste ride-along notes]
  - Reported statements: [paste 6 interview excerpts]
Constraints:
  - Do NOT invent behaviors or quotes.
  - Every claim in your output must cite one of the notes or quotes above, OR be flagged as Inferred.
  - If you generate any claim not grounded in the inputs, tag it AI-generated with a note: "validate before use."
Format: Persona Validation Canvas (6 sections).
```

### Canvas template (drop into your tool of choice)

```markdown
# Persona: [short descriptive handle — behavior-based, not a name]

## 1. Role & context
- …  *(tier)*

## 2. Goals (in their words)
- "…"  *(tier + source)*

## 3. Current behavior (observed)
- …  *(tier + source)*

## 4. Constraints
- …  *(tier)*

## 5. Pain points — verb + circumstance + consequence
- "[role] [verb] because [circumstance], which causes [consequence]"  *(tier + source)*

## 6. Assumptions to validate
- …  *(tier — usually Inferred or AI-generated)*
```

### Deliverable

A completed Persona Validation Canvas per quad: all six boxes filled, evidence-tagged, with three validation targets circled.

---

## Activity 3 — Role-Play Interviews

**Format:** Quad (rotating roles) &bull; **45 min** &bull; Block 3

### Purpose
Rehearse the validation-interview protocol on three character cards while a third quad member tallies bias traps.

### Setup — character cards

Each quad uses one set of three cards (participant handout `week-01/handouts/dispatcher-character-cards.md`, also built to `.pdf`; print A5). Each card has:

- **Public surface:** role, company size, tenure — everyone may read
- **Hidden details:** revealed **only to the "interviewee"** for that round. Interviewers must surface them with good questions — do not read the Hidden section of a card you're interviewing.

**Included characters (public surface):**

1. **Maria R.** — 12yr, 90-tech shop, reputation for keeping the branch running
2. **Trey W.** — 3yr, former tech, 60-tech shop, opinionated and quick to generalize
3. **Susana O.** — 18yr, owner's daughter, 160-tech shop, carries weight with the owner

### Rotation

| Round | Duration | Interviewer | Interviewee | Observer |
|-------|----------|-------------|-------------|----------|
| 1 | 7 min + 3 min debrief | Quad member 1 | Quad member 2 (using card) | Quad member 3 |
| 2 | 7 min + 3 min debrief | Quad member 2 | Quad member 3 | Quad member 1 |
| 3 | 7 min + 3 min debrief | Quad member 3 | Quad member 1 | Quad member 2 |

### The five validation questions (use in order)

1. Walk me through the last time you did X.
2. What was hardest about that?
3. What did you do to work around it?
4. How often does that happen?
5. If you could wave a wand, what would change?

### Observer tally sheet

Tick for each instance observed:

| Bias | Count |
|------|-------|
| Leading question ("Wouldn't it be great if…") | |
| Confirmation (skipping over disconfirming answers) | |
| Enthusiasm conflation ("they loved it!") | |
| Missed opportunity (interviewee hinted; interviewer didn't follow up) | |

### Synthesis (15 min, quad)

After all three rounds:

- Which of your Box 6 assumptions did *not* survive contact with the characters?
- Which assumptions got **stronger** evidence?
- What bias patterns appeared repeatedly? Name them for yourselves.

### Deliverable

A synthesized list per quad: assumptions confirmed, assumptions broken, and the bias patterns the observer caught most often.

---

## Activity 4 — JTBD Cross-Examination

**Format:** Paired quads &bull; **60 min** &bull; Block 4

### Purpose
Stress-test the persona by writing JTBDs for it and letting another quad attack them. This is the day's hardest exercise — and the most useful.

### Setup
Pair with another quad. Both quads have a completed persona canvas from Activity 2 and need a way to capture the parking lot of open validation questions.

### Step 1 — Draft JTBDs (15 min, within quad)

Write **two Jobs to Be Done** for your persona in the canonical form:

> When [circumstance], I want to [motivation], so I can [expected outcome].

### Step 2 — Cross-examination (25 min each direction)

Quads pair. One presents the persona + 2 JTBDs. The other plays "skeptical engineer" and runs the stress-test checklist:

1. For each JTBD, can the persona produce a concrete last-time-this-happened story?
2. Does the persona's current behavior explain what they "hire" today (even if it's paper)?
3. If your product didn't exist, what would they do instead? Is that a credible fallback?
4. What would have to be true for them to **fire** your product?

Every "I don't know" goes on a **parking lot of open validation questions**.

### Step 3 — Revise (bring back to own quad, 10 min)

- Downgrade or remove unsupported claims
- Move failed claims to Box 6 (Assumptions) or delete entirely
- Update evidence tiers

### Readout (60 sec per quad)

> "One claim we upgraded: …. One claim we had to drop: …"

### Deliverable

A revised persona canvas with at least one claim upgraded, one downgraded or dropped, and a captured parking lot of open validation questions.

---

## End-of-day checkpoint

- [x] Completed Persona Validation Canvas per quad
- [x] At least 5 candidate pain points (tagged, sourced) in Box 5
- [x] Parking lot of open validation questions saved
- [x] Observer bias tallies reviewed within each quad

## Bridge to Day 4

Box 5 (pain points) is the direct input to Day 4's extraction activity. Each quad should leave Day 3 with **at least 5 candidate pains**, each phrased as verb + circumstance + consequence. Don't let anyone leave without that.
