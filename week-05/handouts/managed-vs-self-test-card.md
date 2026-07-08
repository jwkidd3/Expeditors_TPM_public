# Managed-vs-Self Decision Card

> **Day 2 handout.** The default and the four-question test for deciding, per component, whether to use a managed cloud service or self-manage it. Plus the table to fill in for every TCD container.

## The default: managed service first

Use the managed service **unless you have a specific reason not to**. For most B2B features, the answer is **managed** — don't reinvent.

Legitimate reasons to self-manage:

- The managed service's failure modes don't match your needs.
- The managed service is significantly more expensive at your scale.
- Compliance requires data control the provider can't offer.
- Your team has unusual operational expertise that would go to waste.

## The four-question test

For each component, ask:

1. Do failure modes match our needs?
2. Is cost reasonable at expected scale?
3. Does compliance allow it?
4. Do we have a specific reason to control this?

---

## The table to fill in

Cover **every** container from your TCD Container diagram.

| Component | Managed option | Choice | Why |
|-----------|----------------|--------|-----|
| | | | |
| | | | |
| | | | |
| | | | |

Common managed options: RDS (Postgres), MSK (Kafka), ElastiCache (Redis), S3 (object storage), ALB (load balancer).

## What "good" looks like

- Most components are **managed**.
- Self-managed choices have a **specific** justification — not "we want control." (If you catch yourself writing "we want full control," ask: *what specific decision do I need to make that the managed service forecloses?*)
- The cost dimension is named, even roughly ("comparable to RDS at our size").
