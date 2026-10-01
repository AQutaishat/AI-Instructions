# Taw — Product Vision and Settled Decisions

## Product vision

Taw is a **free, multi-tenant, white-label-style SaaS platform for water stations/distributors**.

Each distributor receives:

- A branded public water store.
- A private admin/dispatcher dashboard.
- Customer management.
- Water products.
- One-time water orders.
- Recurring water subscriptions.
- Delivery scheduling.
- Driver assignment and driver self-claim when allowed.
- Driver mobile/PWA workflow with customer locations.
- Reusable water-bottle balance tracking.
- Offers.
- Static/custom content pages.
- Support/contact options.
- WhatsApp-friendly communication.
- Push notifications.

## Product positioning

Taw is not a central marketplace initially.

Customers interact with the distributor's branded store and should not feel that they are inside a directory containing many competing distributors.

Example:

```text
alnada.taw.delivery
```

or later a custom domain owned by the distributor.

## Current product is water-only

This decision is strict.

Current UI, onboarding, terminology and workflows are explicitly about water:

- محطة المياه
- منتجات المياه
- قوارير المياه
- القوارير الفارغة
- رصيد القوارير
- اشتراك المياه
- توصيل المياه

The user should not see a selector for another vertical.

Internal code/database design should simply avoid unnecessary coupling so expansion is technically possible later.

## Guest-first ordering

Mandatory registration was rejected.

A customer should be able to order with:

- Name.
- Phone.
- Address/location.
- Delivery date/time.
- Notes when needed.

Customer accounts are optional and introduced only for protected functionality such as full order history, subscription management, saved addresses or bottle balance.

Preferred customer account login later:

```text
Phone → OTP
```

No consumer password should be required unless implementation proves it necessary.

## Multichannel order model

All order sources should converge on one order application flow.

Potential order sources:

- Web storefront.
- Admin/employee entry.
- Phone.
- WhatsApp.
- MCP/AI client.
- Future mobile app.

The system stores the order source but does not duplicate business logic by channel.

## Driver operations are core

Driver schedule/assignment is part of the core product, not future work.

Two assignment modes:

1. Owner/dispatcher assigns an order to a driver.
2. Driver claims an available order when the tenant setting allows self-assignment.

Hybrid usage is allowed.

The driver experience must work as mobile-first Web/PWA and may later be wrapped or replaced by a native app only if justified.

## Map/location decision

Customers can provide/use current location and a delivery address.

Drivers can:

- View customer location.
- Open navigation/maps.
- See list and map views where useful.

Automatic route optimization is future work.

## Subscription decision

Subscriptions are core.

Customers can have recurring water deliveries such as weekly or every two weeks.

Important domain rule:

```text
Subscription != Delivery
Subscription generates Orders
Each Order has its own Delivery lifecycle
```

Customers should be able to:

- Skip next delivery.
- Pause.
- Resume.
- Change quantity.
- Change day/time when allowed.

## Bottle tracking decision

Bottle tracking is core.

At completion, the driver records:

- Full bottles delivered.
- Empty bottles returned.

Bottle balance must come from transactions/ledger records rather than simply overwriting one mutable balance number.

## Store/content decision

Every distributor has a real branded storefront, not only an order form.

Core public content can include:

- Home.
- Products.
- Offers.
- About.
- Contact.
- Support.
- FAQ.
- Custom content pages.
- Order tracking.

Custom pages in V1 are content pages, not arbitrary low-code functional screens.

## Offers decision

Offers are core marketing content in the MVP.

An offer can contain:

- Title.
- Image.
- Description.
- Start/end dates.
- CTA text/link.
- Visibility location.
- Active/draft state.

The first version does **not** automatically calculate discounts. Discount rules belong in future work.

## WhatsApp decision

WhatsApp is an important channel.

V1:

- `wa.me` links.
- Prefilled messages.
- Customer support/contact.
- Admin-to-customer message templates that the human sends.

Later:

- WhatsApp Business API.
- Automated status messages.
- Conversational ordering.

## Push notifications

Push is an early product capability, especially for a PWA.

Useful transactional notifications:

- Order confirmed.
- Driver assigned.
- Out for delivery.
- Delivered.
- Subscription reminder.

Marketing notifications such as offers must be independently controllable.

## MCP decision

MCP is strategically important but must not delay the first beta.

MCP uses the same application services as web/admin channels.

Correct architecture:

```text
AI Client
→ MCP Server
→ Application Services
→ Domain
```

Never:

```text
MCP → Database directly
```

## Free product

Taw should be free for a long initial period.

Do not introduce artificial customer/order limits solely for monetization in the first product.

## Product simplicity rule

When deciding whether to include a feature now, ask:

> Does this clearly make ordering water, delivering water, managing subscriptions, communicating with customers, or managing bottle returns easier?

If not, it usually belongs in future work.
