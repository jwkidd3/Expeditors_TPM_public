# Database Vocabulary Card

> **Day 1 handout.** The nine data-modeling terms to keep straight while you draft TMD §1 — with the TPM-relevant signal each one carries.

Use this as your reference while you model entities, keys, and indexes. You don't have to *implement* any of these — you have to name them clearly enough that an engineer can.

| Term | What it means | TPM-relevant signal |
|------|---------------|---------------------|
| **Entity** | A "thing" the system tracks (Dispatcher, Ticket, Reconcile) | The unit of the data model |
| **Primary key** | The unique identifier for an entity | Affects how entities are referenced |
| **Foreign key** | A reference from one entity to another | Models relationships |
| **Index** | A structure that speeds up specific reads at the cost of writes and storage | Tied directly to query patterns |
| **Normalization** | Splitting data into multiple entities to avoid duplication | Cleaner; sometimes slower |
| **Denormalization** | Duplicating data on purpose for read speed | Faster reads; harder consistency |
| **Constraint** | A rule the database enforces (NOT NULL, UNIQUE, CHECK) | Catches bugs before they ship |
| **Cardinality** | How many of one thing relate to how many of another (1:1, 1:N, N:N) | Governs the relationship shape |
| **Schema** | The set of definitions for entities + relationships + constraints | The artifact we ship today |

---

**The one discipline to remember:** design the *queries* before the schema. If your data model can't be defended by the queries that drive it, it's wrong.
