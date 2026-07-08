# OpenAPI Endpoint Template

> **Day 3 handout.** The shape for documenting one endpoint in detail. Fill this for the central endpoint of your feature — path, params, required headers, request body, and the full range of responses.

```yaml
# <METHOD> /<version>/<resource-path>
summary: <one-line description of what this endpoint does>
parameters:
  - name: <path-or-query-param>
    in: path        # or query
    required: true
    schema:
      type: string
      format: uuid  # or as appropriate
request:
  headers:
    Authorization: Bearer <token type + required scope>
    Idempotency-Key: <client-generated UUID, if mutating>
  body:
    type: object
    required: [<field>, <field>]
    properties:
      <field>:
        type: <type>
        # constraints: minItems / maxItems / format / enum ...
responses:
  200/201: <success> — { <fields returned> }
  400: Validation error — { error: code, fields: [{name, reason}] }
  401: Missing/invalid token
  403: Token lacks <scope> scope
  409: Conflict (e.g. Idempotency-Key reused with different body)
  422: Business-rule violation (e.g. resource not eligible)
  429: Rate limit exceeded — Retry-After: <seconds>
```

---

## What "good" looks like

- URLs are **nouns** (resources), not verbs.
- Methods are used **consistently** across endpoints.
- Status codes are **specific** — `422` vs `400` vs `409` carry distinct meaning.
- **Required headers** (Authorization, Idempotency-Key) are explicit, not assumed.
- Every response the caller can actually receive is listed — happy path *and* the sad-path codes that apply.
