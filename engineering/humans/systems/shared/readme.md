# Shared System Concerns

Some guidance belongs to more than one system because the meaning crosses a boundary. Shared guidance is not a dumping ground and it is not a fourth implementation system. It explains the contracts, flows, models, qualities and lifecycle decisions that client, service, pipeline and testing perspectives must understand together.

A client may show a request as submitted while the service is still reconciling a provider response. The pipeline may know exactly which version is running, while the testing system is holding the evidence that explains the difference. No single system can explain the whole situation alone. Shared guidance gives the people involved a place to meet without moving authority away from the boundary that owns it.

## Shared subjects

### Contracts

[Contracts and Formwork](./contracts.md) explains what a provider offers, what a consumer may rely on, what the provider needs and how failure is expressed. Client-service contracts, service-provider contracts and internal contracts may differ, but the shared contract questions remain visible.

### Flows

[Common Flows](./flows.md) gives the recurring journey language. The client may express the most complete human journey, while the service may coordinate durable business steps. Neither perspective should steal the other's rules or authority.

### Quality

[Quality Perspectives](../../reference/catalogues/qualities.md) connects system quality, data quality and quality in use. [Availability, Capacity and Resilience](./availability-capacity-and-resilience.md) gives one focused path from quality claims to service targets and evidence. Each system contributes evidence for the qualities it controls, while the service outcome remains a whole-system concern.

### Lifecycle

[Data Deletion Guidance](./data-deletion-guidance.md), [Detailed Data Deletion Considerations](./detailed-data-deletion-considerations.md) and [Logical and Physical Models](./logical-and-physical-models.md) cross client, service, storage, pipeline, testing and organisational boundaries. Their authority must remain with the relevant business, privacy, records, security, architecture and system representatives or responsible boundaries.

## Current migration state

The detailed pages now have canonical locations under this Shared route, while compatibility paths remain for readers following older links. This index is the shared-system entry point for material that genuinely crosses boundaries; it does not replace the Client or Service routes.

## Related guidance

- [Human System Guidance](../readme.md)
- [Client System Guidance](../client/readme.md)
- [Service System Guidance](../service/readme.md)
- [Shared Requirements](../../shared/requirements.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)