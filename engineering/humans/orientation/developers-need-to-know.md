# What Developers Need to Know

This paper explains how developers turn a human or technical problem into a dependable system. It is about the order of thought, not a demand that every service use the same number of projects or the same framework.

The first question is not "Which endpoint and table do I need?" The first question is "What must this system know, and what must it reliably do?"

## Architecture is more than construction

Services, frameworks, persistence, deployment, startup and operations are the building work. They provide the concrete structure in which the system can run safely. That work matters, but it is not the whole purpose of architecture.

The building exists for the people, decisions, records, relationships and activities that live inside it. A system can have excellent infrastructure and still be architecturally wrong if it has modelled the wrong world.

Architecture begins by decomposing the stated problem until the important things can be recognised. What is a distinct thing? What makes it the same thing over time? What can happen to it? Which things relate to it? Who may act on it? What must be remembered, protected, proved or recovered?

Those answers reveal the ontological elements of the relevant domain. Contracts then protect their relationships so that the parts can be isolated, tested and changed without silently changing the meaning of the whole.

## Domain thinking applies everywhere

Domain thinking is not reserved for customer-facing business concepts. Every coherent problem space has a domain.

Business domains describe the people, records, decisions, relationships and outcomes the service exists to support. Technical and platform domains describe what the service needs in order to exist and remain dependable: configuration, identity, access, persistence, messaging, startup, diagnostics, caching, deployment and recovery.

Each domain has concepts, boundaries, capabilities, contracts, policies, lifecycles and failure modes. Each needs translation at its boundaries. Infrastructure is not a domain-free basement. It is a set of technical domains whose meaning must also be understood and protected.

The Domain model is logical in architecture because it is independent of a particular transport, vendor or storage implementation. It is conceptual within its problem space because it is how the system knows what that problem means.

Do not copy a current screen, team structure, vendor API or framework object into the domain model. Do not invent an elegant model without evidence either. Abstract from real business or technical needs so that today's local arrangement does not become tomorrow's system constraint.

## Contracts protect meaning

A contract says what a part provides, what another part may rely on and how failure is expressed. It gives a capability a protected relationship with the rest of the system.

Contractual thinking helps developers isolate and test. It also makes replacement possible. A caller can rely on the contract without depending on the database, framework, vendor or current internal arrangement behind it.

The contract should have a responsible boundary, a clear lifecycle, security and data rules, and an observable failure policy. A type or interface is not valuable merely because it exists. It is valuable when it protects a meaningful capability or relationship.

## Place the capability

A Logical Deployment Module, or LDM, is a deployment and ownership boundary. It identifies a coherent purpose, contracts, data and operational responsibility. It is not automatically a DDD bounded context, aggregate or single domain.

The LDM may contain business domains, technical domains or both. Keep those domain boundaries explicit. Do not use a repository or project boundary as a substitute for understanding the problem.

A useful starting structure is to establish a Systems LDM for the service foundations, then develop the business need in a related business LDM. The Systems LDM might begin with User, Role, Permission and Settings domains. Person and Group may also belong there, or may deserve their own LDM when their complexity, reuse, ownership or lifecycle justifies it. This is an example of a reasoning path, not a fixed decomposition.

For a request-oriented business LDM, the team may begin with conceptual DTOs and view models that describe what each consumer needs. It then develops the logical ontological model in the code: the durable concepts, identities, relationships, states and rules that the system must understand. The physical persistence model and ORM mappings are derived from that logical model, rather than allowing a screen or table to define it accidentally. The amount of structure should match the team's capability and the service's consequences. Too little structure creates rework; too much structure can become a design the organisation cannot operate.

The Systems LDM can be simple at first. The important thing is to preserve the ability to keep unrelated responsibilities separate. A service that has only one module today can still use a modular structure so that later growth does not force unrelated concerns into one undifferentiated project.

Read [Logical Deployment Modules](../development/ldms.md) for the human explanation of the boundary, [LDM Layers and Contents](../development/layers.md) for what belongs inside it, and [System LDM Services](../development/services.md) for the first shared services. [Constants](../development/constants.md) and [Contracts](../development/contracts.md) explain two small but important parts of that structure in more depth.

Use the onion direction to protect the model:

```text
UI or API interface
        |
        v
Application and consumer views
        |
        v
Domain model for the relevant problem space
        ^
        |
Infrastructure implements domain contracts
```

The outer parts may depend on inner contracts. The domain model must not depend on transport, persistence, vendor or framework details. Physical entities and framework types stay at the relevant edges, with explicit mappings where their responsibilities differ.

## Build a vertical slice

