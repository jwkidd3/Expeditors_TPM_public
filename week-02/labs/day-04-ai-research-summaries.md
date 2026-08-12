# Day 4 — Using AI for Strategy & Research Summaries

> **Activity packet for participant quads.** Today's job: take the Week-1 prompt patterns and use them at **strategy scale** — multi-source synthesis with traceable evidence — to produce a strategy brief for your FieldPulse problem.

## Where we are in the week

Week 1 taught prompting. Days 1–3 of Week 2 produced metrics, a North Star, and design principles. Today the quads use AI to **compile, summarize, and stress-test secondary research** — the kind of work that, done by hand, eats a TPM's full week.

Quads end the day with an **AI-Assembled Strategy Brief** that integrates everything from Week 1 forward. It's the input to Friday's journey-mapping work.

## Inputs

- The quad's NS Defense Card, Tier Sheet, and 3 design principles (Days 1–3)
- The quad's Week-1 problem statement and Prompt Pattern Library
- The **FieldPulse Research Pack** (handouts):
    - 3 anonymized dispatcher interview transcripts (~5 pages each)
    - 14 support tickets (already used Day 4 of Week 1)
    - 1 industry analyst report (5 pages)
    - 2 competitor product tour transcripts
    - 1 internal "voice of customer" Slack export (33 messages)

The Research Pack is realistic: noisy, redundant, partly contradictory. That's the point.

---

## The day's keeper artifact: the Strategy Brief

Each quad ends the day with a 2–3 page **AI-Assembled Strategy Brief**. The template:

```markdown
# Strategy Brief — <Problem area>
**Quad:** <names>  |  **NS:** <one line>

## Executive summary (5 bullets max, hand-written)
…

## Top 5 user pain themes (AI-summarized, evidence-tagged)
For each theme:
- **Theme:** <verb-based statement>
- **Evidence:** <source citations, e.g., "Interview A3, C2; Tickets T-04, T-11; #voice-of-customer 2025-09-12">
- **Confidence:** H / M / L
- **AI-generated?** Y/N (if Y: which prompt + what we did to validate)

## Competitive snapshot (AI-drafted, hand-edited)
| Competitor | Strength | Weakness | Where they beat us |
|------------|----------|----------|--------------------|

## Strategy implications (hand-written)
- What our NS implies for these themes
- Which design principle from Day 3 most directly addresses each theme
- One open question we still need humans for

## Provenance log
- Prompts used: link to quad's Pattern Library entries
- Manual validation steps taken
- Where the AI was wrong (named openly)
```

The **Provenance log** is mandatory. A strategy brief without it is fiction.

---

## Activity 1 — Multi-source Synthesis Drill

**Format:** Quad &bull; **45 min** &bull; Block 1

### Purpose
Practice the **summarize-with-evidence-tags** pattern at scale before applying it to the real research pack.

### Setup
Each quad gets a small "warm-up pack": **2 interview transcripts + 4 tickets** (from a different domain than FieldPulse — healthcare scheduling, to force generalization).

### Steps

1. **Single-prompt attempt** (10 min). One member writes a single prompt that asks the AI to extract top 5 themes with evidence citations from the warm-up pack. Run it.
2. **Inspect the output** (10 min). For each theme:
    - Did the AI cite real sources or invent them?
    - Did themes get over-generalized into mush?
    - Are any themes missing that you spotted yourself reading?
3. **Iterate the prompt** (25 min). Add one constraint per failure mode. Re-run. Compare.

### Deliverable

A **two-paragraph diagnosis** of the failure modes the quad observed, plus the iterated prompt that worked.

---

## Activity 2 — The Research Pack Pass

**Format:** Quad &bull; **50 min** &bull; Block 2

### Purpose
Apply the iterated prompt pattern to the **real FieldPulse Research Pack** and produce the first draft of the Pain Themes section.

### Setup
Each quad has its iterated prompt from Activity 1, the FieldPulse Research Pack, and AI assistant access (with the ability to split large pastes into multiple calls).

### Steps

