[Up](../readme.md)

# Support

Support is the first point of contact for end users. Support helps people understand and use the service, investigates reported problems and moves issues to the responsible boundary. Service Providers and Operators supply Support with service knowledge, status and operational findings; Support does not become the technical owner merely because it receives the report. Support is a distinct responsibility from Operations, Testing and Maintenance. This route uses the existing support-manual, requirements and system-role guidance as its initial canonical material; substantive support guidance remains Phase 6 work.

## A useful way into the route

[System Roles](../../../shared/reference/catalogues/system-roles.md) explains the purpose-specific access, privacy, audit and escalation boundaries of a Support role. [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md) brings support ownership, symptoms, escalation, manuals and evidence together. The [Deliverables](../../../shared/reference/catalogues/deliverables.md) catalogue distinguishes Support Manuals or Information from Operational and Maintenance material, while [Shared Requirements](../../../shared/requirements.md) connects a reported problem to the requirement, capability, contract or operational condition involved. [Acceptance and Evidence](../product-owners/acceptance-and-evidence.md) helps when a report raises an acceptance, outcome or residual-risk question.

## Support working guidance

- [Support Triage and Escalation](./triage-and-escalation.md): record the user's problem, select the appropriate tier and preserve evidence across handoffs.
- [Support Access and Guided Action](./access-and-guided-action.md): help people through purpose-specific access without creating an administrative bypass.

## The support responsibility

Support helps another user. Support identifies the person, context, symptom, affected capability and safe next action; uses permitted lookup or guided action; communicates clearly; records evidence; and escalates when the issue belongs to another boundary. Support material should explain known symptoms, supported responses, limitations, ownership and escalation routes.

Support first delivers a complete report to the Service Provider and/or Operations when the issue concerns service availability, operational state or an unresolved user-facing condition. If investigation still requires code, schema, dependency, configuration or infrastructure change, the issue moves to Maintenance Developers or the appropriate maintenance owner. Support does not silently become Operations by changing live infrastructure, Testing by declaring a defect proven, or Maintenance by changing code, data, configuration or contracts. Support should not impersonate a user or bypass normal authorisation. A person may perform more than one responsibility, but the authority being exercised must remain explicit and audited.

## Support tiers and the handoff story

Tier numbers are an organisational convention, not a universal standard. The Service Provider should define the actual responsibilities, authority and escalation conditions for each tier. A common model is:

- **Tier 0:** self-service or automated assistance, such as help content, status information, guided recovery or a searchable knowledge base. Tier 0 is optional and must not force a person to diagnose a problem alone when assisted support is needed.
- **Tier 1:** the first point of contact, usually a service desk or customer-support team. Tier 1 receives the user's report, confirms identity and context as appropriate, records the symptom and impact, applies documented safe responses and communicates with the user.
- **Tier 2:** deeper service support supplied by the Service Provider, Operations or another designated specialist team. Tier 2 examines service status, operational evidence, known incidents, configuration within its authority and dependency conditions. It may coordinate recovery or a controlled operational action, but it does not silently change application code or business meaning.
- **Tier 3:** specialist technical investigation, usually including Maintenance Developers or a designated infrastructure or platform maintenance owner. Tier 3 investigates defects, code, schema, dependencies, configuration, infrastructure or compatibility and makes controlled changes with the required evidence, approval, rollback and recovery plan.

The numbering can be adapted. What must remain visible is the progression: user or Tier 0 report -> Tier 1 Support -> Tier 2 Service Provider and/or Operations -> Tier 3 Maintenance when deeper technical investigation or change is needed. A tier is not a measure of personal status. It is a boundary for the depth of investigation, authority and information required.

Every escalation should carry enough information for the next tier to continue without making the user repeat the whole story: reporter and affected subject where permitted, capability, time, environment, symptom, impact, steps already taken, correlation or case identity, relevant evidence, privacy classification, current owner, requested decision and the condition for returning the issue to Support.

## Support deliverables

Support owns or contributes to [Support Manuals or Information](../../../shared/reference/catalogues/deliverables.md), including known symptoms, user language, supported responses, permitted lookup and guided actions, escalation routes, communication templates, ownership and links to authoritative evidence. These are not a substitute for Operational Manuals or Information or Maintenance Manuals or Information.

## Related routes

- [Stakeholders](../readme.md)
- [Stakeholder Analysts](../business-analysts/readme.md)
- [Product Owners](../product-owners/readme.md)
- [Testers](../testers/readme.md)
- [Operators](../operators/readme.md)
- [Maintainers](../maintainers/readme.md)
- [Developers](../developers/readme.md)
