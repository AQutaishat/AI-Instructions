# UX Implementation Regulations

## Preserve approved UX

Follow approved:
- flows;
- wireframes;
- terminology;
- navigation;
- design system.

Do not casually:
- move core actions;
- rename domain terms;
- remove states;
- add steps/settings;
- redesign navigation.

## Required UI states

Every data-driven React screen should consider:

- loading;
- empty;
- populated;
- validation;
- recoverable error;
- unavailable/forbidden;
- disabled action;
- success/confirmation.

## Forms

- visible labels;
- inline validation;
- preserve entered values after recoverable errors;
- disable duplicate submission while processing;
- explicit destructive actions;
- confirm meaningful destructive operations.

## Lists

- empty state;
- pagination/incremental loading for large datasets;
- useful primary information;
- actions discoverable without visual clutter.

## Responsive

- mobile is not simply a shrunken desktop;
- avoid horizontal overflow;
- keep primary actions reachable;
- verify representative widths after significant UI work.

## RTL

If Arabic exists:
- implement from the beginning;
- use logical CSS properties;
- set `lang` and `dir`;
- test directional icons/navigation;
- test actual Arabic strings.

## Accessibility

- semantic HTML;
- keyboard controls;
- visible focus;
- labels;
- accessible dialogs;
- sufficient contrast;
- icons must not be the only critical signal.

## Feedback

Users should know:
- action started;
- success;
- failure;
- next step.

Avoid unnecessary toast spam.

## Visual verification

Do browser/screenshot verification after meaningful UI milestones rather than every small edit.
