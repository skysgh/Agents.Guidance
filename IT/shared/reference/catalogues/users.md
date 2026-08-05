[Up](./readme.md)

# Users to Consider


A [user](../glossary.md#user) is a person, group or connected system that directly uses a site, capability, information or result. A [stakeholder](../glossary.md#stakeholder) is broader: a stakeholder may be affected, hold authority, supply knowledge or carry consequences without directly using the service.

This catalogue is a recognition aid for elicitation. It is not a mandatory checklist and it is not a claim that every category exists in every service. The Stakeholder Analyst should select the categories that matter, identify representative people or systems and record which perspectives remain unrepresented.

## Direct service users

People who use the service directly to achieve a goal. Consider differences in:

- experience, confidence and domain knowledge;
- accessibility, language, device and connection;
- location, working hours and support needs;
- authority, organisation and relationship to the record; and
- frequency, urgency and consequence of use.

Do not treat the most familiar or technically confident user as representative of everyone who must use the service.

## People represented in the service

A person may be the subject of a record, assessment, entitlement, decision or communication without operating the service. Consider applicants, recipients, patients, students, employees, customers, residents, children, dependants, complainants and other people whose information or outcome is managed.

Their interests may require different language, privacy, safety, accessibility, notice, correction, appeal or evidence than the operator's needs.

A person who cannot use the service directly may still be the most important person to understand (eg: the Sponsor, the CEO, etc.).

## Beneficiaries and recipients

People or organisations who receive the service, payment, decision, entitlement, information or other outcome. They may differ from the person who requested or processed it.

Ask what they need to recognise, trust, challenge, correct or act on the result, including what happens when the result is late, wrong, inaccessible or unavailable.

## Applicants, requesters and submitters

People or systems that prepare and submit a request, application, order, claim, report or other formal intent. Consider preparation, saving, validation, submission, acknowledgement, withdrawal, resubmission, evidence, support and recovery from interruption.

Do not assume that submission is an ordinary edit. It may freeze information, establish a version, create an obligation or move a subject into assessment.

## Assessors, reviewers and decision-makers

People who inspect information, apply rules, make recommendations, approve, decline, escalate or request further information. Their needs often include evidence provenance, versioning, separation of duties, reason codes, comparison, conflict handling, history and appeal.

A person who can review information is not automatically authorised to make the decision. Keep user needs separate from system permissions and decision authority.

## Providers and fulfilment users

People or systems that deliver the service, allocate resources, fulfil an approved request, publish content, manage a case or carry out the organisation's responsibility. Provider users may need different concepts, states, queues, controls and evidence from consumers.

Do not design the provider view as merely a larger consumer screen. The provider may own decisions and records that the consumer can only observe.

## Intermediaries and representatives

People who act for, assist or advise another person or organisation, such as advisers, teachers, carers, agents, brokers, advocates or support workers. Their authority may be limited to helping, viewing, preparing or submitting; it does not automatically include making decisions for the represented person.

Record representation, consent, delegation, scope, expiry, conflicts and audit requirements explicitly.

## Support and service-desk users

People who help other users understand or recover from a service problem. Consider guided assistance, investigation, permitted correction, communication, escalation, privacy, impersonation risk and evidence of actions taken on another person's behalf.

Support access should not become unrestricted maintenance or provider access merely because it is convenient during a difficult case.

## Operations and monitoring users

People who keep the live service available, observable, secure and recoverable. Consider readiness, health, alerts, queues, dependency state, capacity, incidents, controlled intervention, escalation and recovery evidence.

The architect or developer may describe a likely operational need, but Operations and Monitoring representatives must provide or validate the operational knowledge and consequences.

## Maintenance and change-control users

People who change, repair, upgrade, migrate, configure, release, approve or retire the service. Consider dependency renewal, compatibility, rollback, schema change, access, deployment, emergency repair, evidence and decommissioning.

Maintenance, release management and change control may be separate responsibilities. Do not collapse them into a generic administrator role.

## Auditors, regulators and assurance users

People who inspect records, controls, decisions, evidence, reports, security, privacy, accessibility or service continuity. They may use the system directly, receive extracts or rely on evidence produced by others.

Understand what they must be able to verify, under which authority, for which period and with what protection. An auditor's need for evidence is not permission for unrestricted access to all operational data.

## Connected system users

A connected system may consume a capability, submit commands, provide information, receive events, reconcile state or depend on a contract. Treat it as a user of the relevant interface while remembering that it is also a stakeholder and external dependency.

Identify its authority, identity, contract version, expected cadence, volume, failure handling, retry behaviour, reconciliation and retirement path. A successful transport response does not prove that the connected system accepted the intended meaning.

## User categories can overlap

One person may be an applicant, provider, assessor and support worker in different contexts. One system may be both a provider and a consumer of capabilities. One site may serve several categories when their responsibilities and information needs remain coherent.

Do not turn the category name into a permission, database table, site or team automatically. First identify the context, responsibility, information, authority, consequences and evidence. Then work with architecture, security and technical roles to decide the appropriate system boundary and access model.

## Questions for elicitation

For each relevant user category, ask:

- What outcome is this user trying to achieve?
- What information do they need, provide, change, receive or rely on?
- What authority and representation do they have in this context?
- What must they understand before acting?
- What happens when information is missing, wrong, late or inaccessible?
- Which states, decisions, records and evidence matter to them?
- What quality, accessibility, safety, privacy and recovery conditions apply?
- What support, operational or maintenance consequence follows from failure?
- Who can represent this perspective, and what perspective is still missing?

## Related guidance

- [Stakeholder Roles](./stakeholder-roles.md)
- [System Roles](./system-roles.md)
- [Sites](./sites.md)
- [Sites, Flows, Views and Components](./sites-flows-views-components.md)
- [Elicitation](../../../stakeholders/deliverers/business-analysts/elicitation.md)
- [Functional and Quality Requirements](../../../stakeholders/deliverers/business-analysts/functional-and-quality-requirements.md)
- [Data Protection Conventions](../../../../agents/conventions/foundations/data-protection.md)
