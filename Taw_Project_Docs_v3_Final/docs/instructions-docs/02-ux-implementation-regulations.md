# Taw — UX Implementation Regulations

This is the single canonical UX regulation document inside the project package.

## Arabic-first / RTL

Arabic is a primary product target.

- Set `lang` and `dir` correctly.
- Use CSS logical properties.
- Make navigation direction-aware.
- Test Arabic continuously, not at the end.
- Suggested fonts: Tajawal for Arabic, Inter for English unless design changes later.

## Form validation

Use a shared validation pattern.

- Ordinary errors appear after blur.
- Errors clear promptly after correction.
- Show inline helper/error text.
- Do not use alerts for ordinary validation.
- Make numeric inputs easy to overwrite.

## Submission errors

- Never clear the user's entered form because the server rejected it.
- Preserve values.
- Show persistent contextual error.
- Map technical failures to understandable messages.
- Never show raw exceptions.

## Confirmation dialogs

Explain actual consequences.

Bad:

> هل أنت متأكد؟

Better:

> إلغاء هذا الطلب سيزيله من جدول السائق ولن يتم توصيله اليوم.

## Nudge, do not gate

Optional profile/setup reminders should not block unrelated work unless security/correctness truly requires it.

## Loading/empty states

Avoid excessive animation/skeleton complexity.

Empty state should explain what is empty and provide a useful action when possible.

## Mobile responsiveness

- No accidental horizontal scrolling.
- Customer checkout is mobile-first.
- Driver experience is mobile-first.
- Mobile dialogs use near-full-width with small margins.
- Collapse desktop navigation rather than shrinking it into an unusable sidebar.

## MUI

MUI is a toolkit, not Taw's visual identity.

Use it for accessibility and component behavior, then apply Taw's theme:

- Flat/clear buttons.
- Restrained shadows.
- Rounded surfaces.
- Water-oriented palette.
- Avoid heavy default Material elevation.

## Status consistency

Centralize order/delivery status visual mapping.

Do not assign arbitrary colors per screen.

## Navigation / actions

- Keep primary action hierarchy clear.
- Avoid duplicate competing CTAs.
- Back/close should return to expected parent.
- Account actions belong together.

## WhatsApp

All simple WhatsApp deep links and prefilled messages use one reusable utility/template mechanism.

Do not hand-build `wa.me` logic in each page.

## Role-based UX

Hide unavailable actions where appropriate, but backend authorization is mandatory regardless of visibility.

## Tooltips/accessibility

Icon-only actions need accessible labels and tooltips where appropriate.

## Simplicity

When two solutions provide similar value, prefer the one with fewer steps, fewer modes and less hidden state.

## Visual verification

Important flows should be inspected in the real rendered app at representative mobile and desktop sizes, especially Arabic RTL.
