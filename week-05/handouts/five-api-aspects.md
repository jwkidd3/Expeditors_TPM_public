# The Five API Aspects a TPM Must Read

> **Day 3 handout.** You won't write the OpenAPI spec line by line — but you must be able to review one and ask sharp questions. These are the five aspects to check in any API contract.

| Aspect | Question to answer |
|--------|--------------------|
| **Resources** | What nouns does the API expose? Are they consistent? |
| **Methods** | What verbs apply? Are they used consistently? |
| **Idempotency** | Can a client safely retry? How? (Idempotency key? Natural idempotence?) |
| **Versioning** | How does the API evolve without breaking existing callers? |
| **Errors** | What does a failure look like? Do error codes carry actionable info? |

---

## REST vs SOAP — the default and the exception

- **REST (often with JSON)** is the right default for most new B2B SaaS features.
- **SOAP** (XML over HTTP, with a WSDL contract) appears at integration boundaries with legacy partners. Consider it only when:
  - The integration partner only speaks SOAP (banks, government, EDI-adjacent systems).
  - WS-Security or WS-ReliableMessaging is contractually required.
  - The partner has invested heavily in SOAP tooling and rewriting them is impractical.

Default to REST. Justify any SOAP touchpoint against a **named partner requirement** — "just in case" SOAP support is gold-plating.
