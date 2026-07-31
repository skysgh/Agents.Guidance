# Engineering Human Guidance

Welcome. This is the human-facing entrance to the engineering guidance.

The purpose is to explain the ideas before asking anyone to use technical vocabulary. You do not need to know the implementation terms to understand the design. The terms are introduced when they add useful precision.

## Start here

- [Why this guidance exists](./orientation/current-state.md)
- [What the guidance gives each role](./orientation/what-this-guidance-gives.md)
- [Design Before Build and What Goes First](./orientation/design-before-build-and-wgf.md)
- [Configuration and Settings](./configuration-and-settings.md)
- [Common Flows](./flows.md)
- [The Palette: First Look](./palette/first-look.md)
- [Palette Elements](./palette/elements.md)
- [Palette Relationships](./palette/relationships.md)
- [Palette Technical Terms](./palette/technical-terms.md)
- [Responsible Boundaries and Deferred Design](./responsible-boundaries-and-deferred-design.md)
- [API Lifecycle](./api-lifecycle.md)
- [Example gallery](./examples/readme.md)
- [Human writing style](./writing-style.md)
- [Guidance Glossary](./glossary.md)
- [Rewrite plan](./rewrite-plan.md)
- [Rewrite register](./rewrite-register.md)

## The high-rise picture

A serious system is like a high-rise building:

- foundations go below the visible surface and must reach dependable ground;
- contracts are part of the structural frame;
- objects and services form the building systems;
- registries and startup assemble the known parts;
- vertical slices carry capabilities through the floors; and
- horizontal flows move between capabilities and are adapted for each tenant or user experience.

The building does not need every room fitted out on the first day. It does need a design that shows where later rooms belong and how they will connect.

## Buildings have different sizes

The right amount of construction depends on the building and on who relies on it:

- a temporary shelter is like a short-lived script or one-off integration;
- a single dwelling is like a small internal application used by one team;
- a multi-unit building is like a shared service used by several teams, with common spaces and services; and
- a high-rise or commercial building is like a service used by external people, organisations and systems.

A small internal application may tolerate lighter construction when its failures can be handled within the team and its life is limited. That does not make disorganisation good; it makes the consequences more contained.

When external consumers rely on a service, the organisation's reputation, obligations and relationships are also exposed. At that point, clear contracts, boundaries, security, diagnostics, recovery and compatibility are not monumental extras. They are the minimum structure needed to operate responsibly.

This guidance is primarily for those services that matter beyond the immediate team. It helps the team choose a construction method that matches the reach and consequences of the service.

## Concept before vocabulary

A human document should first say what a design choice achieves. For example:

> Keeping each layer separate allows each part to change without forcing every other part to change at the same time.

It may then add:

> In technical language, this separation is often called brokering. The term is useful for precision, but understanding the separation is more important than remembering the term.

The explanation comes first. The label is a helper.

## Human and agent guidance

This human route explains the reasons, examples and shared understanding. The compact [agent guidance](../agents/readme.md) states what an agent must load and follow for this domain.

For the concise implementation rules, read the [agent guidance](../agents/readme.md). For a fuller explanation of those rules, continue reading here.
