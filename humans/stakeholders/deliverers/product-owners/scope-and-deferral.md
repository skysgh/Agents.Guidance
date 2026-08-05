[Up](readme.md)

# Scope and Deferral

Scope is the set of responsibilities, outcomes, boundaries and evidence included in a decision. It is not only the list of screens or tickets planned for a release.

The Product Owner makes scope decisions within delegated authority. A good scope decision states what is included, what is excluded or deferred, why the boundary is responsible, who is affected and what evidence will support the choice.

## Define the boundary

For each material outcome, identify:

- the users and stakeholders included;
- the capability and Domain responsible for the meaning;
- the systems, contracts and dependencies involved;
- the functional, quality, transitional and operational conditions;
- the deliverables and evidence needed; and
- the responsibility that remains outside the current scope.

A boundary is useful when it prevents accidental promises. A feature should not quietly become a new source of truth, an authorisation boundary, an operational procedure or a public commitment merely because those consequences were not written down.

## Make exclusions explicit

An exclusion is a deliberate statement that something is outside the current responsibility or delivery. It should identify the reason, the affected people or systems, the owner of the outside responsibility and the consequence of relying on it.

Examples include:

- an external system remains authoritative for a decision;
- a connected partner must provide a contract before integration is enabled;
- a migration cohort is intentionally staged later;
- a support or maintenance capability is provided by another organisation; or
- a policy decision remains with an authorised body outside the product team.

An exclusion does not make the consequence disappear. If the product depends on the outside responsibility, record the dependency, contract and failure behaviour.

## Make deferral safe

A deferral should record:

- what is understood well enough to defer;
- what is not being built or released now;
- why deferral is acceptable at this point;
- who owns the deferred responsibility;
- what condition, date, incident or evidence reopens it;
- what risk and temporary control apply in the meantime; and
- how it affects compatibility, operation, support, maintenance and retirement.

Do not use ÔÇ£future phaseÔÇØ as a substitute for a boundary, owner or trigger. A roadmap is useful only when it preserves the decision and its consequences.

## Protect people from scope language

Scope language should not hide people who do not use the main interface. Check direct users, represented subjects, affected people, providers, support, Operations, Maintenance, Monitoring, security, privacy, records, assurance, suppliers and connected systems where relevant.

The Product Owner may choose to stage an outcome, but should not silently remove accessibility, privacy, security, recovery, operational or evidence requirements that make the outcome dependable.

## Review scope when facts change

Revisit scope when:

- a requirement, policy or authority changes;
- a dependency or contract changes;
- an affected user group or consequence is discovered;
- a test, incident or operational rehearsal falsifies an assumption;
- a migration, support or maintenance condition becomes material; or
- the evidence needed for acceptance cannot be produced.

A changed scope decision is not failure. Keeping the old decision after its assumptions have failed is the greater risk.

## Related guidance

- [Product Owner Guidance](./readme.md)
- [Product Purpose and Outcomes](./product-purpose-and-outcomes.md)
- [Ordering and Sequencing](./ordering-and-sequencing.md)
- [Foundations and Delay](./foundations-and-delay.md)
- [Users to Consider](../../../shared/reference/catalogues/users.md)
- [System Roles](../../../shared/reference/catalogues/system-roles.md)
- [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md)
- [Traceability and Evidence](../business-analysts/traceability-and-evidence.md)
