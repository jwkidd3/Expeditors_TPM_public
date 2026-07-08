# REST Method-Map Card

> **Day 3 handout.** The five HTTP methods, what each is for, and whether it's idempotent. Plus the status codes that carry meaning. Keep it beside you while you sketch resource models.

REST treats the system as a set of **resources** (nouns) accessed by standard HTTP methods (verbs).

| Method | Purpose | Idempotent? |
|--------|---------|-------------|
| GET | Retrieve | Yes |
| POST | Create | No |
| PUT | Replace | Yes |
| PATCH | Update partially | No (typically) |
| DELETE | Remove | Yes |

---

## URLs reflect resources

`/dispatchers/{id}/reconciles/{id}` — nouns, nested for sub-resources. Use `/<plural>/{id}` for an individual resource.

## Status codes carry meaning

`200` · `201` · `204` · `400` · `401` · `403` · `404` · `409` · `422` · `429` · `500` · `502` · `503`

Specific codes carry actionable distinctions — `422` vs `400` vs `409` are not interchangeable. Don't lump everything at 400/500.

## Two rookie errors to avoid

- **Verbs in URLs.** `POST /lists/{id}/shares` (resource) beats `POST /lists/{id}/share` (verb). REST nudges toward nouns even when an action is involved.
- **Path vs query confusion.** Ask "am I *identifying* a resource or *filtering* a set?" Identifying → path parameter. Filtering → query parameter.
