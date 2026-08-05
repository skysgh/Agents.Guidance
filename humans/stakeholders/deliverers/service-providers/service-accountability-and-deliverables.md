[Up](readme.md)

# Service Accountability and Deliverables

A Service Provider is accountable for providing an agreed service capability to its consumers and stakeholders. This is broader than owning a deployment or answering a support ticket. It includes ensuring that the service has the people, boundaries, information, controls and evidence needed across its life.

## The service promise

The Service Provider should be able to state:

- who the service is for and who is affected by it;
- what capability and outcome it provides;
- which contract, quality conditions and obligations apply;
- what is included, excluded or deliberately deferred;
- which dependencies and suppliers it relies on;
- who provides Support, Testing, Operations, Maintenance and specialist assurance;
- what happens when the service is degraded, unavailable, unsafe or retired; and
- what evidence shows that the service is being provided as promised.

The promise is not a brochure. It must connect to the requirements, contracts, deliverable systems, manuals, operational records and acceptance evidence that make the service real.

## Make responsibility visible

The Service Provider ensures that each material responsibility has an accountable owner or an explicit gap:

- **Support:** first human contact for end users, case understanding, communication and escalation;
- **Testing:** evidence that requirements, predicates, boundaries and quality claims hold;
- **Operations:** live-service readiness, observation, intervention and recovery;
- **Maintenance Developers:** technical investigation and controlled changes to the occupied service;
- **Infrastructure or organisational maintenance:** hosting, platform, network, facility or provider arrangements;
- **Security, privacy, records and assurance:** the obligations and evidence within their authority; and
- **Product, business and domain roles:** purpose, meaning, priority, policy and outcome decisions.

One person or supplier may perform more than one responsibility. The Service Provider must still record which responsibility is being exercised, what authority applies and what evidence is expected.

## The three operational information sets

The Service Provider ensures that distinct information exists for the groups that use it:

### Support Manuals or Information

Support needs user language, known symptoms, safe responses, permitted lookup and guided actions, communication material, escalation routes, ownership and links to authoritative evidence. See [Support Guidance](../support/readme.md).

### Operational Manuals or Information

Operations needs readiness, deployment, configuration, monitoring, alert response, access procedures, routine operation, dependency failure, recovery responsibilities and service status information. See [Operations Guidance](../operators/readme.md).

### Maintenance Manuals or Information

Maintenance Developers and other maintenance owners need architecture decisions, contracts, dependency lifecycle, compatibility, rollback, data protection, repair, migration, deprecation, replacement and decommissioning procedures. See [Maintenance Guidance](../maintainers/readme.md).

These information sets may link to common records, but they should not be collapsed into one document that is too technical for Support, too incomplete for Operations or too shallow for Maintenance.

## Readiness and acceptance

Before accepting a service or major change, the Service Provider should verify that:

- the consumer outcome and affected groups are understood;
- the required contracts, security and quality conditions are evidenced;
- Support can receive and explain a problem;
- Operations can identify readiness, degradation and recovery actions;
- Maintenance can investigate and change the occupied service safely;
- the required manuals or information are current and reachable;
- dependencies, suppliers and exit conditions are recorded; and
- exceptions have an owner, authority, temporary control, review trigger and evidence needed for closure.

The Service Provider does not replace the specialist acceptance authority. It ensures the relevant people are involved and that an absence, disagreement or residual risk is visible rather than hidden by a general statement that the service is ready.

## Service life

Accountability continues after first release. The Service Provider must maintain a route for:

- recurring support reports and incident learning;
- changes in workload, users, policy, security or regulation;
- dependency, supplier and platform change;
- compatibility, migration and deprecation;
- staffing changes and loss of local knowledge;
- backup, recovery and continuity evidence; and
- replacement, retirement, records, data and access closure.

A service is not fully provided when it can be started. It is provided when the people who use, support, operate, test, maintain, change and retire it can perform their responsibilities with appropriate authority and evidence.

## Related guidance

- [Service Provider Guidance](./readme.md)
- [Deliverables](../../../shared/reference/catalogues/deliverables.md)
- [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md)
- [Support Guidance](../support/readme.md)
- [Testing Guidance](../testers/readme.md)
- [Operations Guidance](../operators/readme.md)
- [Maintenance Guidance](../maintainers/readme.md)
- [Shared Requirements](../../../shared/requirements.md)
