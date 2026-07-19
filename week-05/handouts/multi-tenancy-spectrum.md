# Multi-Tenancy Spectrum

> **Day 2 handout.** The four tenancy stances, from cheapest/least-isolated to most-isolated/most-expensive. Tenancy is a customer-and-cost decision, not a pure tech decision — pick with contractual evidence.

| Stance | Architecture | Pros | Cons |
|--------|--------------|------|------|
| **Shared** | One deployment serves all tenants | Lowest cost; easiest ops | Noisy neighbor; weakest isolation |
| **Pooled** | One deployment, but per-tenant limits + isolation | Lower cost than dedicated; better isolation | Complex tenant-aware code |
| **Dedicated** | One deployment per tenant | Strongest isolation; per-tenant compliance | High cost; complex deployment |
| **Hybrid** | Most tenants shared; some dedicated | Match cost to value | Operational overhead of two patterns |

---

## The default for FieldPulse's stage

Most B2B SaaS at FieldPulse's stage uses **pooled with per-tenant rate limits**. That's your default; defend anything more isolated.

## How to choose

1. **What did your PRD Section 1 customer actually say?** Are any large customers *contractually* expecting dedicated infra?
2. **Pick a stance.** Pooled is the default. Choosing dedicated requires contractual customer evidence.
3. **Capture the revisit trigger** — e.g., "a customer larger than 5x our current largest signs, OR a regulated-industry customer requires dedicated."

## The classic mistake

**Single-tenant / dedicated without contractual customer evidence** is the classic over-promise. It doubles cost to solve a problem no customer has asked you to solve. Don't stake it on a hypothetical.
