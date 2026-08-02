# Guidance for Developers

This paper explains how developers turn a prepared capability into a dependable part of a service. It is about finding the right responsibility and keeping it clear while the code grows. It does not require every service to use the same number of projects or the same framework.

You are not being asked to invent the building from the first brick. The architect has separated the durable responsibility from the current business arrangement, and the technical lead has worked out an achievable path through the real constraints. Your job is to implement the part in front of you so it serves its responsibility, connects through the agreed boundaries and remains adaptable when the business unit or the organisation changes. If the prepared design cannot support the work, raise that gap rather than quietly turning the first screen, table or provider into the permanent structure.

As you begin local work, the journey around the capability gives useful context. It helps to know why the service exists, what outcome or mission it supports, which stakeholders and connected systems depend on it, and what responsibility the organisation carries around it. You do not need to hold the whole architecture in your head. You need enough context to notice when a local implementation would change a stakeholder promise, cross an organisational boundary, weaken an obligation or make a future change unnecessarily expensive. [Systems Within Systems](./systems-within-systems.md) explains the wider context, [Stakeholder Roles](../reference/catalogues/stakeholder-roles.md) explains whose knowledge and authority must remain visible and [Regulatory and Obligation Domains](../reference/catalogues/regulatory-obligations.md) names the recurring duties that may shape the capability.

The system affected by a change may be the user-facing runtime service, a distinct consumer system, the delivery system, the testing system, the cross-system test context or another deliverable. [Deliverable Systems](../reference/catalogues/deliverable-systems.md) and [Deliverables](../reference/catalogues/deliverables.md) explain why the repository or service runtime is not always the whole delivery. When the change handles stored information, credentials, media, links, network traffic, domains, DNS, certificates or delivery automation, the [Security at Rest Checklist](../reference/checklists/security-at-rest.md) and [Security in Transit Checklist](../reference/checklists/security-in-transit.md) turn that explanation into practical prompts.

