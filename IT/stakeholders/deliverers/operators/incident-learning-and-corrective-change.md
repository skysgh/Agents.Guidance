[Up](./readme.md)

# Incident Learning and Corrective Change


An incident is evidence that the live service did not behave, remain available, remain secure or remain understandable as expected. Incident response restores or protects the service. Incident learning asks what the evidence changes about the service's meaning, design, policy, operation or lifecycle. Corrective change carries that decision into the relevant lifecycle work and verifies that the risk has actually reduced.

This guidance does not make Operations the owner of product meaning or architecture. It gives each responsibility a clear handoff.

## The control boundary

- **Operations** detects or receives the report, protects people and data, restores service within its authority, records the observable facts and escalates the unresolved question.
- **The responsible service or product authority** decides the user, business, policy or risk consequence, including whether a workaround is acceptable and whether work must be prioritised.
- **The Architect** decides or recommends the structural response within architecture authority: a boundary, dependency, contract, model, resilience or observability change. The Architect returns unresolved domain or policy meaning to the relevant authority.
- **Maintenance or Development** implements the approved corrective change, including migration, compatibility, operational material and rollback where needed.
- **Test, Operations and Assurance** provide evidence that the change works under the incident conditions and that the operational control has been restored.

No role should close a material incident merely because the service was restarted or a workaround succeeded.

## Response, learning and change

Keep these stages distinct:

1. **Respond:** make the situation safe, protect affected people and records, communicate through the approved route and restore service or provide a controlled alternative.
2. **Record:** preserve time, symptoms, affected capability and users, relevant versions and configuration, signals, actions, decisions, dependencies and uncertainty. Do not copy secrets or unnecessary personal data into the incident record.
3. **Learn:** determine whether the incident exposed a wrong assumption, unclear requirement, policy conflict, model or boundary problem, contract failure, missing operational control, dependency weakness or inadequate evidence.
4. **Decide:** assign the consequence to the authority that can accept, prioritise, defer or reject it. Record the decision, evidence, residual risk, owner and review condition.
5. **Correct:** create or update the appropriate Definition, Design, Development, Delivery, Operations or Maintenance work. Link it to the incident record rather than relying on memory or an untraceable ticket title.
6. **Verify:** test the original failure condition, confirm the intended operational signal and procedure, and check that the corrective change did not create an unacceptable new risk.

An operational fix may close the response while learning and corrective work remain open. A low-consequence event may need only a recorded operational improvement. The decision must state why further work is not required when the incident reveals a plausible design, policy, security, privacy, records or lifecycle question.

## Incident record minimum

The incident record should make these facts discoverable:

- incident identifier, detection time, reporter and responsible service boundary;
- affected capability, users, connected systems, data or obligations;
- observed symptoms and impact, separated from hypotheses;
- deployed version, relevant configuration, dependencies and change history;
- immediate actions, authority used, recovery result and remaining workaround;
- evidence collected, including links to logs, tests, alerts, communications and records with appropriate access control;
- learning question and classification of the possible gap;
- decision authority, decision, alternatives, accepted residual risk and review condition;
- corrective work items and their responsible boundaries; and
- verification result, closure authority and date.

The record may link to specialist or protected evidence rather than copying it. Retention, privacy, access, provenance and audit requirements still apply.

## When to escalate beyond Operations

Escalate the learning question when any of the following is true:

- recovery required an action outside the documented authority or changed a security boundary;
- the same symptom has recurred or a workaround is becoming normal operation;
- the incident affected a material outcome, obligation, record, privacy boundary or accessibility need;
- the observed behaviour contradicts a requirement, contract, model, policy, quality target or lifecycle condition;
- the cause or affected boundary is uncertain enough that another change could hide the risk; or
- a supplier, dependency, migration, compatibility or deprecation assumption may no longer hold.

The escalation route should identify the responsible product or business authority, Architect, Maintenance owner and specialist owners as applicable. It should not turn every alert into a design meeting.

## Evidence across the lifecycle

A complete corrective-change trail can be followed in both directions:

```text
Incident evidence
  -> learning question
  -> authorised decision or recorded deferral
  -> Definition, Design or policy change
  -> implementation and delivery evidence
  -> operational procedure and signal
  -> test and assurance result
  -> incident closure and review
```

The relevant lifecycle phase is determined by the question. A wrong business outcome may return to Discovery or Discussion. An unclear obligation may return to Definition. A broken boundary, contract or failure behaviour may return to Design. A code, configuration or runbook defect may go to Maintenance or Development. A release, migration or compatibility problem may require Delivery work. The incident record should name the return point and why.

## Verification questions

Before closing the learning part of a material incident, ask:

- Can an operator explain what was observed, what was done and what remained uncertain?
- Is the responsible authority for the consequence and decision explicit?
- Can the corrective work be traced to the incident and back to its verification evidence?
- Does the test reproduce the relevant failure or risk, not only the happy path?
- Are monitoring, alerting, runbook, support and recovery materials updated with the delivered change?
- Has the original workaround been removed, constrained or given an owner and expiry condition?
- Are residual risk, accepted deferral and review date visible to the people who rely on them?

Incident learning is complete when the evidence supports the decision, the responsible boundary owns the remaining risk and the service's future behaviour is more dependable than the behaviour that produced the incident.

## Related guidance

- [Software Development Lifecycle](../../../shared/reference/catalogues/sdlc.md)
- [Readiness, Observability and Recovery](./readiness-observability-and-recovery.md)
- [Shared Requirements](../../../shared/requirements.md)
- [Deliverables](../../../shared/reference/catalogues/deliverables.md)
- [Testing Evidence and Boundaries](../testers/evidence-and-boundaries.md)
- [Maintenance Guidance](../maintainers/readme.md)
