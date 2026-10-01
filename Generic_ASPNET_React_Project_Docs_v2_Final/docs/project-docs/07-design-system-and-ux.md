# Design System and UX

## Product feel

`[Clean / friendly / professional / premium / etc.]`

## Core UX principles

- fewer steps;
- obvious primary action;
- predictable navigation;
- visible system status;
- preserve user input after recoverable errors;
- responsive by default.

## Required UI states

Every data-driven screen should consider:

- loading;
- empty;
- populated;
- validation;
- recoverable error;
- unavailable/forbidden;
- disabled action;
- success/confirmation.

## Forms

- labels remain visible;
- validation appears near the affected field;
- preserve entered values after recoverable errors;
- disable duplicate submission while processing;
- destructive actions must be explicit.

## Lists

- show empty state;
- paginate/incrementally load large collections;
- show useful primary information without forcing record-by-record opening;
- keep actions discoverable but not visually dominant.

## Localization / RTL

If Arabic is supported:
- implement RTL from the start;
- set `lang` and `dir`;
- use CSS logical properties;
- test navigation direction;
- verify dates/numbers;
- use an Arabic-compatible font.

## Responsive design

Mobile layouts must not merely shrink desktop layouts.

Test significant flows at representative widths.

## Accessibility

- semantic HTML;
- keyboard-operable controls;
- visible focus;
- form labels;
- accessible dialogs;
- sufficient contrast;
- icons are not the sole carrier of critical meaning.

## Feedback

Users should know:
- when action started;
- when it succeeded;
- when it failed;
- what to do next.

Avoid excessive toasts for information already obvious on screen.
