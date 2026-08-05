[Up](readme.md)

# Functional and Quality Requirements

Functional and quality requirements describe what the system must provide and the conditions under which it must provide it. They are two views of the same intended outcome, not a list of visible features followed by optional technical polish.

A function that exposes information to the wrong person, loses evidence, cannot recover safely or excludes the people who need it is not complete for a serious system.

## Functional requirements

A functional requirement states what a system, [capability](../../../shared/reference/glossary.md#capability) or connected participant must do, remember, decide, communicate or prevent. It should identify enough context that the team can place it in a responsible boundary and test its result.

A useful functional requirement makes clear:

- the actor, system or capability involved;
- the action or behaviour;
- the information, concept or state affected;
- the rule, condition or authority that applies;
- the result or state change; and
- the evidence that would show the behaviour occurred correctly.

Weak:

> The system shall support applications.

Stronger:

> An authorised assessor can record an assessment against a submitted application, see the evidence available to that assessment, and move the assessment to an approved or declined state only when the required decision conditions are satisfied. The service records who made the decision, when, under which authority and with which evidence version.

The stronger statement still needs analysis. It raises questions about the Application and Assessment meanings, submission state, evidence authority, decision rules, permissions, history, notification, recovery and audit. That is useful: a functional requirement should expose the design questions rather than hide them behind a general verb.

## Capabilities and Functions

A functional requirement may contribute to a [Capability](../../../shared/reference/catalogues/domains-and-capabilities.md), one or more Functions within that capability, a state transition, a use case, a flow or a contract.

Do not confuse:

- a **[Capability](../../../shared/reference/catalogues/domains-and-capabilities.md)**, which is an owned ability within a [Domain](../../../shared/reference/glossary.md#domain);
- a **Function**, which is a focused operation or responsibility within that capability;
- a **flow**, which coordinates several capabilities into a journey; and
- a **feature**, which may be a product description of a change without yet identifying its durable responsibility.

The requirement should help the team decide where the behaviour belongs. It should not make a screen, endpoint or storage record the accidental owner of the meaning.

## State and rule precision

Functional requirements often become vague because they omit state and authority. Ask:

- What state must the subject be in before the action is allowed?
- Which states are distinct, and why does the difference matter?
- Who or what may perform the action?
- What information must be present, current or reconciled?
- What happens when the action is repeated, interrupted, rejected or reversed?
- Which event, decision or record proves the change?
- What must not change as a side effect?

Avoid relying on words such as ÔÇ£manageÔÇØ, ÔÇ£handleÔÇØ, ÔÇ£processÔÇØ or ÔÇ£supportÔÇØ without describing the responsibility beneath them. A concise requirement is valuable when the omitted detail is genuinely private implementation detail. It is incomplete when the omitted detail determines authority, lifecycle, history, safety or evidence.

## Quality requirements

Quality requirements describe how well, how safely or under which constraints the system must provide its functions. They may concern:

- security and authorisation;
- privacy, classification and data minimisation;
- accessibility, language and inclusion;
- reliability and availability;
- performance, capacity and timing;
- recoverability, continuity and data loss;
- compatibility and versioning;
- auditability, traceability and records;
- maintainability, diagnosability and supportability;
- data accuracy, completeness and reconciliation;
- usability, learnability and error recovery; and
- legal, regulatory, contractual or policy obligations.

Quality requirements are not automatically global properties of the whole service. A payment decision, public search, clinical record, recovery operation and internal diagnostic page may have different quality targets because their consequences differ. State the subject, context, condition, target and evidence.

Weak:

> The service must be fast and secure.

Stronger:

> For a representative authorised search during the stated peak workload, the service returns the permitted result or a clear bounded failure within the agreed response target, does not expose restricted fields through filtering or ordering, records the access decision and remains within the defined capacity and availability limits.

The exact target belongs to the responsible product, business, security, operations and technical authorities. The BA's job is to expose the quality need, consequence, context and acceptance question rather than invent a number without evidence.

## Quality is part of the outcome

Connect each quality requirement to the outcome it protects. Examples:

- confidentiality protects people and organisations from unauthorised disclosure;
- accessibility lets representative people achieve the intended result;
- recoverability prevents an interrupted process from becoming an untraceable loss;
- auditability preserves accountability for a decision;
- performance protects timely action and operational capacity;
- compatibility protects consumers and connected systems during change; and
- maintainability protects the service's ability to remain dependable after staff, policy and dependency changes.

This connection helps the Product Owner order quality work, the architect place the responsibility, the developer implement a meaningful boundary, the tester choose evidence and the operator prepare support and recovery.

## Requirement quality

A useful requirement should be:

- understandable to the people whose meaning it represents;
- sufficiently precise to expose the important rule and consequence;
- bounded by a responsible system, capability or Domain;
- necessary for the stated outcome, obligation or risk;
- consistent with related requirements or visibly marked as conflicting;
- feasible within the known constraints, or explicitly recorded as unresolved;
- verifiable through inspection, demonstration, measurement, analysis or test; and
- traceable to its source, decision, acceptance evidence and affected deliverables.

Do not mistake a long sentence for a complete requirement. Break a statement apart when it contains unrelated responsibilities, hides several actors, combines multiple quality targets or cannot be tested as one predicate.

## Boundaries and mappings

The requirement's language may be conceptual. The implementation will need logical and physical decisions. The BA should make the meaning and distinctions clear without silently choosing database tables, framework classes, service projects or provider APIs.

Work with architects and technical leads to identify:

- the Domain and capability that own the meaning;
- the LDM or system boundary that carries the responsibility;
- the contract and predicate that protect it;
- mappings needed for users, connected systems and storage;
- information and authority boundaries;
- lifecycle, transition and operational dependencies; and
- evidence needed at each boundary.

Read [Conceptual, Logical and Physical Models](../../../shared/reference/catalogues/conceptual-logical-physical-models.md) when the team is at risk of turning a screen, endpoint or persistence record into the whole design.

## Requirement patterns to avoid

- ÔÇ£The system shall be user-friendlyÔÇØ without users, context, consequence or evidence.
- ÔÇ£The API shall return all fieldsÔÇØ without classification, purpose, consumer or minimisation.
- ÔÇ£The page shall load quicklyÔÇØ without workload, subject, target or measurement.
- ÔÇ£The application shall be secureÔÇØ without protected resources, actors, permissions, threat or control evidence.
- ÔÇ£The data shall be retainedÔÇØ without purpose, authority, period, access, disposal and record status.
- ÔÇ£The system shall be scalableÔÇØ without demand, growth, failure boundary, cost and operational target.
- ÔÇ£The user can edit the recordÔÇØ without state, authority, history, concurrency and audit rules.

These statements may be useful prompts. They become requirements only when the missing meaning and evidence are made visible.

## Handoff questions

Before functional and quality requirements move into design or acceptance, ask:

- Does each functional requirement identify a meaningful actor, subject, state, rule and result?
- Does each quality requirement identify its context, consequence, target or decision needed to set one?
- Are security, privacy, accessibility, recovery, audit, performance and maintenance concerns included where relevant?
- Can the requirements be placed in capabilities, Domains, contracts, use cases or flows?
- Are the requirements verifiable without pretending that a screen demonstration proves every quality?
- Which requirements need a Product Owner, business owner, policy owner, security, operations or technical decision?
- Which data, content, trust, manuals, testing and evidence deliverables follow from them?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [Drivers, Stakeholders, Objectives and Outcomes](./drivers-stakeholders-objectives-outcomes.md)
- [BUST Requirements](./bust-requirements.md)
- [Domains and Capabilities](../../../shared/reference/catalogues/domains-and-capabilities.md)
- [Quality Perspectives](../../../shared/reference/catalogues/qualities.md)
- [Conceptual, Logical and Physical Models](../../../shared/reference/catalogues/conceptual-logical-physical-models.md)
- [Guidance for System Design Architects](../../../foundations/guidance-for-system-design-architects.md)
- [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md)
- [Deliverables](../../../shared/reference/catalogues/deliverables.md)