1. **Pre-flight** (5 min). Re-read your iterated prompt from Activity 1. Confirm it includes:
    - Role
    - Context (what problem you're investigating)
    - Constraints (must cite source material; flag inferred themes)
    - Format (theme / evidence / confidence / AI-flag)
2. **Run** (25 min). Feed the Research Pack chunks into the AI. Note: most tools have a context limit — split the pack into 2–3 calls.
3. **Cross-validate** (15 min). Each member takes a different theme and verifies *every* citation against the source. Mark any that fail.
4. **Edit** (5 min). Cut themes with failed citations. Lower confidence on inferred themes.

### What "good" looks like for this output

- 5 themes (no fewer; the AI will naturally lump)
- Every theme cites at least 2 distinct sources
- No more than 1 theme is AI-only (no observed evidence) — and it's flagged as a hypothesis to validate
- Themes are verbs, not categories ("Cannot reconcile mid-route" beats "Reconcile UX")

### Deliverable

5 pain themes with citations, confidence ratings, and AI-flag — ready to drop into the Strategy Brief's Pain Themes section.

---

## Activity 3 — Competitive Snapshot

**Format:** Quad &bull; **50 min** &bull; Block 3

### Purpose
Use AI to do the most defensible part of competitive research: **structuring** information you already have access to. This is also the failure mode the AI is most frequently used for *poorly* — generating fake market data.

### Setup
Each quad has the competitor materials from the Research Pack (2 product tour transcripts + public pricing pages) and AI assistant access.

### The bright line

> AI can summarize and structure source material you provide. AI cannot tell you what your competitors actually do.

### The quad's two prompts

**Prompt 1 — "Structure what we know" (safe):**

```
Role: Competitive analyst.
Context: I'm pasting in two competitor product tour transcripts (ServiceTitan, Housecall Pro) plus their public pricing pages.
Task: Structure into a comparison matrix.
Constraints:
  - Only use facts from the materials I pasted; do not pull from your training data
  - Flag any cell where the source is silent (do not infer)
Format: Markdown table — Feature / ServiceTitan / Housecall Pro / Source citation
```

**Prompt 2 — "Tell us what's missing" (also safe):**

```
Continuing from above. Now: looking at the matrix you just built,
what are the THREE most important questions about these competitors
that the source materials do NOT answer? For each, suggest where a
TPM should look (analyst reports, customer interviews, public earnings calls).
```

### What NOT to ask

- "What is ServiceTitan's market share?"
- "Who is the leader in dispatch SaaS?"
- "Cite a study showing dispatcher productivity gains"

These will be confidently fabricated.

### Deliverable

A clean **Competitive Snapshot** (matrix + open questions) added to the Strategy Brief.

---

## Activity 4 — Brief Assembly + Provenance Log

**Format:** Quad &bull; **55 min** + Readouts &bull; Block 4

### Purpose
Stitch the day's outputs into a single strategy brief, write the executive summary by hand, and complete the provenance log.

### Setup
Each quad has all the day's outputs visible: warm-up diagnosis, 5 pain themes, Competitive Snapshot. Brief template is open in the quad's preferred tool.

### Quad protocol

1. **Hand-write the executive summary** (25 min). 5 bullets max. The AI cannot do this — it doesn't know what your audience cares about.
2. **Hand-write the strategy implications** (10 min). What does the NS imply for these themes? Which design principle most directly addresses each?
3. **Complete the provenance log** (10 min). For every AI-generated section:
    - Which prompts (link to Pattern Library)
    - What manual validation was done
    - Where the AI was wrong (named openly — this is the trust-building section)
4. **Polish** (10 min). Brief is shareable: cohort, design partner, engineer would all be able to read it.

### Readout structure (90 seconds per quad)

> 1. "Our top pain theme is [X], cited from [N sources]."
> 2. "The strongest AI failure we caught was [Y]."
> 3. "Tomorrow, we expect this brief to drive our journey map by [how]."

### Deliverable

A 2–3 page Strategy Brief per quad with hand-written executive summary, AI-assembled pain themes (validated), hand-written strategy implications, and a complete Provenance log including at least one named AI failure.

---

## End-of-day checkpoint

Each quad leaves the day with:

- [x] An iterated prompt pattern for **multi-source synthesis with evidence**
- [x] **5 pain themes** with citations and confidence levels
- [x] A **Competitive Snapshot** built from materials they actually pasted in
- [x] An **Executive summary + strategy implications** (hand-written)
- [x] A complete **Provenance log** — including at least one named AI failure
