> **Facilitator answer key — Holocron capstone worked solution.** Facilitator-only — lives in the facilitator folder of every repo; do not hand to participants. Part of the internally-consistent set in this folder (see `README.md`).

# SEP-light — Holocron source-string delivery (release 1)

## 1. Stakeholder map

RACI is for the single most consequential decision: **adopt the Redis read-cache delivery path with ≤60s propagation** (§2).

| Stakeholder | Power / Interest | Engagement (one line) |
|---|---|---|
| **Anna Woods** — Product; scope + MDM/RDM | High / High | Decision-driver; frames the scope line, arbitrates freshness-vs-latency. |
| **Nick Grant** — Engineering; delivery mechanism ★ | High / High | Co-owns the trade-off; brings the cache design; frame SLOs with him before Legal. |
| **Legal / Compliance** — audit + review gates ★ | High / High | Manage closely; speak in risk/exposure; get the staleness window signed in writing. |
| **Enterprise Infrastructure** — Entra ID + AKS | High / Low | Keep satisfied; lead time on identity/provisioning asks; not in product trade-offs. |
| **Architecture** — key/namespace governance | Med / High | Consult on key-schema + cache keying before the publish contract locks. |
| **Chance Kennedy** — future AI/Figma (out of R1) | Low / Low | Monitor; re-engage when the AI-assist slice opens. |

**RACI — "Adopt Redis read-cache with ≤60s propagation":** Anna Woods **A** · Nick Grant **R** · Legal/Compliance **C** (must sign the staleness window) · Enterprise Infra **I** · Architecture **C**.

## 2. Trade-off brief — for Legal/Compliance (in their currency)

**Decision.** Consuming apps read published strings from a fast in-memory copy (Redis) instead of the system of record on every read — serving 20+ apps at p95 ≤200ms and 99.9% availability. **Cost:** after a publish, the copy apps see can lag the true value by up to **60 seconds**.
**Why it matters (exposure).** On a normal label, harmless. On a **compliance-sensitive string** — a legal disclaimer, a regulated notice — that 60-second window is exposure: apps can still render the *old* text after Legal has approved the new one.
**The ask.** Accept ≤60s for **normal** strings in exchange for the latency and scale, and tell us which strings are compliance-critical so we can treat them differently. Revisit the whole trade-off if any consumer needs sub-5-second freshness across the board.

## 3. Simulated negotiation outcome

**Status vocabulary:** `PROPOSED → COUNTERED → AGREED` (with `DEFERRED` / `ESCALATE`).

- **PROPOSED:** Product/Eng propose Legal accept ≤60s propagation across all published strings, for p95 ≤200ms + read scale.
- **COUNTERED:** Legal's strongest objection — "A 60-second window where apps still render a superseded legal string after we've published a correction is unacceptable. We can't sign a blanket staleness window." No objection to the cache for ordinary content.
- **AGREED:** ≤60s stands as the **default** for normal strings. Compliance-critical strings carry a **`critical/legal` flag**; flagging one forces (a) a **required compliance review before publish** — publish blocked until Legal signs — and (b) **synchronous cache invalidation (<5s)** rather than lazy ≤60s refresh. Anna Woods **A**, Nick Grant **R** for the flag-driven invalidation, Architecture **C** on carrying the flag in the key schema.
- **Audit / next step:** Decision recorded with the flag semantics + <5s target; the required-review gate logs to the audit-retention trail Legal owns. **`DEFERRED`:** if any consumer later needs sub-5s for *unflagged* strings, the base ≤60s trade-off reopens (owner: Nick Grant). No `ESCALATE` — settled at the working level.
