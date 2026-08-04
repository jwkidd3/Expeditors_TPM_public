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

## Reference bands (illustrative, Azure)

| Component | Example stance | ROM band | Driver |
|-----------|----------------|----------|--------|
| Postgres (Azure Database for PostgreSQL) | Multi-AZ, D2ds_v5 | $400–$700 | Compute hours; storage; IOPS |
| Read replica | Single-AZ | $200–$350 | Compute hours |
| Event stream (Azure Event Hubs) | Standard tier, 10 throughput units | $700–$1100 | Throughput units; capture storage; egress |
| Blob Storage (audit) | Hot tier | $50 / TB-month | Storage; read/write operations |
| Application Gateway | Standard | $25 + traffic | Hours + capacity units |
| Outbound bandwidth | Estimated | $50–$150 | $/GB egress to internet |

## Two things to remember

- **Don't over-precision.** Numbers tighter than a ROM band are a trap. You're hunting 2x surprises, not modeling finance.
- **Name the egress line.** Outbound bandwidth is the cost that hides. Put it on the table as its own line item even if the number is rough.
