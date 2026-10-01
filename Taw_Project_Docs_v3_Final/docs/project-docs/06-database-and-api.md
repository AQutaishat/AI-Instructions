# Taw — Database Schema and API Contracts v1

This document defines the first practical database/API direction. Exact schema may evolve during implementation, but domain invariants should remain stable unless a deliberate decision changes them.

## Core tables for first beta

```text
Tenants
TenantBranding
TenantSettings
Users
UserTenantRoles
Customers
CustomerAddresses
Products
Orders
OrderItems
Drivers
Deliveries
DeliveryAssignments
ReturnableContainerTypes
ContainerTransactions
DeliveryZones
```

Add soon after the golden path:

```text
Subscriptions
SubscriptionItems
Offers
ContentPages
SupportRequests
Notifications
PushSubscriptions
AuditLogs
```

## Key indexes

At minimum consider:

```text
Customers (TenantId, Phone)
Orders (TenantId, Status)
Orders (TenantId, RequestedDeliveryDate)
Orders (TenantId, CustomerId)
Orders (TenantId, OrderNumber)
Deliveries (TenantId, DriverId, ScheduledDate)
Deliveries (TenantId, Status, ScheduledDate)
Subscriptions (TenantId, NextDeliveryDate, Status)
ContainerTransactions (TenantId, CustomerId, ContainerTypeId)
Products (TenantId, IsActive, SortOrder)
```

Do not create speculative indexes without workload evidence.

## Public store API

Tenant is resolved from host/subdomain, not supplied as trusted public ID.

### Products

```http
GET /api/store/products
```

### Offers

```http
GET /api/store/offers
```

### Content page

```http
GET /api/store/pages/{slug}
```

## Guest order creation

```http
POST /api/store/orders
```

Example request:

```json
{
  "customer": {
    "name": "أحمد محمد",
    "phone": "0791234567"
  },
  "items": [
    {
      "productId": "...",
      "quantity": 2
    }
  ],
  "delivery": {
    "date": "2026-09-25",
    "timeFrom": "16:00",
    "timeTo": "19:00",
    "addressText": "خلدا - شارع ...",
    "latitude": 31.987,
    "longitude": 35.852,
    "building": "12",
    "landmark": "بجانب المدرسة",
    "notes": "اتصل قبل الوصول"
  }
}
```

Example response:

```json
{
  "orderNumber": "W-10243",
  "status": "New",
  "total": 3.0,
  "trackingToken": "..."
}
```

## Track order without login

Prefer secure tracking token rather than exposing history from phone/order number alone.

```http
GET /api/store/orders/track/{trackingToken}
```

## Admin product API

```http
GET    /api/products
POST   /api/products
GET    /api/products/{id}
PUT    /api/products/{id}
DELETE /api/products/{id}
```

`DELETE` should normally become deactivate/soft-delete semantics when history exists.

## Admin orders

```http
GET  /api/orders
GET  /api/orders/{id}
POST /api/orders
POST /api/orders/{id}/confirm
POST /api/orders/{id}/cancel
GET  /api/orders/{id}/repeat-template
```

Example filters:

- status
- date
- driverId
- zoneId
- source
- search
- page/pageSize

## Customers

```http
GET  /api/customers
GET  /api/customers/{id}
POST /api/customers
PUT  /api/customers/{id}
GET  /api/customers/{id}/addresses
POST /api/customers/{id}/addresses
```

Customer search by phone is important for phone/WhatsApp manual orders.

## Delivery assignment

```http
POST /api/deliveries/{deliveryId}/assign
POST /api/deliveries/{deliveryId}/unassign
POST /api/deliveries/bulk-assign
```

## Driver endpoints

```http
GET  /api/driver/deliveries/today
GET  /api/driver/deliveries/available
POST /api/driver/deliveries/{id}/claim
POST /api/driver/deliveries/{id}/start
POST /api/driver/deliveries/{id}/complete
```

Claim conflicts return 409/already assigned.

## Complete delivery

Example:

```json
{
  "bottlesDelivered": [
    { "containerTypeId": "...", "quantity": 2 }
  ],
  "emptyBottlesReturned": [
    { "containerTypeId": "...", "quantity": 1 }
  ],
  "paymentReceived": true,
  "notes": "تم التسليم",
  "latitude": 31.987,
  "longitude": 35.852
}
```

The operation should be one logical/database transaction:

```text
Validate driver/status
→ Create bottle transaction
→ Delivery = Completed
→ Order = Delivered
→ Set timestamps
→ Audit log
→ Notification event/queue
→ Commit
```

## Bottle balance

```http
GET /api/customers/{customerId}/bottles
POST /api/customers/{customerId}/bottles/adjust
```

Manual adjustment requires reason and audit.

## Subscriptions

```http
GET  /api/subscriptions
POST /api/subscriptions
GET  /api/subscriptions/{id}
PUT  /api/subscriptions/{id}
POST /api/subscriptions/{id}/pause
POST /api/subscriptions/{id}/resume
POST /api/subscriptions/{id}/skip-next
```

## Offers

```http
GET    /api/offers
POST   /api/offers
PUT    /api/offers/{id}
DELETE /api/offers/{id}
```

## Pages

```http
GET  /api/pages
POST /api/pages
PUT  /api/pages/{id}
```

## Support

```http
POST /api/store/support
GET  /api/support
GET  /api/support/{id}
POST /api/support/{id}/close
```

## Authentication

Operational users:

```http
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/refresh
```

Customer account later:

```http
POST /api/customer-auth/request-otp
POST /api/customer-auth/verify-otp
```

## API error contract

Use stable machine-readable codes plus localized human message and trace ID.

Validation example:

```json
{
  "code": "VALIDATION_ERROR",
  "message": "تحقق من البيانات المدخلة.",
  "fieldErrors": {
    "phone": "رقم الهاتف غير صالح."
  },
  "traceId": "..."
}
```

## Pagination

Admin lists should use standard pagination such as:

```text
page
pageSize
sort
```

## Idempotency

Design should allow `Idempotency-Key` especially for:

- Guest order creation.
- Subscription-generated orders.
- MCP-created orders.
- Payments later.

## Golden-path integration test

```text
Create tenant
→ Create product
→ Guest creates order
→ Confirm order
→ Delivery created
→ Assign driver
→ Driver fetches today's deliveries
→ Start
→ Complete
→ Bottle transaction created
→ Order delivered
→ Bottle balance correct
```
