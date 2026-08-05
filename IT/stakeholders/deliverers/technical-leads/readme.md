[Up](../readme.md)

# Technical Leads

Technical leads turn an architectural map into an achievable implementation path. This route currently uses the established foundation and development pages as its canonical detailed guidance.

## A useful way into the route

[Guidance for Tech Leads](../../../foundations/guidance-for-tech-leads.md) follows the handoff from architecture into capabilities, Domains, LDMs, logical building blocks, platform readiness, contracts and delivery evidence. [Shared Requirements](../../../shared/requirements.md) explains the requirement chain and role handoffs, including the [specialist controls](../../../shared/requirements.md#specialist-controls-enable-the-outcome-and-protect-it-when-needed) that contribute implementation and readiness evidence. [Guidance for System Design Architects](../../../foundations/guidance-for-system-design-architects.md) makes the boundaries visible that technical design must preserve. [Guidance for Developers](../../../foundations/guidance-for-developers.md) and [Developer Conventions](../../../../agents/conventions/development/guidance-for-developers.md) continue the handoff into code. [Vertical Slices](../../../development/vertical-slices.md) and [Contracts](../../../development/contracts.md) give implementation and evidence a more concrete shape. When entities or relationships have history, [Entity Lifecycle Patterns](../../../shared/reference/catalogues/entity-lifecycle-patterns.md) helps the team think through the LDM, layer, schema, migration and query implications.

## The technical lead's responsibility

The technical lead checks whether the prepared meaning and architecture can be implemented, supported, tested, released and recovered with the available team, technology and dependencies. They decide or coordinate implementation structure within the architectural boundaries and raise contradictions rather than hiding them in local code.

Technical leadership does not replace product authority, Domain knowledge, security or privacy authority, operational ownership or maintenance responsibility. A technical lead may coordinate technical analysis, but the relevant boundary and specialist roles still own their contracts and conditions.

The technical lead checks that the implementation path preserves the logical distinction between [Enduring](../../../shared/reference/glossary.md#enduring) identity and [Transient](../../../shared/reference/glossary.md#transient) relationship. They should expect effective dates, overlap rules, history, migrations, tests and operational evidence when a relationship such as `StudentAt` has a lifecycle of its own, rather than allowing a convenient foreign key or current-status field to erase that responsibility.

## Related routes

- [Stakeholders](../readme.md)
- [Stakeholder Analysts](../business-analysts/readme.md)
- [Product Owners](../product-owners/readme.md)
- [Architects](../architects/readme.md)
- [Developers](../developers/readme.md)
- [Shared Requirements](../../../shared/requirements.md)
