# Engineering Guidance

Delivering software is larger than developing software. Development creates and changes the software. Delivery brings that software, its data, configuration, dependencies, supporting material and responsibilities together so that it can reach operations, become usable by its intended people and remain supportable after release.

Development is therefore one important part of engineering delivery, not the whole of it. Product, analysis, architecture, development, testing, release, deployment, operations, support and maintenance each carry different responsibilities. A service becomes a delivered service when those responsibilities join around something that people can use, operators can run, support can understand and maintainers can change.

## From purpose to operation

The delivery begins with purpose, people, outcomes, obligations and constraints. It becomes a service through domain understanding, logical design, contracts, code, data, interfaces, infrastructure, testing and evidence. It reaches its users through release and deployment, and remains meaningful through observability, support, recovery, controlled change and maintenance.

The visible feature is only one part of this movement. Meaning also has to survive the boundaries between people and systems, the passage from decision to implementation, the first release, the first failure and the arrival of the next team. This is why the delivery view includes operational readiness, security, persistence, recovery, evidence and the conditions in which the service will actually be used.

## Oversight for cohesive delivery

This guidance provides a shared view across the delivery without pretending that one role owns every decision. It makes the relationships between purpose, responsibilities, boundaries, capabilities, systems, evidence and lifecycle visible. That view helps a team recognise what must accompany the software for the outcome to be real, and where an omission would leave users, operators, the organisation or future teams carrying an avoidable burden.

The wider delivery is described through [Deliverable Systems](./humans/reference/catalogues/deliverable-systems.md), [Deliverables](./humans/reference/catalogues/deliverables.md) and [Registries](./humans/reference/catalogues/registries.md). The [catalogues](./humans/reference/catalogues/readme.md) name the important concepts, roles, systems and qualities. The [checklists](./humans/reference/checklists/readme.md) gather practical reference material around them.

## Structures for enduring value

[Logical Deployment Modules](./humans/development/ldms.md) describe coherent packages of responsibility, data, contracts and lifecycle. [Layers and Contents](./humans/development/layers.md) distinguish the purposes within an LDM, while [Vertical Slices](./humans/development/vertical-slices.md) show how a capability can travel through those layers as a complete piece of delivery.

[Contracts](./humans/development/contracts.md) protect the relationships between parts. [Availability, Capacity and Resilience](./humans/development/availability-capacity-and-resilience.md) connects service targets to design, operations and evidence. [Data Deletion Guidance](./humans/development/data-deletion-guidance.md) keeps lifecycle decisions connected to history, privacy and recovery.

The [orientation pages](./humans/orientation/readme.md), [stakeholder guidance](./humans/stakeholders/readme.md), [examples](./humans/examples/readme.md) and [development guidance](./humans/development/readme.md) add context around particular roles, situations and structures. Together they keep the software connected to the people, operating conditions and future changes that give it enduring value.

## Human and agent expressions

The [human guidance](./humans/readme.md) explains the ideas, consequences, roles and examples in an accessible connected story. It gives people the context behind the structures and shows how different contributions belong to the same delivery.

The [agent guidance](./agents/readme.md) is for AI agents working within the repository. It expresses the same engineering intent through compressed conventions, invariants and validation requirements, preserving the useful rule without repeating the full explanation in every task.
