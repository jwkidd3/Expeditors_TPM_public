> **Facilitator answer key — Holocron capstone worked solution.** Facilitator-only — lives in the facilitator folder of every repo; do not hand to participants. Part of the internally-consistent set in this folder (see `README.md`).

# AI Spec — Holocron (release-1 slice)

**Sibling to:** PRD-light, TCD-light, TMD-light, SEP-light, DP-light  |  **Status:** Reviewed
**AI Provenance:** AI-assisted draft; every section validated against a source artifact — see §8.

The integrated, engineering-ready spec — deliberately *shorter* than the sum of PRD + TCD + TMD, with citations back to the deeper artifacts.

## 1. Headline

Holocron gives content owners across 150+ countries one governed place to create, review, and publish UI strings — so 20–30+ apps fetch localized text at render (≤200ms p95) without hardcoding or a redeploy.

## 2. Engineering-ready summary

- **Problem + users (PRD §1–3).** UI text is hardcoded inside each app, so any change needs an engineering change + a redeploy across 20–30+ apps. Holocron centralizes strings in a governed store. Users: *content owners* (create/edit/publish `en-US` + translation variants), *reviewers* (request/complete review), *consuming apps* (read at render). Scale: ~500k strings, 30–40 locales, `en-US` source, Internal data.
- **Architecture (TCD §1).** A **modular service on AKS** with **two paths over one PostgreSQL system of record**: a low-traffic authoring path (management app 99.5%) and a read-optimized delivery path fronted by **Redis** + **API Management/App Gateway** (99.9%, p95 ≤200ms). Publish + audit-write stay in one transaction.
- **Data + delivery (TMD §1, §3).** Immutable by design: namespaced **SourceString** key, immutable **versions** for source + translations, a **PublicationSelection** (approved | previous | `en-US` fallback) per publish, an immutable **AuditEntry** per mutating op. Apps read `GET …/namespaces/{ns}?locale=…` (Entra token) and get published strings with an explicit `fallback` flag.
- **How to build it.** Authoring CRUD + review against Postgres with an append-only audit stream (Event Hubs → Blob); delivery as a separate horizontally-scaled module reading through Redis (read-through + backfill, degrades to direct Postgres). Publish invalidates the cache — ≤60s normal, synchronous <5s for `critical/legal`. Identity, RBAC, and rate limiting are enforced at the APIM edge and re-checked server-side.

## 3. Data + API contract

**Entities (TMD §1), versions append-only:** Product · SourceString (immutable namespaced key `product.namespace.key`, `criticality`) · SourceStringVersion · TranslationVariant · TranslationVersion · ReviewRequest · PublicationSelection · AuditEntry · User (Entra ID; roles Authenticated Employee / Content Owner / Reviewer / Review Admin / Holocron Admin — PRD §7).

**Delivery — the read contract:**
```
GET /v1/products/{productId}/namespaces/{namespace}?locale=<BCP-47>   [Bearer Entra token]
200 → [ {key,value,locale,version,fallback}, … ]
401 no/invalid token · 403 wrong product scope · 404 unknown ns · 429 over 50 req/s (burst 100)
```
`fallback:true` = no published translation for the locale; `en-US` served instead.

**Authoring — RBAC-gated:**
```
POST  …/namespaces/{ns}/strings          create string (+ v1)   [Content Owner]
POST  …/strings/{key}/versions           edit = new version     [Content Owner]
POST  …/strings/{key}/review-requests    request review         [Content Owner]
PATCH …/review-requests/{id} {complete}  complete review        [Reviewer]
POST  …/strings/{key}/publish            publish (+ AuditEntry) [Content Owner / Holocron Admin]
      normal: publish without review allowed, as an audited override.
      critical/legal: completed compliance review REQUIRED (else 409) + synchronous <5s invalidation.
```

## 4. Sequence + failure handling

