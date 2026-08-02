# Acceptance and Evidence

Product acceptance is a decision that the intended outcome is sufficiently true for the agreed scope, conditions and authority. It is not a declaration that every possible risk has disappeared, and it is not proof that a screen looks complete.

The Product Owner contributes the value, priority and outcome perspective. Acceptance also depends on evidence from the relevant business, user, domain, policy, security, privacy, data, technical, testing, operational, support and maintenance authorities.

## Start with the outcome

Acceptance should answer:

- Which outcome is being accepted?
- For which users, stakeholders, systems or population?
- Under what normal, exceptional and failure conditions?
- Which capability, Domain and contract carry the meaning?
- Which functional, quality, transitional and operational requirements apply?
- What evidence demonstrates that the outcome and its constraints are true?

A Product Owner should not accept a feature only because the happy path works, the code is deployed or the visible interface is complete.

## Use predicates and evidence

An acceptance predicate is a statement that can be evaluated as true or false under stated conditions. It should identify the relevant subject, action, resource, state, authority, time, quality condition or result.

Evidence may include:

- user or stakeholder acceptance records;
- automated and exploratory test results;
- contract and integration tests;
- security, privacy, accessibility or data-quality evidence;
- migration, reconciliation and compatibility results;
- operational readiness, monitoring and recovery rehearsal;
- Support, Operational and Maintenance Manuals or Information;
- decision records, approvals, exceptions and residual-risk acceptance; and
- production or service evidence gathered after transition.

No single evidence type proves the whole outcome. A passing test does not prove policy authority. A Product Owner's acceptance does not erase a security, privacy, records or operational obligation owned by another authority.

## Separate acceptance decisions

Record different decisions when different authorities are involved:

- **Product acceptance:** does the delivered result represent the ordered outcome and scope?
- **Business or Domain acceptance:** does it preserve the relevant meaning, rules and responsibility?
- **Technical acceptance:** do contracts, boundaries and implementation conditions meet the agreed technical requirements?
- **Quality and assurance acceptance:** is the evidence sufficient for the applicable security, privacy, accessibility, resilience, data and compliance conditions?
- **Operational readiness:** can the service be supported, observed, recovered, changed and maintained?
- **Transition acceptance:** can users, data, connected systems and support arrangements move safely to the new state?

These decisions may be made by one person in a small organisation, but the authority and evidence must still be named rather than implied.

## Handle exceptions honestly

An exception should identify:

- the requirement or condition not met;
- the affected users, stakeholders, systems and deliverables;
- the immediate and future consequence;
- the authority accepting the residual risk;
- temporary controls, restrictions or fallback;
- the owner, review date and trigger for reconsideration; and
- the evidence required to close the exception.

A Product Owner may decide that an outcome is not ready for product acceptance. They should not accept another specialist's risk merely because release pressure is high or because the specialist was not available.

## Acceptance after transition

Some evidence can only be gathered after release, migration or operational use. Record what is known before transition, what remains to be observed and who will review it.

Post-transition acceptance may include:

- service use and outcome measures;
- incident, support and recovery evidence;
- data reconciliation and correction;
- user accessibility and trust feedback;
- dependency and integration behaviour; and
- confirmation that support, Operations and Maintenance can perform their responsibilities.

Acceptance is complete only when the required evidence exists or an explicit, authorised exception remains visible.

## Related guidance

- [Product Owner Guidance](./readme.md)
- [Product Purpose and Outcomes](./product-purpose-and-outcomes.md)
- [Scope and Deferral](./scope-and-deferral.md)
- [Traceability and Evidence](../business-analysts/traceability-and-evidence.md)
- [Functional and Quality Requirements](../business-analysts/functional-and-quality-requirements.md)
- [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md)
- [Deliverables Checklist](../../reference/checklists/deliverables.md)
