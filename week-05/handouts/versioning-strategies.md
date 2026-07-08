# API Versioning Strategies

> **Day 3 handout.** The "evolve without breaking" guarantee. Three common strategies, their trade-offs, and the default. Pick one and document it — "we don't need versioning yet" defers a cost rather than removing one.

| Strategy | Where the version lives | Pros | Cons |
|----------|--------------------------|------|------|
| **URL path** | `/v1/...` `/v2/...` | Easy to read; clear breaking changes | Code duplication |
| **Header** | `X-API-Version: 2` | URL stays clean | Less discoverable |
| **Content negotiation** | `Accept: application/vnd.acme+json;v=2` | Standard | Often poorly understood |

---

## The default

For most B2B APIs, **URL path versioning** is the right default. It's the most discoverable and makes breaking changes explicit.

## Document your choice

> **Versioning strategy:** ______________________
>
> **Rationale:** ______________________

Force the strategy choice **now**. Deferring it doesn't remove the cost — it just moves it to the first time you need a breaking change, when it's more expensive.