```
HAPPY: publish → Postgres write version + AuditEntry (one tx) → Redis invalidate → Event Hubs (async)
       consumer GET → Entra OK at APIM → Redis HIT → 200 [fallback:false]   p95 ≤ 200ms; visible ≤60s
SAD:   missing translation → serve en-US, fallback:true (never 404 a live key)
       cache miss → read-through Postgres + backfill; Redis down → direct Postgres reads
       401/403/404; 429 over 50 req/s → consumer holds last good cache
WEIRD: Event Hubs down → buffer + retry; the Postgres publish still commits (audit never blocks the write)
```

## 5. Constraints

| Constraint | Target |
|---|---|
| Delivery latency | p95 ≤ 200ms / p99 ≤ 500ms |
| Delivery / management availability | 99.9% / 99.5% |
| Publish → delivery propagation | ≤ 60s normal · <5s `critical/legal` |
| Rate limit | 50 req/s, burst 100 |

**Security (TCD §3–4, PRD §7):** Entra ID token at the APIM edge + server-side; RBAC per operation (product-scoped, least-privilege delivery identity); immutable AuditEntry per op → Event Hubs → Blob; secrets in Key Vault; auth fails closed. **Compliance:** the audit trail is the control for the optional-review default on normal strings; `critical/legal` add an enforced pre-publish review + <5s invalidation (SEP §3). **Scale:** delivery pods scale on read QPS and survive a management outage via Redis + a Postgres read replica.

## 6. Decisions

**Made:** (1) **Redis read-cache**, ≤60s staleness for normal strings; `critical/legal` get synchronous <5s (SEP §3). (2) **Reviews optional + audited override** for normal strings; `critical/legal` require enforced pre-publish review (SEP §3). (3) **Immutable namespaced keys + versions** (rename = create-new + deprecate). (4) **Missing translation → `en-US` fallback** with an explicit indicator (PRD §5 / CS7 AC), so a live key never 404s.
**Not decided (open):** RPO/RTO for Postgres + audit archive (→ Platform/SRE); alias governance (out of slice); export/import format (open).

## 7. Stakeholders + sign-off (SEP §1 + TCD §6)

| Stakeholder | Interest | Status |
|---|---|---|
| Anna Woods — Product | Scope slice + R1 value | Approved |
| Nick Grant — Engineering | AKS, delivery SLOs, Redis/Postgres split | Approved |
| Enterprise Infrastructure | Entra ID + AKS + secrets | Approved (pending Key Vault rotation runbook) |
| Legal / Compliance | Audit + review gates | Approved — `critical/legal` flag enforces pre-publish review + <5s (SEP §3) |
| Architecture | Immutable namespaced key schema | Approved |

## 8. Provenance log

AI-drafted; human judgment shaped every section. **A spec that ships without this section ships fiction.**

| # | Section | Validation | Status |
|---|---|---|---|
| 1 | Headline | Scale + p95 vs PRD §1–3 / TCD §3; roles vs PRD §7 | ✅ |
| 2 | Eng summary | Each claim traced to PRD §1–5, TCD §1, TMD §1/§3; IN/OUT vs PRD §4 | ✅ |
| 3 | Data + API | Entities + immutability vs TMD §1; endpoint/codes/`fallback` vs TMD §3; roles match PRD §7 | ✅ |
| 4 | Sequence | Vs TCD §2 failure handling + TMD §4; SLO figures match TCD §3/§4 | ✅ |
| 5 | Constraints | Every SLO copied (not paraphrased) from TCD §3/§4; security vs STRIDE + PRD §7 | ✅ |
| 6 | Decisions | 3 map to TCD §5 trade-offs; en-US fallback from PRD §5 / CS7 AC; open items confirmed not-decided | ✅ |
| 7 | Sign-off | Names from SEP §1; Legal resolved via the flag (SEP §3); Key Vault condition on Enterprise Infrastructure | ✅ |
| 8 | This log | Instructor confirms every row cites a real source before this spec is "Reviewed" | ✅ |
