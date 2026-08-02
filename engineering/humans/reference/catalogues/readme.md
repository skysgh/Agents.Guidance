# Engineering Catalogues

This folder gathers the named structures that recur across the engineering guidance. A catalogue is a teaching document as well as a reference. It gives a subject enough shape that a reader can recognise it, understand why it exists and see how it relates to the other structures around it.

A catalogue is not a mandatory project layout and it is not a list of technology choices. The names are useful only when they describe a real responsibility. A system may combine several entries, omit entries it does not need or use different implementation names while preserving the same meaning.

If you are meeting the catalogues for the first time, [Stakeholder Roles](./stakeholder-roles.md) gives you a way to see knowledge, authority and evidence, while [Users to Consider](./users.md) brings direct users, represented subjects, affected people and connected systems into view. [System Roles](./system-roles.md) helps when the question is how real-world responsibilities differ from access and authorisation contexts.

The useful direction through the catalogues is from the people and systems around a service towards the code that realises it. Stakeholder Roles explains who contributes knowledge, authority and evidence. Regulatory and Obligation Domains explains the recurring objectives that laws, regulations, policies, contracts and standards create across jurisdictions. Conceptual, Logical and Physical Models explains three kinds of model without confusing them with implementation position. Quality Perspectives connects system and software qualities, data qualities and quality in use without treating them as interchangeable. Platform capabilities establish the technical ground on which a service can run. Sites then curate capabilities for particular responsibilities and audiences. Sites are made from flows, flows use capabilities, and the resulting interfaces are organised into views and components. Logical deployment modules group components that are delivered together. Logical layers keep consumer-facing representations, application and domain responsibilities and physical effects from being confused. Logical building blocks name the responsibilities that technical leads expect inside those implementation areas. Domains and capabilities give the work its meaning before implementation types and design patterns give it a code shape.

The detailed catalogue path depends on the question in front of you. [Stakeholder Roles](./stakeholder-roles.md) and [Regulatory and Obligation Domains](./regulatory-obligations.md) help place authority, evidence and external duties. [Conceptual, Logical and Physical Models](./conceptual-logical-physical-models.md) and [Sites](./sites.md) help give meaning and audience a clearer shape. When the experience needs more detail, [Sites, Flows, Views and Components](./sites-flows-views-components.md) follows that thread. [Registries](./registries.md) distinguishes enterprise-referred sources of options and constraints from project-produced records of actual dependencies, commitments, people, timing and evidence. [External Dependencies](./external-dependencies.md), [Deliverable Systems](./deliverable-systems.md) and [Deliverables](./deliverables.md) become useful when the service reaches beyond its source code into providers, distinct systems, data, content, trust and support. [Domains and Capabilities](./domains-and-capabilities.md), [Logical Deployment Modules](./ldms.md), [Logical Layers](./logical-layers.md) and [Logical Building Blocks](./logical-building-blocks.md) help place implementation responsibility. [Patterns](./patterns.md) gives names to recurring design responses, while [Storage Types](./storage-types.md) helps when physical information storage is part of the decision.

The detailed implementation guidance remains in the development folder. [Logical Deployment Modules](../../development/ldms.md), [LDM Layers and Contents](../../development/layers.md), [System LDM Services](../../development/services.md) and [Vertical Slices](../../development/vertical-slices.md) explain the corresponding subjects in greater depth. The catalogues provide the shared map so those detailed documents are easier to place.

The companion [checklists](../checklists/readme.md) turn the explanations into prompts for design and review. The documents explain the reasoning; the checklists help a team remember to apply it.

## Catalogue index

[Sites](./sites.md) describes the surfaces created for groups with different responsibilities, information needs and capabilities.

[Sites, Flows, Views and Components](./sites-flows-views-components.md) describes the relationship between a site, the flows it offers, the views within those flows and the components within a view. It is an intentionally deeper subject and may be read when the work reaches interface and interaction structure.

[External Dependencies](./external-dependencies.md) describes systems and technical capabilities that a service uses but does not contain within the capability being designed.

[Domains and Capabilities](./domains-and-capabilities.md) describes how meaning and useful system abilities are separated from the implementation shapes used to provide them.

[Logical Deployment Modules](./ldms.md) describes logical packages, their delivery boundary and the relationship between responsibilities, contracts, dependencies and change.

[Logical Layers](./logical-layers.md) describes consumer-facing interface, application and domain responsibility and persistence or external effects within an LDM.

[Logical Building Blocks](./logical-building-blocks.md) describes the responsibility categories that technical leads use between architectural components and developer code.

[Registries](./registries.md) distinguishes enterprise-referred registries from project-produced registries and explains their scope, ownership, lifecycle and evidence.

[Patterns](./patterns.md) explains the recurring principles and structures referred to by names such as OOP, GRASP, SOLID, GoF and DDD.

[Storage Types](./storage-types.md) explains key-value, relational, document, media and derived storage so that other guidance can refer to a shared vocabulary.

[Stakeholder Roles](./stakeholder-roles.md) explains the different stakeholder, architect, developer, testing, operations, maintenance, governance and assurance responsibilities that may contribute to a service.

[Users to Consider](./users.md) identifies direct users, represented subjects, affected people, providers, support users, operational users, assurance users and connected systems whose perspectives may matter during analysis.

[System Roles](./system-roles.md) distinguishes real-world responsibilities from access-context roles, configured permissions, automated actors and implementation roles.

[Quality Perspectives](./qualities.md) explains system and software product quality, data quality and quality in use, together with the evidence needed to support quality claims.

[Regulatory and Obligation Domains](./regulatory-obligations.md) explains the recurring objectives created by legal, regulatory, contractual, policy and standards sources, while preserving the need to check the actual jurisdiction and authority.

[Conceptual, Logical and Physical Models](./conceptual-logical-physical-models.md) explains the three model types and how they relate to physical implementation positions such as interfaces, application and domain code, persistence and infrastructure.

[Entity Lifecycle Patterns](./entity-lifecycle-patterns.md) explains how Enduring concepts and Transient relationships guide the logical decomposition of conceptual language, including identity, membership, effective dates, authority and history.

[Deliverable Systems](./deliverable-systems.md) describes the delivery, service, consumer and testing systems that may be delivered together while remaining distinct systems.

[Deliverables](./deliverables.md) describes the wider set of systems, data, content, addressing, trust, discovery, corporate surfaces, operational material and evidence required for an outcome.

[SDLC](./sdlc.md) explains the iterative lifecycle from Discovery through Decommissioning.
