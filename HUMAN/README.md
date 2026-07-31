# Human Guidance

Welcome. This is the human-facing entrance to the engineering guidance.

The purpose is to explain the ideas before asking anyone to use technical vocabulary. You do not need to know the implementation terms to understand the design. The terms are introduced when they add useful precision.

## Start here

- [Why this guidance exists](../HUMAN-CURRENT-STATE.md)
- [What the guidance gives each role](../HUMAN-WHAT-GUIDANCE-GIVES.md)
- [Design Before Build and What Goes First](../HUMAN-YAGNI-VERSUS-WGF.md)
- [Configuration and Settings](./CONFIGURATION-AND-SETTINGS.md)
- [Common Flows](./FLOWS.md)
- [The Palette: First Look](./PALETTE-FIRST-LOOK.md)
- [Palette Elements](./PALETTE-ELEMENTS.md)
- [Palette Relationships](./PALETTE-RELATIONSHIPS.md)
- [Palette Technical Terms](./PALETTE-TECHNICAL-TERMS.md)
- [Stewardship and Deferred Design](./STEWARDSHIP-AND-DEFERRED-DESIGN.md)
- [API Lifecycle](./API-LIFECYCLE.md)
- [Example gallery](../examples/README.md)
- [Human writing style](./WRITING-STYLE.md)
- [Guidance Glossary](./GLOSSARY.md)
- [Rewrite plan](./REWRITE-PLAN.md)
- [Rewrite register](./REWRITE-REGISTER.md)

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

This human route explains the reasons, examples and shared understanding. The compact [agent guidance](../AGENTS.md) states what an agent must load and follow for a task.

For the concise implementation rules, read the [agent guidance folder](../AGENTS/README.md). For a fuller explanation of those rules, continue reading here.
