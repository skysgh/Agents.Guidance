[Up](../readme.md)

# Deliverables

Delivering software is larger than developing software. Development creates and changes the software. Delivery brings the software together with the data, configuration, infrastructure, dependencies, supporting material and responsibilities that allow a meaningful outcome to become real.

A service is delivered when people can use it for its intended purpose, operators can run it, support can understand it, maintainers can change it and the organisation can stand behind it. A successful build is part of that achievement, but it is not the whole achievement.

## The delivered whole

The delivered whole can include several connected systems and many kinds of supporting material. These are related, but they are not interchangeable:

- the **delivery systems** that define and execute flows, define environments, build, qualify, package, promote and deploy;
- the **service system** that provides capabilities, authoritative data, business rules and durable decisions;
- the **consumer system** through which people or other systems reach the service;
- the **testing system** and the evidence it produces;
- the **service, client, pipeline-definition, environment-definition and test codebases** that are versioned, reviewed and brought together by delivery;
- the **environment instances and baselines** in which the systems are built, tested, qualified, operated or recovered;
- **business and operational data**, including reference values, migrated data, derived information, indexes, queues, reports, backups and other controlled copies;
- **content and branding**, including service names, logos, visual identity, language, legal notices, help content and publication material;
- **media and accessibility material**, including documents, imagery, audio, video, fonts, captions, transcripts and alternative representations;
- **infrastructure and reachability**, including networks, domains, DNS, certificates, identity, access, discovery and hosting;
- **interfaces and boundary contracts**, including compatibility, versioning, deprecation and failure meaning;
- **event and message flows**, where the service uses them, including delivery, acknowledgement, retry, replay, reconciliation and evidence;
- **monitoring and operational material**, including readiness information, runbooks, support material, recovery procedures and maintenance information;
- **decisions and records**, including approvals, acceptance, risk, exceptions, release records and operational evidence; and
- the **responsible people, teams, suppliers and registries** that keep these things current.

The exact set is shaped by the outcome and its consequences. The point is not to create every category. The point is to keep the things that make the outcome possible visible, assigned to a responsible boundary and able to change.

[System Perspectives](./systems/readme.md) provides the reader material for the client, service, pipeline, testing and shared system perspectives. It records which perspectives are developed and which are reserved for future investment.

[Deliverable Systems](../shared/reference/catalogues/deliverable-systems.md) explains the distinct systems that may be delivered together. [Deliverables](../shared/reference/catalogues/deliverables.md) describes the wider things that must be produced, configured, published or maintained around them. [Registries](../shared/reference/catalogues/registries.md) distinguishes enterprise-referred sources of constraints and options from project-produced records of the actual delivery.

## Development within the delivered outcome

Development is where prepared meaning becomes code, configuration and physical change. It gives the service its behaviour, interfaces, persistence, integrations and deployable form. It also reveals ambiguity, missing ownership, unsuitable boundaries and assumptions that need a decision.

Development cannot carry the whole delivery alone. Product and analysis connect the work to purpose, users, outcomes and obligations. Architecture shapes responsibilities and boundaries. Testing establishes evidence about behaviour and quality. Release and deployment connect change to an environment in which it can be used. Operations provide readiness, observability, security, recovery and routine care. Support helps people when the expected path is not enough. Maintenance preserves meaning as dependencies, conditions and teams change.

These are not steps that make one role more important than another. They are different responsibilities around the same service. The delivered outcome depends on their connections, handoffs and evidence.

## Delivery through the life of a service

The delivery perspective remains present after the first release. A service may need new capabilities, changed policies, migrated data, altered dependencies, renewed certificates, revised content, restored environments, incident learning or a controlled retirement. Each change can affect more than the code that initiated it.

The [SDLC catalogue](../shared/reference/catalogues/sdlc.md) gives the lifecycle a shared vocabulary from discovery through decommissioning. [Availability, Capacity and Resilience](../development/availability-capacity-and-resilience.md) connects service targets to design, operation and assurance. [Data Deletion Guidance](../development/data-deletion-guidance.md) connects lifecycle decisions to history, privacy, recovery and evidence.

The delivery is therefore not a moment when development stops. It is the continuing relationship between purpose, people, systems, material, evidence and responsibility.

## Structures that protect enduring value

The service needs enough structure for its meaning to survive change. [Logical Deployment Modules](../development/ldms.md) describe coherent packages of responsibility, data, contracts and lifecycle. [Layers and Contents](../development/layers.md) distinguish the purposes within those packages, and [Vertical Slices](../development/vertical-slices.md) show how a capability can travel through them as a complete piece of delivery.

[Contracts](../development/contracts.md) protect relationships between parts. The [Engineering Catalogues](../shared/reference/catalogues/readme.md) provide shared language for systems, roles, qualities, models, dependencies and responsibilities. The [Engineering Checklists](../shared/reference/checklists/readme.md) gather practical reference material for design, delivery and review.

These structures are not decoration around development. They are part of how a team preserves useful meaning, supports responsible choices within constraints and leaves enough clarity for the people who operate, change and depend on the service later.

## Different perspectives, one delivery

A Product Manager may see investment, objectives, risk and organisational capacity. A Product Owner may see valuable outcomes, foundations and acceptance. An architect may see boundaries, dependencies and systems. A technical lead may see implementation responsibility and readiness. A tester or assurance specialist may see claims, qualities, controls and evidence. An operator may see health, capacity, failure and recovery. A maintainer may see compatibility, lifecycle and the cost of future change.

Each perspective is valid, but none is the whole delivered outcome. [Stakeholders](../stakeholders/readme.md) explains these contributions and the handoffs between them. [Engineering for People](../readme.md) provides the wider explanation, examples and shared meaning around the roles and structures.