A vertical slice is one complete capability. It travels from an external boundary through application coordination and domain rules to the state or external effect it owns. Read [Vertical Slices: Common Shafts](../development/vertical-slices.md) for the common managed-record, read-only, append-only, command, relationship, document, decision, integration and notification shapes.

A slice normally includes its contract, logical model, application orchestration, validation, authorisation, audit, mapping, persistence or integration policy and tests. It is a unit of delivery and testability, not merely a folder or class.

Use governed query contracts for reads. Keep writes and state transitions explicit. Create, submit, recommend, approve, reject, publish and close are not automatically the same operation as editing a field.

Lifecycle is also a capability decision. When personal information is no longer needed, do not assume that the correct implementation is to delete the whole digital record. Start with [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md), then use the [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md) paper when the legal or technical assessment needs more depth. The decision must cover free text, linkage keys, indexes, caches, exports, events, replicas and backups.

## Coordinate flows without stealing ownership

A horizontal flow coordinates several capabilities into an outcome. It may involve actors, decisions, hand-offs, waiting, retries, compensation or multiple stateful steps.

The flow owns orchestration policy. The participating slices retain their own meaning, rules, permissions, data and state transitions. A flow may call a slice, but it must not quietly become the owner of the slice's business or technical rules.

Slices use shared capabilities such as diagnostics, tracing, settings, identity, authorisation, storage, mapping, caching and audit. Read [Cross-Cutting Services](../development/cross-cutting-services.md) for the boundary between a shared System LDM service and the business meaning owned by a slice.

## Interfaces are consumers

A user interface supports human interaction. An API supports application-to-application interaction. Both are ways of entering or using a capability, not separate owners of its meaning.

Their request and response shapes may differ because their consumers differ. Both should invoke an application contract, use the responsible boundary and preserve the relevant domain rules, authorisation, audit and lifecycle decisions.

Do not let a screen, endpoint, vendor API or transport model become the domain model by accident.

## Work has phases and execution modes

The same capability must be understood across time:

- **Deployment** installs a known version of code, configuration references, infrastructure and compatible schema changes.
- **Startup** composes one running instance, validates it, discovers or registers participants, prepares dependencies and establishes readiness.
- **Operation** reacts to requests and processes work.

During operation, a reaction may be synchronous or asynchronous. Use synchronous work when the caller needs a bounded result immediately. Use a durable queue when work is long-running, independently retryable, temporarily unavailable or must continue after the caller disconnects.

Queued work is not fire-and-forget. Define identity, correlation, status, retry and backoff, idempotency, cancellation or expiry, poison-message handling, reconciliation and operator visibility.

## Design before construction spreads assumptions

Design completeness and build completeness are different. A capability may be designed, placed, contracted and deliberately deferred while another capability is built first.

The known structure should include the domain meaning, boundary, contracts, dependencies, security, lifecycle, mappings, persistence intention, tests and operational obligations. The novel parts are usually the organisation's language, relationships, decisions, workflow detail and presentation shape.

Build one real vertical slice through the prepared structure. Let evidence refine the abstractions. Do not make every future capability pay for a missing boundary, and do not build speculative infrastructure without a real need.

## A practical developer check

Before calling a capability ready, be able to point to:

- its ontological meaning and responsible domain;
- its owning LDM or boundary;
- its contracts and mappings;
- its application coordination and vertical slice;
- its security, data and lifecycle rules;
- its persistence or external effect policy;
- its startup and operational participation;
- its synchronous or queued execution behaviour;
- its tests, failure paths and recovery evidence; and
- its deliberate deferrals.

When one of these is missing, raise the design gap. Do not silently encode it in the first model, table, endpoint or framework default.

## Related guidance

- [Current State](./current-state.md)
- [The Structure Before the Feature](./the-structure-before-the-feature.md)
- [What This Guidance Gives](./what-this-guidance-gives.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
- [Human Development Guidance](../development/readme.md)
- [Logical Deployment Modules](../development/ldms.md)
- [LDM Layers and Contents](../development/layers.md)
- [Vertical Slices: Common Shafts](../development/vertical-slices.md)
- [Cross-Cutting Services](../development/cross-cutting-services.md)
- [Constants](../development/constants.md)
- [Contracts](../development/contracts.md)
- [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md)
- [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md)
- [System LDM Services](../development/services.md)
- [Vertical Slices](../../agents/conventions/capabilities/slices.md)
- [Horizontal Flows](../../agents/conventions/capabilities/flows.md)
- [Operations Conventions](../../agents/conventions/development/operations.md)
- [System LDM Service Readiness Reference](../reference/platform-services.md)
- [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md)