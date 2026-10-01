# Taw — Screen Map and User Journeys

## Admin/owner screens

### Onboarding

- Create account.
- Water station information.
- Branding.
- Delivery settings.
- First product.
- Publish store.

### Main navigation

- Dashboard.
- Orders.
- Deliveries.
- Subscriptions.
- Customers.
- Products.
- Offers.
- Pages.
- Support.
- Drivers.
- Settings.

### Dashboard

Key summaries:

- Orders today.
- Waiting for assignment.
- Out for delivery.
- Upcoming subscriptions.

Then recent/today deliveries and useful operational attention items.

Avoid chart-heavy dashboard design.

### Orders list

- Search.
- Date/status/driver/area/source filters.
- Order number.
- Customer.
- Area.
- Driver.
- Status.

### Order details

- Customer information.
- Phone/WhatsApp.
- Delivery location/map.
- Requested date/time.
- Products.
- Bottle expectations/history when relevant.
- Status timeline.
- Driver assignment.
- Confirm/cancel actions.

### Manual order

```text
Enter/search phone
→ Existing customer
→ Address/previous order
→ Repeat or build new order
→ Delivery time
→ Save
```

### Customers

List with search by name/phone.

Customer details tabs:

- Overview.
- Orders.
- Subscriptions.
- Addresses.
- Bottles.

### Products

- List.
- Add/edit.
- Active/inactive.
- Price.
- Image.
- Size.
- Returnable bottle relation.

### Subscriptions

- Active/paused/due filters.
- Customer.
- Products/quantity.
- Frequency.
- Next delivery.
- Skip/pause/resume/change.

### Delivery Board

- Unassigned column/pool.
- Driver columns.
- Bulk assignment.
- Reassign/unassign.
- Optional drag/drop if implementation remains simple.

### Delivery map

Toggle between:

- List.
- Map.

Map can filter unassigned or by driver.

### Drivers

- Add/edit/disable.
- View assigned deliveries.
- Login/access management.

### Offers

- Offers list.
- Add/edit offer.
- Preview/store visibility.

### Pages

- Pages list.
- Add/edit page.
- Navigation order.
- System vs custom page distinction.

### Support

- Requests list.
- Details.
- Call/WhatsApp.
- Mark in progress/closed.

### Settings

Detailed in `09-settings-offers-pages.md`.

## Driver mobile/PWA screens

### Home/Today

- Today's delivery count.
- Completed.
- Remaining.
- Available deliveries when self-assignment enabled.

### Delivery list/card

- Customer.
- Phone.
- Area/address.
- Product summary.
- Status.
- Map.
- Call.
- WhatsApp.
- Start delivery.

### Available deliveries

- Area.
- Distance if available.
- Quantity.
- Take delivery.

### Delivery details

- Customer info.
- Address/location.
- Products.
- Full bottles delivered.
- Empty bottles returned.
- Payment indicator.
- Notes.
- Complete delivery.

## Customer storefront screens

### Home

- Distributor branding.
- Hero.
- Products.
- Offers.
- Order CTA.
- WhatsApp CTA.
- Footer/pages.

### Products

- Water product cards/list.
- Quantity.
- Add/order action.

### Guest order / checkout

Suggested simple stepper:

```text
1 Product
→ 2 Address
→ 3 Delivery time
→ 4 Confirm
```

No login gate.

### Confirmation

- Order number.
- Delivery date/time.
- Track order.
- WhatsApp support.

### Track order

Simple progress:

- Received/New.
- Confirmed.
- Assigned/Out for delivery.
- Delivered.

### Subscription

- Product(s).
- Quantity.
- Frequency.
- Day.
- Time.
- Confirm.

### Optional customer account

- My orders.
- My subscriptions.
- My addresses.
- Bottle balance.
- Reorder.

## Critical user journeys

### Journey A — New guest customer

```text
QR/link
→ Store
→ Product
→ Address/location
→ Delivery time
→ Order
→ Confirmation
```

### Journey B — Returning customer

```text
Store/account/verified identity
→ Previous order
→ Repeat
→ Adjust date/quantity/address
→ Confirm
```

### Journey C — Subscription

```text
Product
→ Subscribe
→ Frequency/day/time
→ Subscription active
→ Order generated
→ Driver delivery
→ Completed
```

### Journey D — Phone/WhatsApp order

```text
Customer contacts distributor
→ Employee searches phone
→ Finds customer
→ Repeat/create order
→ Assign driver
```

### Journey E — Driver

```text
Login
→ Today
→ Open delivery
→ Navigate
→ Deliver
→ Empty bottles
→ Complete
```

### Journey F — Owner/dispatcher

```text
Dashboard
→ Unassigned deliveries
→ Assign driver
→ Monitor status
→ Verify completion
```

## Acceptance priority

These journeys are more important than adding additional modules. If they are not excellent, the project should not expand horizontally.
