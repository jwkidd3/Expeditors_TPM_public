# Alert-Design Template

> **Day 5 handout.** The four-question check for every on-call alert. If you can't answer all four, the alert is noise — it'll be muted within a sprint. Aim for 3–5 alerts per feature.

Copy this block once per alert.

```markdown
### Alert: <name>
**What it means:** <plain English>
**What on-call does:** <specific first runbook step>
**Threshold + window:** <X over Y minutes, e.g. "5xx rate > 1% over 5 min">
**Severity:** Page / Slack / log only
```

---

## The four questions

1. **What does it mean?** (Plain English — no metric jargon.)
2. **What does the on-call do when it fires?** (A specific runbook step, not "investigate.")
3. **What's the threshold + window?** (e.g., "5xx rate > 1% over 5 min.")
4. **What's the severity?** (Page / Slack / log only.)

## The discipline

- An alert **without a runbook step** is noise that gets muted. Force the on-call action.
- Aim for **3–5 alerts** per feature. More alerts means more noise, which means the real one gets missed.
