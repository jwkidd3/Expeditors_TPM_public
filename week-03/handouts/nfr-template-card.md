# NFR Template Card

> **Day 3 handout.** The four-part shape every NFR follows, plus the five categories you must cover (at least one NFR each). The **Defense** is what separates a TPM-quality NFR from boilerplate — it's the part that's actually the work.

---

## The four-part shape

```markdown
### NFR — <short name>
**Category:** Performance / Security / Accessibility / Observability / Compliance

**Requirement:** <specific, measurable target>

**Defense:** <why this number, in plain language; what scenario justifies it>

**Verification:** <how we will test/observe this in production or pre-prod>
```

> A good defense reads like this: *"p95 latency < 400ms because dispatchers tap this 40 times per shift; 1 second feels slow at that frequency, and 400ms is below the threshold of feeling sluggish."* That reasoning is the work.

---

## The five categories — cover all five

| Category | What it pins down |
|----------|-------------------|
| **1. Performance** | Latency targets (p50/p95/p99), throughput, resource caps, cold-start time-to-interactive |
| **2. Security** | AuthN / AuthZ, data classification (PII/PCI/internal/public), encryption in transit + at rest, audit logging |
| **3. Accessibility** | WCAG conformance level (2.1 AA is the floor), the 8 checks, feature-specific keyboard + screen-reader behavior |
| **4. Observability** | Which logs (events, levels, structured fields), which metrics (from your Tier Sheet), which traces, which alerts |
| **5. Compliance** | Data residency, retention windows, industry regimes (SOC 2, HIPAA, PCI), audit-trail requirements |

Most PRDs need **6–10 NFRs total**.

---

## Worked FieldPulse example

```markdown
### NFR — Reconcile flow latency
**Category:** Performance
**Requirement:** Modal opens within 1 second (p95) on the median dispatcher device
            (mid-tier Android, 2-year-old hardware) on a 4G LTE connection.
**Defense:** Dispatchers tap "Reconcile all" 30+ times per shift. At p95 = 1s,
            cumulative wait ≤ 30s/shift. At p95 = 3s, cumulative wait = 90s/shift,
            crossing the threshold dispatchers reported as "I'd rather use paper."
**Verification:** Synthetic transaction in Datadog from a fleet of mid-tier devices.
            p95 reported daily; alert if 7-day trailing p95 > 1.2s.
```

---

## The good-NFR self-check

- [ ] Specific — names a number, a screen, a scope, a regime.
- [ ] Measurable at runtime — not a wish.
- [ ] Defended — grounded in user behavior or a metric, not abstraction.
- [ ] Testable — the Verification line is real, not aspirational.
- [ ] Performance targets are at **p95 or p99**, never "average" (average lies in bimodal distributions).
