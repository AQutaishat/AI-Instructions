# Programming Conventions

## General

- clarity over cleverness;
- focused functions/classes;
- meaningful names;
- avoid magic strings/numbers;
- explicit business rules;
- composition over deep inheritance;
- remove dead code instead of commenting it out;
- no debug code/temp files in commits.

## Backend structure

Recommended modular monolith:

```text
backend/src/
├── Api/
├── Modules/
│   ├── [DomainModule]/
│   └── ...
├── Application/
├── Domain/
├── Infrastructure/
└── Common/
```

Exact module names come from the project domain.

## Frontend structure

Recommended:

```text
frontend/src/
├── app/
├── features/
├── components/
├── pages/
├── layouts/
├── api/
├── hooks/
├── i18n/
└── theme/
```

Prefer feature ownership over dumping everything into global folders.

## Dependency direction

- domain/business rules do not depend on UI;
- infrastructure should not leak into domain unnecessarily;
- external integrations use focused interfaces when useful;
- do not create interface layers for trivial classes without realistic substitution/testing value.

## Naming

Use framework conventions consistently.

Booleans should read naturally:

```text
isActive
canEdit
hasAccess
```

## Validation

Validate at system boundaries:
- required;
- length/range;
- enum/state;
- cross-field business rules;
- ownership/authorization.

Do not rely on React-only validation.

## Date/time

- store timestamps in UTC unless a domain rule requires otherwise;
- convert for display at UI boundary;
- scheduled operations must define timezone explicitly.

## Database

- all schema changes through EF Core migrations;
- meaningful FKs;
- unique constraints for true uniqueness;
- indexes for real lookup/filter/sort paths;
- transactions where atomicity matters;
- avoid unnecessary repository abstractions over EF Core.

## Logging

Use structured events rather than concatenated free text.

Standard properties:

```text
Environment
SourceApp
RequestId
TraceId
UserId
Operation
EntityType
EntityId
DurationMs
Outcome
```

## Configuration

Use:
- environment variables;
- safe environment-specific configuration;
- secret manager for production;
- ignored `docs/credentials/` files only when local/manual secret reference is needed.

## Dependency policy

Before adding a NuGet/npm package:

1. confirm ASP.NET Core/.NET/React/browser built-ins are insufficient;
2. confirm the package is actively maintained;
3. consider security;
4. consider license;
5. avoid large dependencies for trivial functionality;
6. remove unused packages.

## API error envelope

Recommended:

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
