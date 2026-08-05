[Up](readme.md)

# Acceptance and Evidence

Product acceptance is a decision that the intended outcome is sufficiently true for the agreed scope, conditions and authority. It is not a declaration that every possible risk has disappeared, and it is not proof that a screen looks complete.

The Product Owner contributes the value, priority and outcome perspective. Acceptance also depends on evidence from the relevant business, user, domain, policy, security, privacy, data, technical, testing, operational, support and maintenance authorities.

## The outcome as the acceptance lens

Acceptance becomes meaningful when the outcome being accepted is clear, along with the users, stakeholders, systems or population for whom it matters. The normal, exceptional and failure conditions give the outcome its boundaries. The relevant capability, Domain and contract carry its meaning, while the functional, quality, transitional and operational requirements describe the conditions around it. Evidence then shows whether the outcome and its constraints are sufficiently true.

The happy path, a deployed change or a complete-looking interface is not enough by itself to establish product acceptance.

A work item that contains only a business concept or feature description is incomplete. It needs acceptance criteria that make the intended outcome, actors, state, authority, data, failure behaviour and relevant quality conditions understandable to the people who will test, implement and accept it.

## Predicates and evidence

An acceptance predicate is a statement that can be evaluated as true or false under stated conditions. It should identify the relevant subject, action, resource, state, authority, time, quality condition or result.

Evidence may take several forms. User or stakeholder acceptance records can sit alongside automated and exploratory test results, contract and integration tests, and security, privacy, accessibility or data-quality evidence. Migration, reconciliation and compatibility results can be important, as can operational readiness, monitoring and recovery rehearsal. Support, Operational and Maintenance Manuals or Information, decision records, approvals, exceptions and residual-risk acceptance add context, while production or service evidence gathered after transition shows what happened in use.

No single evidence type proves the whole outcome. A passing test does not prove policy authority. A Product Owner's acceptance does not erase a security, privacy, records or operational obligation owned by another authority.

The useful delivery path often begins with acceptance criteria, then moves into an automated Test Suite where repeatable evidence is valuable, and then into Service or Client implementation that makes the suite pass. This does not make testing the sole author of the requirement or make development a mechanical afterthought. It gives both groups a clearer interpretation to challenge and refine. When implementation reveals that the criteria express the wrong meaning, the work returns to the responsible product, business, Domain or specialist authority.

## Separate acceptance decisions

Different authorities may therefore make different decisions. **Product acceptance** considers whether the delivered result represents the ordered outcome and scope. **Business or Domain acceptance** considers whether it preserves the relevant meaning, rules and responsibility. **Technical acceptance** considers whether contracts, boundaries and implementation conditions meet the agreed technical requirements. **Quality and assurance acceptance** considers whether the evidence is sufficient for the applicable security, privacy, accessibility, resilience, data and compliance conditions. **Operational readiness** considers whether the service can be supported, observed, recovered, changed and maintained. **Transition acceptance** considers whether users, data, connected systems and support arrangements can move safely to the new state.

These decisions may be made by one person in a small organisation, but the authority and evidence must still be named rather than implied.

## Handle exceptions honestly

An exception becomes understandable when it names the requirement or condition not met, the affected users, stakeholders, systems and deliverables, and the immediate and future consequence. Its account also identifies the authority accepting the residual risk, any temporary controls, restrictions or fallback, the responsible person or team, the review date and the trigger for reconsideration. The evidence required to close the exception remains visible alongside it.

A Product Owner may decide that an outcome is not ready for product acceptance. They should not accept another specialist's risk merely because release pressure is high or because the specialist was not available.

## Acceptance after transition

Some evidence can only be gathered after release, migration or operational use. The acceptance record can distinguish what is known before transition, what remains to be observed and who will review it.

Post-transition acceptance may include service use and outcome measures, incident, support and recovery evidence, data reconciliation and correction, user accessibility and trust feedback, dependency and integration behaviour, and confirmation that Support, Operations and Maintenance can perform their responsibilities.

Acceptance is complete only when the required evidence exists or an explicit, authorised exception remains visible.

## Related guidance

The [Product Owner Guidance](./readme.md) provides the wider product route. [Product Purpose and Outcomes](./product-purpose-and-outcomes.md) and [Scope and Deferral](./scope-and-deferral.md) develop the product decisions, while [Traceability and Evidence](../business-analysts/traceability-and-evidence.md), [Functional and Quality Requirements](../business-analysts/functional-and-quality-requirements.md) and [Transitional and Operational Requirements](../business-analysts/transitional-and-operational-requirements.md) develop the requirement chain. The [Deliverables Checklist](../../../shared/reference/checklists/deliverables.md) provides the formal completeness prompts.
