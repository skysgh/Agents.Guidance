[Up](readme.md)

# Product Purpose and Outcomes

A product purpose explains the responsibility the product exists to support. An outcome describes what should become true for people, the organisation or connected systems. Product purpose is broader than a list of features and more durable than a release message.

The Product Owner keeps purpose and outcome visible while the team discovers the detail needed to build, test, operate and maintain the product. They do not invent missing policy or specialist knowledge. They bring the relevant decision-makers and SMEs into the work, then make the resulting choice, uncertainty and evidence visible.

## The driver behind the purpose

A useful purpose account answers:

- What pressure, opportunity, obligation, risk or failure caused this work?
- Which responsibility must the organisation perform or preserve?
- Who is affected, who benefits and who has authority over the result?
- What happens if the organisation does nothing or delays?
- Which existing service, record, partner or obligation must remain compatible?

A feature can be attractive without answering these questions. The Product Owner should not treat popularity, urgency or a persuasive request as proof of value.

## Describe an outcome

An outcome is a change in the world that can be recognised and tested. It is not merely that a screen exists, an endpoint returns a status or a ticket is closed.

A useful outcome statement identifies:

- the subject, user, organisation or connected system affected;
- the situation or trigger in which the outcome matters;
- what becomes possible, protected, prevented or proved;
- the quality conditions that make the result usable and trustworthy;
- the time, accessibility, privacy, security and recovery conditions that apply; and
- the evidence that would show the outcome is true.

For example, ÔÇ£add online applicationsÔÇØ is a feature direction. ÔÇ£An eligible applicant can submit a complete application, receive an understandable acknowledgement and later see the authoritative status without contacting supportÔÇØ is an outcome direction. It still needs domain, policy, security, accessibility, operational and evidence analysis before it is a buildable requirement.

## Find the right perspective

The Product Owner should ask the Stakeholder Analyst and relevant SMEs to examine more than the person requesting the feature. Depending on the product, relevant perspectives may include:

- direct users, represented subjects, beneficiaries and affected people;
- providers, assessors, approvers and intermediaries;
- support, Operations, Monitoring, Maintenance and Change Control;
- Security, Privacy, Records, assurance and regulatory authorities;
- suppliers, delivery teams and connected systems; and
- people responsible for migration, training, fallback and retirement.

The architect integrates these constraints into a coherent system map. The architect does not replace the specialist who owns the operational, legal, security, privacy or maintenance knowledge.

## Connect purpose to engineering

Before ordering a substantial outcome, make its route visible:

driver -> stakeholder or user need -> capability and Domain -> requirements -> contract and predicate -> deliverable systems -> evidence

The route should identify the relevant [capability](../../../shared/reference/catalogues/domains-and-capabilities.md) and [Domain](../../../shared/reference/glossary.md#domain) before requirements, contracts and deliverables are ordered.

Each arrow should have an owner or source of authority. A Product Owner may order the outcome, but the Product Owner does not thereby own every concept, policy, system boundary or technical decision in the route.

The route should also show transitional and operational consequences. Migration, training, parallel running, support information, monitoring, recovery, maintenance information and retirement may be part of the outcome even when they are not visible in the feature description.

## Measures and acceptance

A measure should help decide whether the intended outcome is true. Avoid measures that only count delivery activity, such as tickets closed or screens released, unless those measures answer a real readiness question.

A useful outcome measure states:

- what is observed;
- for which population, process or system;
- under which conditions and time period;
- what threshold or comparison matters; and
- who can accept the evidence.

The Product Owner supplies the value and priority judgement. The relevant business, user, policy, domain, operational, security, privacy, assurance and technical authorities supply the conditions and evidence within their responsibilities.

## Make uncertainty visible

When purpose or outcome is not yet clear, record the unresolved question, affected decision, responsible authority, consequence of waiting and next evidence needed. Do not convert uncertainty into a vague feature so that delivery can start without a real decision.

A deliberate deferral can be responsible when its boundary, owner, trigger, risk and future evidence are clear. An unowned omission that transfers cost or risk to future users, developers or operators is technical theft, not healthy product scope management.

## Related guidance

- [Product Owner Guidance](./readme.md)
- [Stakeholder Roles](../../../shared/reference/catalogues/stakeholder-roles.md)
- [Users to Consider](../../../shared/reference/catalogues/users.md)
- [System Roles](../../../shared/reference/catalogues/system-roles.md)
- [Drivers, Stakeholders, Objectives and Outcomes](../business-analysts/drivers-stakeholders-objectives-outcomes.md)
- [Elicitation](../business-analysts/elicitation.md)
- [Functional and Quality Requirements](../business-analysts/functional-and-quality-requirements.md)
- [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md)
- [Traceability and Evidence](../business-analysts/traceability-and-evidence.md)
