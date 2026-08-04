# Registries in Delivery

A registry is a governed set of records used for lookup, decision, control, handoff or lifecycle. It is more than a list: each entry needs meaning, authority, a responsible maintainer, evidence, status and a way to detect or handle stale information.

## Why it matters

Delivery depends on facts that change at different speeds. A certificate expires, a supplier changes terms, a component receives a vulnerability, an environment drifts, a release affects a boundary or a person changes role. If those facts are held only in memory or scattered across private notes, the team may make a decision from information that is incomplete, unauthorised or out of date.

A registry makes a governed set of facts visible. It does not make every fact true, and it does not transfer authority from the person or organisation that owns the decision. Its value comes from connecting the record to its source, maintainer, consumers, review condition and consequence when the record is missing or wrong.

## What we mean by registries

The [Registries catalogue](../../shared/reference/catalogues/registries.md) distinguishes two related but different scopes:

- **Enterprise-referred registries** are maintained outside the project and provide shared options, constraints, authority or information. A project should preserve the source, identifier, version or effective date it relied on.
- **Project-produced registries** record the project's own deliverables, dependencies, risks, decisions, releases, environments, people, schedules, data, integrations or evidence. They are not automatically enterprise policy.

A registry can be a deliverable in its own right, or it can support another deliverable. The physical product may be a document, table, service, repository or platform. The form is secondary to the governance contract. Do not create a registry merely because a collection can be given a name; create one when governed records are needed for a material decision or lifecycle obligation.

Keep registries distinct from nearby concepts. A catalogue explains a category. An inventory records what exists, usually with less decision authority. A software repository provides persisted application data and behaviour. The record's responsibility and authority must remain clear even when one product hosts several of these things.

## How to develop one

Begin with the decision, control, handoff or lifecycle obligation that needs reliable records:

- define the purpose, scope and facts the registry is authoritative for;
- identify the authority for creating, approving, changing and retiring entries;
- name the maintainer and a backup or succession route;
- define entry identity, required fields, provenance, effective date and lifecycle states;
- identify who consumes it and which decisions it informs;
- define access, privacy, security, audit and notification treatment;
- define review, expiry and stale-entry detection; and
- state what happens, and who acts, when an entry is missing, contradicted, expired or withdrawn.

Keep the source, decision and evidence connected. A technology registry may say that an option is permitted; it does not prove that a project chose it well. A component registry may say which version is used; it does not accept a vulnerability. A schedule registry may identify a blackout; it does not approve a release.

Do not put secret values in a registry. Record the protected object, responsible party, expiry or renewal route and evidence location, while keeping credentials, keys and tokens in the appropriate protected system.

## Questions to consider

Start with the [Registries catalogue](../../shared/reference/catalogues/registries.md), then use the relevant [Engineering Checklists](../../shared/reference/checklists/readme.md) to review the consequence. The [Deliverables Checklist](../../shared/reference/checklists/deliverables.md) helps identify registries needed to make an outcome deliverable and maintainable. Security, dependency, regulatory, integration and operational checklists may add subject-specific questions.

Ask:

- What decision or lifecycle obligation becomes unreliable without this registry?
- Is it enterprise-referred or project-produced, and who has authority over that scope?
- Which facts does it own, and which facts must remain in another source?
- How will a consumer know whether an entry is current and trustworthy?
- Who maintains it when the original team, supplier or system changes?
- What is the failure consequence of a missing, stale or conflicting entry?
- What evidence proves that the registry is complete enough for its purpose?
- How are entries notified, reviewed, deprecated, migrated and retired?

The registry route is the human story and decision path. The [Registries catalogue](../../shared/reference/catalogues/registries.md) remains the canonical explanation of registry types and the minimum registry contract. Project teams must still create only the registries their own consequences require.

## Related guidance

- [Delivery Guidance](../readme.md)
- [Registries Catalogue](../../shared/reference/catalogues/registries.md)
- [Deliverables](../../shared/reference/catalogues/deliverables.md)
- [External Dependencies](../../shared/reference/catalogues/external-dependencies.md)
- [Engineering Checklists](../../shared/reference/checklists/readme.md)
- [Technology Registry Conventions](../../../agents/conventions/development/registries.md)
