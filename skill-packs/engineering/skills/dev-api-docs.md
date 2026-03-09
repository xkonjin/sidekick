---
name: api-docs
description: "Document an API endpoint or set of endpoints. Trigger when the user says 'document this API', 'API documentation', 'write API docs', 'document this endpoint', or pastes API code and asks for documentation."
---

# API Documentation

Produces clear, complete endpoint documentation that developers can use without reading source code.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/working-preferences.md` - Output format preferences (if it exists)
- `sidekick/memory/glossary.md` - Internal terminology to use correctly

### Step 2: Gather Information

Ask for anything not already provided:

- What endpoint(s) to document?
- What is the base URL or service name?
- Is there existing code, OpenAPI spec, or Postman collection to reference?
- Who is the audience? (Internal engineers, external developers, both)
- Any authentication or rate limiting that applies?

### Step 3: Document Each Endpoint

For each endpoint, produce:

````markdown
## [Verb] [Path]

[One sentence: what this endpoint does and when to use it.]

**Authentication:** [Required / None / Bearer token / API key]
**Rate limit:** [Requests per minute/hour, or None]

### Request

**Path parameters**

| Parameter | Type   | Required | Description            |
| --------- | ------ | -------- | ---------------------- |
| `id`      | string | Yes      | [What this identifies] |

**Query parameters**

| Parameter | Type    | Required | Default | Description                     |
| --------- | ------- | -------- | ------- | ------------------------------- |
| `limit`   | integer | No       | 20      | [What it controls, valid range] |

**Request body** (if applicable)

```json
{
  "field": "value",
  "nested": {
    "key": "value"
  }
}
```
````

| Field   | Type   | Required | Description               |
| ------- | ------ | -------- | ------------------------- |
| `field` | string | Yes      | [What it is, constraints] |

### Response

**Success (200)**

```json
{
  "id": "abc123",
  "status": "active",
  "created_at": "2024-01-15T10:30:00Z"
}
```

| Field | Type   | Description       |
| ----- | ------ | ----------------- |
| `id`  | string | Unique identifier |

**Error responses**

| Status | Code            | When it happens           |
| ------ | --------------- | ------------------------- |
| 400    | `INVALID_INPUT` | [Specific condition]      |
| 401    | `UNAUTHORIZED`  | Missing or invalid token  |
| 404    | `NOT_FOUND`     | [Resource] does not exist |
| 429    | `RATE_LIMITED`  | Exceeded rate limit       |

### Example

```bash
curl -X POST https://api.example.com/v1/resource \
  -H "Authorization: Bearer TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"field": "value"}'
```

```

### Step 4: Review and Save

- Present to user and ask: "Does this match the actual behavior?"
- Ask where to save (inline in codebase, separate docs file, etc.)
- Save to `sidekick/outputs/api-docs-[service]-[DATE].md` unless otherwise specified

## Rules

- Every error response must have a concrete "when it happens" description, not just the HTTP status
- Include working curl examples, not pseudocode
- If a field's valid values are an enum, list all values
- Do not document behavior you're inferring — ask the user to confirm anything uncertain
- Match field names exactly to what the API returns, including casing
```
