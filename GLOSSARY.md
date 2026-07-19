# TPM Academy — Glossary & Acronyms

A single reference for every acronym and shorthand used across the decks, labs, handouts, and knowledge checks. Grouped by area; the week where each is introduced is noted where useful.

---

## The artifact chain (the backbone of the course)

Each week produces one document; together they're the TPM's integrated spec. Weeks 3–7 build them by hand, Week 8 produces a compressed set with AI.

| Acronym | Full name | What it is |
|---|---|---|
| **PRD** | Product Requirements Document | The *what* and *why* — problem, users, scope, acceptance criteria (Week 3) |
| **TCD** | Technical Concept Document | Architecture, security, components, SLOs, trade-offs (Week 4) |
| **TMD** | Technical Modeling Document | Data model, cloud infra, APIs, sequences, monitoring (Week 5) |
| **SEP** | Stakeholder Engagement Plan | Stakeholder map, engagement plan, negotiated outcomes (Week 6) |
| **DP** | Delivery Plan | Outcomes, ADO setup, tracking, value-stream, bottlenecks (Week 7) |
| **AI Spec** | AI-Generated Technical Spec | The integrated spec that ties the artifact set together (Week 8) |

*"-light" versions (PRD-light, TCD-light, etc.) are the 2-page compressed forms produced in the Week 8 capstone.*

---

## Roles & people

| Acronym | Meaning |
|---|---|
| **TPM** | Technical Product Manager — the role this academy trains |
| **PM** | Product Manager |
| **EM** | Engineering Manager |
| **CEO / CFO / GM / VP** | Chief Executive / Chief Financial Officer / General Manager / Vice President |
| **CS / CSM** | Customer Success / Customer Success Manager |
| **GTM** | Go-To-Market (sales/marketing motion) |

---

## Weeks 1–2 — Customer discovery, metrics, design

| Acronym | Full name | Meaning |
|---|---|---|
| **RCCF** | Role, Context, Constraints, Format | The core AI-prompting scaffold |
| **PR/FAQ** | Press Release / Frequently Asked Questions | Amazon "Working Backwards" artifact (Day 2) |
| **JTBD** | Jobs To Be Done | The progress a customer is trying to make (Day 3) |
| **NS** | North Star (metric) | The one metric that best captures customer value (Week 2) |
| **KPI** | Key Performance Indicator | A supporting metric that ladders to the North Star |
| **UX** | User Experience | |
| **a11y** | Accessibility | Numeronym: "a" + 11 letters + "y" |
| **WCAG** | Web Content Accessibility Guidelines | The accessibility standard behind the a11y floor |
| **VoC** | Voice of Customer | Raw customer input (e.g., the Slack export in the Week-2 research pack) |

**Evidence tiers** (used course-wide to tag every claim, strongest → weakest): **Observed** (seen it happen) › **Reported** (someone said it) › **Inferred** (reasoned from other evidence) › **AI-generated** (drafted by AI; must be upgraded before use).

---

## Week 3 — Requirements

| Acronym | Full name | Meaning |
|---|---|---|
| **AC** | Acceptance Criteria | Given/When/Then conditions that define "done" |
| **NFR** | Non-Functional Requirement | Performance, security, accessibility, compliance requirements |

---

## Week 4 — Architecture, security, reliability

| Acronym | Full name | Meaning |
|---|---|---|
| **C4** | Context, Container, Component, Code | The 4-level architecture-diagram model (TPMs draw Context + Container) |
| **STRIDE** | Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege | Threat-modeling checklist |
| **SLO** | Service Level Objective | Internal reliability target (e.g., p95 ≤ 400 ms) |
| **SLA** | Service Level Agreement | Contractual commitment with consequences |
| **SLI** | Service Level Indicator | The actual measurement behind an SLO |
| **SOC 2** | System & Organization Controls 2 | Security/compliance audit framework |
| **PCI** | Payment Card Industry (Data Security Standard) | Card-handling compliance |
| **PII** | Personally Identifiable Information | |
| **CCPA** | California Consumer Privacy Act | Privacy regulation |
| **SSO** | Single Sign-On | |
| **TLS** | Transport Layer Security | Encryption in transit |
| **p95 / p99** | 95th / 99th percentile | Latency measured at a percentile, not an average |

