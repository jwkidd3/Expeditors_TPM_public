# TPM Academy — Tech Setup

_Last updated: 2026-05-01_

Practical setup guide for participants and facilitators. Cover pre-academy setup once; refer back week-by-week as new tools come into play.

## Audience

- **Participants:** read sections 1–3 before Week 1. Skim section 4 (week-by-week additions) the Friday before each new week.
- **Facilitators:** verify section 5 (pre-flight checklist) before each week. Section 6 covers fallback procedures when tooling fails.

---

## 1. Hardware & connectivity (pre-academy)

| Requirement | Minimum | Recommended |
|------------|---------|-------------|
| Laptop | Modern dual-core, 8 GB RAM, 256 GB | Quad-core+, 16 GB RAM |
| OS | macOS 12+, Windows 10+, Ubuntu 22.04+ | Latest stable |
| Browser | Chrome / Edge / Firefox latest | Same |
| Internet | Reliable broadband | Wired or 5GHz Wi-Fi |
| Webcam + mic | Working for remote sessions | Headset preferred |
| Display | 1 monitor, 1280×720+ | 1080p+; second monitor helpful |

For remote cohorts: confirm video conferencing client installed (Zoom, Teams, or Meet — per academy delivery).

---

## 2. Accounts & access (pre-academy)

Confirm before Week 1 starts. Many of these need IT or admin time — start early.

### 2.1 Generative AI tool access

Every participant needs **at least two** of:

- **Claude** (Anthropic) — free tier acceptable for the academy; paid tier preferred for longer context
- **ChatGPT** (OpenAI) — free tier acceptable; Plus preferred
- **Gemini / Copilot / equivalent** — for cross-tool comparison on Week 1 Day 1

For Week 1 Day 1's "Same Question, Three Models" activity, the cohort collectively needs three different tools available. Coordinate so triads have coverage.

### 2.2 Skills / SkillIQ platform (pre- and post-assessments)

- Pre-assessment access: required before Week 1 (Product Management + Data Literacy)
- Post-assessment access: required for Week 8 Day 5
- Confirm participant logins work the week before academy begins

### 2.3 Azure DevOps (Week 7 only)

Each triad needs one of:

- **Live ADO project** with create-work-item permissions (preferred — sandbox if possible)
- **Sandbox / training ADO instance** provisioned by IT
- **Read-only ADO access** with paper-template fallback (last resort)

If live ADO isn't available by Week 7 Day 1, fall back to the **paper-template** version of Day 2's lab — see section 6.

### 2.4 Document tooling

Each triad needs a shared workspace for collaborative editing:

- **Confluence / SharePoint / Google Docs / Notion** — pick one and use it consistently
- The 5 sibling artifacts (PRD/TCD/TMD/SEP/DP) live here
- Version history is required

### 2.5 Diagramming (Week 4–5)

For C4 diagrams (Wk 4 Day 3) and sequence diagrams (Wk 5 Day 4):

- **Whiteboard + paper** is fully sufficient — phone photos serve as the artifact
- **Miro / Lucidchart / Excalidraw / Figma** if digital is preferred
- **Mermaid** in the team's wiki for inline-in-doc diagrams

Don't over-invest in tooling here; the diagrams are thinking aids, not deliverables.

### 2.6 Communication

- A **cohort channel** (Slack / Teams) for asynchronous Q&A and resource sharing
- A **triad channel** per triad for daily coordination
- An **instructor DM thread** for individual coaching

---

## 3. Installations (pre-academy)

Most academy tools are browser-based. Two local installs help:

### 3.1 Reveal.js decks (already provided)

The daily decks live in `week-XX/presentations/day-XX-*.html`. They render directly in any modern browser:

```
File → Open → week-01/presentations/day-01-ai-fundamentals-prompting.html
```

No build step needed; Reveal.js loads from CDN. Press `S` for speaker notes / clock.

### 3.2 Markdown editor (recommended)

For authoring PRDs, TCDs, etc., a markdown editor with live preview is helpful:

- **Obsidian** (free) — strong cross-doc linking
- **VS Code** + Markdown Preview Enhanced
- **Typora** (paid) — minimal interface

The labs reference markdown templates throughout; a comfortable editor pays off across all 8 weeks.

---

## 4. Week-by-week additions

### Week 1 — Customer-Centric Foundations

- All AI tools confirmed and working
- Persona Validation Canvas, Pain-Point Severity Matrix, Problem Statement Template (printed or digital — see lab packets)

### Week 2 — Strategic Design & Metrics

- Spreadsheet for Tier Sheet (Excel / Google Sheets / Numbers)
- Whiteboard or A2 paper for Journey Map Canvas (Day 5)

### Week 3 — Requirements Engineering & Mini-Capstone

