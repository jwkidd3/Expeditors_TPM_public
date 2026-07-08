# TPM Academy

**Customer:** Expeditors
**Source outline:** [`course-tooling/tools/outline.pdf`](./course-tooling/tools/outline.pdf)

An 8-week immersive Technical Product Manager Academy preparing engineers, analysts, and associate PMs to operate as Technical Product Managers. Every week blends conceptual frameworks, hands-on AI-augmented practice, and heavily small-group collaboration that mirrors the real TPM job.

## Delivery format

- **Length:** 8 weeks × 5 days × **7 instructional hours/day** (≈280 hours)
- **Daily cadence:** 7 hrs instruction, 1 hr lunch, two 15-minute breaks
- **Style:** Small-group oriented — breakouts, pair critiques, stakeholder simulations, and PRD review cycles
- **Tooling:** Reveal.js decks authored as Markdown under `week-XX/markdown/presentations/day-XX-*.md`, built to standalone `.html` by `npm run build`. Activity briefs are Markdown under `week-XX/markdown/labs/day-XX-*.md`. Authoring details: [`course-tooling/tools/AUTHORING.md`](./course-tooling/tools/AUTHORING.md).
- **Assessments:** Pre- and post-academy Product Management and Data Literacy assessments (administered on the Skills/SkillIQ platform)

## Daily template

| Block | Duration | Focus |
|-------|----------|-------|
| Opening & objectives | 0:15 | Frame the day; connect to prior learning |
| Teaching Block 1 + Activity 1 | 1:15 | Introduce concept → small-group application |
| **Morning break** | 0:15 | |
| Teaching Block 2 + Activity 2 | 1:15 | Deepen concept → apply to group artifact |
| **Lunch** | 1:00 | |
| Teaching Block 3 + Activity 3 | 1:15 | New angle → group critique or simulation |
| **Afternoon break** | 0:15 | |
| Teaching Block 4 + Activity 4 + Wrap | 1:30 | Integrate → readouts → reflection |

## Week-by-week topic map

| Week | Theme | Capstone checkpoint |
|------|-------|---------------------|
| 1 | Customer-Centric Foundations | — |
| 2 | Strategic Design & Metrics | — |
| 3 | Requirements Engineering & Mini-Capstone | **Non-AI PRD deliverable + peer review** |
| 4 | Technical Architecture & Constraints | — |
| 5 | Technical Infrastructure & Modeling | — |
| 6 | Stakeholder Alignment & Negotiation | — |
| 7 | Agile Delivery & ADO Mastery | — |
| 8 | AI Spec Development & Capstone | **Real-world capstone + artifact presentations** |

## Pre-work (~3.5 hours, completed before Week 1)

- Exploring Product Management Philosophies and Frameworks
- Agile Methodologies primer
- Getting Started on Prompt Engineering with Generative AI
- Pre-assessment: Product Management
- Pre-assessment: Data Literacy

## Repository layout

```
TPM/
├── README.md                                        ← this file (course overview)
├── Start.command / Start.bat                        ← double-click launchers (mac / windows)
├── course-tooling/                                  ← all build tooling — never edit unless you're maintaining the pipeline
│   ├── package.json, package-lock.json              ← npm scripts: build / pdf / dev / audit / convert / ui
│   ├── scripts/                                     ← shell/cmd wrappers (setup, build-html, build-pdf, preview)
│   └── tools/                                       ← underlying JS + Python
│       ├── AUTHORING.md                             ← authoring guide + GitHub-mirror setup
│       ├── tpm.js                                   ← unified CLI dispatcher
│       ├── build.js, pdf.js, ppt.js, ui.js, convert.js, audit.py  ← underlying tools
│       ├── coverage.json                            ← outline → file map (audit input)
│       ├── theme.css                                ← shared deck theme
│       ├── template-reference.html                  ← visual reference for theme classes
│       └── outline.pdf                              ← canonical course outline (Expeditors)
├── participant-setup/                                           ← pre-academy tech setup
│   ├── markdown/
│   │   └── presentations/TECH-SETUP.md              ← participant-facing setup deck (source)
│   └── TECHNICAL-REQUIREMENTS.md                    ← client-facing requirements doc
├── kickoff/                                         ← half-day pre-Week-1 orientation
│   └── markdown/
│       ├── presentations/kickoff.md                 ← kickoff deck (source)
│       └── labs/                                    ← facilitator schedule + activity packet
├── instructor/                                      ← standalone instructor-intro deck
│   ├── markdown/
│   │   └── presentations/instructor.md              ← about me, prereqs, pledge, ground rules (source)
│   └── assets/avatar.jpg                            ← instructor photo (inlined at build time)
├── capstone/                                        ← consolidated capstone reference (same layout as week-XX)
│   └── markdown/
│       └── labs/README.md                           ← Week-3 + Week-8 capstone summary
└── week-XX/                                         ← one folder per week
    ├── markdown/                                    ← all sources for this week
    │   ├── presentations/                           ← deck sources
    │   │   └── day-XX-*.md                          ← one deck per day
    │   └── labs/                                    ← weekly activity briefs
    │       ├── README.md                            ← week schedule + learning outcomes
    │       └── day-XX-*.md                          ← activity briefs, roles, timeboxes, rubrics
    └── assets/                                      ← per-week binaries (images, diagrams)
```

