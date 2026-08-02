# Human Development Guidance

This folder explains how a service is organised after its purpose and wider obligations are understood. It is the human route for LDMs, their layers and the code-purpose categories within those layers. The shared [Engineering Catalogues](../reference/catalogues/readme.md) describe the wider structures that lead into this route, and the [Engineering Checklists](../reference/checklists/readme.md) provide practical prompts for applying them.

The LDM is only one logical package inside a wider delivery. Read [Deliverable Systems](../reference/catalogues/deliverable-systems.md) for the distinct systems being delivered and [Deliverables](../reference/catalogues/deliverables.md) for the other data, content, infrastructure, registrations and evidence that must accompany the package.

These papers explain ideas and help people learn the reasoning. The [agent development conventions](../../agents/conventions/development/readme.md) state the repository rules, invariants and validation requirements. They are two views of the same engineering intent, not two competing architectures.

## Papers for different questions

[Logical Deployment Modules](./ldms.md) explains the logical package whose components are delivered together and whose contracts, data and lifecycle remain coherent. [LDM Layers and Contents](./layers.md) explains what belongs inside that package, while [Vertical Slices: Common Shafts](./vertical-slices.md) shows the recurring capability shapes that travel through the layers.

[Data Deletion Guidance](./data-deletion-guidance.md) covers deletion, history and anonymisation. [Availability, Capacity and Resilience](./availability-capacity-and-resilience.md) connects service targets to design, operations and assurance evidence. [Cross-Cutting Services](./cross-cutting-services.md) and [System LDM Services](./services.md) describe shared capabilities and system domains.

[Constants](./constants.md) protects stable shared vocabulary, and [Contracts](./contracts.md) explains the formwork that lets objects, services and implementations change safely. Return to whichever paper matches the capability, module or technology decision in front of you. The route is deliberately modular: no service or layer is required merely because it appears in the catalogue.

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
