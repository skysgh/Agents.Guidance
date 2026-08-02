# Guidance for System Design Architects

System design architecture is the responsibility of understanding the whole system that a service must support and making its important boundaries visible. The whole is larger than the business capability and larger than the code repository. It includes the people and connected systems that need the service, the platforms through which it is delivered, the sites that curate its capabilities and the dependencies and obligations that continue beyond it.

The architect's central act is abstraction. A business unit may be the only customer today, but its work will change and the organisation around it may later merge departments, split responsibilities or move the capability to another group. The architect separates those durable responsibilities from the current arrangement so the service can adapt without being rebuilt from scratch. The test of another possible tenant comes later; it is evidence that the structure is not trapped inside today's arrangement, not the reason to ignore the current customer.

## Integrate specialist knowledge; do not impersonate it

The system design architect is an integrator and facilitator, not the organisation's universal IT SME. The architect should identify the specialist responsibilities that affect the design, bring the right people into the work and make their boundaries and evidence visible. The architect must not speak for Operations, Maintenance, Monitoring, Change Control, Security, Privacy, Records, assurance, Support, Supplier or Delivery roles simply because those roles are technically adjacent.

Those specialists must supply or validate their own constraints, authority, failure consequences, procedures and evidence. One person may genuinely hold more than one responsibility, but that is established by the organisation and by evidence, not by title proximity or architectural seniority. If a specialist is unavailable, record the missing input as an assumption, risk, open decision or readiness condition. Do not silently fill the gap with architectural preference.

Start by separating three things that are easy to confuse. The **conceptual** view is what the customer and organisation recognise today: their language, current process, team arrangement and expected outcome. The **logical** design is the durable responsibility the service must preserve as those arrangements change: what it must distinguish, remember, decide, protect and provide. The **physical** design is the technology that implements that responsibility through interfaces, code, storage, infrastructure and runtime behaviour.

If the team builds the conceptual view directly, today's menu, screen, department structure or workflow becomes an accidental foundation. That may satisfy the first request while making later business change expensive. The architect's work is to decompose the evidence logically before construction: preserve what the customer means, identify what must endure, and leave the current arrangement free to change around it. The [Building Metaphor](../reference/building-metaphor.md) gives the plain-language picture; [Conceptual, Logical and Physical Models](../reference/catalogues/conceptual-logical-physical-models.md) gives the precise distinction.

