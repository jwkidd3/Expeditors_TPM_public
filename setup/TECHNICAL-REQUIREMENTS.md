# Technical Requirements — Expeditors TPM Academy

_For client review. Companion document to `setup/TECH-SETUP.md` (which is the participant-facing setup guide)._

The TPM Academy curriculum is **browser-based throughout** — no GPUs, ML training environments, or SDK installs are required. There are four categories of services learners and instructors need.

---

## Generative AI assistants

Every week except Week 3 makes active use of AI assistants for research, summarization, drafting, and critique. Each participant needs working access to **at least two** of:

- **Claude** (Anthropic) — free tier acceptable; paid tier preferred for longer context
- **ChatGPT** (OpenAI) — free tier acceptable; Plus preferred
- **Gemini / Copilot / equivalent** — used for cross-tool comparison on Week 1 Day 1

For the Week 1 Day 1 "Same Question, Three Models" activity, the cohort collectively needs **three different tools** available across triads. Coordinate so each triad has coverage.

We need to verify learners can access these services using either work or personal accounts. If corporate policy blocks all three, that is a hard blocker for the AI-augmented sections (Weeks 1, 2, 4, 5, 6, 7, 8).

## Azure DevOps (Week 7 only)

Week 7's ADO Mastery requires a real ADO project for hands-on work. Per triad, one of:

- **Live ADO project** with create-work-item permissions — preferred (sandbox if possible)
- **Sandbox / training ADO instance** provisioned by IT
- **Read-only ADO access** with paper-template fallback — last resort

If live ADO isn't available by Week 7 Day 1, Day 2's lab falls back to a paper version (same 4-level hierarchy and field discipline, no hands-on practice).

## Document & diagramming workspace

Each triad needs a shared workspace for collaborative editing — **Confluence, SharePoint, Google Docs, or Notion**. Pick one and use it consistently for the 5 sibling artifacts (PRD, TCD, TMD, SEP, DP) and the capstone.

For C4 diagrams (Week 4 Day 3) and sequence diagrams (Week 5 Day 4), any of these works:

- Whiteboard + paper (phone photos are the artifact)
- Miro / Lucidchart / Excalidraw / Figma
- Mermaid in the team's wiki

Diagrams are thinking aids, not deliverables — don't over-invest in tooling.

## Skills / SkillIQ platform

Pre- and post-academy Product Management + Data Literacy assessments. Confirm participant logins work before Week 1 and again before Week 8 Day 5.

## Local installs (optional, recommended)

- A markdown editor with live preview (Obsidian / VS Code + Markdown Preview Enhanced / Typora) for authoring PRDs, TCDs, etc.
- A modern browser (Chrome / Edge / Firefox)
- Video conferencing client (Zoom / Teams / Meet — per delivery)

**Not required for this academy:** Colab, Databricks, Sagemaker, GPUs, Pluralsight VMs, Copilot licenses. The TPM Academy is a Product Manager curriculum, not an ML engineering curriculum.

---

## Schedule

| Week | Theme | Environment / Tools |
|---|---|---|
| **Week 1** | Customer-Centric Foundations | Browser + ≥2 AI assistants (Claude / ChatGPT / Gemini) + markdown editor. **Day 1 needs 3 different AI tools available across the cohort's triads.** |
| **Week 2** | Strategic Design & Metrics | AI assistants, markdown editor, spreadsheet (Excel / Google Sheets / Numbers) for the Metrics Tier Sheet, whiteboard or A2 paper for the Journey Map Canvas (Day 5). |
| **Week 3** | Requirements Engineering & Mini-Capstone | **AI tools OFF for the week (honor system — disable AI features in your editor).** Markdown editor for PRD drafting. PRD template printed or shared digitally per triad. |
| **Week 4** | Technical Architecture & Constraints | AI assistants restored. Diagramming tool for C4 diagrams (Day 3) — Miro / Lucidchart / Excalidraw / whiteboard. STRIDE Card handout (Day 2). |
| **Week 5** | Technical Infrastructure & Modeling | AI assistants with validation discipline. Diagramming tool for sequence diagrams (Day 4). HTTP status-code + REST-methods reference cards (printed or bookmarked). |
| **Week 6** | Stakeholder Alignment & Negotiation | AI assistants. Power × Interest grid (paper or whiteboard). Day 5 negotiation simulation: stakeholder persona scripts + surprise objection sets (instructor prepares ahead). |
| **Week 7** | Agile Delivery & ADO Mastery | **Azure DevOps access required** — live project (preferred) or sandbox; paper-template fallback otherwise. ADO Cheat Sheet handout (Day 2). VSM Canvas on paper or whiteboard (Day 4). |
| **Week 8** | AI Spec Development & Capstone | AI assistants with validation discipline. Capstone subject inputs gathered before Day 1 (per-triad interviews / data / docs). Projector or screen-sharing for Friday presentations. Post-assessment access confirmed (Skills / SkillIQ). |
