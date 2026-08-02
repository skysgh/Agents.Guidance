# Engineering Guidance

Delivering software is larger than developing software. Development creates and changes the software. Delivery brings that software, its data, configuration, dependencies, supporting material and responsibilities together so that it can reach operations, become usable by its intended people and remain supportable after release.

Development is therefore one important part of engineering delivery, not the whole of it. Product, analysis, architecture, development, testing, release, deployment, operations, support and maintenance each carry different responsibilities. A service becomes a delivered service when those responsibilities join around something that people can use, operators can run, support can understand and maintainers can change.

## From purpose to operation

The delivery begins with purpose, people, outcomes, obligations and constraints. It becomes a service through domain understanding, logical design, contracts, code, data, interfaces, infrastructure, testing and evidence. It reaches its users through release and deployment, and remains meaningful through observability, support, recovery, controlled change and maintenance.

The visible feature is only one part of this movement. Meaning also has to survive the boundaries between people and systems, the passage from decision to implementation, the first release, the first failure and the arrival of the next team. This is why the delivery view includes operational readiness, security, persistence, recovery, evidence and the conditions in which the service will actually be used.

## Oversight for cohesive delivery

This guidance provides a shared view across the delivery without pretending that one role owns every decision. It makes the relationships between purpose, responsibilities, boundaries, capabilities, systems, evidence and lifecycle visible. That view helps a team recognise what must accompany the software for the outcome to be real, and where an omission would leave users, operators, the organisation or future teams carrying an avoidable burden.

The wider delivery is described through [Deliverable Systems](./humans/reference/catalogues/deliverable-systems.md), [Deliverables](./humans/reference/catalogues/deliverables.md) and [Registries](./humans/reference/catalogues/registries.md). The [catalogues](./humans/reference/catalogues/readme.md) name the important concepts, roles, systems and qualities. The [checklists](./humans/reference/checklists/readme.md) gather practical reference material around them.

## Many ways into the guidance

This is one body of knowledge, but it does not have one prescribed journey. Its meaning becomes easier to recognise from different perspectives, and each perspective connects with the same delivered whole.

A role perspective is available through [Stakeholder Guidance](./humans/stakeholders/readme.md). It shows how Product, Analysis, Architecture, Development, Testing, Support, Operations and Maintenance contribute knowledge, decisions, work and evidence without separating those contributions from the shared delivery.

An outcome and completeness perspective is available through [Deliverable Systems](./humans/reference/catalogues/deliverable-systems.md), [Deliverables](./humans/reference/catalogues/deliverables.md) and [Registries](./humans/reference/catalogues/registries.md). Together they make visible the systems being delivered, the people and organisations that depend on them, and the supporting material, records and responsibilities that have to accompany the software.

An architecture and technical-structure perspective is available through the [Engineering Catalogues](./humans/reference/catalogues/readme.md), [Logical Deployment Modules](./humans/development/ldms.md), [LDM Layers and Contents](./humans/development/layers.md), [Vertical Slices](./humans/development/vertical-slices.md) and [Contracts](./humans/development/contracts.md). They connect meaning to boundaries, dependencies, implementation responsibility and change.

An assurance perspective is available through [Quality Perspectives](./humans/reference/catalogues/qualities.md), [Testing Evidence and Boundaries](./humans/stakeholders/testers/evidence-and-boundaries.md), the [security checklists](./humans/reference/checklists/security-at-rest.md), [regulatory obligations](./humans/reference/catalogues/regulatory-obligations.md) and [operational readiness and recovery](./humans/stakeholders/operators/readiness-observability-and-recovery.md). Together they give qualities, tests, security, controls, obligations and evidence their own view of the service rather than treating assurance as a final inspection.

A lifecycle and operating perspective is available through [SDLC](./humans/reference/catalogues/sdlc.md), [Availability, Capacity and Resilience](./humans/development/availability-capacity-and-resilience.md) and the [operator guidance](./humans/stakeholders/operators/readme.md). The [orientation pages](./humans/orientation/readme.md), [examples](./humans/examples/readme.md) and [shared guidance](./humans/shared/readme.md) provide further ways to recognise the ideas through explanation, experience and consequence.

## Structures for enduring value

[Logical Deployment Modules](./humans/development/ldms.md) describe coherent packages of responsibility, data, contracts and lifecycle. [Layers and Contents](./humans/development/layers.md) distinguish the purposes within an LDM, while [Vertical Slices](./humans/development/vertical-slices.md) show how a capability can travel through those layers as a complete piece of delivery.

[Contracts](./humans/development/contracts.md) protect the relationships between parts. [Availability, Capacity and Resilience](./humans/development/availability-capacity-and-resilience.md) connects service targets to design, operations and evidence. [Data Deletion Guidance](./humans/development/data-deletion-guidance.md) keeps lifecycle decisions connected to history, privacy and recovery.

The [orientation pages](./humans/orientation/readme.md), [stakeholder guidance](./humans/stakeholders/readme.md), [examples](./humans/examples/readme.md) and [development guidance](./humans/development/readme.md) add context around particular roles, situations and structures. Together they keep the software connected to the people, operating conditions and future changes that give it enduring value.

## Human and agent expressions

The [human guidance](./humans/readme.md) explains the ideas, consequences, roles and examples in an accessible connected story. It gives people the context behind the structures and shows how different contributions belong to the same delivery.

The [agent guidance](./agents/readme.md) is for AI agents working within the repository. It expresses the same engineering intent through compressed conventions, invariants and validation requirements, preserving the useful rule without repeating the full explanation in every task.
