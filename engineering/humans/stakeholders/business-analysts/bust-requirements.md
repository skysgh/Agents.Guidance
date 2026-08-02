# BUST Requirements

BUST is a minimum reminder that a serious system has more than a business feature request. It asks the team to consider **Business, User, System and Transitional** requirements together. It is an engineering-facing mnemonic used alongside the IIBA body of knowledge and BABOK Guide, not a replacement for them.

BUST is a classification aid, not a demand to create four disconnected documents. A single outcome may have requirements in all four categories, and the categories should remain traceable to one another.

## Business requirements

Business requirements state what the organisation must achieve, preserve, provide, prevent or prove. They express the business responsibility rather than the first screen or implementation choice.

Ask:

- What driver makes this necessary?
- What objective does the organisation intend to achieve?
- What outcome will show that the objective has been met?
- Which obligation, policy, risk or decision must remain visible?
- What must be remembered for history, audit or accountability?

A business requirement might say that an organisation must assess an application consistently, retain evidence of the decision and make the outcome available to authorised participants. It should not silently prescribe a database table or a particular page layout.

## User requirements

User requirements state what a person or represented affected group needs from the service in a real context. They include goals, language, accessibility, timing, trust, confidence, error recovery and the consequences of delay or mistake.

Do not treat the person who operates a screen as the only user. A person may be affected by a decision without using the service. A support worker, assessor, approver, administrator, connected system or recovery operator may also be a user of a capability.

Ask:

- Who is trying to achieve what?
- What information and authority do they have?
- What must they be able to understand, change, submit, review or recover?
- What happens when the service is unavailable or the information is incomplete?
- Which accessibility, language, safety or trust conditions matter?

## System requirements

System requirements state what the system must provide to support the business and user responsibilities. Separate functionality from qualities.

### Functional system requirements

Functional requirements describe what the system must do, remember, decide, communicate or prevent. They may become capabilities, Functions, state transitions, contracts, flows or integration behaviours.

A functional requirement should make its subject and boundary clear. “The system shall support applications” is too vague. A stronger statement identifies the relevant [Domain](../../reference/glossary.md#domain), actor or system, action, state, information, rule and result.

### Quality system requirements

Quality requirements describe how well or under which constraints the functionality must operate. They may concern security, privacy, accessibility, reliability, performance, availability, recoverability, compatibility, maintainability, auditability, data quality or usability.

A quality requirement is not secondary because it is not visible in a happy-path screen. For a serious system, a function that cannot protect information, recover safely or provide required evidence is incomplete.

## Transitional requirements

Transitional requirements support movement from the current arrangement to the intended one. They are temporary in subject, but they are still real requirements and deliverables. They are often the least understood or least-used part of BUST; omitting them leaves the team to invent migration, training, fallback, release and retirement behaviour under pressure.

They may include:

- data migration and reconciliation;
- training and assisted operation;
- parallel running;
- staged release;
- communication and change support;
- identity or access transition;
- temporary reports or exports;
- legacy integration;
- rollback or fallback arrangements; and
- decommissioning of the replaced capability.

A transitional requirement should state when it begins, what it enables, who owns it, what evidence proves it ready and when it can be retired.

## Connect the categories

A useful chain looks like this:

```text
Driver
  -> Objective
    -> Outcome
      -> Business requirement
        -> User requirement
          -> System functional and quality requirements
            -> Transitional and operational requirements
              -> Use case or flow
                -> Capability and Domain
                  -> Contract and predicate
                    -> Tests, deliverables and evidence
```

The chain is not always linear. New evidence may send the team back to the driver, stakeholder or outcome. That is healthy correction, not failure. What matters is that the reason for the change remains visible.

## BA completion questions

Before handing requirements into design, ask:

- Are the driver, objective and intended outcome clear?
- Are affected people and representative stakeholders identified?
- Are authority, assumptions, exclusions and unresolved conflicts visible?
- Are business, user, functional, quality, transitional and operational requirements represented where relevant?
- Can the requirements be traced to a capability, Domain, use case or flow?
- Are acceptance predicates and evidence possible to state?
- Which deliverable systems and wider deliverables are affected?
- What must be clarified before a Product Owner, architect or technical lead can make a responsible decision?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md)
- [Domains and Capabilities](../../reference/catalogues/domains-and-capabilities.md)
- [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [Deliverables Checklist](../../reference/checklists/deliverables.md)