---

## Week 5 — Data, cloud, APIs, modeling

| Acronym | Full name | Meaning |
|---|---|---|
| **API** | Application Programming Interface | |
| **REST** | Representational State Transfer | Resource-oriented API style (URLs are nouns) |
| **SOAP** | Simple Object Access Protocol | Older, contract-heavy API style |
| **HTTP** | HyperText Transfer Protocol | Methods: GET/POST/PUT/PATCH/DELETE |
| **PK / FK** | Primary Key / Foreign Key | Database keys |
| **UUID** | Universally Unique Identifier | |
| **URL** | Uniform Resource Locator | |
| **AZ** | Availability Zone | Cloud isolation boundary within a region |
| **RDS** | (Amazon) Relational Database Service | Managed SQL database |
| **S3** | (Amazon) Simple Storage Service | Object storage |
| **MSK** | (Amazon) Managed Streaming for Apache Kafka | Managed event streaming |
| **ALB / GW** | Application Load Balancer / (API) Gateway | Traffic entry points |
| **DLQ** | Dead-Letter Queue | Where failed messages land |
| **ROM** | Rough Order of Magnitude | Ballpark cost estimate |
| **VPN** | Virtual Private Network | |
| **RTT** | Round-Trip Time | Network latency for a request+response |
| **HTTP status** | 400/401/403/404/409/422/429 | Bad request / unauthenticated / forbidden / not found / conflict / unprocessable / rate-limited |

---

## Week 6 — Stakeholders & negotiation

| Acronym | Full name | Meaning |
|---|---|---|
| **SEP** | Stakeholder Engagement Plan | The Week-6 artifact |
| **RACI** | Responsible, Accountable, Consulted, Informed | Decision-rights matrix (exactly one Accountable) |

---

## Week 7 — Agile delivery & Azure DevOps

| Acronym | Full name | Meaning |
|---|---|---|
| **DP** | Delivery Plan | The Week-7 artifact |
| **ADO** | Azure DevOps | The work-tracking platform |
| **WIQL** | Work Item Query Language | ADO's query language for saved queries |
| **VSM** | Value Stream Mapping | Lean technique for finding delivery waste |
| **PT / LT** | Process Time / Lead Time | Time working vs. total elapsed time (flow efficiency = PT/LT) |
| **WIP** | Work In Progress | |
| **ToC** | Theory of Constraints | One bottleneck governs system throughput (Goldratt) |
| **CFD** | Cumulative Flow Diagram | Chart of work states over time |

---

## Week 8 — AI spec & capstone

| Acronym | Meaning |
|---|---|
| **AI** | Artificial Intelligence |
| **AI Spec** | The integrated, AI-drafted technical spec (validated section by section) |

*Capstone subject is the triad's choice — FieldPulse or an internal project of their own.*

---

## The running case study

| Term | Meaning |
|---|---|
| **FieldPulse** | The fictional case-study product: a mobile-first field-service **dispatch SaaS** for HVAC/plumbing/electrical shops with 50–200 technicians |
| **HVAC** | Heating, Ventilation & Air Conditioning |
| **ARR** | Annual Recurring Revenue (FieldPulse: ~$40M) |
| **End-of-Day Reconcile** | FieldPulse's signature feature idea — close out the day in ~5 min instead of ~45 |
| **SaaS** | Software as a Service |

---

## Assessment & document shorthand

| Shorthand | Meaning |
|---|---|
| **MC** | Multiple Choice (knowledge-check question) |
| **T/F** | True / False (knowledge-check question) |
| **TBD** | To Be Determined |
