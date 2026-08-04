# Availability, Capacity and Resilience

Availability, capacity and resilience are service obligations, not infrastructure hopes. A serious system should state what must remain usable, under which conditions, at what load, how it may degrade, how quickly it must recover and what evidence will prove those claims.

A service answers small requests comfortably during development. On the first busy day, a dependency slows down, queues grow and people retry because the page gives no useful status. The service may still be technically available, but the outcome is no longer dependable. A meaningful target gives Product, Architecture, Development, Operations and Testing a shared account of what should remain true and how recovery will be shown.

There is no universal availability percentage, capacity multiplier, Recovery Time Objective (RTO) or Recovery Point Objective (RPO) that is correct for every service. The target follows the outcome, affected people, obligations, operating window, dependency behaviour, cost of failure and recovery authority.

## Define the service target

The Product Manager, Product Owner or business authority brings the outcome, consequence, priority and accepted trade-off. Operations, the Service Provider, Architect and relevant specialists add the conditions and evidence their responsibilities require. The target should distinguish:

- the capability or service promise that must be available;
- the people, connected systems and operating periods affected;
- the workload: requests, users, data volume, concurrency, batch size and expected growth;
- response-time, throughput, error-rate and resource-use expectations;
- the capacity point at which the service must scale, queue, reject or degrade;
- required, optional and replaceable dependencies;
- acceptable degraded modes and the actions that must fail closed or remain available;
- **RTO:** the maximum acceptable time to restore the required service after a defined failure; and
- **RPO:** the maximum acceptable loss or gap in recoverable information after a defined failure.

State the target as a predicate with conditions and evidence. For example:

> During the published operating period and expected peak workload, an authorised user can submit a request within the agreed response-time condition. If the non-critical notification dependency fails, submission remains available and the notification is queued with visible status. If the authoritative store fails, the service stops accepting new submissions rather than claiming success. The service restores the required submission capability within the agreed RTO, with information loss no greater than the agreed RPO.

The example is a shape, not a default target. The actual values, operating period, workload, dependency classification and evidence must be decided for the service.

## Design the boundary

The Architect and technical roles translate the target into a coherent design. The design should make visible:

- which boundary owns the availability promise and which dependencies it cannot control;
- the source of truth for capacity, health, state and recovery evidence;
- required versus optional dependencies and the consequence of each failure;
- timeout, cancellation, retry, backoff, idempotency, queue, quarantine and reconciliation behaviour;
- fail-closed, fail-open, read-only, queued, delayed or unavailable modes, with their authority and user meaning;
- capacity headroom, scaling triggers, saturation limits and admission or load-shedding rules;
- state preservation, backup, restore, replication, failover and migration conditions;
- observability for latency, errors, throughput, saturation, dependency health and degraded mode; and
- the rollback, recovery and compatibility consequences of changing the design.

Do not call a dependency optional merely because the happy path can be coded without it. The decision depends on what the capability is allowed to promise when that dependency is unavailable.

See [Operational Readiness, Observability and Recovery](../../../stakeholders/deliverers/operators/readiness-observability-and-recovery.md) for dependency and degradation decisions and [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md) for dependency contracts and failure policy.

## Build to the target

Development and Delivery implement the designed behaviour and its operational evidence. This may include:

- bounded timeouts and cancellation rather than unbounded waiting;
- retries only where the operation and contract make repetition safe;
- idempotency, deduplication and reconciliation for retried or queued work;
- capacity limits that fail predictably rather than exhausting a shared resource;
- metrics and structured diagnostics that identify capability, dependency, version and correlation context;
- configuration and infrastructure that can be reproduced, changed and rolled back;
- backup, restore, migration and failover procedures exercised with representative data; and
- versioned runbooks, support information and maintenance instructions that match the deployed system.

Implementation must not quietly choose a more generous promise than the accepted target, or hide a capacity or recovery limit because the limitation is inconvenient to expose.

## Operate to the target

Operations and Monitoring establish how the live service is judged against its target. Operational material should state:

- the healthy, degraded, overloaded, recovering and failed conditions;
- the signals and thresholds that trigger investigation, scaling, queueing, communication or recovery;
- the responsible boundary for each resource and dependency signal;
- the permitted actions, authority and safety checks;
- how actual workload and growth are reviewed against capacity;
- how an RTO or RPO breach is detected and recorded; and
- when a repeated breach returns the question to Product, Definition, Design or Maintenance through [Incident Learning and Corrective Change](../../../stakeholders/deliverers/operators/incident-learning-and-corrective-change.md).

An alert without a target or permitted response is not evidence of control. A target without a signal, responsible person or team and operating procedure is not an operational promise.

## Prove the target

Testing and Assurance should select evidence that matches the claim. Depending on the service, this may include:

- representative load, concurrency, data-volume and peak-workload tests;
- latency, throughput, error-rate and saturation evidence at the agreed workload;
- dependency outage, timeout, retry exhaustion, queue backlog and partial-failure tests;
- degraded-mode tests proving that the service does not claim success when it cannot safely provide it;
- backup, restore, failover, migration and recovery rehearsals using representative conditions;
- measurement of the actual RTO and RPO under the defined failure scenarios;
- sustained operation evidence where the target concerns time, accumulation or resource exhaustion;
- accessibility and support evidence for degraded or recovery interactions; and
- operational review showing that alerts, runbooks, escalation and records are usable by the people responsible for them.

A passing local benchmark does not prove a service-level target. Evidence must identify the environment, version, workload, dependency conditions, data shape, measurement method, result, limitation and decision authority.

## Review and change

Targets should be revisited when the outcome, affected population, operating window, workload, dependency, obligation, architecture, supplier or recovery assumption changes. A target may be changed only through the authority that owns the service promise and the specialist conditions it affects. Record the evidence, alternatives, residual risk, implementation work and verification needed for the change.

The control is complete when a reader can trace the target from outcome and consequence through design, implementation, operation and assurance, and can identify who decides when the evidence no longer supports the promise.

## Related guidance

- [Quality Characteristics](../../../shared/reference/catalogues/qualities.md)
- [Acceptance and Evidence](../../../stakeholders/deliverers/product-owners/acceptance-and-evidence.md)
- [Operational Readiness, Observability and Recovery](../../../stakeholders/deliverers/operators/readiness-observability-and-recovery.md)
- [Incident Learning and Corrective Change](../../../stakeholders/deliverers/operators/incident-learning-and-corrective-change.md)
- [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md)
- [Testing Evidence and Boundaries](../../../stakeholders/deliverers/testers/evidence-and-boundaries.md)
- [Performance Conventions](../../../../agents/conventions/development/performance.md)
- [Operations Conventions](../../../../agents/conventions/development/operations.md)
