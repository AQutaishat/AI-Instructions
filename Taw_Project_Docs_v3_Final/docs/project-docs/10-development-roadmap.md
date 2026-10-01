# Taw — Development Roadmap

The roadmap is execution guidance, not a requirement to finish every listed release before testing with a real distributor.

## R1 — Foundation

- Repository/bootstrap.
- Docker development environment.
- PostgreSQL.
- ASP.NET Core API.
- React/MUI frontend.
- Authentication for operational users.
- Tenant creation.
- Tenant isolation.
- Branding basics.

## R2 — Water products and public store

- Water product CRUD.
- Public tenant resolution by subdomain/host.
- Store homepage.
- Product listing.
- Branding application.

## R3 — Guest ordering

- Cart/quantity.
- Guest checkout.
- Address/location.
- Delivery date/time.
- Order confirmation.
- Secure tracking token.

## R4 — Order operations and customers

- Orders list/details.
- Confirm/cancel.
- Manual phone/WhatsApp order.
- Customer records.
- Customer search by phone.
- Repeat-order template.

## R5 — Delivery and driver

- Driver CRUD/login.
- Delivery entity creation.
- Delivery Board.
- Assignment/unassignment.
- Bulk assign.
- Driver Today screen.
- Available-delivery pool.
- Atomic claim.
- Map/navigation links.
- Start delivery.

## R6 — Bottle tracking and delivery completion

- Returnable bottle types.
- Delivered/returned quantities.
- Container transaction ledger.
- Bottle balance.
- Manual adjustment with audit.
- Complete delivery transaction.

### First public beta checkpoint

At the end of R6, give the product to a real water distributor if the golden path is stable.

## R7 — Subscriptions

- Create subscription.
- Subscription items.
- Scheduled/background order generation.
- Idempotency.
- Skip/pause/resume/change quantity.
- Reminder preparation.

## R8 — Communication and tracking

- Customer order tracking page.
- WhatsApp deep links/templates.
- Web Push.
- Notification preferences.
- QR/store sharing.

## R9 — Content experience

- Offers list/create/edit.
- Content pages.
- Page navigation ordering.
- Support requests.

## R10 — Optional customer account

- Phone OTP.
- My Orders.
- My Subscriptions.
- My Addresses.
- Bottle balance.
- Reorder.

## R11 — MCP foundation/implementation

Do not implement until the underlying application operations are stable.

- OAuth/authorization approach.
- Scopes.
- Products read.
- Offers read.
- Order create/read.
- Repeat order.
- Subscription read/manage.

## Priority summary

### P0

- Multi-tenancy.
- Operational auth.
- Products.
- Public store.
- Guest order.
- Orders.
- Customers.
- Driver.
- Delivery.
- Bottle ledger.

### P1

- Subscriptions.
- Tracking.
- WhatsApp V1.
- Push.
- Zones.
- QR.

### P2

- Offers.
- Pages.
- Support.
- Customer account.

### P3

- MCP.
- Advanced integrations.

## Definition of done for a feature

A production-facing feature should normally be:

- Tenant-safe.
- Authorized correctly.
- Mobile responsive where applicable.
- Arabic RTL correct.
- English-compatible if localized.
- Validated.
- Error messages contextual.
- Audited where business-sensitive.
- Tested for critical business rules.
- Tested in real browser flow when user-facing.
- Not dependent on users having technical knowledge.
