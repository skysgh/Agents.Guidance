# Service System Guidance

The service system is the server-side system that owns and enforces capabilities. It normally includes application and domain behaviour, interfaces, persistence, external integrations, diagnostics, authorisation, durable work and recovery responsibilities.

The browser says that a request is ready to submit. The service sees that one required piece of evidence is missing. If the client decides the outcome by itself, people may see a success that the organisation cannot defend later. The service boundary exists so that the authoritative meaning, permission and durable result have a dependable home.

The service is not the client, delivery pipeline or testing system. A browser may present a request and coordinate a human journey, but the service validates permissions, owns business rules, controls durable state and records consequential outcomes.

## Current route

The detailed service-system material is currently staged in [Human Development Guidance](../../development/readme.md). Its pages are being classified before relocation because the current Development folder contains service-specific material alongside concepts that cross client and service boundaries.

The relocated service implementation group is now canonical here:

- [Logical Deployment Modules](./ldms.md);
- [LDM Layers and Contents](./layers.md);
- [System LDM Services](./services.md); and
- [Vertical Slices](./vertical-slices.md).

The remaining service candidates are:

- [Cross-Cutting Services](../../development/cross-cutting-services.md); and
- [Constants and Shared Vocabulary](../../development/constants.md), where the vocabulary belongs to an LDM or service boundary.

The service route links to shared [Contracts](../shared/readme.md#contracts), [Flows](../shared/readme.md#flows), [Quality](../shared/readme.md#quality) and [Lifecycle](../shared/readme.md#lifecycle) guidance. Those subjects remain shared because client, service, pipeline and testing participants all need to understand their consequences.

## Related guidance

- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md#2-service-system)
- [Guidance for Developers](../../orientation/guidance-for-developers.md)
- [Technical Lead Guidance](../../stakeholders/technical-leads/readme.md)
- [Shared System Concerns](../shared/readme.md)
- [Client System Guidance](../client/readme.md)