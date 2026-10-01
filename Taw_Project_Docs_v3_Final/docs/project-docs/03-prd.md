# Taw — Product Requirements Document (PRD v1)

## 1. Summary

Taw is a free multi-tenant SaaS platform for water distributors/stations. Each tenant receives a branded customer storefront and an operational dashboard for products, customers, one-time orders, subscriptions, drivers, delivery scheduling, reusable-bottle tracking, offers, content and support.

## 2. Primary goals

1. Let a water distributor publish a digital ordering channel in minutes.
2. Let customers order without mandatory account creation.
3. Organize delivery work and driver assignment.
4. Support recurring water delivery subscriptions.
5. Track full bottles delivered and empty bottles returned.
6. Give each distributor a customizable public presence.
7. Make WhatsApp and push communication easy.
8. Stay simple enough for small distributors.
9. Keep architecture ready for MCP/AI channels.

## 3. Primary users

### Platform Admin

Operates Taw itself.

### Tenant Owner

Owns/manages one water distributor/station account.

### Tenant Employee / Dispatcher

Manages orders, customers and delivery assignment.

### Driver

Receives/claims assigned deliveries, opens location/navigation and completes delivery.

### Customer

Can order as guest, phone-verified customer or registered customer.

## 4. Tenant onboarding

Flow:

```text
Create account
→ Business information
→ Branding
→ Delivery settings
→ Add first water product
→ Publish store
```

Required initial capabilities:

- Tenant/station creation.
- Unique slug/subdomain.
- Owner account.
- Store display name.
- Logo.
- Primary/secondary color.
- Phone/WhatsApp.
- City.
- Working hours.
- First product.

## 5. Storefront

Public storefront can show:

- Hero section.
- Water products.
- Offers.
- About/custom pages.
- Contact.
- Support.
- FAQ.
- Order CTA.
- WhatsApp CTA.

Tenant controls branding/content without a complex page builder.

## 6. Water products

Product fields:

- Name.
- Description.
- Image.
- Size value/unit.
- Price.
- Active state.
- Sort order.
- Whether product uses a returnable bottle.
- Returnable bottle type/deposit if relevant.

Examples:

- 18.9 L returnable water bottle.
- 5 L water bottle.
- 500 ml carton.
- 330 ml carton.
- Cups.
- Water-related accessories if the distributor sells them.

## 7. Guest ordering

The customer can place an order without logging in.

Basic flow:

```text
Product
→ Quantity
→ Name + Phone
→ Address/Location
→ Delivery Date/Time
→ Confirm
```

Order data can include:

- Customer name.
- Phone.
- Address text.
- Current map location.
- Building/floor/apartment.
- Landmark.
- Delivery notes.
- Requested date.
- Requested time window.

After submission:

- Generate order number.
- Generate safe tracking token/link.
- Show confirmation page.
- Allow WhatsApp contact.

## 8. Returning/repeat ordering

When identity is safely known/verified, Taw can show previous orders and support "Order again".

Do not expose private history based only on entering a phone number.

## 9. Order lifecycle

Core statuses:

- New.
- Confirmed.
- Assigned.
- OutForDelivery.
- Delivered.
- Cancelled.

Order source values initially include:

- Web.
- Admin.
- Phone.
- WhatsApp.
- Mcp.

## 10. Manual orders

Admin/employee can create an order for a customer who ordered via phone/WhatsApp/in person.

Useful flow:

```text
Phone search
→ Existing customer found
→ Address + previous order available
→ Repeat or create new order
```

## 11. Customers

Customer profile includes:

- Name.
- Phone.
- Email optional.
- Addresses.
- Order history.
- Active subscriptions.
- Bottle balance.
- Notes.

A customer record can exist without a user login account.

## 12. Subscriptions

Subscription contains:

- Customer.
- Address.
- Product items.
- Quantity.
- Frequency.
- Delivery day.
- Preferred time.
- Start/end where relevant.
- Next delivery date.
- Status.

Customer/admin actions:

- Skip next.
- Pause.
- Resume.
- Change quantity.
- Change permitted delivery timing.

Background processing generates future order instances idempotently.

## 13. Delivery operations

### Delivery Board

Admin/dispatcher sees:

- Unassigned deliveries.
- Driver columns/assignments.
- Date.
- Area.
- Customer.
- Quantity summary.
- Status.

Actions:

- Assign.
- Bulk assign.
- Reassign.
- Unassign.

### Driver self-assignment

Tenant can enable an open delivery pool.

Driver can press "Take Delivery".

Claiming must be atomic so two drivers cannot claim the same delivery.

## 14. Driver Web/PWA

Driver navigation should remain minimal:

- Today.
- Available.
- Completed.
- Profile.

Delivery card shows:

- Customer.
- Phone.
- Address/area.
- Products/quantity.
- Map/navigation.
- Call.
- WhatsApp.
- Start delivery.

## 15. Complete delivery

Driver records:

- Bottles/products delivered.
- Empty bottles returned.
- Payment received indicator if used.
- Notes.
- Optional completion location.

Completion should atomically:

- Complete delivery.
- Mark order delivered.
- Set timestamps.
- Record bottle transaction.
- Write audit record.
- Queue/send appropriate notification.

## 16. Bottle tracking

UI terminology must be water-specific:

- القوارير
- القوارير الفارغة
- رصيد القوارير

Ledger operations can include:

- Delivery transaction.
- Return transaction.
- Manual adjustment with reason/audit.

## 17. Delivery zones

Tenant can define zones/areas with:

- Name.
- Enabled state.
- Delivery fee.
- Minimum order.

V1 can use named areas instead of geographic polygons.

## 18. Offers

Admin module:

- Offers list.
- Create/edit offer.
- Active/draft state.
- Start/end dates.
- Image.
- CTA text/link.
- Show on home/offers page.

MVP offer is marketing content, not automatic pricing logic.

## 19. Pages

Admin module includes:

- Pages list.
- Add/edit custom page.
- Title.
- Slug.
- Rich content.
- SEO title/description.
- Show in main navigation.
- Show in footer.
- Published state.
- Navigation ordering.

System pages remain separate from custom content pages.

## 20. Support

Customer support page can expose:

- WhatsApp.
- Phone.
- FAQ.
- Submit support request.

Simple request fields:

- Name.
- Phone.
- Order number optional.
- Category.
- Message.

Statuses:

- New.
- InProgress.
- Closed.

## 21. Notifications

Channels conceptually include:

- Push.
- WhatsApp.
- Email.
- SMS later.
- In-app later.

Settings distinguish operational vs marketing notifications.

## 22. Optional customer account

Preferred login:

```text
Phone → OTP
```

Account can expose:

- My orders.
- My subscriptions.
- My addresses.
- Bottle balance.
- Reorder.

## 23. QR/share

Tenant dashboard can provide:

- Store URL.
- Copy link.
- Share via WhatsApp.
- Download/print QR.

QR can be placed on store, invoices, delivery vehicles or bottles.

## 24. Platform admin

Minimal super-admin capabilities:

- Tenants.
- Users.
- Tenant status.
- Usage/order volume.
- Error monitoring.
- Feature flags.
- Platform support.
- Integration status.

Billing is not required initially.

## 25. Public beta definition

Beta is successful when a real distributor can:

```text
Register water station
→ Add branding/product
→ Publish store
→ Guest orders
→ Admin receives order
→ Driver assigned
→ Driver navigates to customer
→ Driver completes delivery
→ Empty bottles recorded
→ Bottle balance correct
```

Anything not required for this experience should not block beta.
