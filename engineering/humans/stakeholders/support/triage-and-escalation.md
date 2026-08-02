# Support Triage and Escalation

Support is the first human point of contact for end users. The first task is not to guess the technical cause. It is to understand the report well enough to help the person, protect their information and send the right evidence to the responsible boundary.

## The person and the impact

Record the minimum information needed to understand and act on the report:

- who is reporting and, where relevant, who is affected;
- the service, capability or journey involved;
- what the person expected and what happened instead;
- when and where it happened, including environment or channel;
- the visible symptom, error or confusing state;
- the impact, urgency and whether work is blocked;
- what the person has already tried;
- the case or correlation identity;
- the classification and privacy limits for the information; and
- the safe next action or explanation already given.

Do not collect sensitive information merely because it might be useful later. Do not ask a person to send credentials, tokens, unnecessary personal information or unrestricted screenshots. Use approved evidence routes and redact or minimise material before sharing it.

## The tier decision

Tier labels are defined by the Service Provider. A common route is:

- **Tier 0:** the person may use approved self-service, status information or guided help when the problem is suitable for it.
- **Tier 1 Support:** the first human contact records the report, confirms the relevant context, applies documented safe responses and remains responsible for communication with the person.
- **Tier 2:** see [Operator Guidance](../operators/readme.md) for the Service Provider, Operations or another designated specialist to check service status, known incidents, operational evidence, dependency state and actions within its authority.
- **Tier 3:** Maintenance Developers or an infrastructure or platform maintenance owner investigate code, schema, dependencies, configuration, compatibility or infrastructure and make controlled changes where authorised.

A report may move between tiers more than once. The tier is not a statement about the user's worth or the staff member's seniority. It identifies the depth of investigation and authority required for the next action.

## What each handoff must preserve

When Support escalates a report, the receiving group should not need to reconstruct the user's story. The handoff should include the case identity, affected capability, expected and observed behaviour, time and environment, impact, reproduction or attempted steps, relevant safe evidence, classification, actions already taken, current owner, requested question and return condition.

Tier 2 should return an operational finding, such as a known incident, dependency condition, readiness problem, permitted recovery action or statement that no operational cause has been found. It should not silently turn an operational observation into an application change.

Tier 3 should return a technical finding, controlled change, workaround, defect record, compatibility decision, rollback or recovery result, and the evidence that supports it. A technical finding does not automatically decide business meaning, policy, entitlement or product acceptance.

## Return the answer to the person

The case is not complete when the technical group closes its task. Tier 1 Support must receive enough information to explain the result, workaround, limitation, restoration or next expectation to the person. The response should state what is known, what was done, what remains uncertain, what the person should do next and how to report a recurrence.

If the same report recurs, Support should link the cases and raise the pattern to the Service Provider. Repeated reports may indicate a defect, an unclear journey, a missing requirement, an operational weakness, a manual that is not useful or a capability whose boundary is wrong.

## What Support must not do

Support must not:

- bypass normal authorisation by impersonating a user;
- disclose information merely because it is technically visible;
- alter business records without a permitted, evidenced correction route;
- change code, schema, infrastructure or protected configuration as an informal workaround;
- declare a defect, security event, operational incident or product acceptance decision without the relevant authority; or
- close a report without a user-facing explanation, a recorded reason or an explicit handoff.

## Related guidance

- [Support Guidance](./readme.md)
- [Support Manuals or Information](../../reference/catalogues/deliverables.md)
- [System Roles](../../reference/catalogues/system-roles.md)
- [Operations Guidance](../operators/readme.md)
- [Maintenance Guidance](../maintainers/readme.md)
- [Testing Guidance](../testers/readme.md)
- [Shared Requirements](../../shared/requirements.md)
