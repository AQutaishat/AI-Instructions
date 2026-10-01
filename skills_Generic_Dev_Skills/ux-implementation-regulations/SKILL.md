---
name: ux-implementation-regulations
description: Use when building or reviewing any UI/frontend screen, form, dialog, or component — covers i18n/RTL, validation, error-handling, mobile responsiveness, component-library theming, and status-consistency rules.
---

## When to use
Whenever writing, editing or reviewing frontend/UI code — forms, dialogs, navigation, status displays, deep links, or any customer/admin-facing screen.

## When not to use
Backend-only changes with no user-facing surface.

## Rules

### Internationalization / RTL (if the project requires it)
- Set `lang` and `dir` correctly; use CSS logical properties; make navigation direction-aware.
- Test right-to-left languages continuously, not only at the end.
- Pick a deliberate font pairing per script/language rather than defaulting silently.

### Form validation
- Use a shared validation pattern; show errors after blur, clear them promptly after correction.
- Inline helper/error text — never alerts for ordinary validation.
- Numeric inputs must be easy to overwrite.

### Submission errors
- Never clear a user's entered form on server rejection — preserve entered values.
- Show a persistent contextual error; map technical failures to understandable messages.
- Never show raw exceptions to the user.
- Example: show "We couldn't save your order. Check your connection and try again." — not `500: NullReferenceException at ...`.

### Confirmation dialogs
- Explain actual consequences, not a generic "are you sure?".
- Bad: "Are you sure?" — Better: state exactly what will change and what cannot be undone.
- Example: "Cancel order #123? The customer is notified and the payment is refunded. This cannot be undone." with buttons "Cancel order" / "Keep order".

### Nudge, don't gate
Optional profile/setup reminders must not block unrelated work unless security/correctness truly requires it.

### Loading/empty states
- Avoid excessive animation/skeleton complexity.
- Empty states explain what's empty and offer a useful action when possible.

### Mobile responsiveness
- No accidental horizontal scrolling.
- Identify the actual mobile-first flows in your product (commonly checkout/purchase and any field/on-the-go user role) and prioritize them.
- Mobile dialogs are near-full-width with small margins.
- Collapse desktop navigation rather than shrinking it into an unusable sidebar.

### Component library usage
A UI component library (MUI, Chakra, etc.) is a toolkit, not your product's visual identity — use it for accessibility/behavior, then apply your own theme: deliberate button styles, restrained shadows, consistent surface treatment, a palette that matches the product, and avoid heavy unstyled defaults.

### Status consistency
Centralize any status → color/label mapping (order status, task status, etc.) in one place. Never assign arbitrary colors per screen.

### Navigation / actions
- Keep a clear primary action hierarchy; avoid duplicate competing CTAs.
- Back/close returns to the expected parent screen.
- Group account actions together.

### External deep links
Any deep link to an external service with a prefilled message/template (WhatsApp, email, SMS, etc.) should go through one reusable utility/template — never hand-built per page.

### Role-based UX
Hide unavailable actions where appropriate, but backend authorization is mandatory regardless of UI visibility.

### Accessibility
Icon-only actions need accessible labels and tooltips where appropriate.

### Simplicity
Prefer the solution with fewer steps, fewer modes, less hidden state when value is similar.

### Visual verification
Inspect important flows in the real rendered app at representative mobile and desktop sizes, including any required RTL/localization, before considering a UI milestone done.
