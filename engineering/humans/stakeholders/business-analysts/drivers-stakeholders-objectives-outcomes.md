# Drivers, Stakeholders, Objectives and Outcomes

A requirement should have a reason that can be understood and challenged. This page gives the BA a route from the pressure or obligation that starts the work to the outcome the service must help make true.

These terms are related, but they are not interchangeable:

```text
Driver -> Objective -> Outcome -> Requirements -> Evidence
              \-> Stakeholders and affected people shape every step
```

The chain is a reasoning aid, not a promise that analysis is linear. Evidence may reveal that the driver was misunderstood, the objective was not measurable, an affected group was missed or the proposed outcome belongs to a different Domain.

## Driver

A driver is the pressure, opportunity, obligation, risk, failure, change or decision that makes work necessary. It answers **why now, why this and why does it matter?**

Examples include:

- a legal or policy obligation;
- unacceptable harm, risk or control failure;
- a service outcome that people cannot currently achieve;
- a material cost, delay or error;
- a change in organisation, funding, technology or external dependency;
- a need to preserve or improve a capability; and
- an opportunity supported by evidence rather than enthusiasm alone.

Record the source and authority of the driver. “Leadership wants a new dashboard” may be a useful starting statement, but it does not yet explain the decision, risk or outcome the dashboard is meant to support.

Ask:

- Who or what created the pressure?
- What happens if nothing changes?
- Is the driver an obligation, a risk, an opportunity, a failure or a preference?
- What evidence supports it?
- How long does it remain relevant?
- Which other drivers compete with or constrain it?

Do not turn a driver directly into an implementation. A driver can justify analysis without proving that the proposed feature, vendor or architecture is the right response.

## Stakeholders and affected people

A stakeholder is anyone who can affect the service, is affected by it, depends on its result, supplies knowledge or evidence, or has authority over an obligation. An affected person may never use the interface and may still carry the consequences of the service's decision.

Identify:

- direct service users and their goals;
- people represented in records or decisions;
- beneficiaries, customers, applicants and recipients;
- assessors, approvers, administrators and support staff;
- operators, maintainers, security and recovery roles;
- connected systems, providers and data owners;
- policy owners, regulators, auditors and sponsors; and
- groups whose accessibility, safety, privacy or trust may be affected.

For each important perspective, record what the representative knows, what authority they have, who or what they represent, what they need, what they contribute and what happens if their view is absent. The [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md) catalogue provides the fuller structure.

Do not use the Product Owner or a single SME as a substitute for every stakeholder. Product priority, business authority, domain knowledge, lived experience, operational responsibility and technical responsibility are different contributions.

## Objective

An objective is what the organisation intends to achieve in response to the driver. It gives the work direction while leaving the implementation open enough for responsible analysis.

A useful objective states:

- the responsible organisation or boundary;
- the intended change;
- the people, capability or obligation affected;
- the relevant time or condition; and
- how progress or achievement can be assessed.

“We need a portal” is a proposed solution shape. “Reduce the time authorised applicants spend gathering and submitting evidence while preserving decision quality and auditability” is closer to an objective. The second statement can still lead to a portal, but it can also reveal that assisted operation, integration, better guidance or a policy change is needed.

Separate objectives from success measures. The objective says what is intended; measures say how the team will recognise progress or achievement. An objective may need several measures because speed alone can hide worse quality, accessibility, safety or fairness.

## Outcome

An outcome is a meaningful change that becomes true for people, the organisation or connected systems. It is not merely that code was deployed, a screen was displayed or a ticket was closed.

A good outcome identifies:

- who experiences or depends on the change;
- what they can now do, understand, receive, decide or avoid;
- what the organisation can now preserve, provide, prevent or prove;
- the conditions under which the result is valid; and
- the evidence that distinguishes success from activity.

For example:

> An authorised applicant can submit complete evidence once, receive a clear acknowledgement, and have the evidence available to the responsible assessor without losing provenance or exposing it to unauthorised people.

That outcome implies more than a submission form. It raises questions about identity, evidence, completeness, acknowledgement, ownership, access, storage, audit, notification, recovery and operational support. Those questions become requirements and design evidence rather than being discovered accidentally in implementation.

An outcome can be positive, protective or preventative. “No unauthorised person can view restricted evidence” and “operators can recover an interrupted submission without duplication” are outcomes even though they describe prevented harm and dependable operation.

## Measures and evidence

Choose measures that reflect the outcome rather than only the delivery activity. Useful measures may include:

- completion or success rate for representative people;
- time, effort or delay under stated conditions;
- accuracy, reconciliation or decision quality;
- accessibility and error recovery;
- security, privacy and authorisation results;
- availability, recovery time and data-loss limits;
- support volume, incident patterns and maintenance effort;
- auditability, traceability and record completeness; and
- evidence that a transitional arrangement has been retired safely.

A measure must have a defined subject, population, condition, owner, source and interpretation. “Users are happy” is not useless, but it needs a method, representative population and decision purpose before it can support acceptance.

Do not optimise one measure while damaging the outcome. A faster submission that creates duplicate records, excludes people using assistive technology or loses evidence is not a successful outcome.

## From outcome to requirements

Once the outcome is clear, ask what must be true to achieve and protect it:

- What business responsibility or obligation must be fulfilled?
- What does each user or affected person need in context?
- What must the system do, remember, decide, communicate or prevent?
- What quality, security, privacy, accessibility, performance, recovery and audit conditions apply?
- What must change during migration, training, release, operation and retirement?
- Which capability and Domain own the meaning, state and rules?
- Which deliverable systems, content, data, trust, discovery and manuals are needed?
- What predicate and evidence will show that the outcome is true?

Use [BUST Requirements](./bust-requirements.md) to organise the requirement views. Use [Elicitation](./elicitation.md) when an answer depends on knowledge that has not yet been drawn out.

## Common distortions

Watch for these substitutions:

- **Driver becomes feature:** the proposed response is treated as the reason for the work.
- **Stakeholder becomes user:** only the person at the screen is considered.
- **Objective becomes output:** a delivered component is mistaken for an organisational result.
- **Outcome becomes metric:** a number is improved without checking whether the meaningful result improved.
- **Preference becomes requirement:** a convenient choice is presented as an obligation.
- **Current process becomes Domain:** today's team structure or workaround becomes permanent system meaning.
- **Acceptance becomes demonstration:** a happy-path walkthrough is treated as proof of quality, transition, operation and evidence.

The BA helps the team name these distinctions without dismissing the original request. A feature may still be the right response. It earns that position when it can be connected to the driver, objective, outcome, requirements, responsible capability and evidence.

## Handoff questions

Before the analysis moves into product ordering and architecture, ask:

- Is the driver evidenced, sourced and still relevant?
- Are the objective and intended outcome stated in plain language?
- Are direct users, affected people, authorities, operators and connected systems represented?
- Can the team tell the difference between activity, output, outcome and evidence?
- Are measures meaningful, representative and protected from harmful optimisation?
- Which requirements and deliverables follow from the outcome?
- Which Domain and capability should own the meaning and lifecycle?
- What remains disputed, assumed, excluded or deliberately deferred?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [Elicitation](./elicitation.md)
- [BUST Requirements](./bust-requirements.md)
- [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md)
- [Domains and Capabilities](../../reference/catalogues/domains-and-capabilities.md)
- [Conceptual, Logical and Physical Models](../../reference/catalogues/conceptual-logical-physical-models.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
