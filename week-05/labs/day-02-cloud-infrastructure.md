# Day 2 — Cloud Architecture & Infrastructure

> **Activity packet** for facilitators and participant triads. Today's job: take the entities from Day 1 and the components from the TCD, decide where they **physically run**, and draft TMD §2 — Cloud topology.

## Where we are in the week

Day 1 produced the entity model. Today decides **where each entity and each component runs in the cloud** — region, availability zone, managed service vs custom, multi-tenancy stance, and the cost / latency trade-offs that fall out.

By 16:00, every triad has TMD §2 with a topology that an SRE / platform engineer would accept.

## Inputs

- TMD §1 (data model)
- TCD §2 (Container diagram)
- TCD §4 (SLOs — region/AZ choices affect availability and latency budgets)
- TCD §3 (compliance — data residency drives region choice)

---

## The cloud vocabulary card (today's reference)

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

## The five cloud-topology decisions

For most features, the topology decision reduces to five choices. Today's TMD §2 documents each:

1. **Region choice** — which region(s)?
2. **Multi-AZ stance** — single AZ, multi-AZ, multi-region?
3. **Managed vs self-managed** — for each component, who runs it?
4. **Multi-tenancy stance** — shared / dedicated / hybrid?
5. **Network boundary** — public, private, VPN, direct connect?

Each decision has a **cost dimension** and a **risk dimension**. The TPM job: surface both, name the trade-off, and frame the choice in customer terms.

---

## Activity 1 — Region & Availability Zone Choice

**Format:** Triad &bull; **35 min** &bull; Block 1

### Purpose
Decide which region(s) the feature deploys to and which multi-AZ stance it takes. Defend in customer + compliance + cost terms.

### Setup
Each triad needs PRD §2 (customer base), TCD §3 (compliance), TCD §4 (SLOs), and the Week-4 trade-off template. AI optional.

### Triad protocol

1. **Pull customer-location facts from PRD §2** (5 min). Where do users live? Where is the bulk of traffic?
2. **Pull compliance facts from TCD §3** (5 min). Any data-residency requirements?
3. **Decide on region(s)** (10 min). Single region? Multi-region active-passive? Multi-region active-active?
4. **Decide on multi-AZ** (10 min). At minimum, 2-AZ for any production workload. 3-AZ for stateful workloads with quorum requirements.
5. **Capture the trade-off** (5 min). Use the Week-4 template.

### Worked example — FieldPulse reconcile

```markdown
### Region + AZ stance

**Region:** us-east-1 (primary), us-west-2 (warm-DR).
- Customer base: 92% US-based; 8% Canada (cross-region acceptable
  for Canadian users; latency ~80ms additional).
- Compliance: SOC 2 audit retention requires named region; no
  EU residency requirement currently.

**AZ stance:** Multi-AZ active-active for all stateful tiers
        (Postgres primary + 2 read replicas across 3 AZs).

**Trade-off — multi-region active-active vs warm-DR:**
**Option A:** us-east-1 primary, us-west-2 warm-DR (RPO 5 min,
            RTO 30 min).
**Option B:** Both regions live, traffic split via DNS.
**Choice:** Option A.
**Why:** Active-active doubles cost and adds cross-region
        consistency complexity; we don't have evidence of single-
        region outages costing more than the doubled cost. Multi-AZ
        within us-east-1 satisfies our 99.5% availability SLO.
**Accepted cost:** A full us-east-1 outage would breach SLO
        for ~30 minutes.
**Revisit trigger:** A second us-east-1 multi-hour outage in 12
        months, OR availability SLO tightens to 99.9%+.
```

### Output

A regional-stance section ready for TMD §2.

---

## Activity 2 — Managed vs Self-Managed for Each Component

**Format:** Triad &bull; **40 min** &bull; Block 2

### Purpose
For each container in the TCD's Container diagram, decide whether to use a managed service or self-manage. Defend each.

### Setup
Each triad needs the TCD Container diagram and the four-question test card. AI optional.

### The "managed service first" default

Default: **use the managed service unless you have a specific reason not to**. Reasons to self-manage:

- The managed service's failure modes don't match your needs
- The managed service is significantly more expensive at your scale
- Compliance requires data control the provider can't offer
- Your team has unusual operational expertise that goes to waste

For most B2B features, the answer is **managed**. Don't reinvent.

### Triad protocol

1. **List each container** (5 min). Pull from TCD §2.
2. **For each, identify the managed-service option** (10 min). e.g., RDS for Postgres, MSK for Kafka, ElastiCache for Redis, ALB for the load balancer.
3. **For each, decide managed or self** (15 min). Use the four-question test:
    - Do failure modes match our needs?
    - Is cost reasonable at expected scale?
    - Does compliance allow it?
    - Do we have a specific reason to control this?
4. **Capture the table** (10 min):

```markdown
| Component | Managed option | Choice | Why |
|-----------|----------------|--------|-----|
| Postgres | AWS RDS | Managed (RDS) | Default; team ops capacity is finite |
| Kafka | AWS MSK | Managed (MSK) | Same |
| Object storage | S3 | Managed (S3) | Industry-standard durability |
| Custom AI service (if any) | None | Self-managed | No managed equivalent |
```

### What "good" looks like

- Most components are **managed**
- Self-managed choices have a **specific** justification — not "we want control"
- The cost dimension is named (rough — "comparable to RDS at our size")

### Deliverable

Managed-vs-self table covering every TCD container, with a specific reason for each self-managed choice.

---

## Activity 3 — Multi-Tenancy + Network Boundary

**Format:** Triad &bull; **40 min** &bull; Block 3

