[Up](readme.md)

# Support Access and Guided Action

Support often needs more information than an ordinary user can see, but that does not make Support a universal administrator. Support access exists to help a person with a defined case and must remain limited, purposeful, visible and reversible.

## Purpose-specific access

For each Support capability, define:

- the user problem it helps resolve;
- the actor, case, resource and context that limit access;
- the information Support may view and why it is necessary;
- the actions Support may perform, including any correction or replay;
- the consent, delegation or notification condition where another person is affected;
- the approval or separation-of-duties condition;
- the audit record and retention requirement;
- the safe failure and escalation route; and
- the condition that ends or removes access.

A support role should normally be case-scoped, time-limited or task-specific where the service can provide that boundary. A broad role name is not enough evidence that every support action is appropriate.

## Assisted use is not impersonation

Support may guide a person through a normal journey or perform a permitted action on their behalf. Those are different from silently pretending to be the person. The system should preserve the identity of the Support actor, the represented person, the case, the reason and the action taken.

Where an action changes a protected record, entitlement, consent, approval, payment, submission or other consequential state, define whether Support may prepare it, request it, witness it, execute it under delegated authority or only explain how the person can perform it. Do not use a support tool to bypass the service's ordinary authorisation or evidence requirements.

## Minimum necessary information

Support should see the smallest amount of information needed to understand and resolve the case. Mask, filter or project protected fields. Do not expose full credentials, secrets, tokens, payment information or unrelated records. Screenshots, exports, logs and diagnostic bundles need their own classification and retention rules.

Support should be able to explain to the person what information was accessed and why where policy or law requires it. Access that is technically available but not necessary for the case is not justified by convenience.

## Guided actions and correction

A guided action is a controlled operation that helps resolve a known situation without changing the service's underlying design. It may include resending an approved notification, reopening a permitted user step, initiating a documented reconciliation or recording a correction request.

For every guided action, define:

- the preconditions and permitted scope;
- whether it is idempotent and safe to repeat;
- the information shown before confirmation;
- who may request, approve and execute it;
- the audit and user-notification record;
- the failure, cancellation and rollback behaviour; and
- when the action must become a Maintenance, Operations, security, privacy, records or business decision.

Support must not edit a database, replay a message, change configuration or alter a business record through an informal script merely because the normal interface is inconvenient. A recurring need for such action is evidence that the service or its Support deliverables need improvement.

## Support tooling is a deliverable system

A Support console, case system, diagnostic view, export or communication channel is part of the delivered support capability. Define its users, permissions, data classification, audit, availability, retention, support route and retirement conditions. A tool used by Support can create a second path into the service; it must be designed and tested as a real boundary.

## Related guidance

- [Support Guidance](./readme.md)
- [Support Triage and Escalation](./triage-and-escalation.md)
- [Support Manuals or Information](../../../shared/reference/catalogues/deliverables.md)
- [System Roles](../../../shared/reference/catalogues/system-roles.md)
- [Data Protection](../../../development/data-deletion-guidance.md)
- [Operations Guidance](../operators/readme.md)
- [Maintenance Guidance](../maintainers/readme.md)
