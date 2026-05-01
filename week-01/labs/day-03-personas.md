# Day 3 — Building & Validating Personas

> **Activity packet** for facilitators and participant triads. Day 3 produces a validated persona per triad and trains the core validation-interview muscle.

## Prerequisite artifacts (from Day 2)

- Completed triad PR/FAQ (including customer quote, FAQs, Evidence log)
- "Most worrying unvalidated assumption" sentence from end of Day 2

## Materials for the day

### FieldPulse Research Packet (distributed at start of day)

Each triad receives:

1. **Dispatcher Interview A** — "Maria R., 12yr dispatcher, 90-tech shop" (1 page, 8 excerpted quotes, 3 behaviors observed)
2. **Dispatcher Interview B** — "Trey W., 3yr dispatcher, former tech, 60-tech shop" (1 page, 6 quotes, 2 behaviors)
3. **Dispatcher Interview C** — "Susana O., 18yr dispatcher, 160-tech shop, owner's daughter" (1 page, 7 quotes, 3 behaviors)
4. **Ride-along field note** — 1-page observation of Maria for a Tuesday shift
5. **Screen-time analytics excerpt** — 1 chart showing average time-in-app per section, aggregated across 90 dispatchers

### Persona Validation Canvas

Provided as a printable sheet (one per triad, A3 recommended; digital template also in this folder as `canvas.md` — see below). The canvas has six boxes:

1. Role & context
2. Goals (in their words)
3. Current behavior (observed)
4. Constraints
5. Pain points (verb + circumstance + consequence)
6. Assumptions to validate

Each box has a column on the right for evidence tier tags.

---

## Activity 1 — Persona Triage

**Format:** Triad &bull; **30 min** &bull; Block 1

### The three provided personas

> Distribute a single handout: three personas on one page each.

1. **Persona 1 — "Dispatcher Diana"** *(intentionally weak, demographic-heavy)*
   - 35 years old, married, two kids
   - Drives a Honda CR-V
   - Busy, tech-savvy, loves efficiency tools
   - Wants to feel appreciated at work

2. **Persona 2 — "Reliable Rita"** *(intentionally decent, behavioral)*
   - Lead dispatcher, 50–120 tech HVAC
   - Observed: retypes paper tickets into system after shift (6/8 ride-alongs)
   - Reported: "mid-day re-routes are my worst hour" (7/10 interviews)
   - Workaround: keeps a paper map next to the monitor
   - Assumption: distrusts software that hides inventory (inferred from 3 observations)

3. **Persona 3 — "Tech-lead Tom"** *(misleading — mixes real behaviors with stock adjectives)*
   - Junior technician, 2 years in trade
   - Observed: checks in at job sites via app 60% of the time
   - Reported: "my dispatcher doesn't know where my truck is half the time"
   - "Young, digital native, eager to learn new tools" ← adjective-salad
   - "Loves to be efficient" ← unfalsifiable

### Triad task (20 min)

For each persona:

1. Highlight every claim as **behavioral** / **demographic** / **adjectival**
2. Mark which claims would change a product decision
3. Rewrite the weakest persona (Diana) in 10 minutes using what you've seen of Rita's form

### Full-room debrief (10 min)

- Which persona changes the most decisions?
- Where does Tom's mixed form do harm?
- What's one element you'd add to any of them?

---

## Activity 2 — Build Your Persona

**Format:** Triad &bull; **45 min** &bull; Block 2

### Instructions

1. Review the FieldPulse Research Packet as a triad (10 min)
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

---

## Activity 3 — Role-Play Interviews

**Format:** Triad (rotating roles) &bull; **45 min** &bull; Block 3

### Setup — character cards

Each triad uses one set of three cards (provided in `character-cards.md` if running digital; print A5 otherwise). Each card has:

- Public surface: role, company size, tenure
- Hidden details: specific workarounds, frustrations, and a *wrong assumption the interviewer will carry into the room*

> Hidden details are only revealed to the "interviewee" role. Interviewers must surface them with good questions.

**Included characters:**

1. **Maria R.** — 12yr, 90-tech, hates mid-day re-routes, secretly uses a paper notebook for truck stock because the app's inventory view is 3 clicks deep
2. **Trey W.** — 3yr, former tech, will volunteer opinions confidently; some are wrong (genuinely misremembers how often re-routes happen)
3. **Susana O.** — 18yr, owner's daughter, constraint: shop owner insists on same-day reconcile but the real bottleneck is payroll's Wednesday deadline, not dispatch

### Rotation

| Round | Duration | Interviewer | Interviewee | Observer |
|-------|----------|-------------|-------------|----------|
| 1 | 7 min + 3 min debrief | Triad member 1 | Triad member 2 (using card) | Triad member 3 |
| 2 | 7 min + 3 min debrief | Triad member 2 | Triad member 3 | Triad member 1 |
| 3 | 7 min + 3 min debrief | Triad member 3 | Triad member 1 | Triad member 2 |

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

### Synthesis (15 min, triad)

After all three rounds:

- Which of your Box 6 assumptions did *not* survive contact with the characters?
- Which assumptions got **stronger** evidence?
- What bias patterns appeared repeatedly? Name them for yourselves.

---

## Activity 4 — JTBD Cross-Examination

**Format:** Paired triads &bull; **60 min** &bull; Block 4

### Step 1 — Draft JTBDs (15 min, within triad)

Write **two Jobs to Be Done** for your persona in the canonical form:

> When [circumstance], I want to [motivation], so I can [expected outcome].

### Step 2 — Cross-examination (25 min each direction)

Triads pair. One presents the persona + 2 JTBDs. The other plays "skeptical engineer" and runs the stress-test checklist:

1. For each JTBD, can the persona produce a concrete last-time-this-happened story?
2. Does the persona's current behavior explain what they "hire" today (even if it's paper)?
3. If your product didn't exist, what would they do instead? Is that a credible fallback?
4. What would have to be true for them to **fire** your product?

Every "I don't know" goes on a **parking lot of open validation questions**.

### Step 3 — Revise (bring back to own triad, 10 min)

- Downgrade or remove unsupported claims
- Move failed claims to Box 6 (Assumptions) or delete entirely
- Update evidence tiers

### Readout (60 sec per triad)

> "One claim we upgraded: …. One claim we had to drop: …"

### Facilitator note

Celebrate triads who drop a claim publicly. This is the hardest thing we ask all week and the most important signal of intellectual honesty.

---

## End-of-day checkpoint

- [x] Completed Persona Validation Canvas per triad
- [x] At least 5 candidate pain points (tagged, sourced) in Box 5
- [x] Parking lot of open validation questions saved
- [x] Observer bias tallies reviewed within each triad

## Bridge to Day 4

Box 5 (pain points) is the direct input to Day 4's extraction activity. Each triad should leave Day 3 with **at least 5 candidate pains**, each phrased as verb + circumstance + consequence. Don't let anyone leave without that.
