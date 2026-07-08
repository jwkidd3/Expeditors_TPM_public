# ROM Cost Table

> **Day 2 handout.** A rough-order-of-magnitude cost table for your topology. The goal is not finance modeling — it's catching the 2x cost surprise before it ships.

For each component, capture a **rough monthly cost band** and the driver. We're surfacing relative scale, not pricing exactly — engineering will refine.

| Component | Stance | ROM cost / month | Cost driver |
|-----------|--------|-------------------|-------------|
| | | | |
| | | | |
| | | | |
| | | | |
| | | | |
| | | | |

---

## Reference bands (illustrative, AWS)

| Component | Example stance | ROM band | Driver |
|-----------|----------------|----------|--------|
| Postgres (RDS) | Multi-AZ, db.m5.large | $400–$700 | Instance hours; storage; IOPS |
| Read replica | Single-AZ | $200–$350 | Instance hours |
| Kafka (MSK) | 3-broker, m5.large | $700–$1100 | Brokers; storage; egress |
| S3 (audit) | Standard tier | $50 / TB-month | Storage; PUT/GET requests |
| ALB | Standard | $25 + traffic | Hours + LCUs |
| Outbound bandwidth | Estimated | $50–$150 | $/GB egress to internet |

## Two things to remember

- **Don't over-precision.** Numbers tighter than a ROM band are a trap. You're hunting 2x surprises, not modeling finance.
- **Name the egress line.** Outbound bandwidth is the cost that hides. Put it on the table as its own line item even if the number is rough.
