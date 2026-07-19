# PRD Sections 8–11 — Templates

> **Day 4 handout.** Fillable templates for the four sections that complete the PRD: Section 8 Metrics & validation, Section 9 Risks & open questions, Section 10 Dependencies, Section 11 Out-of-scope follow-ups. Pull consistently from your Week-2 Tier Sheet and NS Defense Card.

---

## Section 8 — Metrics & validation

```markdown
## 8. Metrics & validation

### Primary metric (the one we're trying to move)
> [Single op-signal or KPI from your Tier Sheet]
> Baseline: <current value>
> Target: <30-day target>
> Why this number: <2-sentence defense>

### Counter-metric (the guardrail)
> [Counter-metric from your NS Defense Card]
> If this moves *the wrong way*, we are winning the primary for the wrong reasons.

### Secondary metrics (3 max)
- <op-signal 1>: directional indicator
- <op-signal 2>: directional indicator
- <op-signal 3>: directional indicator

### Validation plan
- **Pre-launch:** smoke tests (link to AC verification)
- **Launch + 7 days:** check primary metric directional correctness
- **Launch + 30 days:** measure primary against target
- **Launch + 90 days:** check counter-metric for guardrail violation

### What "good enough" looks like
We'll consider this feature successful if [primary metric] moves
≥ [target delta] within 30 days, AND [counter-metric] stays within
[acceptable band].
```

> **Rookie tells to avoid:** "we'll watch a few things" (force *one* primary), "improve" (force a specific delta), a counter-metric that drifted from Week 2 Day 2 (consistency — if it changed, one of the two is wrong).

---

## Section 9 — Risks & open questions

**Risks** (named, with mitigation):

```markdown
| Risk | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation |
|------|--------------------|----------------|------------|
| Dispatchers refuse the new flow because it's longer | M | H | Optional toggle in v1; observe adoption; remove old flow only if adoption > 70% by week 4 |
| Audit-log volume blows our log budget | L | M | Tier-2 sample for non-error events; full sample for errors |
| Auth integration breaks if SSO IdP changes | L | H | Pre-coordinate with SecOps; document fallback to local auth |
```

**Open questions** (needed before or during build — every one gets an owner and a deadline):

```markdown
- Will the operations VP accept the temporary read-only manager view in week 1?
  (Owner: <name>; needed by: <date>)
- Does the audit store handle 24-month retention at this volume,
  or do we need an archival tier?
  (Owner: <name>; needed by: <date>)
```

**Assumptions** (treated as true; we'll learn if we're wrong — cite the basis):

```markdown
- Median dispatcher device is mid-tier Android on 4G LTE
  (basis: device-fleet snapshot Q3; revisit if changes)
- 30-day adoption signal is sufficient to declare success
  (basis: prior reconcile rollout; revisit if behavior is non-stationary)
```

> **"No risks" is a fail. Risks without mitigations are wishlist items. "TBD" as an owner is the unowned risk that slips — force a name.**

---

## Section 10 — Dependencies

```markdown
## 10. Dependencies

| Dependency | Owner | What we need | By when | Status |
|------------|-------|--------------|---------|--------|
| Auth team — SSO scope addition | <name> | New scope `reconcile.write` | Week of build kickoff | Confirmed in Slack 2026-04-15 |
| Data platform — event schema | <name> | Schema review for 7 new events | Day 1 of sprint 1 | Pending |
| Mobile build pipeline — signing | <name> | New signing cert for the new bundle ID | Pre-launch | Pending |
| Customer success — release messaging | <name> | Customer comms 1 week pre-launch | T-7 days | Pending |
```

> Every dependency has a **named owner**, not a team name. "Status" is honest — most will be *Pending*, and that's fine; pretending they're confirmed is the bug.

---

## Section 11 — Out-of-scope follow-ups

```markdown
## 11. Out-of-scope follow-ups (for the backlog)

- **Tablet layout** — same flow, different breakpoint. Tracked: TICKET-1234.
- **Spanish localization** — copy + reading order. Tracked: TICKET-1235.
- **Multi-shop manager view** — pulls reconcile data across shops. Tracked: TICKET-1236.
- **Offline-first sync** — current PRD supports offline draft + manual reconnect;
  full offline-first deferred. Tracked: TICKET-1237.
```

> Pull these from Section 3 non-goals + Section 4 scope-out + anything that surfaced this week. Items written as "future work" or "v2" are unactionable — be specific and add a ticket placeholder.