### Purpose
Decide the multi-tenancy stance and the network boundary. Both are stakeholder-touching decisions.

### Setup
Each triad needs PRD §1 (customer context), the tenancy spectrum card, and the TCD §6 sign-off matrix. AI optional.

### Multi-tenancy spectrum

| Stance | Architecture | Pros | Cons |
|--------|--------------|------|------|
| **Shared** | One deployment serves all tenants | Lowest cost; easiest ops | Noisy neighbor; weakest isolation |
| **Pooled** | One deployment, but per-tenant limits + isolation | Lower cost than dedicated; better isolation | Complex tenant-aware code |
| **Dedicated** | One deployment per tenant | Strongest isolation; per-tenant compliance | High cost; complex deployment |
| **Hybrid** | Most tenants shared; some dedicated | Match cost to value | Operational overhead of two patterns |

Most B2B SaaS at FieldPulse's stage uses **pooled with per-tenant rate limits** (revisited from Week 4 Day 4).

### Triad protocol

1. **Identify your customers' tenancy expectations** (10 min). What did your PRD §1 customer say? Are any large customers contractually expecting dedicated infra?
2. **Pick a stance** (10 min). Pooled is the default; defend if you choose dedicated.
3. **Network boundary** (15 min). Decide:
    - Public internet (default for SaaS APIs)
    - Customer-VPN-only (some enterprise contracts)
    - Direct Connect / Private Link (large enterprise, regulated industries)
4. **Stakeholder implications** (5 min). Who needs to sign off? Add to TCD §6 if not already there.

### Worked example

```markdown
### Multi-tenancy stance

**Choice:** Pooled.

**Why:** All current and prospective customers fit the small-mid
        shop profile. None have contractually expected dedicated
        infra. Pooled with per-tenant rate limits (NFR from TCD §4)
        provides isolation against runaway scripts.

**Accepted cost:** A noisy-neighbor incident from one tenant could
        affect others. Mitigated by rate limits (TCD §4).

**Revisit trigger:** A customer larger than 5x our current largest
        signs, OR a regulated-industry customer requires dedicated.

### Network boundary

**Choice:** Public HTTPS for the API + mobile app traffic.
            Internal services in a private VPC.

**Why:** Standard for B2B SaaS at our segment. No customer has
        requested VPN-only.

**Revisit trigger:** Compliance (e.g., HIPAA-bound customer) or
        contractual demand.
```

### Deliverable

Tenancy stance and network boundary documented with rationale, revisit triggers, and updated sign-off matrix entries for any new stakeholders.

---

## Activity 4 — Cost Awareness + AI Sanity Check

**Format:** Triad &bull; **45 min** + Wrap &bull; Block 4

### Purpose
A TMD §2 without a cost dimension reads as wishful thinking. Today's last block: rough out the cost shape and use AI to surface gaps.

### Setup
Each triad needs the topology decisions from Activities 1–3, rough pricing references (RDS / MSK / S3 / ALB), and the AI sanity-check prompt. AI required.

### Cost awareness — the rough-order-of-magnitude pass

For each component, capture a rough monthly cost band. We're not pricing exactly — we're surfacing relative scale.

```markdown
| Component | Stance | ROM cost / month | Cost driver |
|-----------|--------|-------------------|-------------|
| Postgres (RDS) | Multi-AZ, db.m5.large | $400–$700 | Instance hours; storage; IOPS |
| Read replica | Single-AZ | $200–$350 | Instance hours |
| Kafka (MSK) | 3-broker, m5.large | $700–$1100 | Brokers; storage; egress |
| S3 (audit) | Standard tier | $50 / TB-month | Storage; PUT/GET requests |
| ALB | Standard | $25 + traffic | Hours + LCUs |
| Outbound bandwidth (estimated) | | $50–$150 | $/GB egress to internet |
```

The numbers are illustrative — engineering will refine. The TPM job: catch the **2x cost surprise** before it ships.

### AI sanity check

```
Role: SRE reviewing a feature's cloud topology.
Context: <paste TMD §2 sections — region, AZ, managed services,
         tenancy, network boundary, ROM cost>
Task: Identify the top 3 risks in this topology that could
      surprise the team within 6 months.
Constraints:
  - Be specific to the configurations described
  - For each: scenario, likelihood (L/M/H), suggested mitigation
  - Do not invent platform features
Format: Numbered — Risk / Scenario / Likelihood / Mitigation.
```

### Triad protocol

1. **ROM cost table** (15 min). Rough numbers for each component.
2. **AI sanity check** (10 min). Run the prompt; capture the 3 risks.
3. **Adopt / defer / reject** (10 min).
4. **Update §2** (10 min). Polish for sharing.

### Deliverable

Polished TMD §2 with ROM cost table, AI-surfaced topology risks adopted/deferred/rejected, and a provenance note.

### Wrap (last 15 min)

Each triad shares:

- Their region + AZ stance, in one sentence
- One trade-off they made (with revisit trigger)
- One cost surprise they want to flag for review

---

## End-of-day checkpoint

Each triad ends Day 2 with:

- [x] Region + AZ stance with trade-off
- [x] Managed-vs-self table for every component
- [x] Multi-tenancy stance with revisit trigger
- [x] Network boundary stance
- [x] **ROM cost table**
- [x] AI provenance log entry
- [x] TMD §2 drafted

## Facilitator reflection prompts (end of day)

- Which triad's ROM cost was most realistic? Hold up Friday.
- Did anyone pick multi-region active-active without justification? Most rookie expensive choice.
- Did any triad pick self-managed for components that have clear managed equivalents? Coach toward defaults.
- Did anyone treat tenancy as a tech decision rather than a customer-and-cost decision?
