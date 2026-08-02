# Human Development Guidance

This folder explains how a service is organised after its purpose and wider obligations are understood. It is the human route for LDMs, their layers and the code-purpose categories within those layers. The shared [Engineering Catalogues](../reference/catalogues/readme.md) describe the wider structures that lead into this route, and the [Engineering Checklists](../reference/checklists/readme.md) provide practical prompts for applying them.

The LDM is only one logical package inside a wider delivery. Read [Deliverable Systems](../reference/catalogues/deliverable-systems.md) for the distinct systems being delivered and [Deliverables](../reference/catalogues/deliverables.md) for the other data, content, infrastructure, registrations and evidence that must accompany the package.

These papers explain ideas and help people learn the reasoning. The [agent development conventions](../../agents/conventions/development/readme.md) state the repository rules, invariants and validation requirements. They are two views of the same engineering intent, not two competing architectures.

## Read in this order

1. [Logical Deployment Modules](./ldms.md): understand the logical package whose components are delivered together and whose contracts, data and lifecycle remain coherent.
2. [LDM Layers and Contents](./layers.md): understand why an LDM contains layers, and what belongs inside them.
3. [Vertical Slices: Common Shafts](./vertical-slices.md): recognise the recurring capability shapes that travel through those layers.
4. [Data Deletion Guidance](./data-deletion-guidance.md): understand why deletion can damage history, when it may be required or blocked, and how anonymisation can preserve useful records.
5. [Availability, Capacity and Resilience](./availability-capacity-and-resilience.md): understand how service targets become design, operational and assurance evidence.
6. [Cross-Cutting Services](./cross-cutting-services.md): understand shared system capabilities that support many slices.
7. [System LDM Services](./services.md): understand the services and system domains commonly established first.
8. [Constants](./constants.md): understand how stable shared vocabulary is built without creating magic strings or global bags of values.
9. [Contracts](./contracts.md): understand the formwork that lets objects, services and implementations change safely.

Return to the relevant paper when a capability, module or technology decision raises one of these questions. The route is deliberately modular: a team can read the LDM paper without pretending that every service or layer must be built immediately.

## Related guidance

- [Guidance for Developers](../orientation/guidance-for-developers.md)
- [Guidance for Tech Leads](../orientation/guidance-for-tech-leads.md)
- [Guidance for System Design Architects](../orientation/guidance-for-system-design-architects.md)
- [Vertical Slices: Common Shafts](./vertical-slices.md)
- [Data Deletion Guidance](./data-deletion-guidance.md)
- [Availability, Capacity and Resilience](./availability-capacity-and-resilience.md)
- [Detailed Data Deletion Considerations](./detailed-data-deletion-considerations.md)
- [Cross-Cutting Services](./cross-cutting-services.md)
- [Human Engineering Guidance](../readme.md)
- [Agent Development Conventions](../../agents/conventions/development/readme.md)
- [Human Examples](../examples/readme.md)
