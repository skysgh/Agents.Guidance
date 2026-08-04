# Guidance for Tech Leads

Technical leadership begins with a map made by architecture. The architect identifies the groups and systems that use the service, the sites that serve their responsibilities, the platform capabilities the service needs and the downstream obligations created by its outputs. The tech lead turns that map into an implementable service shape and keeps the team from losing the relationships while construction is staged.

The lead's job is more than translating boxes into projects. The lead recognises the architect's abstraction, checks whether it is achievable with the available team, technology, dependencies and constraints, and plots the path to implementation. That includes deciding what must be settled before construction, what can be safely deferred, which foundations come first and what evidence will show that the structure is ready. The aim is to help the current business unit adapt over time and to keep the service resilient when the wider organisation changes around it.

Keep the reason for the service in view while planning the construction. The service has a mission and intended outcomes, named stakeholders and connected systems, and a place within wider organisational responsibilities, policies and obligations. The delivery path is successful only when it preserves those relationships, not merely when the code can be compiled and deployed.

When the service map is new or incomplete, [Guidance for System Design Architects](./guidance-for-system-design-architects.md) explains the decisions that need to come first. This page starts after that map exists and explains how to translate it into capabilities, domains, logical deployment modules, implementation areas, components, platform services, contracts and delivery evidence.

Keep the delivery map wider than the service project. [Deliverable Systems](../reference/catalogues/deliverable-systems.md) distinguishes the delivery, service, consumer, testing and cross-system test-context systems. [Deliverables](../reference/catalogues/deliverables.md) identifies the data, content, registrations, discovery surfaces, dependencies and operational evidence that the team must coordinate. [Registries](../reference/catalogues/registries.md) separates enterprise-referred options and constraints from project-produced records of the components, expiries, schedules, releases, risks and evidence the team actually owns.

The scale handoff is deliberate: the architect defines stakeholder-facing **components** and LDM boundaries; the tech lead defines **logical building blocks** within those boundaries; developers express the blocks through **code types and design patterns**. A logical building block is not automatically one class, and a component is not automatically a UI class.

