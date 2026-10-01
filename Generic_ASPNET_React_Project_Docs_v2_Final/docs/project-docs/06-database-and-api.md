# Database and API

## Database rules

- PostgreSQL;
- EF Core migrations;
- UTC timestamps;
- proper foreign keys;
- constraints for enforceable invariants;
- indexes based on real queries;
- transactions for atomic multi-step state changes;
- pagination for unbounded collections;
- avoid N+1 queries.

Do not add nullable columns merely to avoid designing data integrity correctly.

## Naming

Recommended:

```text
PostgreSQL: snake_case
C#: PascalCase
JSON: camelCase
```

Use one consistent convention.

## API design

- stable resource naming;
- HTTP semantics;
- explicit DTOs;
- input validation;
- pagination where needed;
- authorization on server;
- backwards compatibility for public contracts where practical.

When reasonable, design mutating operations to be safely retryable/idempotent.

## Standard error envelope

```json
{
  "code": "validation_error",
  "message": "One or more fields are invalid.",
  "errors": {
    "field": ["Message"]
  },
  "requestId": "..."
}
```

Common responses:

```text
400 validation
401 unauthenticated
403 unauthorized
404 not found
409 business/state conflict
500 unexpected failure
```

Never return raw exception details.
