# Engineering Guidance: Human Start Here

This is the human introduction to the portable engineering guidance. It is deliberately more explanatory than the compact agent entry point. Read it when you want to understand why the guidance exists, what problem it addresses, and how the documents fit together.

## The short version

Most enterprise application structures are not unknown. After decades of building systems, the recurring engineering problems are visible:

- boundaries between consumers, application logic, domain meaning and storage;
- contracts between those boundaries;
- objects that implement those contracts;
- services that compose the objects;
- registries and startup lifecycle that assemble the participants;
- access, security, classification and audit;
- persistence schema, mapping and query policy; and
- vertical capabilities and horizontal journeys.

What is usually novel is the organisation's domain language, conceptual relationships, decisions, workflow detail and presentation shape. The reusable engineering structure should be designed before feature coding. The novel business meaning should be explored inside that structure.

This is the governing idea:

> Design the knowable. Build it in stages. Discover the novel inside the formwork.

Design completeness does not require build completeness. A capability may be deliberately deferred, but its intended place, stewarding boundary, contract, dependencies and lifecycle should not be left for a future team to invent from fragments.

## What goes first?

Use two short reminders when planning work:

- **DBB: Design Before Build.** Define the known structure, stewardship, dependencies, security and lifecycle before implementation spreads assumptions across code.
- **WGF: What Goes First?** Once the intended structure is clear, decide which part should be built first based on value, risk, dependency, evidence and available capacity.

DBB does not mean build everything before learning. WGF does not mean design only the first ticket. Together they separate architectural understanding from construction priority. The design should be achievable from the available problem and system evidence; it should not wait for a particular person to become available.

WGF asks two questions for each proposed inclusion or omission:

1. What consequence follows if we include this now?
2. What consequence follows if we omit or defer it?

The answer should consider value, risk, dependency, security, reversibility, operational cost, evidence gained and the effect on later construction. An omission is a decision with consequences, not the absence of a decision.

## Why read the problem first?

A team is more likely to use guidance when it recognises the problem it is meant to solve. Start with [the current state and recurring failure patterns](./current-state.md), then read [what the guidance gives each stakeholder](./what-this-guidance-gives.md).

After that, use the [developer orientation](../../agents/conventions/developers-need-to-know.md) for the practical mental model and the [work instructions](../../agents/conventions/.md) to select the detailed conventions relevant to a task.

## The two reading speeds

These documents serve two different needs:

- **Human orientation** explains the problem, the reasoning and the vocabulary in plain language. It is intentionally readable and may be longer.
- **Agent and implementation guidance** states the compact rules needed to make or review a change. It is intentionally selective so an agent does not load every explanation for every task.

The short agent path is [agents.md](../../../agents.md). It is not a replacement for the human introduction. It is a loading contract.

## The structural model

Think of a system as a building:

- contracts are the structural frame;
- objects are the contract-bearing parts;
- services compose and operate those parts;
- registries and startup discovery assemble the known participants;
- vertical slices carry owned capabilities through the layers; and
- horizontal flows coordinate capabilities into journeys.

The aim is not to build every room at once. The aim is to know where each room belongs and what structure it will connect to before different teams build different interpretations.

## A shared act of seeing

This guidance is not architecture standing above developers, testers, business analysts or operations. No single role sees the whole system alone:

- business analysis supplies domain meaning, decisions and language;
- developers test whether contracts can actually be implemented;
- testers expose whether the claimed boundaries are real;
- operations exposes lifecycle, readiness, recovery and support needs;
- security and assurance expose protection and evidence obligations; and
- architecture preserves coherence across the whole structure.

The design becomes stronger when these views meet. The guidance gives each role a way to contribute to the same design, not a list of instructions for everyone else to obey.

The [example gallery](../examples/readme.md) shows the same movement through several ordinary situations. Start with the example that feels most familiar.

## Where to go next

- [Current state and recurring failure patterns](./current-state.md)
- [What the guidance gives each stakeholder](./what-this-guidance-gives.md)
- [YAGNI versus WGF](./design-before-build-and-wgf.md)
- [Example gallery](../examples/readme.md)
- [Developers Need to Know](../../agents/conventions/developers-need-to-know.md)
- [Development Principles](../../agents/conventions/principles.md)
- [Development Constraints](../../agents/conventions/constraints.md)
- [Vertical Slices](../../agents/conventions/slices.md)
- [Horizontal Flows](../../agents/conventions/flows.md)
- [Startup and Discovery](../../agents/conventions/startup.md)
- [IQueryable and Governed Queryability](../../agents/conventions/iqueryable.md)
