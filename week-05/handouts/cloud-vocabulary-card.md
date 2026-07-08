# Cloud Vocabulary Card

> **Day 2 handout.** The eight cloud-topology terms you'll use to draft TMD §2 — with the TPM-relevant signal each one carries.

| Term | What it means | TPM-relevant signal |
|------|---------------|---------------------|
| **Region** | A geographic cloud location (us-east-1, eu-west-2) | Drives data residency + base latency to users |
| **Availability Zone (AZ)** | A failure-isolated facility within a region | Multi-AZ = survives single facility failure |
| **Multi-region** | Deployment across regions | Survives whole region failure; expensive |
| **Managed service** | Cloud provider runs it (RDS, S3, SQS) | Less ops cost; less control |
| **Self-managed** | You run it on raw compute | More control; more ops cost |
| **Multi-tenant** | One deployment serves all customers | Lower cost; harder isolation |
| **Single-tenant** | Each customer gets their own deployment | Stronger isolation; higher cost |
| **Edge / CDN** | Static and cached content served closest to users | Reduces latency for static assets |

---

## The five cloud-topology decisions TMD §2 documents

1. **Region choice** — which region(s)?
2. **Multi-AZ stance** — single AZ, multi-AZ, multi-region?
3. **Managed vs self-managed** — for each component, who runs it?
4. **Multi-tenancy stance** — shared / dedicated / hybrid?
5. **Network boundary** — public, private, VPN, direct connect?

Each decision has a **cost dimension** and a **risk dimension**. The TPM job: surface both, name the trade-off, and frame the choice in customer terms.
