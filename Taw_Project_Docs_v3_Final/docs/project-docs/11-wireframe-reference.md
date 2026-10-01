# Taw — Wireframe Reference Summary

This document records the wireframe decisions created during product design. It is a textual reference; generated PNG boards can be recreated/refined later from these screen definitions.

## Customer mobile/store wireframes

### 1. Store home

- Taw/distributor brand area.
- Hero text/image.
- `Order now` CTA.
- Water products.
- Offers.
- WhatsApp contact shortcut.

### 2. Products

- Water-product list/cards.
- 18.9 L bottle and other water products.
- Quantity stepper.
- Price.
- Add/order action.

### 3. Guest order

- Name.
- Phone.
- Address.
- Map/current location.
- Delivery date.
- Delivery time.
- Optional notes.
- Confirm.

Later revised into a simple four-step flow:

```text
Product → Address → Appointment → Confirmation
```

### 4. Order tracking

Progress:

```text
New → Confirmed → Out for Delivery → Delivered
```

### 5. Subscription

- Product.
- Quantity.
- Weekly/frequency setting.
- Delivery day.
- Time.
- Confirm.

### 6. My account / orders

- Previous orders.
- Reorder.
- Addresses.
- Bottle balance.
- Subscriptions.

## Admin wireframes

### Dashboard

Updated sidebar includes:

```text
Dashboard
Orders
Deliveries
Subscriptions
Customers
Products
Offers
Pages
Support
Drivers
Settings
```

Dashboard summaries emphasize:

- Today's orders.
- Waiting assignment.
- Out for delivery.
- Upcoming subscriptions.

### Orders

- Search.
- Filters.
- Order table.
- Customer/area/driver/status.

### Order detail

- Customer info.
- Address/map.
- Products.
- Timeline/status.
- Driver assignment.

### Delivery Board

- Unassigned orders.
- Driver columns.
- Assignment/reassignment.

## Driver wireframes

### Driver home/today

- Today's delivery count.
- Waiting to start.
- In delivery.
- Completed.
- Cards with location/call/WhatsApp/start.

### Delivery detail

- Customer.
- Phone.
- Address.
- Map.
- Call.
- WhatsApp.
- Products.
- Full bottles delivered.
- Empty bottles returned.
- Notes.
- Complete delivery.

## Settings wireframes

### Store information

- Store name.
- Phone.
- WhatsApp.
- Email.
- City.
- Working hours.

### Identity and appearance

- Logo upload.
- Primary/secondary colors.
- Hero/banner image.
- Tagline.
- Theme/style selection.

### Order settings

- Guest order.
- Location requirement.
- Order notes.
- Minimum order.
- Same-day ordering.
- Auto confirm.
- Booking lead time.
- Payment-method options.

### Subscription settings

- Enable subscriptions.
- Weekly/every-two-weeks/custom.
- Skip.
- Pause.
- Quantity changes.
- Generate-order lead time.
- Reminder timing.

### Notification settings

Operational and marketing notification matrix with channel columns such as Push, WhatsApp, Email.

### Customers/account settings

- Optional vs required registration.
- OTP.
- Multiple addresses.
- Order history.
- Bottle balance.
- Reorder.
- Customer subscription management.

### Store/content settings

- Show/hide supported public sections.
- Navigation ordering.
- SEO defaults.
- Footer text.
- Shortcuts to Offers and Pages modules.

## Offers wireframes

### Offers list

- Offer name.
- State.
- Start/end.
- Visibility.
- Add Offer.

### Add offer

- Title.
- Description.
- Image.
- Dates.
- CTA text/link.
- Show on Home / Offers page.
- Active/Draft.

### Store preview

Shows offers as a storefront section, not as automatic discount logic.

## Pages wireframes

### Pages list

Examples:

- About Us.
- Delivery Areas.
- FAQ.
- Privacy Policy.
- Corporate Orders.

### Add page

- Title.
- Slug.
- Rich editor.
- SEO.
- Show in main nav/footer.
- Published.

### Navigation order

Simple sortable list.

### Page types

- System pages.
- Custom content pages.

Custom content pages are not arbitrary functional screens in V1.


## Packaged visual materials

Current generated wireframe/icon assets are stored under `docs/materials/` and are reference materials, not normative UI specifications. The Markdown UX/design documents remain the implementation source of truth.
