# System Roles to Consider

A system role is a named access or responsibility context used by a service to decide what an actor may see, change, invoke or administer. It is not automatically a job title, stakeholder category, site, Domain or implementation class.

The service should evaluate permissions using the actor, resource, action, context and applicable policy. A role can help group permissions, but a role name alone is not proof that an action is safe or authorised.

This catalogue is a recognition aid for analysis and design. Select the roles that fit the service, define their scope and authority, and record the evidence for each important permission. Do not create every role merely because the name appears on this page.

## Public or anonymous visitor

An actor without an established authenticated identity. This role may discover deliberately public information, begin registration or submit a narrowly controlled request.

Define what is genuinely public, what is rate-limited, what can be submitted without an account, how abuse is controlled and what information must not be disclosed through errors, search or enumeration.

## Authenticated consumer

A person or organisation acting for itself within a consumer relationship. The role may view, prepare, submit, track, update or withdraw its own work according to lifecycle and policy.

Do not assume that authentication grants access to every record associated with an email address, organisation or account. Resource scope, representation, consent and current authority still matter.

## Representative or delegated consumer

An actor helping or acting for another person or organisation under a defined delegation, representation or consent. The role needs explicit subject scope, permitted actions, duration, revocation, conflict handling and audit.

Assistance is not automatically decision authority. A representative may prepare information without being allowed to approve, withdraw or alter the represented person's rights.

## Provider or fulfilment role

An actor delivering the service, managing a case, fulfilling an approved request, allocating a resource or publishing an outcome. Provider permissions are usually scoped by organisation, team, case, resource, geography, period or separation-of-duty rule.

Do not implement “provider” as unrestricted access to all consumer data or all administrative functions.

## Assessor or reviewer

An actor who examines information, evidence or a request and records findings, recommendations or review status. The role may have read, annotation and request-for-information permissions without having approval authority.

Define evidence version, confidentiality, conflict of interest, assignment, reassignment, escalation and audit requirements.

## Decision-maker or approver

An actor authorised to make a formal decision, approve a transition, reject a request or accept a controlled outcome. The role must be tied to the relevant decision, authority, scope, delegation, separation of duties and record.

A person may be an assessor and an approver in different contexts, but do not combine the permissions when independence or policy requires separation.

## Support role

An actor who investigates and assists another user. Support permissions should be purpose-specific and may include limited lookup, guided actions, communication, permitted correction and escalation.

Support access must respect privacy, classification, impersonation, consent, audit and minimum-necessary principles. A support role is not a hidden route around normal authorisation.

## Operations role

An actor responsible for running, observing and recovering the live service. The role may view readiness, health, alerts, queues, dependency state and operational evidence, and may perform controlled interventions within a defined authority.

Operations access should not automatically grant business decision, unrestricted data, deployment or maintenance authority. Operational actions need safe boundaries, audit and recovery evidence.

## Monitoring or observability role

An actor or system that collects, views or analyses health, performance, security and operational signals. Monitoring data may contain personal, confidential or security-sensitive information and needs its own classification and access rules.

Separate the ability to observe a signal from the ability to change the service. Do not assume that logs, traces and metrics are harmless merely because they are not primary records.

## Maintenance role

An actor who changes, repairs, upgrades, migrates, configures or retires the service. Maintenance permissions can affect the conditions under which every other role operates and therefore need strong scope, approval, audit, separation, rollback and recovery controls.

Maintenance access is not a general-purpose administrator shortcut. It should be available only through controlled procedures and only for the required capability.

## Release or change-control role

An actor who reviews, schedules, approves, coordinates or records a change to the service, environment, configuration, data or dependency. This role may approve a change without being able to implement it, or implement an emergency change under a separate procedure.

Keep change authority, technical execution, business acceptance and operational readiness distinct where the consequences require it.

## Security, privacy or records role

An actor responsible for reviewing or administering security, privacy, records, retention, access, classification, legal hold, deletion or anonymisation controls. The role's authority should be specific to the applicable obligation and data or system scope.

Do not use this role as a reason to give unrestricted access to all records. Define the evidence needed and the least-privilege route for obtaining it.

## Auditor, regulator or assurance role

An actor who inspects evidence, controls, records, decisions, reports or service operation under a defined authority. The role may be read-only, time-limited, case-scoped or mediated through an export or evidence package.

An assurance role should be able to verify the relevant claim without automatically becoming an operator, maintainer or data administrator.

## Service account or automated actor

A non-human actor that invokes a capability, exchanges information, runs a scheduled operation or performs a controlled lifecycle action. Identify its owner, purpose, credential or key lifecycle, scope, source, destination, rate, retry, idempotency, audit and retirement conditions.

Do not model a service account as a human administrator merely because it needs a technical permission. Give it the narrowest machine capability and make its actions distinguishable from human actions.

## Integration partner role

An external organisation or connected system acting through an agreed contract. The role needs explicit data, operation, version, identity, trust, rate, availability, failure, reconciliation and termination rules.

A partner role does not imply access to internal models, shared storage or every capability available to the organisation's own staff.

## Role scope and context

Every system role should be analysed with its scope:

- **Subject:** who or what is acting.
- **Resource:** which record, capability, Domain or system is affected.
- **Action:** what the actor may read, create, change, submit, approve, publish, export or administer.
- **Context:** organisation, team, case, site, location, relationship, time, device or workflow state.
- **Authority:** why the action is permitted and who can grant, delegate, revoke or review it.
- **Conditions:** what must be true before the action is allowed.
- **Evidence:** what is recorded and how the decision can be inspected.
- **Lifecycle:** how the role is established, changed, suspended, expired and retired.

The permission predicate should be expressed at the responsible boundary. A role should help the system find a policy; it should not become the policy's only explanation.

## Role discovery questions

For each proposed system role, ask:

- Which stakeholder or user responsibility does it support?
- Is it a real access distinction or only a job title, screen or team label?
- Which resources and actions are in scope?
- What is the least authority that fulfils the responsibility?
- Which contextual conditions affect the decision?
- What must be denied, separated or independently reviewed?
- What evidence, notification, retention and recovery obligations apply?
- Who owns role creation, review, delegation, revocation and emergency access?
- Does the role need a site, an API, a support route or no direct interface?
- What happens when the person changes team, organisation or responsibility?

## Do not collapse these terms

- A **stakeholder** may be affected without using the system.
- A **user** directly uses a capability or consumes its result.
- A **system role** is an access or responsibility context enforced by the service.
- A **business role** describes responsibility in the real world.
- An **implementation role** describes what a software component does.
- A **site** curates capabilities and information for a responsibility; it is not a permission boundary by itself.

See the [Guidance Glossary](../glossary.md#polysemy) for the wider distinction.

## Related guidance

- [Users to Consider](./users.md)
- [Stakeholder Roles](./stakeholder-roles.md)
- [Sites](./sites.md)
- [Regulatory and Obligation Domains](./regulatory-obligations.md)
- [Security Conventions](../../../agents/conventions/foundations/data-protection.md)
- [Elicitation](../../stakeholders/business-analysts/elicitation.md)
- [Functional and Quality Requirements](../../stakeholders/business-analysts/functional-and-quality-requirements.md)
