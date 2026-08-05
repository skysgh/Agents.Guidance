[Up](readme.md)

# Controlled Change and Lifecycle Maintenance

Maintenance changes an occupied service while people, connected systems, operators and obligations already rely on it. The maintenance question is therefore not only whether a change works in isolation. It is whether the change preserves or deliberately manages the existing meaning, compatibility, data, operation, evidence and recovery that the service already owes.

## Establish the change boundary

Before changing code, configuration, schema, dependencies or infrastructure, identify:

- the capability, contract, data or operational behaviour being changed;
- the people, systems, providers and processes that depend on it;
- the current deployed versions and compatibility obligations;
- the authority for meaning, policy, security, privacy, records and operation;
- the required evidence and recovery route; and
- the condition under which the change is complete, deferred, rolled back or retired.

Use the accepted solution and technical design records as inputs, but inspect the occupied service and its evidence. A maintenance change must not treat undocumented behaviour as irrelevant merely because it is inconvenient or absent from the original design.

## Preserve compatibility deliberately

For every published interface, event, file, schema, user journey or operational procedure, decide whether compatibility is required, can be adapted, or may be broken under an approved transition. Record:

- the current and target versions;
- consumers and producers that must continue to work;
- additive, tolerant or translation behaviour where compatibility is preserved;
- deprecation communication and support period where removal is planned;
- migration order and rollback limits; and
- the tests and operational evidence that prove the transition.

A version number alone does not make a change compatible. Compatibility belongs to the meaning and behaviour that consumers rely upon. Do not remove an old contract until its consumers, data, support route, monitoring and recovery consequences are understood and the retirement authority has approved the removal.

## Treat data and dependencies as lived obligations

Schema, data and dependency changes require more than a successful build. Define the authority, classification, transformation, validation, reconciliation, retention, deletion, recovery and rollback behaviour for affected data.

For dependency or provider changes, record the reason, supported versions, security and operational consequences, licensing or supplier obligations, exit path, performance and capacity effects, and the evidence needed before promotion. A provider's upgrade guide is input, not a substitute for the service's own responsibility and acceptance evidence.

A migration should identify its preconditions, sequencing, resumability, duplicate or partial-work behaviour, verification, failure handling and post-migration cleanup. If rollback is impossible after a point, state that boundary and provide recovery or forward-correction evidence instead.

## Change the occupied service safely

Use a controlled path that includes:

- a linked work item and accepted change intent;
- the relevant Technical Design Document, decision or contract update;
- impact, risk, security, privacy, records and operational review where applicable;
- focused tests and broader regression evidence appropriate to the affected boundary;
- deployment, migration, monitoring and rollback or recovery preparation;
- Support and Operations communication for user-visible or live-service consequences; and
- post-change verification and a record of what actually happened.

Maintenance Developers make the technical change and investigate its consequences. They do not silently accept a new business rule, policy, security decision, data authority or operational policy merely because the change is being made in code. The responsible authority must decide those matters.

## Learn from incidents without hiding the cause

An incident, recurring Support report, failed test, operational warning or difficult recovery may expose a defect in the service, a missing requirement, an unclear contract, an inadequate test, an unsafe operational procedure or an incorrect ownership boundary. Record the evidence and route the underlying question to the responsible role.

Do not close the learning by weakening the test, deleting the warning, changing the record without explanation or making a private workaround permanent. A temporary mitigation needs an owner, expiry or review condition and a credible path to a durable correction.

## Retire and replace deliberately

Retirement is a change with its own obligations. Define the replacement or end state, affected consumers, data retention and deletion, export or archive, contract communication, access removal, monitoring removal, provider termination, support closure, operational recovery implications and evidence of completion.

A service is not retired merely because its deployment was stopped. Its domains, data, identities, certificates, routes, queues, integrations, documentation, support knowledge and supplier commitments must each have an explicit disposition.

## Maintenance deliverables

The resulting [Maintenance Manuals or Information](../../../shared/reference/catalogues/deliverables.md) should make the occupied service understandable to a maintainer who did not build it. They should cover architecture decisions, contracts, dependencies, compatibility, migration, rollback, recovery, data protection, repair, deprecation, replacement and decommissioning.

These are distinct from:

- **Operational Manuals or Information**, which enable safe live operation and recovery; and
- **Support Manuals or Information**, which enable user assistance, diagnosis and escalation.

## Related guidance

- [Maintenance Guidance](./readme.md)
- [SDLC: Maintenance and Decommissioning](../../../shared/reference/catalogues/sdlc.md)
- [API Lifecycle](../../../foundations/api-lifecycle.md)
- [Dependency and Supply-Chain Conventions](../../../../agents/conventions/development/dependencies.md)
- [Deliverables](../../../shared/reference/catalogues/deliverables.md)
- [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md)
- [Operations Guidance](../operators/readme.md)
- [Testing Evidence and Boundaries](../testers/evidence-and-boundaries.md)
- [Support Triage and Escalation](../support/triage-and-escalation.md)
