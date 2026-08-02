# Engineering Guidance

Delivering software is larger than developing it. A delivered service joins software with its data, configuration, dependencies, supporting material, evidence and responsibilities so that people can use it, operators can run it, support can understand it and maintainers can change it.

This guidance is one connected body of knowledge with several useful perspectives. It does not require one reading order or ask one role to own every decision. It helps the team see what must accompany a feature, where responsibility belongs and what evidence will keep the outcome dependable after release.

## A useful way in

Choose the question closest to the work in front of you, or use the [short, story-led way into the guidance](./humans/orientation/ways-into-guidance.md) when the vocabulary is not familiar yet:

- **What are we trying to deliver?** [Delivery Guidance](./humans/delivery/readme.md) explains the wider delivered whole.
- **What does the service mean and where does it belong?** [Architecture](#architecture) connects purpose to systems, boundaries and dependencies.
- **How do we build a capability?** [Technical Leadership and Development](#technical-leadership-and-development) connects design to contracts, slices and implementation.
- **How do we know it is dependable?** [Quality](#quality), [Assurance](#assurance) and [Operating](#operating) keep qualities, controls, evidence and live service concerns visible.
- **What is my contribution?** [Delivery Team Roles](#delivery-team-roles) leads to the stakeholder routes and their handoffs.

These are invitations, not gates. The same service will appear differently from each perspective, but the responsibilities, boundaries and evidence still need to join up.

The delivery begins with purpose, people, outcomes, obligations and constraints. It becomes a service through domain understanding, logical design, contracts, code, data, interfaces, infrastructure, testing and evidence. It reaches its users through release and deployment, then remains meaningful through observability, support, recovery, controlled change and maintenance.

The visible feature is only one part of this movement. Meaning also has to survive the boundaries between people and systems, the first release, the first failure and the arrival of the next team.

## Oversight for cohesive delivery

This guidance makes the relationships between purpose, responsibilities, boundaries, capabilities, systems, evidence and lifecycle visible. It helps a team recognise what must accompany the software for the outcome to be real, and where an omission would leave users, operators, the organisation or future teams carrying an avoidable burden.

The [Delivery Guidance](./humans/delivery/readme.md) explains how software, supporting material, operational responsibility and evidence become one usable delivered service. When the situation is not yet clear, the [short way into the guidance](./humans/orientation/ways-into-guidance.md) begins with stories and questions. Once the question is understood, the [catalogues](./humans/reference/catalogues/readme.md) name the important concepts, roles, systems and qualities, and the [checklists](./humans/reference/checklists/readme.md) gather practical prompts for applying them.

## Many ways into the guidance

This is one body of knowledge, but it does not have one prescribed journey. Its meaning becomes easier to recognise from different perspectives, and each perspective connects with the same delivered whole.


### Delivery Team Roles

A role perspective is available through [Stakeholder Guidance](./humans/stakeholders/readme.md). It shows how Product, Analysis, Architecture, Development, Testing, Support, Operations and Maintenance contribute knowledge, decisions, work and evidence without separating those contributions from the shared delivery.


### Product Management and Lifecycle

[Product Manager Guidance](./humans/stakeholders/product-managers/readme.md) connects objectives, investment, organisational capacity, obligations and risk to the outcomes a service should pursue. [Product Owner Guidance](./humans/stakeholders/product-owners/readme.md) connects those objectives to ordered outcomes, foundations, acceptance and evidence. [Delivery Guidance](./humans/delivery/readme.md) explains how those outcomes become usable, operable and supportable services. [SDLC](./humans/reference/catalogues/sdlc.md) then describes how the service is discovered, discussed, decided, defined, designed, developed, delivered, maintained and eventually decommissioned. Together they keep product direction connected to the service's full life rather than treating delivery as the end of product responsibility.

The product outcome also needs a completeness view. [Deliverables](./humans/reference/catalogues/deliverables.md) makes the supporting systems, data, content, reachability, operational material and evidence visible. [Registries](./humans/reference/catalogues/registries.md) makes the decisions, dependencies, responsibilities and time-bound obligations that keep those deliverables current visible. Together they help Product and delivery roles see what must accompany the software for the intended outcome to remain real.


### Architecture

An architecture perspective is available through the [Human System Guidance](./humans/systems/readme.md), the [Engineering Catalogues](./humans/reference/catalogues/readme.md), [Guidance for System Design Architects](./humans/orientation/guidance-for-system-design-architects.md), [Deliverable Systems](./humans/reference/catalogues/deliverable-systems.md), [Conceptual, Logical and Physical Models](./humans/reference/catalogues/conceptual-logical-physical-models.md), [Domains and Capabilities](./humans/reference/catalogues/domains-and-capabilities.md) and [External Dependencies](./humans/reference/catalogues/external-dependencies.md). These pages connect purpose and meaning to systems, boundaries, dependencies and responsibility before implementation choices narrow the design.

### Technical Leadership and Development

[Technical Lead Guidance](./humans/stakeholders/technical-leads/readme.md) turns architecture into an achievable implementation and readiness path. [Developer Guidance](./humans/stakeholders/developers/readme.md) gives the general implementation route, while [Front-end Developer Guidance](./humans/stakeholders/developers/front-end.md) follows the distinct browser consumer system, its client-side horizontal flows, component assemblies, accessibility, usability and browser security. [Human System Guidance](./humans/systems/readme.md) keeps the client, service, pipeline, testing and shared boundaries visible while that path is built. [Logical Deployment Modules](./humans/development/ldms.md), [LDM Layers and Contents](./humans/development/layers.md), [Vertical Slices](./humans/development/vertical-slices.md) and [Contracts](./humans/development/contracts.md) remain the current detailed development pages while their ownership is migrated.

### Quality

[Quality Perspectives](./humans/reference/catalogues/qualities.md) describes the qualities of the system, its data and its use. It connects qualities to the outcomes people and organisations need, without reducing quality to a list of technical attributes or a final test result.

### Assurance

An assurance perspective is available through [Testing Evidence and Boundaries](./humans/stakeholders/testers/evidence-and-boundaries.md), the [security checklists](./humans/reference/checklists/security-at-rest.md), [regulatory obligations](./humans/reference/catalogues/regulatory-obligations.md) and [operational readiness and recovery](./humans/stakeholders/operators/readiness-observability-and-recovery.md). These routes explain how claims become controls, tests, decisions and evidence, and how missing evidence is returned to the responsible boundary.

### Operating

[Availability, Capacity and Resilience](./humans/development/availability-capacity-and-resilience.md) connects service targets to design, operation and evidence. The [operator guidance](./humans/stakeholders/operators/readme.md) covers the live service, observability, support, diagnosis, recovery and the conditions that keep it dependable after release.

The [orientation pages](./humans/orientation/readme.md), [examples](./humans/examples/readme.md) and [shared guidance](./humans/shared/readme.md) provide further ways to recognise these subjects through explanation, experience and consequence.

## Structures for enduring value

[Logical Deployment Modules](./humans/development/ldms.md) describe coherent packages of responsibility, data, contracts and lifecycle. [Layers and Contents](./humans/development/layers.md) distinguish the purposes within an LDM, while [Vertical Slices](./humans/development/vertical-slices.md) show how a capability can travel through those layers as a complete piece of delivery.

[Contracts](./humans/development/contracts.md) protect the relationships between parts. [Availability, Capacity and Resilience](./humans/development/availability-capacity-and-resilience.md) connects service targets to design, operations and evidence. [Data Deletion Guidance](./humans/development/data-deletion-guidance.md) keeps lifecycle decisions connected to history, privacy and recovery.

The [orientation pages](./humans/orientation/readme.md), [stakeholder guidance](./humans/stakeholders/readme.md), [examples](./humans/examples/readme.md) and [development guidance](./humans/development/readme.md) add context around particular roles, situations and structures. Together they keep the software connected to the people, operating conditions and future changes that give it enduring value.

## Human and agent expressions

The [human guidance](./humans/readme.md) explains the ideas, consequences, roles and examples in an accessible connected story. It gives people the context behind the structures and shows how different contributions belong to the same delivery.

The [agent guidance](./agents/readme.md) is for AI agents working within the repository. It expresses the same engineering intent through compressed conventions, invariants and validation requirements, preserving the useful rule without repeating the full explanation in every task.