After build, the dist/ output (and public mirror) reorganizes for participant browsing:

```
<folder>/
├── presentations/    ← built outputs grouped by format
│   ├── reveal/       (HTML)
│   ├── pdf/          (PDF)
│   └── ppts/         (PowerPoint)
├── labs/             ← flattened out of source markdown/labs/
└── assets/
```

Other instructors get the source `markdown/` layout via the instructor mirror; participants get the flat `presentations/`/`labs/`/`assets/` layout via the public mirror.

## How to run a deck

Each deck can be delivered in three formats — pick whichever fits the audience:

| Format | Command | When to use |
|---|---|---|
| **Reveal.js HTML** (default) | `npm run build` | Live presentation. Open `dist/<folder>/presentations/reveal/<name>.html` in any browser; press `S` for speaker notes/clock. Self-contained — works offline, no CDN. |
| **PDF + PowerPoint** | `npm run pdf` | Both render together in one pass. PDFs land in `dist/<folder>/presentations/pdf/<name>.pdf`, PPTs in `dist/<folder>/presentations/ppts/<name>.pptx`. Both incremental (skip unchanged). Add `-- --force` to re-render everything. |
| **PowerPoint** (one-off) | `npm run ppt -- <deck.md>` | Single deck override when you don't need a full PDF rebuild. Output at `dist/<folder>/presentations/ppts/<name>.pptx`. **Lossy** — gradients, cards, multi-column layouts don't survive; content only. PDF is the better visual-fidelity hand-off. |

### First-time setup for a new instructor

**Easiest path — double-click the launcher** (no command-line typing):

| Platform | Double-click |
|---|---|
| macOS | `Start.command` (Finder may ask to allow first run — right-click → Open) |
| Windows | `Start.bat` |

A console window opens, runs first-time setup if needed (prereq check + `npm install`), then opens your browser to a build UI at `http://localhost:3000`. The UI has buttons for:

- **Build HTML decks** — all 43 to `dist/<folder>/presentations/reveal/`
- **Build PDF + PowerPoint** — incremental, with a Force button alongside
- **Live preview a deck** — pick from a dropdown, opens reveal-md at `localhost:1948`
- **Open the output folder** — opens `dist/` in Finder / Explorer
- **Curriculum coverage audit** — runs the audit script

Output streams live into the UI; close the console window when done.

**Prerequisites the launcher checks for you:** Node 18+, Python 3, pandoc. If any are missing it prints the exact install command for your OS.

**If you prefer the command line:**

```bash
# macOS / Linux
git clone https://github.com/kiddcorplp/Expeditors_TPM_instructor.git
cd Expeditors_TPM_instructor
./course-tooling/scripts/setup           # checks prerequisites, installs npm deps
./course-tooling/scripts/preview         # live preview at http://localhost:1948
./course-tooling/scripts/build-html      # all HTML decks
./course-tooling/scripts/build-pdf       # all PDFs + PPTs
```

```cmd
REM Windows
git clone https://github.com/kiddcorplp/Expeditors_TPM_instructor.git
cd Expeditors_TPM_instructor
course-tooling\scripts\setup.cmd
course-tooling\scripts\preview.cmd
course-tooling\scripts\build-html.cmd
course-tooling\scripts\build-pdf.cmd
```

**If you prefer the underlying npm scripts:**

```bash
# Prerequisites: Node 18+, Python 3 (for audit), pandoc (for PPT)
npm install                                                          # one time
npm run build                                                        # all HTML decks
npm run pdf                                                          # all PDFs + PPTs (incremental, add -- --force to rebuild)
npm run dev                                                          # live preview
npm run audit                                                        # curriculum coverage check
```

Detailed setup walkthrough and per-tool install commands: [`course-tooling/tools/AUTHORING.md`](./course-tooling/tools/AUTHORING.md#one-time-local-setup).

### CI behavior

The HTML build runs in CI on every push to `main`. PDFs and PPTs render together in CI on manual workflow dispatch — they're produced in the same pass. PPTs are skipped if you don't have `pandoc` installed locally (PDF-only still works via the bundled Chromium).

### One-deck PPT override

```bash
npm run ppt -- week-01/markdown/presentations/day-01-ai-fundamentals-prompting.md
```

## Current build status

- [x] Week 1 — Customer-Centric Foundations
- [x] Week 2 — Strategic Design & Metrics
- [x] Week 3 — Requirements Engineering & Mini-Capstone
- [x] Week 4 — Technical Architecture & Constraints
- [x] Week 5 — Technical Infrastructure & Modeling
- [x] Week 6 — Stakeholder Alignment & Negotiation
- [x] Week 7 — Agile Delivery & ADO Mastery
- [x] Week 8 — AI Spec Development & Capstone