The handoff must also preserve the [Enduring](../reference/glossary.md#enduring) versus [Transient](../reference/glossary.md#transient) distinction. Before selecting physical building blocks, confirm which identities outlast a membership, appointment, assignment or workflow and which relationships need their own dates, state, history, authority, migration and evidence. See [Entity Lifecycle Patterns](../reference/catalogues/entity-lifecycle-patterns.md).

The service also sits inside wider systems of enterprise process, policy, regulation and law. [Systems Within Systems](./systems-within-systems.md) and [Legal and Regulatory Context](./legal-context.md) explain why privacy, data protection, storage, audit, retention and recovery are obligations carried into technical delivery. The [Regulatory and Obligation Domains](../reference/catalogues/regulatory-obligations.md) catalogue provides the recurring outcome vocabulary, and its [checklist](../reference/checklists/regulatory-obligations.md) helps turn the applicable sources into delivery evidence. The architect makes those obligations visible; the tech lead makes them technically real and keeps them visible during implementation.

The same applies to quality. The tech lead connects intended outcomes to the data and system qualities that must enable them, then makes the required evidence visible in contracts, tests, deployment and operation. [Quality Perspectives](../reference/catalogues/qualities.md) explains that relationship across quality in use, data quality and system or software product quality.

Security readiness includes both the running service and the system that delivers it. Use the [Security at Rest Checklist](../reference/checklists/security-at-rest.md) and [Security in Transit Checklist](../reference/checklists/security-in-transit.md) to turn classification, access, encryption, key and certificate ownership, expiry, rotation, copies, transport, evidence and recovery into delivery decisions. The [External Dependencies](../reference/catalogues/external-dependencies.md) catalogue includes the code repository, pipeline, registries, Domain Registry, DNS, certificate authority and hosting control plane. The lead should make the release path, rollback path, urgent security-fix path and recovery path testable.

The tech lead also chooses the language and framework path that will make the architect's logical design achievable. Teams often begin with the language they know best, which is a reasonable starting point rather than the whole decision. [Selecting a Language and Framework](./language-and-framework-selection.md) explores how execution boundary, workload, security, maintainability, operational skill, deployment, recovery and the capabilities of the engineers who will build and support the service shape that choice.

For data deletion decisions, [Data Deletion Guidance](../development/data-deletion-guidance.md) sets out the preferred preservation outcome: irreversible anonymisation or de-identification where the applicable rule allows it, while keeping technical erasure available where preservation cannot remain lawful. [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md) provides the deeper analysis.

## Receive the architecture map

The architect's interface and dependency maps give the delivery team a useful place to begin. They bring together the stakeholder groups and connected systems, the sites that serve each responsibility, the flows, views and components that express important journeys, and the capabilities and domains that give those journeys their meaning. They also make visible which platform and external dependencies are required, optional, authoritative or derived, which runtime and delivery dependencies support operation, release, security maintenance, repair and recovery, and what classification, lifecycle, failure and recovery obligations follow the data across each boundary.

When an answer is missing, record the missing decision and its consequence. Do not silently fill the gap with a controller, database table, provider SDK or local helper. The [Engineering Catalogues](../reference/catalogues/readme.md) provide the shared vocabulary for resolving the next question.

## Turn the map into a service shape

The tech lead translates the architecture map through a deliberate sequence. Each step gives the next one a boundary to work with.

### From sites to flows and components

A site is a curated surface for a responsibility. It is not a platform choice and it is not a security control. A site is made from flows; a flow is made from views; a view is made from collection, input and output components. Use this structure to keep an experience understandable without allowing the interface to become the business model.

The same backend capability may support more than one site. The same site may coordinate several capabilities. That reuse is healthy when the contracts and responsibilities remain clear. It becomes dangerous when a flow starts owning rules that belong to a capability or when a component writes directly to storage.

The [Sites](../reference/catalogues/sites.md) catalogue and [Sites, Flows, Views and Components](../reference/catalogues/sites-flows-views-components.md) guide the interface shape. The [Sites and Interfaces Checklist](../reference/checklists/sites-and-interfaces.md) turns that shape into review questions for the team.

### From flows to capabilities and domains

Name the capabilities required by the flows before naming the classes that will implement them. A capability is a useful system ability with a clear purpose, contract and boundary. A domain gives related capabilities a coherent meaning and protects the rules that belong together.

Keep a flow as a coordinator of a journey. It may call several capabilities, but it should not absorb their rules merely because the journey is visible in one screen or endpoint. Keep domain rules close to the concepts that make them meaningful. [Domains and Capabilities](../reference/catalogues/domains-and-capabilities.md) explains the distinction, while the [Domains and Capabilities Checklist](../reference/checklists/domains-and-capabilities.md) provides review prompts for exposing accidental coupling.

### From capabilities to LDMs

Group components into logical deployment modules when they share a meaningful delivery boundary. An LDM is a logical package of components delivered together. It is not automatically an independently deployable service, an ownership boundary or a database boundary.

The tech lead should be able to explain why each component is in its LDM, what contract the LDM exposes, which dependencies it requires and what is delivered together. A shared deployment can contain several well-separated LDMs. Separate deployments cannot compensate for unclear responsibilities. The [Logical Deployment Modules](../reference/catalogues/ldms.md) catalogue explains the boundary, while the [Logical Deployment Modules development guidance](../development/ldms.md) explains what that boundary means for delivery before project or assembly boundaries are created.

### From LDMs to layers and logical building blocks

Within each LDM, keep model types distinct from implementation responsibilities. The consumer-facing interface physically represents the interaction the capability offers. Application and domain code physically implements and coordinates the logical model. Persistence and external-effect code connects to storage, transports, providers and other infrastructure.

This separation prevents a table, ORM entity, HTTP payload or vendor SDK from silently defining the domain. It also gives developers a place to put translation and failure handling. The [Conceptual, Logical and Physical Models](../reference/catalogues/conceptual-logical-physical-models.md) catalogue explains the model types; [Logical Layers](../reference/catalogues/logical-layers.md) explains the implementation responsibilities.

At this level, name the logical building blocks needed by each responsibility rather than starting with classes. [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md) describes services, state-management coordinators, repositories, brokers, providers, registries, mappings, validators, handlers, models and contracts. The tech lead should expect these blocks to have clear layer placement, contracts and dependency direction, while leaving concrete language and framework choices to development.

The [Logical Layers](../reference/catalogues/logical-layers.md) catalogue explains the distinction, and [LDM Layers and Contents](../development/layers.md) describes how the logical package can express it in code.

## Establish platform readiness after the shape is clear

The platform is the technical ground on which the service runs. It is not a bag of shared utilities and it is not the same thing as a site. Once the service shape and its obligations are understood, establish the platform capabilities that make the later capabilities safe and observable.

The default readiness sequence is:

1. Configuration
2. Diagnostics
3. Key Vault and secret resolution
4. Storage foundations
5. Settings
6. Routing
7. Mapping
8. Startup reflection and contract-based discovery
9. EF schema and model contribution
10. Local caching
11. Remote caching
12. Templating
13. Notifications, including SMTP
14. Local user authentication
15. Remote user authentication
16. Remote service authentication
17. Authorisation
18. Auditing
19. Queuing
20. Workflow

This is a dependency-led default, not a demand that every service implement every item or that all work happen in one irreversible pass. A small service may not need remote caching, templating, SMTP, queues or workflow. Work may proceed in parallel once contracts and lower-level dependencies are understood. The sequence shows what must be established before a dependent capability can be treated as a reliable platform service.

The human explanation in [System LDM Services](../development/services.md) and the detailed purpose and readiness questions in [System LDM Service Readiness Reference](../reference/platform-services.md) support this sequence. A capability is **Available** when its contract, responsible boundary, registration, readiness signal and tests are known. It is **Planned** when its boundary, contract and delivery condition are recorded. It is **Not applicable** when the reason is explicit and fits the service's consequences. It is **Missing** when the gap is visible, assigned and treated as a dependency rather than hidden in feature code.

## Make storage and dependencies explicit

The architect's dependency map becomes a technical lead's delivery plan. For each dependency, name the contract, responsible boundary, data crossing it, authority, classification, lifecycle, availability expectation, recovery behaviour and evidence that proves it is ready.

Storage choice belongs here, after the logical information and its access needs are understood. [Storage Types](../reference/catalogues/storage-types.md) gives the shared vocabulary for key-value, relational, document, media and derived storage. A service may use relational storage for authoritative transactional state, media storage for attachments, key-value storage for settings or idempotency records, document storage for a bounded document representation and a search index for discovery. That combination is coherent only when authority, mapping, consistency, failure, recovery, classification and deletion are explicit.

The [External Dependencies](../reference/catalogues/external-dependencies.md) catalogue, together with the [External Dependency Checklist](../reference/checklists/external-dependencies.md) and the data deletion guidance, helps keep those copies visible when a dependency crosses the boundary. A physical store should not become the domain model by accident, a cache should not become a second source of truth, and a media URL should not be mistaken for authorisation. Indexes, queues, exports, reports, replicas, archives and backups also belong in the lifecycle decision when personal or regulated information is copied.

The delivery path needs the same explicit treatment. Confirm that source, build actions, dependencies, artifacts, infrastructure changes, deployment permissions, domain and DNS changes, certificate renewal and hosting access are owned, reviewable, auditable and recoverable. A healthy runtime cannot be maintained safely when the system that builds or reaches it is opaque or unavailable.

## Preserve the boundary in code

Separation of concerns, high cohesion and low coupling are the tests applied to every translation from the map into code. A view should not own provider concerns. A flow should not become the storage boundary. A domain rule should not depend on a transport payload. A platform service should not quietly acquire business meaning.

Use named patterns when they make one of those responsibilities clearer. [Patterns](../reference/catalogues/patterns.md) explains OOP, GRASP, SOLID, GoF, DDD and architectural patterns in one place. The tech lead does not need to impose a pattern catalogue on every class. They do need to recognise when a team is using a name as a substitute for a design decision, or when a small amount of indirection would protect a real variation.

The practical questions are simple: who has the information needed for this responsibility, which object or component should coordinate it, which contract is stable, where does variation belong and which dependency should be replaceable? GRASP and SOLID help developers answer those questions inside the boundaries already established by the architecture. They do not replace the decisions about sites, capabilities, domains, LDMs or layers.

## Prove the design with a vertical slice

Choose one representative vertical slice and follow it through the shape described by the architect. Start at the site, flow, view or system interface. Follow the contract through mapping, authentication, authorisation, application and domain rules, storage or an external effect, audit, diagnostics and recovery. If it queues work or participates in a workflow, follow durable identity, status, retry, correlation and operator visibility as well.

The slice should prove that the platform services are actually invoked. A discovered mapper, schema contributor, cache policy or notification provider that is never used is not a working platform capability. A startup log that says only "started" is not evidence that required composition succeeded. A test that bypasses the boundary may prove a function but not the service design.

The [Vertical Slices](../development/vertical-slices.md), [Contracts](../development/contracts.md) and [Cross-Cutting Services](../development/cross-cutting-services.md) guidance gives this proof its shape. The result should make the next slice easier to build because its boundaries, dependencies and failure choices are now concrete.

## Manage gaps and divergence

When a required capability is not ready, make the gap visible at the boundary that needs it. Do not allow a feature team to create a private copy merely because the shared capability is inconvenient or incomplete. First identify the contract, the missing readiness evidence, the affected slice and the condition for convergence.

A local exception may be correct. Record why it is necessary, what risk it carries, who is responsible for it, how it will be observed and what would allow the service to return to the common capability. A deliberate omission is architecture evidence. Call it technical debt only when it has an owner, a repayment condition and a credible source of capacity to repay it. An omission hidden in feature code, or a compromise knowingly left for future people to pay, is [technical theft](../reference/glossary.md#technical-theft), not a neutral form of platform debt.

## Keep the map alive

The tech lead protects coherence as the design changes. When a capability, dependency, storage representation or downstream obligation changes, update the relevant map, contract, readiness evidence, tests and operational material together. When a new platform capability is introduced or retired, update its purpose, dependency position, responsible boundary and inventory.

The aim is not to block delivery until an ideal platform exists. The aim is to keep each staged decision connected to the known whole, so that later work can extend the service without rediscovering its responsibilities from scattered code.

## Related guidance

- [Stakeholder Analysts](../stakeholders/business-analysts/readme.md)
- [Product Owners](../stakeholders/product-owners/readme.md)
- [Shared Requirements](../shared/requirements.md)
- [Technical Lead Route](../stakeholders/technical-leads/readme.md)
- [Architect Route](../stakeholders/architects/readme.md)
- [Guidance for System Design Architects](./guidance-for-system-design-architects.md)
- [Guidance for Developers](./guidance-for-developers.md)
- [Engineering Catalogues](../reference/catalogues/readme.md)
- [Patterns](../reference/catalogues/patterns.md)
- [Storage Types](../reference/catalogues/storage-types.md)
- [Sites](../reference/catalogues/sites.md)
- [Sites, Flows, Views and Components](../reference/catalogues/sites-flows-views-components.md)
- [External Dependencies](../reference/catalogues/external-dependencies.md)
- [Domains and Capabilities](../reference/catalogues/domains-and-capabilities.md)
- [Logical Deployment Modules](../reference/catalogues/ldms.md)
- [Logical Layers](../reference/catalogues/logical-layers.md)
- [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md)
- [Quality Perspectives](../reference/catalogues/qualities.md)
- [Regulatory and Obligation Domains](../reference/catalogues/regulatory-obligations.md)
- [Regulatory and Obligation Checklist](../reference/checklists/regulatory-obligations.md)
- [Sites and Interfaces Checklist](../reference/checklists/sites-and-interfaces.md)
- [External Dependency Checklist](../reference/checklists/external-dependencies.md)
- [Security at Rest Checklist](../reference/checklists/security-at-rest.md)
- [Security in Transit Checklist](../reference/checklists/security-in-transit.md)
- [Logical Deployment Modules](../development/ldms.md)
- [LDM Layers and Contents](../development/layers.md)
- [Vertical Slices](../development/vertical-slices.md)
- [Contracts](../development/contracts.md)
- [Cross-Cutting Services](../development/cross-cutting-services.md)
- [System LDM Services](../development/services.md)
- [System LDM Service Readiness Reference](../reference/platform-services.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Startup and discovery](../../agents/conventions/foundations/startup.md)
- [Operations](../../agents/conventions/development/operations.md)
- [Data Protection](../../agents/conventions/foundations/data-protection.md)
- [Data Deletion Guidance](../development/data-deletion-guidance.md)
- [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md)
