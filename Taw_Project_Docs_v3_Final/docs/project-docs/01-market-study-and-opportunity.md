# Taw — Market Study and Opportunity History

## 1. Original inspiration

The project started from a consumer experience similar to the Saudi **Tania Water** ordering model: a customer saves an address, chooses water products, subscribes or orders on demand, and selects delivery timing.

The first question was whether Jordan had a meaningful gap for a similar consumer water-ordering application.

## 2. What the Jordan research changed

Research showed that the idea was **not an empty category**.

### Qatra

Qatra is an active Jordan-focused water-ordering app. Its public store description includes nearby water ordering and recurring/flexible subscriptions. This substantially reduced the value of building a simple consumer water-delivery app whose differentiation was only "order water from an app".

Source used during project validation:

- Google Play — Qatra: https://play.google.com/store/apps/details?id=com.qatra.waterdelivery

### Zad

Zad also demonstrates that Jordan consumer delivery can combine water and gas products in one app. Its App Store description includes water bottles/gallons, gas cylinders, address selection on a map, secure payment and real-time order tracking.

Source:

- App Store Jordan — Zad: Water & Gas Delivery: https://apps.apple.com/jo/app/zad-water-gas-delivery/id6799771203

### Interpretation

The consumer marketplace/order-app opportunity is therefore validated as a real need, but it is not sufficiently differentiated for Taw's initial strategy. Competing as another central app would also require consumer traffic, supply acquisition and marketing budget.

## 3. First pivot — white-label / multi-tenant distributor platform

The project then moved from:

> "A central app where consumers order water"

To:

> "A multi-tenant platform where every water distributor gets its own branded digital store and operational system."

The business reason is important: the distributor can bring existing customers to its own store without Taw first solving a marketplace chicken-and-egg problem.

Each distributor/tenant can have a branded storefront and operational dashboard, potentially on a Taw subdomain and later on a custom domain.

## 4. Discovery of WaterCopon

Further validation found **WaterCopon**, a Jordanian SaaS focused on water distributors/stations.

WaterCopon validates the operational problem strongly. Its public materials include customer management, digital water coupon books, customer balances, delivery movements, PWA use, WhatsApp notifications, reports, Excel, referral/marketing tools, inventory in higher plans and driver-related functionality.

WaterCopon is explicitly described as SaaS for water distributors in Jordan and nearby markets.

Sources:

- Main site: https://watercopon.com/
- Features: https://www.watercopon.com/features
- Pricing: https://watercopon.com/pricing
- Terms: https://watercopon.com/terms

As checked during September 2026 research, published pricing included a free digital-coupon tier and annual paid tiers around 25 JOD, 50 JOD and 80 JOD, although pricing can change and must be rechecked before any external market presentation.

## 5. Why Taw still proceeds

Finding WaterCopon did **not** kill the project. It changed the competitive strategy.

Taw should not try to win by implementing every ERP-like feature. The intended differentiation is:

- Simpler onboarding.
- Simpler day-to-day use.
- Strong customer-facing branded storefront.
- Guest-first ordering with minimal friction.
- Useful customizable content pages.
- Offers/marketing content.
- Support page.
- WhatsApp-friendly communication.
- Push notifications.
- Practical driver schedule and assignment workflow.
- Customer subscriptions with skip/pause/change controls.
- Bottle delivered/empty-returned tracking.
- Strong future MCP/AI ordering channel.
- Free product for a long initial adoption period.

## 6. Strategic distinction from WaterCopon

WaterCopon is an important benchmark and source of future ideas, but Taw's initial identity is intentionally narrower:

> "A simple branded ordering + delivery operations platform for a water distributor."

Not:

> "A complete water ERP from day one."

That distinction controls scope.

## 7. Marketplace strategy

A central marketplace is **not** the initial model.

Initial model:

```text
Taw Platform
  ├── Distributor A branded store
  ├── Distributor B branded store
  └── Distributor C branded store
```

Each distributor operates privately and customers do not need to know that other tenants exist.

A central discovery marketplace can be reconsidered only after meaningful distributor adoption.

## 8. Business model decision

Taw should be free for a long early period.

Reasoning:

- Adoption and real workflow learning are more valuable than early billing.
- A paid competitor already exists at low annual prices, so competing primarily on price would be weak.
- The product needs real distributors and real delivery activity before monetization assumptions become reliable.

The architecture may keep a simple internal `Plan = Free` concept so monetization can be added later without redesigning tenant records.

## 9. Market-risk conclusions

### Main risks

- Water distributors may remain comfortable with phone/WhatsApp/manual processes.
- Competitors already cover some operational needs.
- Distributor acquisition still requires direct outreach even when the product is free.
- Too many features could destroy the intended simplicity.

### Main opportunity

The problem is validated: distributors need customer records, recurring water delivery, delivery scheduling, driver operations, reusable-bottle accounting and easy customer communication.

The product opportunity is therefore not "invent water ordering"; it is to deliver a **simpler and more customer-friendly execution** of a validated workflow.

## 10. Research note on usage/download figures

App-store download/review counts are time-sensitive. Earlier project discussions considered visible store activity, reviews and public adoption signals, but any exact counts should be refreshed immediately before investor/marketing material is produced. This document deliberately preserves the strategic conclusion rather than freezing ephemeral store metrics.
