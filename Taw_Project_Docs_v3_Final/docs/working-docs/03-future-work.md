# Taw — Future Work Backlog

This document collects useful ideas that are intentionally outside the first working product. An item appearing here does **not** mean it should be built now.

## Guiding rule

If a feature does not directly make water ordering, delivery, subscriptions, customer communication, or distributor operations materially easier in the current product, keep it here until real usage proves the need.

## WaterCopon parity / competitor-derived future ideas

The following are valuable capabilities observed in WaterCopon or discussed during research, but are not required in Taw's first beta unless separately promoted into active scope:

- Digital coupon books / prepaid bottle packages.
- POS / in-store sales.
- Selling by liter for customer-owned containers.
- Advanced inventory tracking.
- Excel import/export.
- Customer statement links.
- Referral programs.
- Loyalty points.
- Customer ratings.
- Driver/helper ratings.
- Water-quality ratings.
- Advanced customer ledgers and debt/collections.
- SMS sender customization.
- Trusted-device locking.
- Advanced role/screen permissions.
- Full offline operation.
- Advanced marketing lists captured from QR/POS.
- Bulk WhatsApp/SMS marketing.
- Advanced analytics and reports.
- Advanced audit history.
- Full white-label deployment on customer infrastructure.
- Multiple branches.
- Corporate accounts and corporate billing.
- Fleet management and vehicle records.
- Route optimization / nearest-route calculation.
- Live driver/fleet tracking.
- Advanced stock movements and warehouses.
- PDF invoices/statements/receipts.
- Accounting integrations.
- Payment gateway integrations.
- Customer wallet / saved payment methods.
- Marketplace/discovery layer after enough distributors join.

## Communication / automation

- WhatsApp Business API automation.
- Automated order creation from WhatsApp conversations.
- Automated status replies over WhatsApp.
- SMS notifications.
- Email notifications.
- Bulk campaigns.
- Customer segmentation.
- Scheduled campaigns.
- Notification template editor.

## AI / MCP

MCP is strategically important and should remain in the product roadmap.

Possible MCP tools:

- `get_products`
- `get_offers`
- `create_order`
- `repeat_last_order`
- `get_order_status`
- `get_subscriptions`
- `skip_next_delivery`
- `pause_subscription`
- `resume_subscription`

Future AI experiences:

- Customer orders water from supported AI clients.
- Customer asks when the next delivery is due.
- Customer skips or changes an upcoming subscription delivery.
- Owner asks operational questions such as "كم طلب عندي بكرا؟".
- Owner asks for summaries of customers, orders, delivery workload, bottle balances, or subscription activity.
- Driver assistant for delivery context.
- AI-generated operational summaries and retention suggestions.

MCP must remain an adapter over existing application services, never a separate business-logic path.

## Store/content growth

- Custom domains.
- More storefront themes.
- Block-based lightweight page builder:
  - text
  - image
  - products
  - offers
  - CTA
  - FAQ
  - contact block
- Advanced SEO controls.
- Theme marketplace.
- Product-specific QR codes.
- Customer-specific QR codes.
- Referral QR codes.
- Vehicle/bottle QR campaigns.

## Offers and promotions

Current MVP offers are marketing content only. Later:

- Percentage discounts.
- Fixed discounts.
- Coupon codes.
- Bundles.
- Buy-X-get-Y.
- Automatic offer rules.
- Customer segment targeting.
- Subscription-specific promotions.

## Delivery

- Route entity / route stops.
- Automatic route optimization.
- Driver live location.
- Customer live driver tracking link.
- Proof of delivery.
- Delivery photos.
- Failed-delivery workflow.
- Re-attempts.
- Vehicle management.
- Fuel/maintenance tracking if ever justified.

## Customer experience

- Native Android/iOS apps if PWA proves insufficient.
- Saved payment method.
- Wallet.
- Customer ratings.
- Driver ratings.
- Advanced order ETA.
- Smart reorder reminders.
- Personalized offers.

## Platform / technical

- Public REST API.
- Webhooks.
- Third-party integrations.
- More granular feature flags.
- Advanced tenant plans/billing only after monetization is intentionally introduced.
- Dedicated database per tenant only if scale/compliance later requires it.
- Services extraction from modular monolith only when operationally justified.

## Possible future vertical expansion

The current product must not show another vertical in UI, onboarding, or documentation. However, internal naming should avoid unnecessary water-specific coupling where a generic concept is equally clear.

If the business later expands beyond water, the existing order, delivery, subscription, notification, tenant, and returnable-container core should be reusable. Such expansion requires separate product validation and is not part of the current user experience.
