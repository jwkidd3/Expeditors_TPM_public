# Monitoring: The Three-Layer Reference

> **Day 5 handout.** A monitoring plan has three layers, each answering a different question for a different audience. The goal across all three: fire before users notice.

| Layer | Audience | Rhythm | The question it answers |
|-------|----------|--------|-------------------------|
| **On-call alerts** | Engineers on rotation | Real-time | "Is something on fire right now?" |
| **Operator dashboards** | TPM, eng lead, SREs | Daily / weekly | "Is the system trending the right way?" |
| **Executive dashboards** | Leadership | Weekly / monthly | "Are we meeting our SLOs / KPIs / NS?" |

---

## What each layer holds

**On-call alerts** — 3–5 alerts per feature (more = noise). Each passes the four-question test (see the alert-design template).

**Operator dashboard** — what a TPM looks at every Monday morning. Cap at **< 6 charts**:
- Top-line metric (the SLO you care most about)
- Operational signals trending
- Alert volume / mute reasons
- Any deferrals from the previous week

**Executive dashboard** — what leadership sees in the weekly review. Cap at **< 4 charts**:
- The NS-relevant operational signal (from the Tier Sheet)
- The KPI the feature is meant to move
- Status: green / yellow / red against SLOs

## The discipline

- Operator dashboards over 6 charts go unread. Prioritize ruthlessly.
- Track **mute reasons** at the operator level — that's where the alert-tuning conversation lives.
