# NFR Triage Pack

> **Day 3 · Activity 1 handout.** Ten Non-Functional Requirements drawn from real (anonymized) FieldPulse PRDs. Some are clean. Most carry at least one failure mode. **Your job:** triage all ten, then rewrite the five worst using the four-part NFR template. No labels are provided — the judging is the work.

Failure modes to check against: **Boilerplate · Unmeasurable · No defense · No verification · Wrong category.**

---

### NFR-1
```
Category: Performance
Requirement: The reconcile flow shall perform acceptably under normal load.
```

### NFR-2
```
Category: Performance
Requirement: The reconcile modal opens within 1 second (p95) on a mid-tier
             Android device on 4G LTE.
Defense: Dispatchers tap "Reconcile all" 30+ times per shift; above ~1s p95
         the cumulative wait crosses the "I'd rather use paper" threshold they
         reported in interviews.
Verification: Synthetic transaction in Datadog from a mid-tier device fleet;
         p95 reported daily, alert if 7-day trailing p95 > 1.2s.
```

### NFR-3
```
Category: Security
Requirement: The system shall be secure and protect user data.
```

### NFR-4
```
Category: Observability
Requirement: p99 write latency for the audit-event store shall be < 50ms.
```

### NFR-5
```
Category: Accessibility
Requirement: The reconcile flow conforms to WCAG 2.1 AA — all interactive
             elements keyboard-focusable, visible focus indicators, 4.5:1 text
             contrast minimum, form fields labeled, errors identify the field.
Defense: Interview 3 was a screen-reader user; ADA exposure is non-trivial in
         our customer segment.
Verification: axe-core scan on every PR; manual screen-reader pass before launch.
```

### NFR-6
```
Category: Performance
Requirement: The confidence banner shall let dispatchers jump straight to the
             field that is missing data.
```

### NFR-7
```
Category: Compliance
Requirement: Reconcile-flow user-action events are retained for 24 months in the
             audit store, queryable by dispatcher_id and date range.
Defense: SOC 2 Type II requires a user-action audit trail; dispatch decisions
         are subject to wage-and-hour audit by some state authorities.
Verification: Quarterly test — a random user-event from 18 months ago must be
         retrievable in < 10 minutes.
```

### NFR-8
```
Category: Security
Requirement: All reconcile API traffic is encrypted with TLS 1.2 or higher in
             transit; audit-event payloads are encrypted at rest with
             platform-managed keys.
```

### NFR-9
```
Category: Observability
Requirement: The system shall have good logging and monitoring.
```

### NFR-10
```
Category: Compliance
Requirement: The reconcile feature shall be highly available.
```

---

## Triage worksheet

| NFR | Failure mode(s) or "clean" | (Rewrite the 5 worst below) |
|:--:|-----------------------------|-----------------------------|
| 1 | | |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |
| 6 | | |
| 7 | | |
| 8 | | |
| 9 | | |
| 10 | | |

**Hardest NFR to defend even after rewriting:** ______________________
**Why (one sentence):** ______________________
