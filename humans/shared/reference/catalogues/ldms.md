[Up](./readme.md)

# Logical Deployment Modules


A Logical Deployment Module, or LDM, is a logical package whose components are delivered together. The components may be deployed at the same time as components from other LDMs, including in one whole-system deployment. An LDM does not promise independent deployment.

The word **logical** matters. An LDM describes which responsibilities, contracts, dependencies and changes belong together as a delivery package. It is not automatically one project, one process, one container, one database, one independently released service or one organisational ownership boundary.

## Why use an LDM

An LDM gives a service a meaningful package boundary before project and deployment choices are made. It helps a team answer:

- which responsibilities are delivered together;
- which contracts are exposed or consumed;
- which data and dependencies are relevant to the package;
- which changes should be considered together; and
- which parts can remain logically separate even when delivered in one deployment.

Use an LDM when the boundary protects a coherent responsibility or delivery decision. Do not create one merely because a folder is large, a framework makes another project possible or a team prefers more namespaces.

## Common LDM shapes

A service may contain a **System LDM** for shared technical and system capabilities and one or more **Business LDMs** for the domains that give the service its purpose. This is a recognition aid, not a universal decomposition.

A System LDM may provide shared capabilities such as configuration, diagnostics, secrets, storage, identity, access, audit, startup, messaging or workflow infrastructure. Business LDMs retain the meaning of business concepts, decisions, states and outcomes. A shared technical capability must not acquire business meaning merely because several business areas use it.

The number and names of LDMs should follow the service's responsibilities, dependencies, delivery shape and consequences. A small service can have one LDM and still preserve internal logical boundaries. A larger service can have several LDMs while deploying them together.

## LDMs and other boundaries

An LDM is not the same as a domain, capability, bounded context, aggregate, site, database or deployment. A domain gives concepts and rules their meaning. A capability provides a useful ability within that meaning. A site curates capabilities for a stakeholder group. An aggregate protects a domain consistency boundary. A database is a physical storage mechanism. A deployment is an operational release decision.

These boundaries may align in a particular service, but alignment must be demonstrated rather than assumed. A single LDM may contain several domains. Several LDMs may share one database. One capability may serve several sites. Several LDMs may be delivered together.

## What an LDM should make visible

For each LDM, make its purpose, responsibilities, consumers, contracts, dependencies, data classification, lifecycle, delivery relationship and deliberate exclusions understandable. Record whether a dependency is required, optional, authoritative or derived and what happens when it is unavailable.

The LDM boundary should be stable enough for the technical lead to plan layers, logical building blocks, readiness and slices. It should be meaningful enough for developers to know which domain and contracts they are working within. It should not prescribe every class, provider option or project folder.

## Related scales

The architect uses LDMs as architectural building blocks. The tech lead decomposes each LDM into logical layers and logical building blocks. Developers express those responsibilities through contracts, code types and design patterns. The same word, such as component or service, can mean different things at different scales, so the boundary and responsibility should always be stated.

Read [Logical Layers](./logical-layers.md) for the material distinction within an LDM, [Logical Building Blocks](./logical-building-blocks.md) for the next implementation-design vocabulary and [LDM Layers and Contents](../../../development/layers.md) for detailed layer placement.

For delivery and project guidance, read [Logical Deployment Modules](../../../development/ldms.md). For review prompts, use the [LDM and logical layers checklist](../checklists/ldms-and-logical-layers.md).
