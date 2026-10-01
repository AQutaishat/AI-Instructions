# Taw — Technical Architecture v1

## Architecture choice

Use a **Modular Monolith**.

Do not start with microservices, Kubernetes or an external event bus.

Reasoning:

- Small team/individual development.
- Need fast iteration.
- Domain boundaries can still be explicit.
- Operational cost stays low.
- Services can be extracted later only if scale justifies it.

## Stack

### Backend

- ASP.NET Core
- EF Core
- PostgreSQL

### Frontend

- React
- TypeScript
- Vite
- MUI
- React Router
- React Query
- i18next

### Driver

- Same web platform / PWA, mobile-first.

### Infrastructure

- Docker Compose
- PostgreSQL
- Seq
- Adminer or similar DB inspection tool in development

### Observability

- Structured logging to Seq.
- OpenTelemetry.
- Production export such as Application Insights.

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
/mcp                 # added when MCP implementation begins
/docs
  /project-docs
  /instructions-docs
  /working-docs
  /materials
  /credentials
/docker-compose.yml
```

## Module boundaries

```text
Tenancy
Identity
Catalog
Customers
Orders
Subscriptions
Delivery
Containers
Content
Offers
Support
Notifications
Integrations
```

Integrations may later include:

- WhatsApp
- Push
- MCP
- Maps
- Payments
- SMS

## Vertical-slice application organization

Prefer feature folders such as:

```text
Orders/
  CreateOrder/
  GetOrder/
  SearchOrders/
  ConfirmOrder/
  CancelOrder/
  RepeatOrder/
```

rather than building a large architecture around generic `Controller → Service → Repository → Helper` layers.

A feature may contain:

- Request/Command/Query
- Validator
- Handler
- Endpoint
- Response/DTO

## Multi-tenancy

Initial strategy:

```text
Shared PostgreSQL database
+ Shared schema
+ TenantId on business entities
```

Do not use one database per tenant initially.

## Tenant resolution

### Storefront

Resolve tenant from host/subdomain.

```text
alnada.taw.delivery
→ slug = alnada
→ CurrentTenant
```

### Admin/Driver

Resolve from authenticated user membership.

### MCP later

Resolve from authorized MCP/customer connection context.

Never trust an arbitrary public `tenantId` query parameter as the security boundary.

## Tenant isolation

Use centralized tenant filtering where practical, such as EF Core global query filters, plus authorization tests.

Do not depend on every developer remembering to append `WHERE TenantId = ...` manually.

Tenant isolation must be covered by integration tests.

## Authentication

### Owner/Employee/Driver

Standard authenticated operational accounts.

### Customer

Guest-first.

Optional protected customer account later:

```text
Phone → OTP
```

Guest creation of an order does not grant access to protected history.

## Order architecture

All channels reuse one application operation, conceptually:

```text
CreateOrderCommand
```

Callers can be:

- Public web store.
- Admin manual order.
- WhatsApp adapter later.
- MCP adapter later.

No business logic should be implemented uniquely in the React frontend or MCP server.

## Subscription processing

Use an internal background worker initially.

Responsibilities:

- Find subscriptions whose next order must be created.
- Create order idempotently.
- Advance next-delivery date.

Hangfire/Quartz can be introduced later if operational needs justify it.

## Delivery claim concurrency

Driver self-claim must be atomic.

If two drivers attempt to claim one delivery:

- First succeeds.
- Second receives conflict/already-assigned result.

Use database concurrency constraints/versioning/update conditions.

## Map architecture

Persist customer/delivery latitude/longitude when available.

V1:

- Display pins/list.
- Open external navigation.

Do not create route/route-stop domain entities until route optimization becomes an actual feature.

## Bottle ledger

Container transactions are the source of truth.

A cached balance may be added later only as an optimization; it must not replace the transaction history.

## Notifications

Define an abstraction such as:

```text
INotificationSender
```

Potential implementations:

- Push
- WhatsApp Business later
- SMS later
- Email later

Simple WhatsApp V1 deep links do not require a full notification provider integration.

## MCP architecture

When implemented:

```text
AI Client
→ MCP Server
→ Taw API/Application Services
→ Domain
```

MCP should have scoped authorization such as:

- products.read
- orders.read
- orders.create
- subscriptions.read
- subscriptions.manage

Do not use a phone number alone as MCP identity proof.

## Error handling

Use a consistent API error contract, for example:

```json
{
  "code": "DELIVERY_ALREADY_ASSIGNED",
  "message": "تم تعيين هذا الطلب لسائق آخر.",
  "fieldErrors": null,
  "traceId": "..."
}
```

Do not expose raw exceptions to customers.

## Time

Store timestamps in UTC.

Render business/customer times in tenant time zone.

## Soft deletion / lifecycle

Prefer deactivate/archive for products, drivers and customers when history references them.

Orders should not be physically deleted.

## Deployment safety

Production schema changes must use migrations and follow backup/verification practices in the working-docs backup document.


## Logging correlation requirements

Structured logging must consistently enrich events with context where available:

- `Environment`.
- `SourceApp` such as `web`, `admin`, `mobile`, `mcp`, `worker`.
- `RequestId`/correlation ID, propagated across downstream HTTP requests.
- `TraceId` from OpenTelemetry when available.
- `TenantId` after resolution.
- `UserId` after authentication.
- `CustomerId` when useful.
- Endpoint/operation.

The same request/correlation ID should follow related HTTP calls so Seq can be used to reconstruct a logical request path. Never log passwords, OTPs, tokens, private keys or client secrets.
