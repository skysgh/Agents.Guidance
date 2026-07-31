# Accessibility Conventions

Apply these conventions to user interfaces, documents, notifications and interactive client features.

For the accessible explanation of inclusive user experiences, read [Human Documentation Writing Style](../HUMAN/WRITING-STYLE.md).

## Purpose

Accessibility makes the service usable by people with different abilities, devices, languages and ways of interacting. It is part of the experience contract, not decoration added after the building is complete.

## The short version

Every important action should be possible to find, understand and complete. Information should remain understandable when a person uses a keyboard, assistive technology, zoom, high contrast, reduced motion or a different language.

Business roles describe the people and situations the service must support. Developers build the accessible structure. Testers check keyboard, screen-reader, zoom and automated evidence. Design and operations help ensure that accessible behaviour remains present after release.

- Target the applicable WCAG conformance level and record exceptions.
- Make every operation available by keyboard and preserve a visible, logical focus order.
- Use semantic structure, accessible names, headings, labels, landmarks and meaningful status messages.
- Associate validation errors with their fields and describe how to correct them.
- Maintain sufficient colour contrast and never use colour as the only signal.
- Support zoom, text resizing, reflow, high contrast and reduced-motion preferences.
- Keep controls, touch targets, tables, dialogs, menus and notifications usable with assistive technology.
- Test with automated checks and representative keyboard, screen-reader and zoom workflows.
- Do not treat accessibility as a visual polish step after implementation; it is part of the contract and acceptance criteria.
