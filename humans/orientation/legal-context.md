# Legal and Regulatory Context

A serious service operates inside legal, regulatory and policy systems. These systems create obligations even when a product ticket mentions only a screen, endpoint, report or workflow step.

This paper is an engineering orientation, not legal advice. The team must obtain advice appropriate to the service, the people affected and the jurisdictions involved.

## The jurisdiction map

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

The exact legal sources vary by jurisdiction and sector, but the recurring objectives are recognisable. The [Regulatory and Obligation Domains](../shared/reference/catalogues/regulatory-obligations.md) catalogue groups them without pretending that one country's source applies everywhere. It covers purpose and fairness, personal information, tracking, records, retention, security, accessibility, trustworthy use, safety, financial responsibilities, cross-border suppliers and content rights.

Use the [Regulatory and Obligation Checklist](../shared/reference/checklists/regulatory-obligations.md) when the team needs to record the actual sources, owners, capabilities, evidence, gaps and review triggers. The catalogue explains the subject; the checklist helps apply it to a service.

## Why omitted requirements still matter

A ticket is not a complete statement of the service's obligations. If a ticket says "allow a user to upload a document", the team must still ask who may access it, where it is stored, how it is scanned, how it is retained, whether it is copied to search or backup, how it is deleted, what is logged and what happens when storage is unavailable.

If a ticket is silent about an applicable obligation, that silence is not permission to omit it. Failure can result in fines, remediation orders, restrictions on processing or service operation, contractual consequences, loss of trust and reputational damage. The exact consequence depends on the source, jurisdiction, sector and facts, but the engineering response is the same: make the obligation visible before implementation hides it in local choices.

## Related guidance

- [Systems Within Systems](./systems-within-systems.md)
- [Guidance for System Design Architects](./guidance-for-system-design-architects.md)
- [Guidance for Tech Leads](./guidance-for-tech-leads.md)
- [Regulatory and Obligation Domains](../shared/reference/catalogues/regulatory-obligations.md)
- [Regulatory and Obligation Checklist](../shared/reference/checklists/regulatory-obligations.md)
- [Stakeholder Roles](../shared/reference/catalogues/stakeholder-roles.md)
- [Data Deletion Guidance](../development/data-deletion-guidance.md)
- [Detailed Data Deletion Considerations](../development/detailed-data-deletion-considerations.md)
- [Data Protection Conventions](../../agents/conventions/foundations/data-protection.md)
- [Design Standards](../../agents/conventions/development/design-standards.md)
