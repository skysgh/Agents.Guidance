# The Structure Before the Feature

Imagine a team preparing its first useful capability. The visible request is modest: a person should be able to submit something, another person should be able to review it and the service should remember what happened. The team can begin with a screen, a controller and a table. That route is attractive because it produces something recognisable quickly.

It also leaves several questions unanswered. Who owns the submission? Which information is a durable business record and which is only a screen detail? What does review mean compared with editing? Which boundary decides whether the submission is visible, valid or complete? What will an operator need to recover when an external call fails? If those questions are left inside the first implementation, the first feature quietly becomes the structure that every later feature must work around.

Most service structures are not unknown. Teams repeatedly need places for the consumer experience, application decisions, business meaning and stored information. They need agreements between those places, objects that give the agreements concrete form, services that compose useful behaviour, and a way to assemble, protect, observe and change the result. They also need to distinguish a complete capability from the longer journey that connects several capabilities.

What is usually novel is the organisation's language, relationships, decisions, workflow detail and presentation shape. The reusable engineering structure should be designed before feature coding, while the novel business meaning is explored inside that structure. The [Building Metaphor](../reference/building-metaphor.md) helps make this distinction visible: the rooms and activities may be new, but the need for dependable structure and clear responsibility is familiar.

This is the governing idea:

> Design the knowable. Build it in stages. Discover the novel inside the formwork.

Design completeness does not require build completeness. A capability may be deliberately deferred, but its intended place, responsible boundary, contract, dependencies and lifecycle should not be left for a future team to invent from fragments.

## What goes first?

Two different decisions are often collapsed into one. The first is to design the known structure: the responsible boundaries, dependencies, security and lifecycle that later work must fit. The second is to choose which part of that structure should be built first, based on value, risk, dependency, evidence and available capacity.

We call the first decision **Design Before Build**, or **DBB**, and the second **What Goes First?**, or **WGF**. The names are reminders, not a ceremony. DBB does not mean building everything before learning. WGF does not mean designing only the first ticket. Together they separate architectural understanding from construction priority.

DBB does not mean build everything before learning. WGF does not mean design only the first ticket. Together they separate architectural understanding from construction priority. The design should be achievable from the available problem and system evidence; it should not wait for a particular person to become available.

When the team considers including, omitting or deferring part of the design, it should follow the consequences in both directions. Including something may provide evidence or safety while adding cost and support burden. Deferring it may reduce immediate construction while creating a missing extension point, migration risk or assumption that a later team must uncover. The answer should consider value, risk, dependency, security, reversibility, operational cost, evidence gained and the effect on later construction. An omission is a decision with consequences, not the absence of a decision.

## Why the order matters

A team is more likely to use guidance when it recognises the problem it is meant to solve. [The current state and recurring failure patterns](./current-state.md) describe what happens when visible features arrive before the structure that supports them. [What the guidance gives each stakeholder](./what-this-guidance-gives.md) shows how different roles add the knowledge the design needs.

A system is easier to change when its parts have clear jobs. Contracts hold the intended shape. Objects give those contracts concrete form. Services compose the parts into useful behaviour. Registries and startup assemble the known participants. Vertical slices carry capabilities through the layers. Horizontal flows connect those capabilities into journeys.

There is a deeper reason to keep these concerns distinct. Infrastructure and services are the dependable building work. The Domain is the model of what lives in that building: the things, relationships, states, decisions and rules that make the business problem recognisable over time. Architecture begins by decomposing the stated problem until those ontological elements can be seen. Contracts then isolate them so that each part can be understood, tested and changed without silently changing the meaning of the whole.

The team is therefore doing two kinds of work together. It is building the concrete structure that makes the system dependable, and it is deciding what kind of world that structure is meant to support. The first without the second produces a well-built answer to an unclear problem. The second without the first produces a compelling model that cannot be trusted in operation.

The aim is not to implement every capability at once. Establish the shared boundaries, dependencies and responsibilities before different teams build different interpretations. Some capabilities may remain unfinished when priorities change. That is acceptable when the structure remains sound and the unfinished work has a known place.

## A shared act of seeing

No single role sees the whole system alone. Business analysis supplies domain meaning, decisions and language. Developers test whether contracts can actually be implemented. Test developers expose whether the claimed boundaries are real. Operations exposes lifecycle, readiness, recovery and support needs. Security and assurance expose protection and evidence obligations. Architecture preserves coherence across the views.

The design becomes stronger when these views meet. A developer may discover that a proposed boundary cannot express the required rule. A tester may show that a boundary is only written down and is not enforced. An operator may reveal that the proposed lifecycle cannot be recovered after a dependency fails. A business analyst may explain that two apparently similar states carry different decisions for the people involved. The guidance gives each role a way to contribute to the same design, not a list of instructions for everyone else to obey.

The [example gallery](../examples/readme.md) shows the same movement through several ordinary situations. A reader can choose the example that feels most familiar, then follow the supporting guidance that explains the decision behind it.

## Related guidance

- [Current state and recurring failure patterns](./current-state.md)
- [What the guidance gives each stakeholder](./what-this-guidance-gives.md)
- [Different Types of Builders](../reference/builders-metaphor.md)
- [YAGNI versus WGF](./design-before-build-and-wgf.md)
- [Example gallery](../examples/readme.md)
- [Developers Need to Know](../../agents/conventions/development/developers-need-to-know.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Development Constraints](../../agents/conventions/foundations/constraints.md)
- [Vertical Slices](../../agents/conventions/capabilities/slices.md)
- [Horizontal Flows](../../agents/conventions/capabilities/flows.md)
- [Startup and Discovery](../../agents/conventions/foundations/startup.md)
- [IQueryable and Governed Queryability](../../agents/conventions/foundations/iqueryable.md)
