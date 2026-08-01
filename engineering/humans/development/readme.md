# Human Development Guidance

This folder explains how a service is organised after its purpose and wider obligations are understood. It is the human route for LDMs, their layers and the code-purpose categories within those layers.

These papers explain ideas and help people learn the reasoning. The [agent development conventions](../../agents/conventions/development/readme.md) state the repository rules, invariants and validation requirements. They are two views of the same engineering intent, not two competing architectures.

## Read in this order

1. [Logical Deployment Modules](./ldms.md): understand the boundary that owns deployment, contracts, data and lifecycle.
2. [LDM Layers and Contents](./layers.md): understand why an LDM contains layers, and what belongs inside them.
3. [Vertical Slices: Common Shafts](./vertical-slices.md): recognise the recurring capability shapes that travel through those layers.
4. [Data Deletion Guidance](./digital-data-lifecycle-overview.md): understand why deletion can damage history, when it may be required or blocked, and how anonymisation can preserve useful records.
5. [Cross-Cutting Services](./cross-cutting-services.md): understand shared system capabilities that support many slices.
6. [System LDM Services](./services.md): understand the services and system domains commonly established first.
7. [Constants](./constants.md): understand how stable shared vocabulary is built without creating magic strings or global bags of values.
8. [Contracts](./contracts.md): understand the formwork that lets objects, services and implementations change safely.

Return to the relevant paper when a capability, module or technology decision raises one of these questions. The route is deliberately modular: a team can read the LDM paper without pretending that every service or layer must be built immediately.

## Related guidance

- [What Developers Need to Know](../orientation/developers-need-to-know.md)
- [What Tech Leads Need to Know](../orientation/tech-leads-need-to-know.md)
- [What Architects Need to Know](../orientation/architects-need-to-know.md)
- [Vertical Slices: Common Shafts](./vertical-slices.md)
- [Data Deletion Guidance](./digital-data-lifecycle-overview.md)
- [Detailed Data Deletion Considerations](./digital-data-lifecycle.md)
- [Cross-Cutting Services](./cross-cutting-services.md)
- [Human Engineering Guidance](../readme.md)
- [Agent Development Conventions](../../agents/conventions/development/readme.md)
- [Human Examples](../examples/readme.md)
