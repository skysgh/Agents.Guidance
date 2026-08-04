# Operator Guidance

Operators keep the delivered service available, observable, secure and recoverable. This route uses the established operations conventions, readiness references and deliverable guidance as its canonical detailed material.

## A useful way into the route

[Operations Conventions](../../../agents/conventions/development/operations.md) gives the precise language for readiness, diagnostics, dependency failure, recovery and runbooks. [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md) explains the conditions that make a service supportable and operable over time. The [Deliverables](../../reference/catalogues/deliverables.md) catalogue and [System LDM Service Readiness](../../reference/platform-services.md) bring operational information, manuals, dependencies and readiness decisions into view.

When a service crosses boundaries, [External Dependencies](../../reference/catalogues/external-dependencies.md) helps make failure, classification, recovery and reconciliation understandable. [Registries](../../reference/catalogues/registries.md) explains the project records Operations may maintain or consult, including expiry, schedule, people-to-role, dependency and release records. [Guidance for Tech Leads](../../orientation/guidance-for-tech-leads.md) and [Guidance for Developers](../../orientation/guidance-for-developers.md) provide a route back to the design when the service lacks the signals, controls or failure behaviour needed for safe operation.

## The operator's responsibility

An operator uses the service's defined signals, controls and procedures to provide it safely. Operators verify readiness, interpret healthy and degraded states, respond to alerts, perform permitted routine actions, coordinate recovery and record evidence. Monitoring is a capability within or alongside Operations: it observes and reports conditions, while Operations interprets them and coordinates an authorised response. Elevated resets, restores and other privileged actions must have separately defined authority and must not be granted to every operator by default. Operators should be able to operate the service without relying on private knowledge held by its original developers. Operations does not own the user conversation that belongs to Support, the test claim that belongs to Testing or the code and contract change that belongs to Maintenance.

An operator is not automatically the architect, developer, tester, Support role, security authority or maintainer. Operational action must not silently bypass authorisation, data protection, audit or recovery boundaries.

## Operational deliverables

Operations owns or contributes to [Operational Manuals or Information](../../reference/catalogues/deliverables.md), including readiness, deployment, configuration, monitoring, alert response, access procedures, routine operation, dependency failure, recovery responsibilities and the status information Support needs when users report a problem. These are not Support Manuals or Information and do not replace Maintenance Manuals or Information.

## Operations working guidance

- [Operational Readiness, Observability and Recovery](./readiness-observability-and-recovery.md): interpret service states, act on operational signals and recover the service through controlled procedures.
- [Incident Learning and Corrective Change](./incident-learning-and-corrective-change.md): preserve incident evidence, assign the learning decision and trace corrective work through verification.
- [Availability, Capacity and Resilience](../../development/availability-capacity-and-resilience.md): operate and prove service-specific availability, capacity, degradation and recovery targets.

## Related routes

- [Stakeholder Guidance](../readme.md)
- [Stakeholder Analysts](../business-analysts/readme.md)
- [Product Owners](../product-owners/readme.md)
- [Architects](../architects/readme.md)
- [Technical Leads](../technical-leads/readme.md)
- [Developers](../developers/readme.md)
- [Testers](../testers/readme.md)
- [Support](../support/readme.md)
- [Maintainers](../maintainers/readme.md)
