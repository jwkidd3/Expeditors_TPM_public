# Week 5 Knowledge Check — Technical Infrastructure & Modeling

> A short retention check covering the week's core ideas: data models & access patterns, cloud architecture, REST/SOAP APIs, high-level sequence modeling, and performance baselines, monitoring & AI-summary validation. Answer each question, then check yourself against the key at the end. Aim for concepts, not trivia — every answer maps back to something we used in a lab.

**Format:** 12 questions (multiple choice + true/false). ~15 minutes. Individual or triad.

---

## Questions

**1. (MC)** In the "Access Pattern First" discipline, what is the *first* step before designing a schema?

- A) Pick the database engine (Postgres by default)
- B) List the queries the feature needs
- C) Draw the entity-relationship diagram
- D) Add indexes to speed up reads

**2. (MC)** Which storage bucket do you reach for when you need high throughput, simple lookups, caches, and sessions?

- A) Relational (Postgres, MySQL)
- B) Document (MongoDB, Firestore)
- C) Key-value (Redis, DynamoDB)
- D) Search (Elasticsearch, OpenSearch)

**3. (T/F)** In this course, the TPM's job is to pick the database engine — for example, deciding Postgres vs MongoDB.

**4. (MC)** In the managed-vs-self "Four-Question Test," which justification for self-managing is called a "smell"?

- A) "The managed service's failure modes don't match our needs"
- B) "Compliance forbids the managed service"
- C) "We want full control"
- D) "Cost is unreasonable at our expected scale"

**5. (T/F)** "We should be more secure" is a sufficient reason to adopt a customer-VPN-only network boundary.

**6. (MC)** In the ROM cost table, which cost is called out as the most-forgotten?

- A) Postgres (RDS) hours
- B) Egress bandwidth
- C) S3 storage
- D) Load balancer LCUs

**7. (MC)** Which HTTP status code signals an idempotency or state collision?

- A) 400 Bad request
- B) 403 Unauthorized
- C) 409 Conflict
- D) 422 Unprocessable

**8. (T/F)** For a "share" action, `POST /share` (a verb in the URL) is the recommended REST pattern.

**9. (MC)** In a weird-path sequence diagram, what is described as the "senior-author signal"?

- A) Showing every lifeline in the whole system
- B) Naming the invariant the design preserves
- C) Redrawing the full happy path first
- D) Adding a latency-budget note

**10. (T/F)** A sad-path sequence that ends with the user stuck (no recovery action) is acceptable as long as the error is rare.

**11. (MC)** The 4-Question Alert Test says that an alert which can't answer all four questions is:

- A) A page-level (Sev1) alert
- B) Noise — it'll be muted within a sprint
- C) An executive-dashboard metric
- D) A performance baseline

**12. (MC)** In the AI-Summary Validation Log, which status means "used as input but not yet validated — track to closure"?

- A) Cross-checked all citations
- B) Spot-checked
- C) Adopted with rationale
- D) Pending

---

# Answer Key

**1. B** — List the queries first, then design the schema so those queries are cheap. If a data model can't be defended by the queries that drive it, it's wrong.

**2. C** — Key-value (Redis, DynamoDB) is the bucket for high throughput, simple lookups, caches, and sessions. Relational is the B2B default; document is for flexible/hierarchical shapes; search is for full-text.

**3. False** — The TPM doesn't pick the engine. The TPM describes the access pattern clearly enough that the architect can.

**4. C** — "We want full control" is the smell. Default to the managed service; push for the specific decision the managed service forecloses. The other three are legitimate reasons to self-manage.

**5. False** — Don't volunteer for VPN-only; it triples ops complexity. "More secure" is a reason for stronger TLS, not a customer-VPN boundary — only choose it if a customer requires it.

**6. B** — Egress bandwidth is the most-forgotten cost. The ROM goal is rough order of magnitude; the TPM job is catching the 2x surprise before it ships.

**7. C** — 409 Conflict is idempotency / state collision. (401 = unauthenticated; 403 = authenticated but lacks permission; 422 = validated but violates a business rule.)

**8. False** — URLs are nouns; the verb is the HTTP method. `POST /share` is wrong; `POST /shares` is right.

**9. B** — Naming the invariant (e.g., "at most one ReconcileEvent per Idempotency-Key per 24h") is the senior-author signal. If a triad can't name the invariant, the weird-path design isn't done.

**10. False** — The user must have a path forward, not a dead-end. A sad path that ends "user is stuck" is not designed — force the recovery action.

**11. B** — If you can't answer all four (meaning, on-call action, threshold + window, severity), the alert is noise and will be muted within a sprint.

**12. D** — "Pending" means used as input but not yet validated; it needs a deadline and must be tracked to closure, or it becomes "we trusted the AI."
