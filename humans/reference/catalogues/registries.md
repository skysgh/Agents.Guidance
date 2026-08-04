# Registries

A registry is an owned, governed collection of records that supports a decision, lookup, control, handoff or lifecycle. It is more than a list. Each entry needs a defined meaning, responsible maintainer, authority, evidence, status, review condition and treatment when it becomes stale.

Registries have two important scopes. Keeping these scopes separate prevents a project from treating its own temporary records as enterprise policy, and prevents enterprise guidance from pretending to know every project detail.

## Two registry scopes

### Enterprise-referred registries

An enterprise-referred registry is maintained outside a project and is referred to by projects as a source of options, constraints, authority or shared information. It is enterprise-wide only when the organisation has given it that scope and has assigned the authority and maintenance needed to keep it trustworthy.

A project should record which enterprise registry entries it relies on, the version or effective date consulted, any exception it needs and the consequence of a later change. Referring to a registry does not mean copying it into project documentation. Use a link, identifier, snapshot or controlled import that preserves provenance and makes staleness visible.

Common enterprise-referred registries include:

- **Technology registry:** permitted, conditionally permitted, unsupported, prohibited, sunsetting and retired languages, frameworks, platforms, components and provider capabilities. Entries should include support, security, licensing, skills, operating, portability, cost, replacement and exit evidence. This informs technology choices; it does not choose the technology for every capability.
- **System and service registry:** known enterprise systems, services, owners, interfaces, authoritative sources, data classifications, lifecycle state, support route and integration conditions. It helps architects and integration teams find existing capabilities and identify the system authoritative for a fact or decision.
- **Principles registry:** approved principles grouped by concern, such as architecture, security, privacy, data, accessibility, operations, records, delivery and sustainability. Each principle needs an owner, rationale, applicability, priority or conflict rule and review condition.
- **Integration-pattern registry:** permitted, conditional and prohibited ways to connect systems, including synchronous APIs, events, queues, files, scheduled transfers, callbacks and reconciliation patterns. It describes the how of connection, not the technology used to implement it. A pattern entry should state when it fits, trust and identity expectations, failure and retry behaviour, compatibility, observability, reconciliation, ownership and exit conditions.
- **Enterprise risk registry:** material enterprise risks, their owners, affected objectives, treatments, residual risk, acceptance authority, review date and escalation route. A project refers to relevant risks and may add a project-specific risk or treatment; it must not silently rewrite enterprise risk.
- **Reference-data and classification registry:** shared codes, categories, jurisdictions, organisational identifiers, data classifications, retention classes or other values whose meaning must remain consistent across projects. Authority, effective dates, compatibility and deprecation are essential.
- **Policy, obligation and control registry:** applicable policies, legal or regulatory obligations, control objectives, evidence expectations and accountable owners. The registry points to the authority; it does not replace the project's interpretation of what must be true.
- **Approved supplier and dependency registry:** suppliers, providers, contracts, support status, service conditions, renewal or exit terms, known restrictions and accountable commercial or technical owners.

A development-pattern registry may be useful when the organisation has recurring engineering problems, a real review audience and evidence that named patterns improve decisions. It should not become a catalogue of fashionable names. Keep reusable design patterns in the patterns catalogue unless the organisation needs to approve, prohibit, support or measure particular patterns. The same distinction applies to component registries: enterprise guidance may list approved component families or supported versions, while a project records the components it actually uses.

### Project-produced registries

A project-produced registry is created and maintained by a project, product or service to make its own scope, dependencies, commitments, people, timing and evidence visible. It is not automatically enterprise policy and should not be presented as an enterprise source merely because several teams can read it.

Common project-produced registries include:

- **Deliverables registry:** the systems, data, content, registrations, infrastructure, documentation, support material and evidence that must exist for the intended outcome. Record owner, status, dependency, readiness evidence and retirement condition.
- **Backlog and work-item register:** ordered outcomes, decisions, defects, risks, dependencies, deliberate deferrals and work items with their owner, status, acceptance evidence and review condition. A backlog is a registry when it is governed as a record of work, not merely a transient task list.
- **Component and dependency registry:** the components, packages, images, providers and versions actually used by the project, including provenance, owning boundary, upgrade status, vulnerability findings, exceptions, support state and replacement path. This is how a team can identify whether it depends on a component with an active exploit.
- **Expiry and renewal registry:** subscriptions, certificates, domains, licences, keys, credentials, support agreements and other time-bounded obligations. Do not store secret values in the registry. Record the protected object, owner, expiry, renewal route, alerting, evidence and failure consequence.
- **Schedule and operational-window registry:** releases, migrations, maintenance windows, brownouts, blackouts, holiday restrictions, supplier windows, known events and other timing constraints. Include timezone, affected services, authority, communication route, exception process and rollback or recovery implications.
- **People and role assignment registry:** the people currently assigned to project roles, responsibilities, approvals, on-call duties or escalation routes, with effective dates and a source of authority. Keep the two questions distinct: who is assigned to a role, and which roles a person holds. Do not use this registry as a substitute for an authorisation system.
- **Project risk and decision registry:** project risks, assumptions, issues, decisions, accepted residual risk, owners, evidence, due dates and review triggers. Link enterprise risks rather than copying their meaning.
- **Release and change registry:** planned and completed releases, migrations, approvals, affected boundaries, compatibility expectations, deployment evidence, rollback or recovery route and post-release verification.
- **Data and integration inventory:** project-owned data sets, authoritative sources, consumers, classifications, transformations, interfaces, schedules, reconciliation, retention and deletion obligations.
- **Environment and configuration registry:** environments, purposes, versions, dependencies, configuration ownership, access route, data rules, readiness state and differences that affect testing or delivery. Never use it to record secret values.
- **Evidence and assurance register:** tests, reviews, approvals, control checks, incidents, recovery exercises and acceptance evidence, including the claim supported, responsible role, date, scope, result and follow-up.

