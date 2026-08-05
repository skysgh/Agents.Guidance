[Up](../readme.md)

# Maintainers

ÔÇ£MaintainerÔÇØ is a broad label that can hide two different responsibilities. This route uses **Maintenance** for the controlled change of an occupied service, especially Maintenance Developers who investigate and change system code, configuration, schema, dependencies or infrastructure. Organisational or infrastructure service maintenance may be carried by a separate maintenance owner or provider and must not be assumed to be the same group.

## A useful way into the route

[SDLC: Maintenance and Decommissioning](../../../shared/reference/catalogues/sdlc.md) explains why an occupied service has a different risk posture and why retirement is part of responsible maintenance. [API Lifecycle](../../../foundations/api-lifecycle.md) follows compatibility, deprecation, migration and removal of published contracts. Provider change and exit decisions come into view through [Dependency and Supply-Chain Conventions](../../../../agents/conventions/development/dependencies.md) and [Vendor Material and Engineering Competence](../../../foundations/vendor-material-and-engineering-competence.md).

The [Deliverables](../../../shared/reference/catalogues/deliverables.md) catalogue describes the Maintenance Manuals or Information, migration, rollback, recovery, compatibility and decommissioning material that helps a service remain understandable. [Data Deletion Guidance](../../../development/data-deletion-guidance.md), [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md) and [Operations Conventions](../../../../agents/conventions/development/operations.md) widen the view to lifecycle consequences beyond the main codebase.

## Maintenance responsibilities

Maintenance Developers investigate what existing people, systems, data, contracts and operations rely upon before changing an occupied service. They preserve compatibility where required, add evidence for new risks, manage dependency and schema change, support correction and migration, and make retirement or replacement conditions visible. A separate organisational or infrastructure maintenance owner may maintain hosting, networks, facilities, platforms or provider arrangements. Both groups need an explicit boundary, owner and escalation path.

Maintenance does not replace Support's user assistance, Operations' live-service control or Testing's independent evidence responsibility. A maintenance role is not automatically the Product Owner, Business Analyst, architect, tester, Support role, operator, security authority or records authority. One person may hold several responsibilities, but changes to meaning, authority, protection, operation and retirement must be decided and evidenced by the relevant roles.

## Maintenance deliverables

Maintenance owns or contributes to [Maintenance Manuals or Information](../../../shared/reference/catalogues/deliverables.md), including architecture decisions, contracts, dependency lifecycle, compatibility, rollback, data protection, repair, migration, deprecation, replacement and decommissioning procedures. These are not Support Manuals or Information or Operational Manuals or Information.

## Maintenance working guidance

- [Controlled Change and Lifecycle Maintenance](./controlled-change-and-lifecycle.md): change an occupied service while preserving compatibility, evidence, recovery and retirement obligations.

## Related routes

- [Stakeholders](../readme.md)
- [Stakeholder Analysts](../business-analysts/readme.md)
- [Product Owners](../product-owners/readme.md)
- [Architects](../architects/readme.md)
- [Technical Leads](../technical-leads/readme.md)
- [Developers](../developers/readme.md)
- [Testers](../testers/readme.md)
- [Support](../support/readme.md)
- [Operators](../operators/readme.md)
