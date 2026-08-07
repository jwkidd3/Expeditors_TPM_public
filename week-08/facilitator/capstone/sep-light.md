> **Facilitator answer key — Holocron capstone worked solution.** Facilitator-only — lives in the facilitator folder of every repo; do not hand to participants. Part of the internally-consistent set in this folder (see `README.md`).

# SEP-light — Holocron source-string delivery (release 1)

## 1. Stakeholder map (compressed)

Power × Interest placement for the named stakeholders, plus a one-line engagement approach each. RACI is for the single most consequential decision: **adopt the Redis read-cache delivery path with ≤60s propagation staleness** (see §2).

```
         HIGH POWER
              │
  Enterprise  │  Legal/Compliance ★      Named high-power/high-interest:
  Infra       │  Nick Grant (Eng) ★      Legal/Compliance + Nick Grant.
  ────────────┼────────────────────────  Manage both closely; they can
  (Chance     │  Anna Woods (Product)     block or reshape the delivery
   Kennedy)   │  Architecture             stance.
              │
          LOW │  HIGH INTEREST
```

| Stakeholder | Power / Interest | Engagement approach (one line) |
|---|---|---|
| **Anna Woods** — Product; owns scope + MDM/RDM coordination (Master/Reference Data Management) | High / High | Partner as decision-driver — she frames the scope line and arbitrates freshness-vs-latency; align early and keep her the single throat to choke on scope. |
| **Nick Grant** — Engineering; delivery-mechanism architecture ★ | High / High | Co-own the trade-off; he proposes the cache design, so bring him into the SLO framing before it reaches Legal. |
| **Legal/Compliance** — audit retention + compliance-review gates ★ | High / High | Manage closely and translate everything into risk/exposure currency (§2); secure sign-off on the staleness window in writing. |
| **Enterprise Infrastructure** — Entra ID + AKS provisioning (Azure identity + Azure Kubernetes Service) | High / Low | Keep satisfied — give lead time on Entra ID / AKS asks; consult on provisioning, don't involve in product trade-offs. |
| **Architecture** — key-schema / namespace governance | Med / High | Consult on namespace + key-schema conventions before publish contract locks; keep informed on cache keying. |
| **Chance Kennedy** — future AI / Figma (out of scope for release 1) | Low / Low | Monitor only — one-line release-1 update; re-engage when the AI-assist slice opens. |

**RACI — decision: "Adopt Redis read-cache with ≤60s propagation for the delivery path"**

| | Anna Woods | Nick Grant | Legal/Compliance | Enterprise Infra | Architecture |
|---|---|---|---|---|---|
| Role | **A** (accountable) | **R** (responsible) | **C** (consulted — must sign the staleness window) | I | C |

## 2. Trade-off brief — for Legal/Compliance (in their currency)

**Decision (plain terms):** Consuming apps will read published source strings from a fast in-memory copy (Redis cache) instead of hitting the system of record on every read. This lets us serve 20+ apps at p95 ≤ 200ms delivery latency and 99.9% availability. **The cost:** after someone publishes or edits a string, the copy every app sees can lag the true value by up to **60 seconds** before it refreshes.

**Why you should care (the risk, in exposure terms):** For a compliance-sensitive string — a legal disclaimer, a regulated notice, a takedown-driven wording change — there is a window of up to 60 seconds where consuming apps can still be showing the *old* text after Legal has approved and published the new one. On a normal UI label that is harmless. On a legal string, that 60-second window is the exposure.

**The ask:** Accept the ≤60s propagation window for **normal** strings in exchange for the latency and scale it buys, and tell us which strings you consider compliance-critical so we can treat them differently. We revisit the whole trade-off if any consumer needs sub-5-second freshness across the board.

**SLO context we're committing to:** delivery p95 ≤ 200ms, availability 99.9%, propagation ≤ 60s.

## 3. Simulated negotiation outcome

**Status vocabulary used:** `PROPOSED → COUNTERED → AGREED` (with `DEFERRED` / `ESCALATE` paths).

- **The ask (PROPOSED):** Product/Eng propose Legal/Compliance accept the ≤60s propagation window across all published strings, in exchange for p95 ≤ 200ms delivery and read scale across 20+ apps.
- **The pushback (COUNTERED):** Legal/Compliance's single strongest objection — "A 60-second window where apps still render a superseded legal string after we've published a correction is unacceptable exposure. We can't sign a blanket staleness window." They do not object to the cache for ordinary content.
- **The settle point (AGREED):** ≤60s propagation stands as the **default** for normal strings. Compliance-critical strings carry a **`critical/legal` flag**; flagging one forces (a) a **required compliance review before publish** — publish is blocked until Legal signs — and (b) **synchronous cache invalidation on publish (<5s propagation)** rather than the lazy ≤60s refresh. Product (Anna Woods) is Accountable; Nick Grant is Responsible for the flag-driven invalidation path; Architecture is Consulted on how the flag is carried in the key schema.
- **Audit / next step:** Decision recorded with the `critical/legal` flag semantics and the <5s target for flagged strings; the required-review gate is logged to the audit-retention trail Legal already owns. **Open item — `DEFERRED`:** if any consumer later needs sub-5s freshness for *unflagged* strings, the base ≤60s trade-off reopens (owner: Nick Grant, revisit trigger). No `ESCALATE` needed — settled at the working level.