The platform provides the technical ground. A site curates information and [capabilities](../reference/glossary.md#capability) for a responsibility. A site is a collection of flows, a flow is a collection of views, and a view is a collection of collection, input or output components. Those interface structures use capabilities from [Domains](../reference/glossary.md#domain). The domains and capabilities sit inside an LDM, and the LDM contains logical layers and logical building blocks. The scale handoff is deliberate: architects name components, technical leads name logical building blocks, and developers express those blocks through code types and design patterns.

The language and framework are part of that physical expression. Follow the decision recorded by the tech lead and raise evidence when the chosen runtime no longer fits the workload, security, support or recovery needs. [Selecting a Language and Framework](./language-and-framework-selection.md) explains the defaults and exception path.

When you receive a feature or defect, start from the capability and boundary already identified for it. Follow the path to the site, flow, view or system interface that needs it, then into the domain, LDM, logical layer and component that should carry the work. The [Engineering Catalogues](../reference/catalogues/readme.md) provide the shared vocabulary when that path is not yet familiar, and [Sites, Flows, Views and Components](../reference/catalogues/sites-flows-views-components.md) gives the interface structure more detail when it becomes part of the work.

## Keep the meaning visible

The code is not the purpose of the service. It is the working representation of people, records, decisions, relationships and activities that the service supports. A system can have excellent infrastructure and still be wrong if a screen, database table, framework object or vendor API has accidentally become the definition of the problem.

The team protects meaning by separating the conceptual language that people recognise from the logical model the system needs and the physical structures that make execution possible. The conceptual view may use familiar language that is imprecise or polysemous. The logical view does the harder work of distinguishing the things, identities, relationships, states and rules that must behave consistently. The physical view contains the code, transport, storage and infrastructure that implement those decisions.

One of the most important logical distinctions is [Enduring](../reference/glossary.md#enduring) versus [Transient](../reference/glossary.md#transient). Preserve enduring identity separately from transient membership, appointment, assignment, access, decision or workflow. A `StudentAt` relationship may translate the conceptual phrase "student at a school" while Person, School or Group and Location retain their own identity and lifecycle. Read [Entity Lifecycle Patterns](../reference/catalogues/entity-lifecycle-patterns.md) before changing the relevant domain, contract, mapping or persistence representation.

Developers help make that separation real. They use contracts and mappings so that a view does not become a domain model, a table does not become a business rule and a provider API does not become the service's vocabulary.

The same separation supports quality. The [Quality Perspectives](../reference/catalogues/qualities.md) catalogue explains how system qualities and data qualities enable the outcomes that people and organisations need to achieve in use, and what evidence developers help provide.

## Domain thinking applies everywhere

Domain thinking is not reserved for customer-facing business concepts. Every coherent problem space has a domain.

Business domains describe the people, records, decisions, relationships and outcomes the service exists to support. Technical and platform domains describe what the service needs in order to exist and remain dependable: configuration, identity, access, persistence, messaging, startup, diagnostics, caching, deployment and recovery.

Each domain has concepts, boundaries, capabilities, contracts, policies, lifecycles and failure modes. Each needs translation at its boundaries. Infrastructure is not a domain-free basement. It is a set of technical domains whose meaning must also be understood and protected.

The Domain model is a logical model because it is independent of a particular transport, vendor or storage implementation. Domain code is its physical representation, and it is conceptual within its problem space because it is how the system knows what that problem means.

Do not copy a current screen, team structure, vendor API or framework object into the domain model. Do not invent an elegant model without evidence either. Abstract from real business or technical needs so that today's local arrangement does not become tomorrow's system constraint.

## Contracts protect meaning

A contract says what a part provides, what another part may rely on and how failure is expressed. It gives a capability a protected relationship with the rest of the system.

Contractual thinking helps developers isolate and test. It also makes replacement possible. A caller can rely on the contract without depending on the database, framework, vendor or current internal arrangement behind it.

The contract should have a responsible boundary, a clear lifecycle, security and data rules, and an observable failure policy. A type or interface is not valuable merely because it exists. It is valuable when it protects a meaningful capability or relationship.

## Place the capability

The interface may already have a site, flow, view or component that needs the capability. Treat those as consumers of the capability rather than places to put its business rules. A collection component can present items, an input component can collect a value and an output component can present a result. None of them should become the authority for state transitions, permissions or persistence merely because the first request arrives through that surface.

The capability belongs in the domain that gives it meaning. Its application boundary coordinates the use case, its logical model expresses the relevant concepts and rules, and its physical implementation translates those decisions into storage or an external effect. The same capability may serve several sites with different views and contracts.

A Logical Deployment Module, or LDM, is a logical package whose components are delivered together as one package. It identifies a coherent purpose, contracts, data and responsibility for change. It is not automatically independently deployable, a DDD bounded context, an aggregate or a single domain.

The LDM may contain business domains, technical domains or both. Keep those domain boundaries explicit. Do not use a repository or project boundary as a substitute for understanding the problem.

A useful starting structure is to establish a Systems LDM for the service foundations, then develop the business need in a related business LDM. The Systems LDM might begin with User, Role, Permission and Settings domains. Person and Group may also belong there, or may deserve their own LDM when their complexity, reuse, responsibility or lifecycle justifies it. This is an example of a reasoning path, not a fixed decomposition.

For a request-oriented business LDM, the team may begin with conceptual DTOs and view models that describe what each consumer needs. It then develops the [logical ontological model](../reference/catalogues/conceptual-logical-physical-models.md#logical-model) in the code: the durable concepts, identities, relationships, states and rules that the system must understand. The physical persistence model and ORM mappings are derived from that logical model, rather than allowing a screen or table to define it accidentally. The amount of structure should match the team's capability and the service's consequences. Too little structure creates rework; too much structure can become a design the organisation cannot operate.

The Systems LDM can be simple at first. The important thing is to preserve the ability to keep unrelated responsibilities separate. A service that has only one module today can still use a modular structure so that later growth does not force unrelated concerns into one undifferentiated project. A service is one implementation shape for a capability or coordinator, not the starting point for discovering every responsibility.

The [Logical Deployment Modules](../reference/catalogues/ldms.md) catalogue and [Logical Deployment Modules development guidance](../development/ldms.md) explain the package. The [Logical Layers](../reference/catalogues/logical-layers.md) catalogue and [LDM Layers and Contents](../development/layers.md) describe what belongs inside it, while [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md) names the responsibility categories you may implement. [System LDM Services](../development/services.md) describes the first shared services, and [Constants](../development/constants.md) and [Contracts](../development/contracts.md) explain two small but important parts of that structure in more depth.

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

## Keep code responsibilities clear

Separation of concerns, high cohesion and low coupling are not just architecture words. They are daily coding tests. Keep code that changes for the same reason close together. Keep unrelated reasons for change apart. Make the relationships between separate responsibilities explicit and small.

[GRASP](../reference/catalogues/patterns.md#grasp) gives names to useful ways of assigning responsibility between objects. [SOLID](../reference/catalogues/patterns.md#solid) gives names to ways of keeping those objects focused, substitutable and safe to extend. You do not need to memorise the names before applying the ideas. They are useful when a component is becoming convoluted, when a class needs information that belongs elsewhere or when a small change forces unrelated callers to change.

A service is one way to package cohesive behaviour. A repository expresses governed persistence access. A broker crosses an external boundary. A presenter prepares output. A coordinator sequences a journey. A registry manages participants or definitions. A constant protects stable shared meaning. A contract protects a relationship that another part of the system relies on. The [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md) catalogue brings these categories together, so the code shape can follow the responsibility rather than forcing every responsibility into a class called a service.

## Build a vertical slice

A vertical slice is one complete capability. It travels from an external boundary through application coordination and domain rules to the state or external effect controlled by its responsible boundary. [Vertical Slices: Common Shafts](../development/vertical-slices.md) describes common managed-record, read-only, append-only, command, relationship, document, decision, integration and notification shapes.

A slice normally includes its contract, logical model, application orchestration, validation, authorisation, audit, mapping, persistence or integration policy and tests. It is a unit of delivery and testability, not merely a folder or class.

Use governed query contracts for reads. Keep writes and state transitions explicit. Create, submit, recommend, approve, reject, publish and close are not automatically the same operation as editing a field.

Lifecycle is also a capability decision. When personal information is no longer needed, do not assume that the correct implementation is to delete the whole digital record. Start with [Data Deletion Guidance](../development/data-deletion-guidance.md), then use the [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md) paper when the legal or technical assessment needs more depth. The decision must cover free text, linkage keys, indexes, caches, exports, events, replicas and backups.

## Coordinate flows without taking over responsibility

A horizontal flow coordinates several capabilities into an outcome. It may involve actors, decisions, hand-offs, waiting, retries, compensation or multiple stateful steps.

The flow carries orchestration policy. The participating slices retain their own meaning, rules, permissions, data and state transitions. A flow may call a slice, but it must not quietly become responsible for the slice's business or technical rules.

Slices use shared capabilities such as diagnostics, tracing, settings, identity, authorisation, storage, mapping, caching and audit. [Cross-Cutting Services](../development/cross-cutting-services.md) explains the boundary between a shared System LDM service and the business meaning carried by a slice.

## Interfaces are consumers

A user interface supports human interaction. An API supports application-to-application interaction. Both are ways of entering or using a capability, not separate authorities for its meaning.

Their request and response shapes may differ because their consumers differ. Both should invoke an application contract, use the responsible boundary and preserve the relevant domain rules, authorisation, audit and lifecycle decisions.

Do not let a screen, endpoint, vendor API or transport model become the domain model by accident.

## Work has phases and execution modes

The same capability must be understood across time. The delivery system turns reviewed source, dependencies, configuration and infrastructure definitions into a known version of code and deploys it. Deployment installs that version together with compatible schema changes and references. Startup composes one running instance, validates it, discovers or registers participants, prepares dependencies and establishes readiness. Operation reacts to requests and processes work.

During operation, a reaction may be synchronous or asynchronous. Use synchronous work when the caller needs a bounded result immediately. Use a durable queue when work is long-running, independently retryable, temporarily unavailable or must continue after the caller disconnects.

Queued work is not fire-and-forget. Define identity, correlation, status, retry and backoff, idempotency, cancellation or expiry, poison-message handling, reconciliation and operator visibility.

## Design before construction spreads assumptions

Design completeness and build completeness are different. A capability may be designed, placed, contracted and deliberately deferred while another capability is built first.

The known structure should include the domain meaning, boundary, contracts, dependencies, security, lifecycle, mappings, persistence intention, tests and operational obligations. The novel parts are usually the organisation's language, relationships, decisions, workflow detail and presentation shape.

Build one real vertical slice through the prepared structure. Let evidence refine the abstractions. Do not make every future capability pay for a missing boundary, and do not build speculative infrastructure without a real need.

## A practical developer check

Before calling a capability ready, you should be able to point to its ontological meaning and responsible domain, its responsible LDM or boundary, its contracts and mappings, its application coordination and vertical slice, its security, data and lifecycle rules, its persistence or external-effect policy, its startup and operational participation, its synchronous or queued execution behaviour, its tests, failure paths and recovery evidence, its delivery path and its deliberate deferrals. The [Domains and Capabilities Checklist](../reference/checklists/domains-and-capabilities.md), [Security at Rest Checklist](../reference/checklists/security-at-rest.md) and [Security in Transit Checklist](../reference/checklists/security-in-transit.md) provide the prompts without interrupting the explanation here.

When one of these is missing, raise the design gap. Do not silently encode it in the first model, table, endpoint or framework default.

## Related guidance

- [Stakeholder Analysts](../stakeholders/business-analysts/readme.md)
- [Product Owners](../stakeholders/product-owners/readme.md)
- [Shared Requirements](../shared/requirements.md)
- [Developer Route](../stakeholders/developers/readme.md)
- [Technical Lead Route](../stakeholders/technical-leads/readme.md)
- [Architect Route](../stakeholders/architects/readme.md)
- [Current State](./current-state.md)
- [The Structure Before the Feature](./the-structure-before-the-feature.md)
- [What This Guidance Gives](./what-this-guidance-gives.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
- [Human Development Guidance](../development/readme.md)
- [Logical Deployment Modules](../development/ldms.md)
- [LDM Layers and Contents](../development/layers.md)
- [Logical Deployment Modules](../reference/catalogues/ldms.md)
- [Logical Layers](../reference/catalogues/logical-layers.md)
- [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md)
- [Quality Perspectives](../reference/catalogues/qualities.md)
- [Regulatory and Obligation Domains](../reference/catalogues/regulatory-obligations.md)
- [Vertical Slices: Common Shafts](../development/vertical-slices.md)
- [Cross-Cutting Services](../development/cross-cutting-services.md)
- [Constants](../development/constants.md)
- [Contracts](../development/contracts.md)
- [Data Deletion Guidance](../development/data-deletion-guidance.md)
- [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md)
- [System LDM Services](../development/services.md)
- [Vertical Slices](../../agents/conventions/capabilities/slices.md)
- [Horizontal Flows](../../agents/conventions/capabilities/flows.md)
- [Operations Conventions](../../agents/conventions/development/operations.md)
- [System LDM Service Readiness Reference](../reference/platform-services.md)
- [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md)