> **Facilitator answer key — Holocron capstone worked solution.** Facilitator-only — lives in the facilitator folder of every repo; do not hand to participants. Part of the internally-consistent set in this folder (see `README.md`).

# PRD-light — Holocron (Release-1 slice)

**Persona.** Content Owner — owns the UI text (labels, buttons, errors, help, legal notices) for one or more enterprise apps.
**Job.** "Fix or publish a piece of UI text myself, in minutes — including compliance strings — without an engineering ticket or a release."
**Top pain (anchors this PRD).** Every text change needs an engineer + a deploy. Secondary: no durable record of compliance approvals; translation quality varies by team.

## 1. Context

Mandate: a centralized, governed way to create, review, and publish UI text without hardcoding or redeploying — with traceability, ownership, and approval controls. **Scale:** 150+ countries, 20–30+ consuming apps, 30–40 locales, `en-US` authoritative source, ~500k strings, Internal data classification. Entra ID covers identity; hosting is AKS. Today a one-word legal-disclaimer fix is a ticket → code change → review → release; compliance strings can ship with no consistent gate and no central approval record — a live audit exposure.

## 2. Problem

The Content Owner can't change the words their product shows — every edit is blocked behind engineering + a deploy. Three consequences: **delivery drag** (copy stays wrong, competing for engineering it doesn't need); **governance risk** (compliance strings ship without a consistent gate; approval evidence scattered); **global inconsistency** (per-team translation and unseen `en-US` drift across 30–40 locales).

## 3. Goals + non-goals

**Goals (outcomes):** (1) correct/publish a live string in minutes — no ticket, no deploy; (2) every content + approval action leaves a durable, tamper-evident record; (3) consuming apps always render published, locale-appropriate text — `en-US` fallback when a translation is missing, never a blank.
**Non-goals (R1):** no AI translation or vendor import/export; no aliases, advanced reviewer config, or rollback; no Figma, screenshot preview, or public/unauthenticated delivery.

## 4. Scope

| In (Release-1: CS1–7, CS11–12, CS15) | Out (deferred) |
|---|---|
| Role + product/locale access via Entra ID (CS1) | Aliases / shared strings (CS9) |
| Product setup, namespace root, target languages (CS2) | Advanced reviewer pools (CS10) |
| Create/edit/publish source strings + version history (CS3–5) | Export/import exchange (CS16–18) |
| Search across keys / content / metadata (CS6) | Source-string rollback (CS8) |
| Governed delivery: published-only + fallback (CS7) | AI translation; Figma; screenshot preview |
| Request/complete review + audited override (CS11–12) | Emailed-link review UX; binary assets |
| Translation variants + lifecycle, `en-US` fallback (CS15) | RTL scope (open → Architecture) |

*Invariants across the slice: immutable namespaced keys, `en-US` authoritative source, append-only audit.*

## 5. Solution sketch

- **Management app (web).** Sign in via Entra ID → your products. Create a product (unique app id → namespace root), set target languages, create a string: dotted namespaced key (immutable), `en-US` text, optional review designations. Editing = new Draft version; prior versions kept. **Publish** is explicit; publishing without a resolved designated review shows a confirm-warning and records the override + reason.
- **Governance.** Reviews optional by default. Compliance-critical strings carry a **`critical/legal` flag** that *requires* review before publish. Every version, transition, and decision is immutable and reverse-chronological, filterable by actor / type / language / date.
- **Delivery.** A consuming app fetches all **Published** strings for a namespace prefix at a locale — the approved translation, or `en-US` with a `fallback` flag. Served from Redis; a change propagates **≤60s** (normal) or **<5s** (`critical/legal`).
- **Translation.** Per locale per string, a Translation State (Not Translated → Awaiting → Pending Review → Approved → Published → Outdated), versioned and pinned to the `en-US` source version; republishing source flips stale translations to Outdated.

## 6. Acceptance Criteria (7)

1. **Create + publish with audit.** Content Owner, valid key + `en-US`, no review designated → confirm the no-review warning → saved Published, available to apps; create + publish recorded with identity + timestamp.
2. **Delivery = published + fallback.** Mixed-state namespace, no `fr-FR` translation for one key → authenticated fetch at `fr-FR` returns only Published; the untranslated key served `en-US` with the fallback flag; no Draft/Retired.
3. **Translation lifecycle.** `fr-FR` Published against source v3 → publish source v4 → that `fr-FR` variant → Outdated, its source reference stays v3, no other locale changes.
4. **Publish blocked without active owner.** Product whose only Content Owner is deactivated → any publish is blocked until an active Content Owner is assigned.
5. **Compliance override audited.** String with a `critical/legal` designation, review Pending/Rejected → publish requires cancel or explicit override-with-reason; on override, publish + override + reason + review outcome + identity + timestamp are recorded.
6. **Concurrent edit.** Two owners edit version 5 → optimistic locking: first save = v6; the second gets a conflict dialog showing both versions; no silent overwrite.
7. **Key immutability.** Published key `checkout.button.submit` → rename is prevented; the system directs create-new, so apps referencing the original key don't break.

## 7. NFRs (one per category — requirement · verification)

- **Performance.** Delivery p95 ≤200ms / p99 ≤500ms; publish→delivery ≤60s (normal) / <5s (`critical/legal`); rate limit 50 req/s (burst 100). *Verify:* load test at target RPS; assert percentiles + propagation.
- **Security.** All management + delivery access authenticated via Entra ID, authorized by role + product/locale scope; unauthenticated delivery denied with an empty body. *Verify:* authz matrix per role (Authenticated Employee / Content Owner / Reviewer / Review Admin / Holocron Admin).
- **Accessibility.** Management app WCAG 2.1 AA (keyboard, focus, contrast). *Verify:* axe scan + keyboard-only pass of create→publish→review.
- **Observability.** Emit propagation latency, delivery p95/p99, availability, cache staleness, fallback rate per locale. *Verify:* dashboards + per-SLO alerts; synthetic publish probe.
- **Compliance.** Every change / transition / decision (incl. overrides) in an immutable, append-only audit trail (actor, timestamp, before/after), retained per policy. *Verify:* mutate/delete of an audit record must fail. *Open:* retention period → Legal (assume ≥7 yrs).
