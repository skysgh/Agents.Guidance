# Legal and Regulatory Context

A serious service operates inside legal, regulatory and policy systems. These systems create obligations even when a product ticket mentions only a screen, endpoint, report or workflow step.

This paper is an engineering orientation, not legal advice. The team must obtain advice appropriate to the service, the people affected and the jurisdictions involved.

## Start with the jurisdiction map

For a genuinely local service, the jurisdiction where the service is offered and the jurisdiction from which it is delivered may be the same. That is often the simplest case, but it still needs to be established rather than assumed.

Identify at least two dimensions:

- **Where the service is offered**: the places where it is marketed, made available, accessed, consumed or offered to people and organisations.
- **Where the service is delivered**: the places from which the service is operated, hosted, supported or processed, including relevant offices, suppliers and infrastructure locations.

Both sets of jurisdictions can create obligations. They may overlap completely, overlap partly or be different. A service described as local can acquire wider implications when it accepts remote access, serves people from elsewhere, uses cross-border providers, transfers data, provides support from another location or makes information and functionality available beyond the intended local boundary.

The map may also need to account for the location of people whose data is processed, employees and contractors, identity providers, storage and backup regions, payment or messaging providers, and organisations connected by contract or regulation. Do not claim that one identical law applies everywhere. Identify the applicable sources and their territorial scope for the actual service arrangement.

## Laws are not the same as technical controls

Keep four things distinct:

- a **legal or regulatory source** creates or explains an obligation;
- an **organisational duty** assigns responsibility for meeting it;
- a **technical capability** helps fulfil that duty; and
- **evidence** shows that the obligation was understood, the control operated and failures were handled.

For example, a legal requirement may create a duty to protect personal information. The service may need classification, minimised collection, authorisation, secure storage, retention, audit, export, correction and erasure capabilities. Those capabilities are not the law itself, and their existence is not evidence that they work. The team must define tests, records, monitoring and review evidence appropriate to the obligation.

## Recurring outcomes

The exact legal sources vary by jurisdiction and sector, but serious services commonly need to address outcomes such as:

- **Confidentiality**: information is disclosed only to an authorised person, system or purpose.
- **Records and retention**: required records remain trustworthy and retrievable for the approved period, then are disposed of safely when disposal is permitted.
- **Logical retrieval and identification**: authorised people can find the correct record, person, case, transaction or decision without relying on ambiguous names or unsafe manual reconstruction.
- **Erasure and the right to be forgotten**: the service can remove or irreversibly anonymise information where erasure applies, while handling lawful retention exceptions and copies in caches, indexes, exports, backups and archives.
- **Safe network messaging**: information sent between people and systems is protected, correctly addressed, traceable where required and not exposed through URLs, logs, notifications or insecure integration paths.
- **Accessibility**: people with disabilities can use the service and complete the relevant outcome.
- **Usability**: people can understand the service, make the required decisions and recover from errors without unreasonable confusion or avoidable harm.
- **Branding and identity**: people can recognise the responsible service, distinguish official communication from fraud and understand who is making a decision or request.
- **Mobility**: the service works across the supported devices, locations, connectivity conditions and assistive technologies required by its audience.
- **Availability**: the service and its critical dependencies are available for the promised purpose, with clear degradation, recovery and communication behaviour.

These outcomes are not automatically satisfied by adding a field, a login screen, a delete button or a responsive layout. Each needs an owner, a boundary, a failure policy and evidence suited to the service.

## Why omitted requirements still matter

A ticket is not a complete statement of the service's obligations. If a ticket says "allow a user to upload a document", the team must still ask who may access it, where it is stored, how it is scanned, how it is retained, whether it is copied to search or backup, how it is deleted, what is logged and what happens when storage is unavailable.

If a ticket is silent about an applicable obligation, that silence is not permission to omit it. Failure can result in fines, remediation orders, restrictions on processing or service operation, contractual consequences, loss of trust and reputational damage. The exact consequence depends on the source, jurisdiction, sector and facts, but the engineering response is the same: make the obligation visible before implementation hides it in local choices.

## Role responsibilities

The **architect** identifies the offering and delivery jurisdictions, legal and regulatory sources, affected people, wider systems, obligations, interfaces, dependencies and required evidence. They translate the obligation map into architectural duties and assign each duty to a responsible boundary.

The **tech lead** makes those duties technically real. They ensure that platform capabilities, data boundaries, identity, authorisation, storage, messaging, audit, retention, recovery, accessibility and availability support the required outcomes. They treat a known legal or regulatory obligation as a delivery constraint, even when the local feature request is silent.

The **developer** implements the assigned contracts, controls, persistence, interfaces, failure paths and evidence. They raise missing decisions and must not quietly remove a required protection because it is inconvenient or absent from the ticket.

The **operator and assurance roles** keep the controls effective after release. They monitor the service, protect evidence, review changes, test recovery and escalate when a dependency, jurisdiction, provider or business process changes.

## Review questions

Before building or materially changing a capability, ask:

1. Where is the service offered, marketed, made available or consumed?
2. From where is it delivered, operated, hosted, supported or processed?
3. Are the offering and delivery jurisdictions the same, or has the service crossed that boundary?
4. Which people, organisations, providers, data locations and downstream systems widen the map?
5. Which legal, regulatory, contractual and organisational sources apply in those places?
6. What recurring outcomes do those sources require?
7. Which boundary owns each duty and which technical capability fulfils it?
8. What evidence proves the capability works, including during failure, recovery, deletion and change?

Record the answers with the service design. Revisit them when the audience, access model, hosting location, supplier, data flow or operating model changes.

## Related guidance

- [Systems Within Systems](./systems-within-systems.md)
- [What Architects Need to Know](./architects-need-to-know.md)
- [What Tech Leads Need to Know](./tech-leads-need-to-know.md)
- [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md)
- [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md)
- [Data Protection Conventions](../../agents/conventions/foundations/data-protection.md)
- [Design Standards](../../agents/conventions/development/design-standards.md)
