# Threat Documentation Template

> **Day 2 · Activity 2 handout.** After your STRIDE walk, document the top 5 threats. Each threat pins to a specific box or arrow in your feature's data flow, with a specific mitigation and a named owner.

---

### Per-threat template (fill one per threat, five total)

```markdown
### Threat — <short name>
**STRIDE letter:** S / T / R / I / D / E
**Where:** [box or arrow in your data flow]
**Scenario:** [one sentence]
**Likelihood:** L / M / H
**Impact:** L / M / H
**Mitigation:** [specific control; "TLS" is not a complete answer]
**Owner:** [who will validate this — security team, you, the architect]
```

---

### What "good" looks like

- Threats reference **specific arrows or boxes** in your data flow — not "the system generally."
- Mitigations are **specific controls**, not "use security best practices." Name version, scope, and how it's verified.
- **At least 2 of the 5** are *not* Spoofing or Information Disclosure (the easy ones). Push toward Tampering and Repudiation.
- Every threat has an **owner** named for validation.

> "TLS" is a hint, not a mitigation. Force the specific control: which version, what scope, how verified.

---

### Top-5 roll-up

| # | Threat | Letter | Where | L | I | Owner |
|---|--------|--------|-------|---|---|-------|
| 1 | | | | | | |
| 2 | | | | | | |
| 3 | | | | | | |
| 4 | | | | | | |
| 5 | | | | | | |