- **AI tools off** for the week — honor system. Disable AI features in your editor.
- Markdown editor for PRD drafting
- Print or share digitally: PRD template (1 per triad)

### Week 4 — Technical Architecture & Constraints

- AI tools restored
- Whiteboard / Miro / Lucidchart for C4 diagrams (Day 3)
- STRIDE Card handout (Day 2)

### Week 5 — Technical Infrastructure & Modeling

- AI tools, with validation discipline
- Diagramming tool for sequence diagrams (Day 4)
- Reference cards for HTTP status codes, REST methods (printed or bookmarked)

### Week 6 — Stakeholder Alignment & Negotiation

- Power × Interest grid (paper or whiteboard)
- Stakeholder persona scripts (Day 5 simulation handouts) — instructor prepares ahead
- Surprise objection sets (Day 5) — instructor prepares ahead

### Week 7 — Agile Delivery & ADO Mastery

- **ADO access confirmed** (see 2.3 above)
- ADO Cheat Sheet handout (Day 2)
- VSM Canvas — large paper or whiteboard (Day 4)

### Week 8 — AI Spec Development & Capstone

- AI tools, with validation discipline
- Capstone subject inputs gathered before Day 1 (interviews / data / docs — per triad)
- Presentation projector / screen sharing for Friday
- Post-assessment access confirmed (Skills / SkillIQ)

---

## 5. Facilitator pre-flight checklist (per week)

Run this checklist the **Friday before each week begins**:

- [ ] All participants have access to required tools (cross-check section 4)
- [ ] Print or digitally share the lab packet for Monday
- [ ] Pre-print handouts called out in each day's `Facilitator pre-flight checklist`
- [ ] Confirm any Week-specific instructor-prepared materials (Wk 6 stakeholder personas, Wk 7 ADO sandbox, etc.)
- [ ] Verify cohort channel and triad channels are live
- [ ] Verify the deck file for each day opens correctly in browser

For **Week 7 specifically**: test ADO access with a sample work item by Friday Week 6. Don't discover ADO issues at 09:00 Monday.

For **Week 8 specifically**: confirm the post-assessment platform is active and participants can log in by Thursday Week 7.

---

## 6. Fallback procedures

When tools fail, the academy continues. Don't let tooling block learning.

| If this fails | Do this |
|--------------|---------|
| AI tool down for one cohort | Pair-up with a triad whose tool works; document as a constraint in the provenance log |
| All AI tools down | Day's AI activity becomes a **paper exercise**: triads write the prompt, predict the output, then review when AI returns |
| ADO unavailable Week 7 | Run Day 2 as **"ADO concepts on paper"** — same 4-level hierarchy, same field discipline, captured in markdown. Coverage similar; hands-on practice is the loss. |
| Whiteboard / projector fails | Triads work on paper; phone photos are the artifact |
| Document workspace down | Local markdown files; sync when service returns |
| Pre/post-assessment platform down | Run paper version of the same instruments; submit when platform returns |

The academy's content is the muscle, not the tool. Tooling failures are an inconvenience, not a blocker.

---

## 7. Common setup issues

| Issue | Fix |
|-------|-----|
| AI tool rate-limits during heavy use | Distribute prompts across triad members' accounts; stagger API-heavy activities |
| ADO permission errors | IT ticket; meanwhile use sandbox or paper |
| Reveal.js deck won't render | Try a different browser; confirm internet for CDN; check `console` for blocked scripts |
| Markdown editor doesn't show tables | Switch to a CommonMark-compliant editor; preview in a browser |
| Network can't reach Slack/Teams | Triad channels via SMS / personal email as fallback |

---

## 8. Pre-academy participant onboarding email (template)

Adapt and send 1 week before academy start:

```
Subject: TPM Academy — Setup Steps Before [Date]

Welcome. Before academy begins on [date], please confirm:

1. Hardware: laptop with webcam, modern browser, reliable internet
2. AI tools: at least two of Claude, ChatGPT, Gemini/Copilot — confirmed working
3. Pre-assessments: Product Management + Data Literacy submitted
   on the Skills platform [link]
4. Cohort channel: you've joined [Slack/Teams workspace link]
5. Pre-work (~3.5 hrs): complete the linked self-paced modules:
   - Exploring PM Philosophies and Frameworks [link]
   - Agile Methodologies primer [link]
   - Getting Started on Prompt Engineering [link]

Please reply with any access issues by [3 days before start].

Looking forward to Monday.
```

---

## 9. Resources

- Course README: `README.md`
- Source outline: `Expeditors _ TPM Immersive Academy _ Outline.pdf`
- Daily decks: `week-XX/presentations/day-XX-*.html`
- Lab packets: `week-XX/labs/day-XX-*/README.md`
- Week overviews: `week-XX/labs/README.md`
