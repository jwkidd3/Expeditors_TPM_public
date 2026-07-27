# C4 Diagram Legend Card

> **Day 3 · Activities 1–2 handout.** Every C4 diagram needs a legend so non-architects can read it. A diagram without a legend is a Rorschach test — force the legend.

---

### The legend (copy onto every diagram)

```
Legend
- ◻ Box with no fill   = system / module owned by us
- ◼ Box with fill      = external system (out of our control)
- 👤 Stick figure / labeled box = person (role)
- → Solid arrow        = synchronous call
- ⇢ Dashed arrow       = async / event
- (label on arrow)     = intent in plain English
```

---

### The two levels we draw (and why only two)

| Level | What it shows | Audience | We draw it? |
|-------|---------------|----------|-------------|
| **Context** | The system + its users + neighbors | Everyone, including stakeholders | ✅ Today |
| **Container** | Deployable units inside the system | TPMs, architects, devs | ✅ Today |
| **Component** | Code-level building blocks within a container | Engineers | ❌ Engineering job |
| **Code** | Class-level detail | Engineers | ❌ Engineering job |

**Context + Container is TPM scope.**

---

### Context diagram (Level 1) — the rules

Answers: *who interacts with this system, and what other systems does it talk to?*

Include: **people** (roles), the **one system in scope**, and **external systems**. Arrows carry brief intent labels ("submits reconcile" / "issues SSO token" / "writes audit events").

**Deliberately NOT in the Context diagram:** database choices, internal services, protocols (REST vs gRPC), hostnames, environments, deployment units.

> Keep it under **12 boxes**. If it has 20, you're sneaking Container concerns in.

---

### Container diagram (Level 2) — the rules

Answers: *inside the system, what are the deployable units, and how do they talk?*

A **container** is anything you'd update independently — a web app, a mobile app, a service, a database, a queue, a CDN, an event bus. Arrows show protocol and direction with brief intent labels.

> A **modular monolith** looks like *one* big container with internal modules listed as sub-boxes. A **microservice split** looks like *multiple* containers. The container diagram is where the Day-1 stance becomes visible — don't promote modules to standalone containers without justification.