Make the [Enduring](../reference/glossary.md#enduring) versus [Transient](../reference/glossary.md#transient) classification explicit during that decomposition. A Person, Group, School or Location may retain identity while a `StudentAt` membership, access grant, assignment or appointment begins, changes and ends. The [Entity Lifecycle Patterns](../reference/catalogues/entity-lifecycle-patterns.md) catalogue gives the questions and translations that prevent a current arrangement from becoming the accidental logical identity.

The wider context is described in [Systems Within Systems](./systems-within-systems.md). [Legal and Regulatory Context](./legal-context.md) explains how access, processing, hosting, suppliers and jurisdictions can widen the system that must be understood. The [Regulatory and Obligation Domains](../reference/catalogues/regulatory-obligations.md) catalogue names recurring objectives, while its [checklist](../reference/checklists/regulatory-obligations.md) helps record the actual sources, duties and evidence. Before the route is treated as a service-only design, read [Deliverable Systems](../reference/catalogues/deliverable-systems.md) and [Deliverables](../reference/catalogues/deliverables.md) to map the multiple systems and wider deliverables that make the outcome usable and reachable. This page applies that context through a simple architecture route:

1. Identify stakeholders and their responsibilities.
2. Determine the platform or platforms needed to serve those responsibilities.
3. Determine the sites that curate the relevant capabilities for each group.
4. Identify the runtime, delivery and deployment dependencies and responsibilities that cross the service boundary.
5. Determine the Logical Deployment Modules that provide coherent delivery packages.
6. Determine the logical layers within those packages.
7. Move from architectural components to technical-lead implementation design.

The system design architect does not need to prescribe every framework, class or provider. They do need to make the decisions that those later choices must respect. Other architect roles may contribute enterprise, business, data, integration, security, platform or domain concerns; [Stakeholder Roles](../reference/catalogues/stakeholder-roles.md) explains how those responsibilities differ.

Building blocks depend on scale. At architecture scale, **components** are meaningful parts of a site, flow, view or LDM. At technical-lead scale, **logical building blocks** describe responsibilities such as services, repositories, brokers and registries within those components and layers. At developer scale, **code types and design patterns** express those responsibilities in a language and framework. These are related views of the same design, not interchangeable names for the same physical thing.

## The stakeholder map

The map includes the groups and connected systems that participate in, depend on or are affected by the service. A stakeholder is not only a person who clicks a screen. It may be a public group, consumer, partner, intermediary, provider, support team, operator, maintainer, regulator, downstream system or organisation carrying a contractual or legal obligation.

For each stakeholder, understand:

- the responsibility they perform or depend on;
- the information and capabilities they need;
- what they may provide, change, receive or observe;
- what must be protected, remembered, evidenced or retained; and
- what happens to them when the service or a connected dependency is unavailable.

Different groups may use the same capability while needing different information, permissions or evidence. Do not turn those differences into sites, platforms or LDMs before understanding the responsibility they represent. The stakeholder map is the reason for the rest of the architecture.

Quality concerns belong in that map from the beginning. Identify the outcomes people and organisations need to achieve, the information they must be able to trust and the system qualities that enable those outcomes. [Quality Perspectives](../reference/catalogues/qualities.md) gives the shared vocabulary for connecting quality in use with data and system qualities without treating one metric as proof of the whole experience.

## Determine platforms

A platform is the technical context through which the service is delivered and operated. Depending on the stakeholder map, the service may need a web platform, mobile platform, API or partner integration platform, together with runtime, hosting, identity, storage, messaging and operational capabilities. The architect determines the platform context needed to reach the stakeholders and satisfy the service obligations.

Platform is not the same thing as site. Web, mobile, API and partner technologies describe ways of delivering or integrating a service. A site describes the responsibility and curated surface offered to a group or connected system. Several sites may share one platform, and one platform may support several LDMs.

Platform choices should be justified by reach, accessibility, interoperability, security, data handling, availability, operating model, support capability and likely change. Do not select a platform because its framework makes the first screen quick to create. Do not treat a hosting or vendor choice as the complete architecture.

The system design architect should identify the platform capabilities and important dependency classes the service requires. This includes the delivery system that turns source and infrastructure definitions into a deployable release. The delivery system may not receive user requests at runtime, but the service depends on it for release, security maintenance, repair and recovery. The detailed treatment of storage, identity, caching, messaging, search, media, providers, delivery systems and downstream systems belongs in [External Dependencies](../reference/catalogues/external-dependencies.md). The technical lead turns those needs into contracts, readiness decisions and delivery evidence.

## Determine sites

A site is a curated surface through which a defined stakeholder group or connected system reaches the information and capabilities provided by the service. It may be a user experience, an API for a partner to use directly or an interface for another system to build its own experience.

Not every stakeholder needs a site of its own. Several groups may use one site when their responsibilities and information needs remain coherent. One group may use more than one site when its contexts, responsibilities or risks differ. Public, consumer, partner, intermediary, provider, support, operations and maintenance are useful site families, but they are recognition aids rather than a mandatory list.

A site is not a security control. A missing button is not an authorisation decision. Authentication, authorisation, validation, data protection and audit remain enforced by the responsible backend boundary. The site map should show the intended audience, purpose and interface contract; it should not pretend that presentation separation replaces system controls.

The [Sites](../reference/catalogues/sites.md) catalogue provides the site vocabulary, while [Sites, Flows, Views and Components](../reference/catalogues/sites-flows-views-components.md) explains the interaction structure that follows from those decisions. The [Sites and Interfaces Checklist](../reference/checklists/sites-and-interfaces.md) turns the stakeholder-to-site relationship into review questions.

## Determine external dependencies

Once the sites are understood, ask what each site and capability must connect to. The answer is not yet a list of vendors or connection strings. It is a high-level list of the capabilities the service needs from other systems, providers or platform services.

Common dependency categories include:

- **Access and identity:** network firewalls, gateways, identity and access management services, identity providers and authorisation policy sources. An identity provider can tell the service who or what is acting and may provide claims; the service still needs to decide what that actor may do unless an explicit external authority owns that decision.
- **Information and storage:** relational, document, key-value, media and object storage, together with caches, search indexes, replicas, archives and backups.
- **Communication and integration:** service buses, queues, partner APIs, synchronisation services, email and notification providers, document delivery and payment or other financial providers.
- **Rules and specialist capabilities:** external rule engines, calculation services, geolocation and other providers whose decisions or information the service needs to use.
- **Operational evidence:** monitoring, logging, alerting, security information and event management, group reporting, enterprise analytics, data warehouses and regulatory or operational archives.
- **Delivery and deployment:** the code repository, build and deployment pipeline, artifact or package registries, infrastructure automation and state, Domain Registry, DNS, certificate authority and cloud hosting control plane. These may not be request-time dependencies, but they remain dependencies for release, security maintenance, repair and recovery.

The [External Dependencies](../reference/catalogues/external-dependencies.md) catalogue gives these categories more detail. The [Registries](../reference/catalogues/registries.md) catalogue distinguishes enterprise-referred technology, system, principle, integration-pattern, obligation and risk registries from project-produced dependency, expiry, schedule, release and evidence registries. At the architecture stage, the important decision is which category is needed, what responsibility it supports and which boundary is responsible for its contract, data, availability and failure consequences. The technical lead can later turn that category into a concrete provider, internal component and readiness plan.

## Map responsibilities across system boundaries

The service is part of the wider organisation and enterprise described in [Systems Within Systems](./systems-within-systems.md). The organisation may expect access control, reporting, monitoring, retention, evidence or downstream information even when the digital service does not own every part of the supporting arrangement. Those expectations are architectural responsibilities because the service must show where each duty is fulfilled and what happens when a connected system is unavailable.

For every important incoming or outgoing exchange, capture the high-level shape before designing the exact message. Identify:

- the direction and the source and destination boundary;
- the information category, decision, event or capability being exchanged;
- which system is authoritative and which system receives a copy or derived result;
- the device, interface, gateway, provider or service that carries the exchange;
- the trigger or cadence, such as a user action, scheduled transfer, event or continuous signal;
- the expected volume, size, frequency and peak behaviour; and
- the availability, security, classification, retention, recovery and reconciliation expectations.

At this stage, “a partner sends application status information each night” is useful architecture information even though the exact fields, message version and transport contract are not yet designed. Later modelling can define those message shapes through the responsible capability and contract. The [External Dependencies](../reference/catalogues/external-dependencies.md) catalogue describes the dependency categories and boundaries, while [Systems Within Systems](./systems-within-systems.md) explains how wider organisational obligations cross those boundaries. The [External Dependency Checklist](../reference/checklists/external-dependencies.md) provides the separate review prompts for checking that the map is complete.

## Determine Logical Deployment Modules

A Logical Deployment Module, or LDM, is a logical package whose components are delivered together. It is not automatically an independently deployable service, one project, one process, one container, one database or an ownership boundary.

LDMs group responsibilities that need a coherent delivery package and make the relationship between capabilities, contracts, dependencies and change visible. A service may contain a System LDM for shared technical capabilities and one or more Business LDMs for the domains that give it purpose. The number of LDMs follows meaningful separation and coherent delivery, not folder size or technology preference.

At this point the architect should identify the LDM boundaries and the responsibilities each package must provide or consume. The architect should not prescribe the project tree, class names or deployment topology unless those are themselves architectural constraints. Several LDMs may be delivered together while retaining distinct logical responsibilities.

The [Logical Deployment Modules](../reference/catalogues/ldms.md) catalogue explains the boundary, and the [Logical Deployment Modules development guidance](../development/ldms.md) explains what that boundary means for delivery.

## Determine logical layers

Within each LDM, distinguish implementation responsibilities without presenting them as the three model types:

- **Consumer-facing interface:** physical interface code that presents the language and interaction recognised by people or connected systems.
- **Application and domain responsibility:** physical code that coordinates use cases and expresses or implements the logical model of things, identities, relationships, states, rules and transitions.
- **Persistence and external effects:** physical code and resources that represent information through records, files, providers, transports, messages and runtime mechanisms.

These are architectural [Logical Layers](../reference/catalogues/logical-layers.md), not mandatory projects or folders. The architect needs them to protect the distinction between what stakeholders understand, what the service means and how a platform or provider executes it. The technical lead decides how the LDM expresses these implementation areas through contracts and boundaries. The [Conceptual, Logical and Physical Models](../reference/catalogues/conceptual-logical-physical-models.md) catalogue explains the separate model-type distinction, and [Ontological Decomposition](./ontological-decomposition.md) explains how to select the useful decomposition level while keeping every implementation position physicalized.

The [Logical Layers](../reference/catalogues/logical-layers.md) catalogue explains the conceptual distinction. The architect identifies the layers; the technical lead and developer decide their implementation responsibilities through [LDM Layers and Contents](../development/layers.md).

## Compose domain components within the layers

An LDM is still too large a unit to explain every responsibility. Within it, group related domain concepts and capabilities into cohesive components or assemblies. Here, an assembly means a group that is kept together because its concepts, rules, lifecycle or reasons for change belong together. It does not automatically mean a .NET assembly, a project, a separate deployment or a new LDM.

Domain-Driven Design gives useful names to the logical parts that may appear inside such a component: entities, value objects, aggregates, domain services, repositories and domain events. The [Patterns](../reference/catalogues/patterns.md) catalogue explains these patterns and their limits. The architect does not need to decide every class, but should make clear which concepts belong together, which consistency boundary protects them and which capabilities the component provides or consumes. The [Domains and Capabilities](../reference/catalogues/domains-and-capabilities.md) catalogue provides the vocabulary for that decision.

Keep components or assemblies apart when they have different meanings, authorities, lifecycles, data classifications, dependencies or reasons to change. Separation of concerns, high cohesion and low coupling are the test: each component should have a coherent purpose, and communication between components should be visible through contracts, mappings or meaningful events rather than shared tables or private implementation types.

These domain components sit inside the LDM and across its [Logical Layers](../reference/catalogues/logical-layers.md). The consumer-facing interface presents or collects information, application and domain code protects meaning and rules, and persistence and external code implements storage and provider effects. A domain component may therefore contain several logical building blocks, while one physical code project may contain several components during delivery. Keeping these distinctions visible prevents the component name from becoming another accidental deployment or folder rule.

## Move from architectural components to logical building blocks

At this point, the architect has taken the design to the level of stakeholder-facing components, domain components, LDMs and layers. The next question is a change in zoom rather than a transfer of unfinished architecture: technical leadership decides which **logical building blocks** will carry those responsibilities inside the boundaries already established.

This is a better umbrella than “classes” because it describes responsibility before it describes language syntax or framework shape.

Examples include services, state-management coordinators, repositories, brokers, providers, registries, mappings, validators, handlers, models and contracts. These names are useful only when each represents a real, cohesive responsibility. A repository is not a domain merely because it reads a table. A provider is not a policy. A registry is not a general-purpose collection. A service is not automatically the owner of every rule in a journey.

The architect should identify the responsibility and boundary that a component must preserve, not choose its logical building block, concrete type or pattern. The technical lead then identifies the logical building blocks and expects the development team to place them deliberately. Developers use the [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md) catalogue, relevant [Patterns](../reference/catalogues/patterns.md), [Contracts](../development/contracts.md) and layer guidance to decide how the blocks collaborate and how provider detail is contained.

## Make dependencies visible, then stop at the right depth

The architecture map should show which platform, runtime and delivery dependencies are required, optional, authoritative or derived. It should show the broad data, availability, lifecycle, security and recovery obligations that cross each boundary. It should also record important downstream systems such as reporting, analytics, warehouses and archives when the service must provide them with information or evidence.

Show the user-facing runtime service and the delivery/deployment system as separate systems. Map the path from code repository through build, test, security checks, artifact storage, approval and deployment to hosting. Map the domain, DNS and certificate authorities that make the deployed service reachable and trusted. Record which path is needed for normal release, urgent security repair, rollback and recovery, even when it is not involved in each request.

The architect does not need to specify every provider option, cache key, migration, retry policy or repository method in this page. Those details belong in [External Dependencies](../reference/catalogues/external-dependencies.md), the relevant catalogues and the technical lead's delivery design. This keeps the architecture useful as a map rather than turning it into a provider manual.

## Complete the architecture map

Before handing the design to technical leadership, make the following relationships visible:

- stakeholders and the responsibilities they perform or depend on;
- the platform or platforms that can serve those responsibilities;
- sites and the capabilities each site curates;
- LDMs and the responsibilities delivered by each package;
- implementation areas within those packages, with the Conceptual, Logical and Physical model types kept distinct;
- runtime and delivery dependency categories, including code repository, pipeline, registries, Domain Registry, DNS, certificate authority and hosting control plane, with the responsible boundaries that provide or consume them;
- incoming and outgoing exchanges, including their information category, authority, connection, cadence and expected volume;
- domain components or assemblies and the reasons their responsibilities are kept together or apart;
- downstream obligations crossing the boundaries; and
- deliberate omissions, deferred decisions and the evidence needed before they become ready.

The architect's output is not a promise that every part will be built immediately. It is a coherent map of the known whole, with enough boundary information for the tech lead to plan delivery and enough logical meaning for developers to avoid inventing private substitutes. The [External Dependency Checklist](../reference/checklists/external-dependencies.md) supplies prompts for the dependency review, while the [LDM and logical layers checklist](../reference/checklists/ldms-and-logical-layers.md) covers the package and layer relationships. From there, [Guidance for Tech Leads](./guidance-for-tech-leads.md) carries the map into readiness, logical building blocks, contracts, patterns and vertical-slice evidence.

## Related guidance

- [Stakeholder Analysts](../stakeholders/business-analysts/readme.md)
- [Product Owners](../stakeholders/product-owners/readme.md)
- [Shared Requirements](../shared/requirements.md)
- [Architect Route](../stakeholders/architects/readme.md)
- [Guidance for Tech Leads](./guidance-for-tech-leads.md)
- [Guidance for Developers](./guidance-for-developers.md)
- [Engineering Catalogues](../reference/catalogues/readme.md)
- [External Dependencies](../reference/catalogues/external-dependencies.md)
- [Storage Types](../reference/catalogues/storage-types.md)
- [Patterns](../reference/catalogues/patterns.md)
- [Sites](../reference/catalogues/sites.md)
- [Sites, Flows, Views and Components](../reference/catalogues/sites-flows-views-components.md)
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
- [Contracts](../development/contracts.md)
- [Data Protection](../../agents/conventions/foundations/data-protection.md)
- [Operations](../../agents/conventions/development/operations.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Data Deletion Guidance](../development/data-deletion-guidance.md)
- [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md)
