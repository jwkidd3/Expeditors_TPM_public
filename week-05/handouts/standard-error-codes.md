# Standard Error-Codes Reference

> **Day 3 handout.** The "what do I do now?" guarantee. The seven most-needed error responses, what each means, what the body should carry — and a standard error-body shape to use across your whole API.

| Code | Meaning | Body should include |
|------|---------|---------------------|
| 400 | Bad request (validation) | Field-by-field errors with codes |
| 401 | Unauthenticated | Hint: SSO challenge or token-refresh path |
| 403 | Authenticated but unauthorized | Required scope name |
| 404 | Resource doesn't exist | Resource type + identifier |
| 409 | Conflict (idempotency / state) | What conflicted; how to resolve |
| 422 | Validated but business-rule violation | Which rule; which fields involved |
| 429 | Rate-limited | Retry-After header; current limit |

---

## Standardize the error-body shape across the API

Every error response should use the same shape, so callers can parse failures uniformly:

```json
{
  "error": {
    "code": "ticket_not_eligible",
    "message": "Ticket cannot be reconciled in current state",
    "fields": [{"name": "ticket_ids[3]", "reason": "ticket already reconciled"}]
  },
  "request_id": "req_01H...",
  "documentation_url": "https://docs.../errors/ticket_not_eligible"
}
```

## The discipline

- Don't lump failures at `400` / `500`. The specific `409` / `422` / `429` codes carry actionable distinctions a caller can act on.
- A machine-readable `code`, a human `message`, a `request_id` for support, and a `documentation_url` turn "it failed" into "here's what to do next."
