# Taw — Domain Model v1

## Core principles

- Multi-tenant SaaS.
- Water-specific UI.
- Internally extensible without exposing generic wording to users.
- Guest customer is a first-class flow.
- Subscription generates orders.
- Order and Delivery are separate concepts.
- Bottle balance derives from transactions.
- All channels reuse the same application operations.

## Main modules

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

## Tenant

Represents a water station/distributor.

Typical fields:

- Id
- Name
- Slug
- Status
- DefaultLanguage
- DefaultCurrency
- TimeZone
- Phone
- WhatsAppNumber
- Email
- CreatedAt
- UpdatedAt

## TenantBranding

- TenantId
- StoreDisplayName
- Tagline
- LogoUrl
- FaviconUrl
- HeroImageUrl
- PrimaryColor
- SecondaryColor
- FooterText

## TenantSettings

Examples:

- GuestOrderingEnabled
- SubscriptionsEnabled
- DriverSelfAssignmentEnabled
- PushNotificationsEnabled
- DefaultDeliveryFee
- MinimumOrderAmount
- DefaultDeliveryStartTime
- DefaultDeliveryEndTime
- AllowSameDayDelivery
- AllowCustomerBottleBalance

## Users and roles

Operational roles:

- TenantOwner
- TenantEmployee
- Driver

Platform admin remains system-level.

A user may belong to a tenant through a role membership structure.

## Customer

Important rule:

```text
Customer != User account
```

Customer can exist because of:

- Guest order.
- Phone order.
- WhatsApp order.
- Employee entry.
- Registration.

Possible fields:

- Id
- TenantId
- UserId nullable
- Name
- Phone
- Email nullable
- IsPhoneVerified
- Notes
- IsActive

## CustomerAddress

- Id
- TenantId
- CustomerId
- Label
- AddressText
- Latitude
- Longitude
- Building
- Floor
- Apartment
- Landmark
- DeliveryNotes
- DeliveryZoneId nullable
- IsDefault

## Product

UI label: water product.

Internal entity can remain `Product`.

- Id
- TenantId
- Name
- Description
- ImageUrl
- SizeValue
- SizeUnit
- Price
- IsReturnable
- ReturnableTypeId nullable
- DepositAmount nullable
- IsActive
- SortOrder

## ReturnableContainerType

UI label should say bottle type / water bottle.

- Id
- TenantId
- Name
- DepositAmount nullable
- IsActive

## Order

- Id
- TenantId
- OrderNumber
- CustomerId nullable
- GuestName nullable
- GuestPhone nullable
- Status
- Source
- RequestedDeliveryDate
- RequestedTimeFrom/To
- DeliveryZoneId nullable
- Delivery address snapshot
- Latitude/Longitude
- CustomerNotes
- InternalNotes
- Subtotal
- DeliveryFee
- Discount
- Total
- CreatedAt
- ConfirmedAt
- DeliveredAt
- CancelledAt

Address and pricing snapshots are important because master data can change later.

## OrderItem

- Id
- OrderId
- ProductId
- ProductNameSnapshot
- UnitPrice
- Quantity
- LineTotal

## Order statuses

- New
- Confirmed
- Assigned
- OutForDelivery
- Delivered
- Cancelled

## Order sources

- Web
- Admin
- Phone
- WhatsApp
- Mcp

## Subscription

- Id
- TenantId
- CustomerId
- AddressId
- Status
- FrequencyType
- IntervalValue
- PreferredDayOfWeek nullable
- PreferredTimeFrom/To
- StartDate
- EndDate nullable
- NextDeliveryDate

## SubscriptionItem

- SubscriptionId
- ProductId
- Quantity

## Delivery

Separating Delivery from Order supports assignment, retries/history and driver operations.

- Id
- TenantId
- OrderId
- DriverId nullable
- Status
- ScheduledDate
- StartedAt nullable
- CompletedAt nullable
- CompletionLatitude/Longitude nullable
- DriverNotes
- concurrency token/version

## DeliveryAssignment

Keeps assignment history.

- Id
- TenantId
- DeliveryId
- DriverId
- AssignmentType
- AssignedByUserId nullable
- AssignedAt
- AcceptedAt nullable
- EndedAt nullable

Assignment types:

- Manual
- SelfAssigned
- Automatic (future)

## Driver

- Id
- TenantId
- UserId
- Name
- Phone
- IsActive

## ContainerTransaction

Source of truth for bottle balance.

- Id
- TenantId
- CustomerId
- ContainerTypeId
- OrderId nullable
- DeliveryId nullable
- QuantityOut
- QuantityReturned
- AdjustmentQuantity
- TransactionType
- CreatedByUserId nullable
- Notes
- CreatedAt

Bottle balance is derived from transactions.

## DeliveryZone

- Id
- TenantId
- Name
- DeliveryFee
- MinimumOrder
- IsActive

## Offer

- Id
- TenantId
- Title
- Description
- ImageUrl
- StartDate nullable
- EndDate nullable
- CtaText nullable
- CtaUrl nullable
- IsActive

## ContentPage

- Id
- TenantId
- Title
- Slug
- Content
- SeoTitle
- SeoDescription
- IsPublished
- ShowInMainNav
- ShowInFooter
- SortOrder

## SupportRequest

- Id
- TenantId
- CustomerId nullable
- OrderId nullable
- Name
- Phone
- Category
- Message
- Status
- CreatedAt
- ClosedAt nullable

## Notification

- Id
- TenantId
- CustomerId nullable
- OrderId nullable
- Type
- Channel
- Title
- Body
- Status
- ScheduledAt nullable
- SentAt nullable
- CreatedAt

## AuditLog

- Id
- TenantId nullable
- UserId nullable
- Action
- EntityType
- EntityId nullable
- RequestId
- TraceId
- MetadataJson nullable
- CreatedAt

## Relationship summary

```text
Tenant
├── Users/Roles
├── Customers
│   ├── Addresses
│   ├── Orders
│   ├── Subscriptions
│   └── ContainerTransactions
├── Products
├── Orders
│   ├── OrderItems
│   └── Delivery
│       └── DeliveryAssignments
├── Drivers
├── Offers
├── ContentPages
├── SupportRequests
└── Notifications
```
