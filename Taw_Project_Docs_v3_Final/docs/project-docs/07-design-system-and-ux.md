# Taw — Design System and UX Direction v1

## Visual direction

Taw should feel:

- Simple.
- Clean.
- Friendly.
- Practical.
- Mobile-first for customers and drivers.
- Easier than an ERP.
- Arabic-first.

Avoid a visually heavy enterprise dashboard.

## MUI

Use **MUI** as the component/accessibility toolkit.

Taw must have its own visual language rather than default Material styling.

Use MUI for:

- Accessible forms.
- Dialogs.
- Menus.
- Drawers.
- Responsive breakpoints.
- Tables.
- Focus management.

Customize:

- Buttons.
- Cards.
- Typography.
- Radius.
- Shadows.
- Colors.
- Status badges.

## Base color direction

Initial design direction, subject to branding refinement:

```text
Primary:      #2478C5
Primary Dark: #195D9B
Primary Soft: #EAF4FC
Secondary:    #28A8A1
Background:   #F7F9FB
Surface:      #FFFFFF
Text:         #17212B
Muted:        #667085
Border:       #E4E7EC
```

Tenant storefront can override limited branding variables such as primary/secondary colors, logo and hero image.

Do not give tenants unrestricted styling that can destroy accessibility/usability.

## Typography

Preferred direction:

- Arabic: Tajawal
- English: Inter

Simple scale:

```text
H1    32 / 700
H2    26 / 700
H3    21 / 600
H4    18 / 600
Body  16 / 400
Small 14 / 400
Tiny  12 / 400
```

## Spacing

Use a consistent 4/8-based system:

```text
4, 8, 12, 16, 24, 32, 48
```

Avoid arbitrary per-screen spacing values.

## Radius

Suggested:

- Small: 8px
- Normal: 12px
- Large: 16px
- Buttons: about 10–12px

## Shadows

Restrained.

Prefer borders/surface separation over elevation-heavy Material design.

## Buttons

Four main types:

- Primary.
- Secondary.
- Text.
- Destructive.

Avoid multiple competing primary CTAs in the same visual area.

## Forms

Standard field pattern:

```text
Label
[ Input ]
Helper/Error
```

Validation behavior:

- Show ordinary field errors after blur, not on every keystroke.
- Clear promptly after correction.
- Keep entered values if submission fails.
- Use contextual messages, not generic technical errors.

Numeric fields should be easy to replace/select instead of appending to a default zero.

## Confirmation dialogs

Explain the consequence.

Bad:

> هل أنت متأكد؟

Better:

> إلغاء هذا الطلب سيزيله من جدول السائق ولن يتم توصيله اليوم.

## Status mapping

Use one central mapping for order/delivery statuses across admin, driver and customer tracking.

Example direction:

- New: blue
- Confirmed: cyan
- Assigned: purple
- OutForDelivery: orange
- Delivered: green
- Cancelled: red

Do not depend on color alone; include label/icon/state text.

## Responsive behavior

Hard requirement:

> No accidental horizontal page scrolling.

Customer checkout and driver screens are mobile-first.

Admin tables can transform to cards on small screens rather than becoming unreadable compressed tables.

## Admin navigation

Desktop sidebar:

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

Mobile admin uses drawer navigation rather than a squeezed sidebar.

## Driver navigation

Keep minimal:

```text
Today
Available
Completed
Profile
```

A bottom navigation is appropriate on mobile.

## Customer storefront navigation

Keep simple:

```text
Home
Products
Offers
Contact
```

Primary CTA remains "Order now".

## Loading and feedback

Prefer simple feedback:

- `جاري التحميل...`
- Disabled submit button with spinner/text.
- Inline errors.

Use toasts sparingly for lightweight success feedback such as "تم نسخ الرابط".

Do not hide important submission failures in transient toasts.

## Empty states

Explain what is empty and give a useful CTA.

Example:

> لم تضف أي منتجات مياه بعد.

Button:

> إضافة أول منتج

## Accessibility

- Every input has a label.
- Visible keyboard focus.
- Icon-only actions have `aria-label` and desktop tooltip where useful.
- Touch targets roughly 44px or larger.
- Good contrast.
- Status not conveyed only by color.

## RTL implementation

Arabic is not an afterthought.

Use:

```html
<html lang="ar" dir="rtl">
```

Use CSS logical properties such as:

```text
margin-inline-start
padding-inline-end
inset-inline-start
```

Avoid hardcoded left/right positioning unless the meaning is truly physical.

## Store customization

Do not build a full page builder initially.

Allow tenant to control:

- Logo.
- Primary/secondary color.
- Hero image.
- Tagline.
- Content/pages.
- Offers.
- Visibility/order of supported navigation items.

A small set of good themes/templates is preferable to unrestricted design freedom.

## Icon direction

Current icon direction for Taw:

- Water-inspired.
- Blue/cyan.
- Flat/vector.
- Minimal.
- Avoid glossy/3D complexity.

The icon can reference a droplet/flow and the brand mark while remaining scalable at small app-icon sizes.
