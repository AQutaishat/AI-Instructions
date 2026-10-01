# Taw — Platform Publishing Metadata

This document centralizes non-secret metadata commonly required by hosting, app-store, identity, AI/MCP, Firebase and cloud-console platforms. Keep it updated when public product details change.

## Core product identity

- Product title: **Taw**
- Arabic title: **توّ**
- Working domain direction: **taw.delivery**
- Current product focus: water delivery SaaS for water stations/distributors
- Business model at launch: free
- Primary language: Arabic
- Secondary language: English
- Default direction: RTL

## Recommended short description — Arabic

منصة بسيطة لمحطات وموزعي المياه لإنشاء متجر طلبات خاص وإدارة الطلبات والاشتراكات والعملاء والسائقين والتوصيل والقوارير.

## Recommended short description — English

A simple water-delivery platform for distributors to run a branded storefront, customer orders, subscriptions, drivers, deliveries, and reusable-bottle tracking.

## Long description — Arabic

توّ منصة رقمية مخصصة لمحطات وموزعي المياه. تمكّن كل موزع من إنشاء متجر إلكتروني خاص به، عرض منتجات المياه والعروض، استقبال الطلبات من العملاء بدون إجبارهم على إنشاء حساب، إدارة الاشتراكات الدورية، تنظيم السائقين وجدول التوصيل، متابعة الطلبات، والتعامل مع رصيد القوارير الفارغة والمسترجعة. صُممت المنصة لتكون بسيطة وسريعة ومناسبة للاستخدام من الهاتف وسطح المكتب، مع دعم العربية وواجهة RTL من البداية.

## Long description — English

Taw is a digital platform built for water stations and distributors. Each distributor can run a branded ordering storefront, list water products and offers, accept guest orders without forcing account creation, manage recurring subscriptions, coordinate drivers and delivery schedules, track order progress, and maintain reusable-bottle balances. Taw is designed to stay simple, mobile-friendly, Arabic-first, and easy to operate from both desktop and mobile devices.

## Store/category guidance

These are working recommendations and should be validated against the platform's categories at publication time.

- Google Play customer-facing app/PWA wrapper: **Shopping** is the strongest initial fit.
- Admin/driver utility app if published separately: **Business** or **Productivity**, depending on the store taxonomy at publication time.
- Website/SaaS classification: water delivery / business operations / ordering platform.

## Suggested keywords/tags

Arabic:

- مياه
- توصيل مياه
- طلب مياه
- اشتراك مياه
- موزع مياه
- قوارير مياه
- توصيل

English:

- water delivery
- water subscription
- water distributor
- bottle delivery
- delivery management
- recurring delivery

## Public URLs — fill when available

- Main website:
- Customer storefront root:
- Admin portal:
- API base URL:
- Driver/PWA URL:
- Privacy statement URL:
- Terms and conditions URL:
- Support page URL:
- Support email:
- Support WhatsApp:

## Google Play / Android

- App title: Taw / توّ
- Short description: use the approved short description above, adapted to current store limits.
- Long description: use/adapt the long description above.
- Category candidate: Shopping
- Default language: Arabic
- Privacy policy URL: required before production publication.
- Support/contact email: required.
- App icon asset: store under `docs/materials/` or the application asset tree.
- Feature graphic/screenshots: store source assets under `docs/materials/` and final production assets in the platform-specific release workflow.

Identifiers to record when created:

- Android package/application ID:
- Google Play Console app ID:
- Google Play developer/account name:

## Google Cloud Console / OAuth consent

Record public non-secret values here when created:

- Google Cloud project name:
- Google Cloud project ID:
- OAuth app name: Taw
- App homepage:
- Privacy policy URL:
- Terms URL:
- Authorized domains:
- Support email:
- Developer contact email:

Do **not** record OAuth client secrets here. Store sensitive values only under the local ignored `docs/credentials/` folder or the deployment secret store.

## Firebase

Record non-secret identifiers:

- Firebase project name:
- Firebase project ID:
- Android app ID:
- Web app ID:
- Messaging sender ID:
- Hosting domains:

Sensitive service-account files and private keys belong only in ignored credential storage / secret management.

## OpenAI / MCP publishing

Working public metadata when MCP publishing begins:

- Connector/MCP name: Taw
- Arabic display name: توّ
- Description: Access a connected water distributor to browse products, create/repeat orders, check order status, and manage supported water subscriptions.
- MCP server URL:
- OAuth authorization URL:
- OAuth token URL:
- Public documentation URL:
- Privacy URL:
- Terms URL:
- Support URL/email:

Suggested initial MCP capabilities when implemented:

- products read
- offers read
- order create
- order status read
- repeat order
- subscription read
- supported subscription management

## PWA manifest metadata

- `name`: Taw
- `short_name`: Taw
- `lang`: ar
- `dir`: rtl
- `display`: standalone
- `start_url`: / or tenant storefront entry as appropriate
- Theme/background colors: derive from the approved Taw design system, not tenant branding unless implementing tenant-specific manifests.

## Legal/publication checklist

Before public launch, verify that the current product behavior matches:

- `15-privacy-statement.md`
- `16-terms-and-conditions.md`
- actual data collection and retention
- notification opt-in behavior
- location usage
- account/OTP behavior
- third-party service disclosures

Do not publish placeholder URLs, emails, IDs or legal statements without replacing and validating them.