The list is not a mandatory project template. Create a registry when a governed set of records is needed to make a material decision or lifecycle obligation reliable. Do not create one merely because a collection could be given a name.

## Ownership and use

Different registries have different maintainers. The registry's audience, maintainer and decision authority must be explicit:

| Registry or record set | Typical maintainer | Typical users or decision roles |
| --- | --- | --- |
| Technology, principles, integration patterns and enterprise systems | Enterprise architecture, platform, integration or policy owners | Architects and technical leads choosing or reviewing options |
| Enterprise risk and obligations | Enterprise risk, compliance, business or accountable service authorities | Product Managers, Product Owners, sponsors, architects and assurance |
| Deliverables, backlog and work items | Product Owner, Product Manager or delivery facilitator, according to the organisation's authority | Delivery team, architects, testers, Operations and stakeholders |
| Project components, dependencies and versions | Technical lead or component/dependency owner | Developers, testers, security, Operations and maintainers |
| Expiry and renewal | The owner of the certificate, subscription, licence, key or agreement, coordinated with Operations | Technical leads, Operations, security, procurement and release coordination |
| Schedule and operational windows | Operations, service owner or change authority | Release Manager, Change Manager, Product Owner, Operations and affected suppliers |
| People-to-role assignments and role-to-person views | Service or project authority, delivery leadership or people operations | Everyone who needs a current contact, escalation or approval route |
| Project risks, decisions and assurance evidence | The role with authority for the decision, coordinated by delivery or assurance support | Product, architecture, delivery, testing, Operations and auditors |

The assignment must reflect the actual organisation. A dedicated Release Manager is useful when release volume, risk or coordination complexity justifies it. In a smaller firm, Operations, a Change Manager, a delivery facilitator or another named person may carry the Release Manager responsibility. The organisation must still name the person or role, preserve the separation between change approval and release coordination where that matters, and record an unassigned responsibility as a delivery risk. Do not assume that a Product Owner, architect or most senior developer will perform it silently.

A person may maintain a registry without having authority over every decision recorded in it. A team lead may keep the component register current, while security owns vulnerability acceptance and the Product Owner or service authority decides whether the resulting risk changes scope or release. A person may also hold several roles, but the accountabilities and conflicts must remain visible.

## Minimum registry contract

For every registry that affects a serious-system decision, define:

- the purpose and scope;
- the authority for creating, approving, changing and retiring entries;
- the maintainer and backup or succession route;
- the record identity and required fields;
- source, provenance and effective date;
- status and lifecycle states;
- consumers and decisions informed by the registry;
- review, expiry and stale-entry detection;
- access, privacy, security and audit treatment;
- change notification and compatibility expectations; and
- the action and owner when an entry is missing, contradicted, expired or withdrawn.

A registry should be authoritative only for the facts it owns. A technology registry may say that a framework is permitted; it does not prove that a project has selected it well. A component registry may say which version is deployed; it does not accept an active vulnerability. A schedule registry may identify a blackout; it does not approve a release. Keep the source, decision and evidence connected.

## Registry, catalogue, inventory and repository

These terms overlap but are not interchangeable:

- A **catalogue** explains a category or shared vocabulary, such as the kinds of technology or integration pattern that exist.
- An **inventory** records what exists or is in use, usually with less decision authority than a registry.
- A **registry** governs identified entries used for lookup, decision or lifecycle, with an owner and rules for change and staleness.
- A **repository** provides governed access to persisted information for an application or domain. It is a software building block, not automatically a governance registry.

The same physical product may host several registries or an inventory, but the responsibility and authority of each record set must remain distinct.

## Related guidance

- [Delivery Guidance](../../delivery/readme.md) explains how registries support the wider delivered outcome and its continuing responsibilities.
- [Stakeholder Roles](./stakeholder-roles.md) explains who may maintain, consult or decide from a registry.
- [Logical Building Blocks](./logical-building-blocks.md) explains the software building block called a registry.
- [Deliverables](./deliverables.md) explains the wider deliverables that project registries help track.
- [External Dependencies](./external-dependencies.md) explains provider, system, domain, DNS, certificate and deployment dependencies.
- [Software Development Lifecycle](./sdlc.md) places registry updates in discovery, decision, delivery, operations, maintenance and decommissioning.
- [Technology Registry Conventions](../../../agents/conventions/development/registries.md) states the implementation rules for governed registries.
