# Taw — Settings, Offers and Pages Specification

## Settings structure

The current settings area should use clear tabs/sections rather than one huge form.

### 1. Store information

- Store name.
- Display name.
- Phone.
- WhatsApp.
- Email.
- City.
- Address.
- Working days.
- Working hours.
- Social links.
- Currency.
- Default language.

### 2. Identity and appearance

- Logo.
- Favicon.
- Primary color.
- Secondary color.
- Hero image.
- Tagline.
- Footer text.
- Theme selection from limited supported themes.
- Store preview.

### 3. Order settings

Wireframe/settings items discussed:

- Allow guest order.
- Require/allow location.
- Show order notes.
- Minimum order amount.
- Allow same-day order.
- Auto-confirm order.
- Advance booking lead time.
- Available payment methods where relevant.

### 4. Delivery

- Default delivery fee.
- Delivery zones.
- Per-zone fee/minimum order.
- Delivery hours/time windows.
- Allow driver self-assignment.
- Allow reassignment when policy permits.
- Auto-create delivery when order confirmed.

### 5. Subscriptions

- Enable subscriptions.
- Allowed frequency types.
- Allow skip.
- Allow pause.
- Allow quantity changes.
- Number of days before generating next order.
- Reminder lead time.
- Auto-renew behavior if a period-based model is later used.

### 6. Bottles

- Enable bottle tracking.
- Bottle types.
- Deposit value.
- Allow manual adjustment.
- Show bottle balance to customer.
- Require driver to enter empty returns at completion.

### 7. WhatsApp

V1:

- Support WhatsApp number.
- Show WhatsApp CTA in store.
- Default support message.
- Store sharing message.
- Order support/follow-up message.
- Confirmation template used in human-assisted flow.

Full API automation belongs in future work.

### 8. Notifications

Separate operational and marketing notifications.

Operational examples:

- Order confirmed.
- Driver assigned.
- Delivery started.
- Delivered.
- Subscription reminder.

Marketing examples:

- New offers.
- Promotional subscription messages.

Channel matrix can include:

- Push.
- WhatsApp when automation exists.
- Email when used.
- SMS later.

### 9. Customers and account

- Registration optional/required setting; default strategy is optional.
- OTP login enabled.
- Multiple addresses.
- Show order history.
- Show bottle balance.
- Allow reorder.
- Allow customer subscription management.
- Optional create-account-after-order invitation/behavior.

### 10. Store and content

- Show products.
- Show offers.
- Show About.
- Show FAQ.
- Show Contact.
- Show Support.
- Navigation ordering.
- Default SEO title.
- Default SEO description.
- Footer text.
- Shortcuts to separate Pages and Offers modules.

## Offers module

Offers should remain a standalone sidebar module, not buried inside Settings.

### Offers list

Columns/summary:

- Offer.
- Status.
- Start.
- End.
- Visibility.
- Actions.

Primary action:

> + Add Offer

### Add/Edit Offer

Fields:

- Title.
- Description.
- Image.
- Start date.
- End date.
- CTA text.
- CTA URL/target.
- Show on homepage.
- Show on offers page.
- Active/Draft.

### MVP semantics

An offer is marketing content.

It does **not** automatically change product pricing in V1.

## Pages module

Pages should also remain a standalone sidebar module.

### Pages list

Examples:

- About Us.
- Delivery Areas.
- FAQ.
- Privacy Policy.
- Corporate Orders.

### Add/Edit page

- Title.
- Slug.
- Rich text content.
- SEO Title.
- SEO Description.
- Show in main navigation.
- Show in footer.
- Published.

### Navigation ordering

A simple sortable/draggable list can control menu order:

```text
Home
Products
Offers
About Us
Delivery Areas
Contact
```

### System pages vs custom pages

System pages are functional built-ins such as:

- Home.
- Products.
- Offers.
- Order tracking.
- Support.

Custom pages are content pages such as:

- About.
- Corporate Orders.
- Delivery Areas.
- FAQ.
- Privacy.

V1 custom page creation does not allow tenants to build arbitrary functional forms/screens.

## Settings UX rule

Settings should be clear and grouped, but independent operational modules such as Products, Offers, Pages, Support and Drivers should remain in the main navigation instead of being hidden inside Settings.
