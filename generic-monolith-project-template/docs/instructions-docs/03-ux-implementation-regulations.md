# UX Implementation Regulations

## Preserve Approved UX

Implementation should follow approved flows, wireframes, and design-system decisions.

Do not casually:
- move core actions;
- rename domain terminology;
- remove states;
- add extra steps;
- invent settings;
- change navigation structure.

## Required UI States

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

- Labels must remain visible.
- Validation should be near the affected input.
- Preserve entered values after recoverable errors.
- Disable duplicate submissions while a request is processing.
- Make destructive actions explicit.
- Ask for confirmation where accidental execution has meaningful consequences.

## Lists

- Support empty state.
- Use pagination/incremental loading for large collections.
- Show useful primary information without forcing users to open every record.
- Keep actions discoverable but not visually dominant.

## Responsive Design

- Mobile layouts must not merely shrink desktop screens.
- Avoid horizontal overflow for normal content.
- Keep primary actions reachable.
- Test significant flows at representative widths, not every tiny code change.

## Accessibility

Minimum baseline:

- semantic HTML where applicable;
- keyboard-operable controls;
- visible focus;
- form labels;
- descriptive button/link text;
- accessible dialogs;
- sufficient contrast;
- icons must not be the only carrier of critical meaning.

## Feedback

Users should know:

- when an action started;
- when it succeeded;
- when it failed;
- what they can do next.

Avoid excessive toast notifications for information already obvious on screen.
