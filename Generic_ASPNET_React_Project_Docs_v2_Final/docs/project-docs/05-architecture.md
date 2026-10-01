# Technical Architecture

## Required technology baseline

### Backend

```text
ASP.NET Core
C#
EF Core
```

### Frontend

```text
React
TypeScript
Vite
```

### Database

```text
PostgreSQL
```

### Local infrastructure

```text
Docker Compose
PostgreSQL
Adminer
Seq
```

### Observability

```text
Serilog structured logging
OpenTelemetry where useful
```

These are standard project rules for this template. Change them only when the project explicitly approves a different architecture.

## Architecture style

Use a **Modular Monolith**.

Do not introduce microservices unless explicitly approved.

Keep:
- one deployable backend;
- coherent business modules;
- clear internal boundaries;
- simple infrastructure.

Avoid distributed-system patterns when an in-process solution is sufficient.

## Suggested repository structure

```text
/backend
  /src
    /Api
    /Application
    /Domain
    /Infrastructure
    /Modules
  /tests

/frontend
  /src
    /app
    /features
    /components
    /pages
    /layouts
    /api
    /i18n
    /theme
  /tests

/docs
  /project-docs
  /instructions-docs
  /working-docs
  /materials
  /credentials
```

## Vertical slices

Prefer feature-oriented implementation:

```text
Feature/
  Create/
  Get/
  Update/
  Delete/
```

Avoid giant generic service classes.

## Dependency direction

- business/domain logic must not depend on UI concerns;
- infrastructure concerns should not leak unnecessarily into business rules;
- external integrations should use focused abstractions when substitution/testing is useful;
- do not add interfaces for trivial classes without realistic alternative implementations.

## API

Use explicit request/response DTOs.

Do not expose EF entities directly as public contracts.

## Real-time progression

Use only as needed:

1. normal request/refresh;
2. lightweight polling;
3. SignalR if real-time materially improves UX.

## Background work

Do not add Hangfire/Quartz/etc. until durable jobs are actually required.

## Premature complexity to avoid

Without demonstrated need, do not introduce:
- Kubernetes;
- message broker;
- service mesh;
- Redis;
- Elasticsearch;
- multiple databases;
- event sourcing;
- blanket CQRS frameworks;
- microservices.
