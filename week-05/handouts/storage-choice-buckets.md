# Storage-Choice Buckets

> **Day 1 handout.** The four storage families most B2B features choose between — and when to reach for each. Your job is not to pick the engine; it's to describe the access pattern clearly enough that the architect can.

| Bucket | When to reach for it |
|--------|----------------------|
| **Relational (Postgres, MySQL)** | Strong relationships, transactions, complex queries; default for most B2B |
| **Document (MongoDB, Firestore)** | Flexible schema, hierarchical data; good when shape varies per record |
| **Key-value (Redis, Azure Cosmos DB)** | High throughput, simple lookups, caches, session state |
| **Search (Elasticsearch, OpenSearch)** | Full-text search, analytics on text |

---

**How to use this on your feature:**

1. Describe the dominant access pattern (from your Access Pattern Sheet).
2. Match it to the bucket that serves it cheapest.
3. Note where a second bucket might carry a secondary pattern (e.g., relational primary + search index for full-text).

A TPM **describes the access pattern**; the architect **picks the engine**. Don't skip straight to the engine name.
