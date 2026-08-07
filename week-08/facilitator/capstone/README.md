# Holocron Capstone — Full Worked Solution (Facilitator Answer Key)

> **Facilitator-only — do not hand to participants.** This folder is the complete worked Holocron capstone: a model artifact set a strong quad could produce in the Week-8 build. It ships in the **facilitator folder of every repo** (public + instructor) — the facilitator folder is the separation from student-facing content, not a withheld file.
>
> **What it is:** one internally-consistent solution across the whole chain — PRD-light → TCD-light → TMD-light → SEP-light → DP-light → AI Spec — all scoped to the same **release-1 slice** and built on the same Azure stack and Holocron entities. Derived from `../holocron-reference-prd.md`.
>
> **How to use it:** a comparison reference during Day 2–5 coaching and Friday review — **not** a grading key. A quad's solution will differ (different scope line, different trade-offs) and can still be excellent. Use this to check that their chain is *internally consistent* (does each AC have a sequence? does each SLO have monitoring? does the AI Spec trace back to the PRD?), not to match it line-for-line.

## The release-1 scope slice (what this solution builds)

**In:** the core source-string lifecycle — access roles (CS1), product setup (CS2), create/edit/publish strings (CS3–4), version history + audit (CS5), search (CS6), delivery to consuming apps (CS7), request/complete review (CS11–12), and translation variants + lifecycle (CS15).

**Out (defensible non-goals for release 1):** aliases (CS9), advanced reviewer configuration (CS10), export/import exchange (CS16–18), rollback (CS8), AI-assisted translation, Figma integration, per-locale screenshot preview.

## The artifacts

| File | Artifact | Models |
|---|---|---|
| `prd-light.md` | PRD-light | The compressed requirements for the slice |
| `tcd-light.md` | TCD-light | Architecture stance, threat model, SLOs, trade-offs |
| `tmd-light.md` | TMD-light | Data model, Azure topology, API contract, sequences, monitoring |
| `sep-light.md` | SEP-light | Stakeholder map + one trade-off brief + one negotiated outcome |
| `dp-light.md` | DP-light | Outcome map, backlog, tracking, value stream, one experiment |
| `ai-spec.md` | AI Spec | The integrated, engineering-ready spec tying it all together |
