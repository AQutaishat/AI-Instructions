# Programming Conventions

## General

- Prefer clarity over cleverness.
- Keep functions and classes focused.
- Use meaningful names.
- Avoid magic strings and magic numbers.
- Keep business rules explicit.
- Prefer composition over deep inheritance.
- Remove dead code instead of commenting it out.
- Do not leave debugging code or temporary files in committed code.

## Structure

For a monolithic backend, organize by coherent business feature/module rather than one giant technical-layer folder.

Example:

```text
src/backend/
├── Modules/
│   ├── Identity/
│   ├── Users/
│   ├── Orders/
│   └── Notifications/
├── Common/
├── Infrastructure/
└── Program.*
```

The exact module names must come from the project domain.

## Dependency Direction

- Domain/business logic should not depend on UI concerns.
- Infrastructure concerns should not leak unnecessarily into business rules.
- Keep external integrations behind focused interfaces when substitution/testing is useful.
- Do not introduce interface layers for trivial classes with no realistic alternate implementation.

## Naming

- Use one naming style consistently per language/framework.
- API field names must be consistent.
- Database naming must be consistent.
- Boolean names should read naturally (`isActive`, `canEdit`, `hasAccess`).

## Validation

Validate at system boundaries.

Examples:

- required fields;
- length/range;
- valid enum/state;
- cross-field business constraints;
- ownership/authorization.

Do not rely solely on frontend validation.

## Date and Time

- Store timestamps in UTC unless a domain rule requires otherwise.
- Convert for display at the client/UI boundary.
- Be explicit about timezone for scheduled operations.

## Logging

Use structured logs rather than concatenated free text.

Recommended properties:

```text
Environment
SourceApp
RequestId
UserId
Operation
EntityType
EntityId
DurationMs
Outcome
```

Do not log secrets or credentials.

## Database

- All schema changes through migrations.
- Meaningful foreign keys.
- Unique constraints for actual uniqueness rules.
- Index lookup/filter/sort columns based on real queries.
- Use transactions for multi-step state changes that must be atomic.
- Avoid unnecessary repository abstractions if the chosen data access technology already provides an appropriate unit of work.

## API

Suggested error envelope:

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

Do not expose internal exception details.

## Configuration

Configuration belongs in:

- environment variables;
- environment-specific configuration files without secrets;
- a secret manager for production;
- `docs/credentials/` only for local/manual sensitive material that must not be committed.

## Dependency Policy

Before adding a package:

1. confirm built-in/framework functionality is insufficient;
2. confirm the package is actively maintained;
3. consider security and license;
4. avoid large dependencies for trivial functions.
