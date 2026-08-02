# Operational Readiness, Observability and Recovery

Operations keeps the delivered service available, observable, secure and recoverable. The operator's first question is not only whether the process is running. It is whether the service is ready to provide its promised capabilities, whether its dependencies are safe to use and what controlled action is appropriate when a condition changes.

You may be reading this because a condition was detected from a user report or a service signal. When the problem came from a user report, see [Support Triage and Escalation](../support/triage-and-escalation.md) to preserve the case context before diagnosis.

## Readiness is a decision

Readiness should answer whether the service can accept or complete the work it claims to support. Define the conditions that must hold before readiness is reported, including configuration, secret resolution, storage, identity, required dependencies, schema, startup participants and any capability-specific prerequisites.

Keep these states distinct:

- **Starting:** the service is assembling its required participants and dependencies.
- **Ready:** the service can safely accept the work covered by the readiness contract.
- **Not ready:** the service must not receive or advertise work that depends on an unavailable or unsafe condition.
- **Degraded:** the service is available with an explicit limitation, such as a read-only mode, delayed processing or unavailable optional capability.
- **Failed:** the service cannot provide the required capability and needs restart, intervention, dependency recovery or another defined response.
- **Stopping:** the service is withdrawing safely, completing or abandoning work according to its shutdown contract.

A process that responds to a health endpoint is not necessarily ready. A readiness result must be meaningful to the boundary that routes work and to the operator who must decide whether to continue, drain, restart, isolate, fail over or escalate.

## Observability supports action

Operational information should help an operator answer:

- What is happening now?
- Which capability, dependency or resource is affected?
- When did the condition begin and how wide is its impact?
- Is the service failing, degrading, recovering or behaving normally?
- What action is authorised and safe at this stage?
- How can the action and its result be recorded?

Provide the signals needed to answer those questions:

- structured logs with correlation, operation, actor, resource and outcome fields where appropriate;
- metrics for throughput, latency, failures, saturation, dependency health and resource use;
- traces for work that crosses service boundaries, without copying sensitive payloads into spans;
- dashboards that distinguish user impact, service condition and infrastructure condition; and
- alerts tied to an operator decision, not merely to an interesting measurement.

Diagnostics must be useful without exposing credentials, tokens, secrets or unnecessary personal information. A technically detailed signal that cannot be safely shown to an operator is not a complete operational signal.

## Operations, Monitoring and privileged restoration

**Monitoring** is the capability that observes service signals and makes relevant conditions visible. **Operations** is the broader accountability for using those signals, readiness definitions, controls and procedures to keep the live service available, secure and recoverable. Monitoring may be performed by a dedicated monitoring or observability team, by Operations or through an automated service, but producing an alert is not the same as deciding or performing the response.

Recovery actions must have explicit authority. Identify which actions are routine and permitted to an operator, which require approval or a second person, and which require an elevated role such as infrastructure, platform, database, Security, Service Provider or Maintenance authority. Resets, restores, failover, secret rotation, data correction and disabling protections must not become generally available merely because they are useful during an incident. Every privileged action needs a defined trigger, scope, audit record, verification step and escalation or rollback path.

Operations may coordinate an action without owning every privilege needed to execute it. A monitoring team may detect and communicate a condition without owning recovery. A Maintenance Developer may repair the service without receiving unrestricted production access. The service provider or infrastructure owner may perform a platform restoration without becoming the authority for business meaning or user support. Keep detection, decision, execution and verification responsibilities visible.

## Dependency and degradation decisions

For each required dependency, define the expected failure conditions and the service response. The service may fail closed, fail open, degrade, queue work, become read-only or stop accepting requests, but the choice must follow the capability's meaning and risk.

Define:

- timeout and cancellation behaviour;
- retry conditions, limits, backoff and jitter;
- idempotency for retried commands;
- queue, quarantine and replay rules for durable work;
- partial-success and reconciliation behaviour;
- the boundary between optional and required dependencies;
- the condition that returns the service to normal operation; and
- the evidence and communication required when users or connected systems are affected.

Operations applies these rules and records what happened. Operations does not invent new business meaning or silently change authorisation to work around a dependency failure.

## Recovery is part of normal design

Recovery procedures should cover failures that can reasonably recur, including dependency outage, timeout, retry exhaustion, process restart, failed deployment, data inconsistency, queue backlog, poison messages, capacity exhaustion and loss of an operational resource.

A recovery procedure should identify:

- the trigger and evidence that justify the action;
- the responsible operator and required authority;
- the safety checks and protected data boundaries;
- the exact permitted action and its expected effect;
- how concurrent work, retries and duplicate execution are controlled;
- how success or continued failure is verified; and
- when to escalate to Support, the Service Provider, Maintenance, Security or another owner.

Testers provide evidence that the service's failure and recovery behaviour works under stated conditions. Operations verifies that the resulting signals, procedures and access are usable in the actual operating environment. Maintenance changes the service when the behaviour or operational material is insufficient.

Recovery evidence should not disappear after service restoration. See [Incident Learning and Corrective Change](./incident-learning-and-corrective-change.md) for the handoff from recovery evidence to learning, an authorised decision and verification.

## Operational deliverables

The resulting [Operational Manuals or Information](../../reference/catalogues/deliverables.md) should include readiness definitions, health and diagnostic interpretation, deployment and configuration responsibilities, monitoring and alert response, routine actions, dependency failure, recovery, escalation and evidence retention. They are distinct from:

- **Support Manuals or Information**, which help Support understand user reports and provide permitted assistance; and
- **Maintenance Manuals or Information**, which help maintainers change, repair, upgrade, migrate, deprecate or retire the service.

Operational information must be versioned with the service and environment it describes. An obsolete runbook can be more dangerous than no runbook if it gives an operator confidence in an action that no longer matches the deployed system.

## Related guidance

- [Operations Guidance](./readme.md)
- [Operations Conventions](../../../agents/conventions/development/operations.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [External Dependencies](../../reference/catalogues/external-dependencies.md)
- [System LDM Service Readiness](../../reference/platform-services.md)
- [Testing Evidence and Boundaries](../testers/evidence-and-boundaries.md)
- [Support Triage and Escalation](../support/triage-and-escalation.md)
- [Maintenance Guidance](../maintainers/readme.md)
