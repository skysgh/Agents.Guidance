[Up](../readme.md)

# Business Analysts


A Stakeholder Analyst (Business Analyst) helps the team understand the world the service must support before implementation turns one person's explanation into permanent system behaviour. The repository uses Stakeholder Analyst as a working emphasis, while retaining Business Analyst for the IIBA/BABOK discipline and external terminology.

The analyst does not merely transcribe requests into tickets. The analyst identifies all material stakeholder and user groups, including specialist operational and technical groups, finds representative subject matter experts, elicits meaning and consequences, exposes ambiguity and conflict, and helps the team turn that material into requirements that architecture, development, testing, operation and maintenance can use.

## A useful way into the route

[Liberation Through Clarity](../../../shared/liberation-through-clarity.md) explains why making meaning explicit helps the next person work with less uncertainty. The [Stakeholder Roles](../../../shared/reference/catalogues/stakeholder-roles.md), [Users to Consider](../../../shared/reference/catalogues/users.md) and [System Roles](../../../shared/reference/catalogues/system-roles.md) catalogues help keep representation, authority, knowledge, user context and access responsibilities visible.

The route then opens in several directions. [Elicitation](./elicitation.md) explores how tacit knowledge, exceptions, consequences and unresolved questions become visible. [Shared Requirements](../../../shared/requirements.md) connects that material to Product Owners, architects, technical analysts, developers, testers and operators. The pages on [Drivers, Stakeholders, Objectives and Outcomes](./drivers-stakeholders-objectives-outcomes.md), [Functional and Quality Requirements](./functional-and-quality-requirements.md), [Transitional and Operational Requirements](./transitional-and-operational-requirements.md), [BUST Requirements](./bust-requirements.md), [Use Cases and Flows](./use-cases-and-flows.md) and [Traceability and Evidence](./traceability-and-evidence.md) each deepen a different part of that shared account.

[Guidance for Product Owners](../product-owners/readme.md) shows the adjacent prioritisation and outcome decisions, while [Guidance for System Design Architects](../../../foundations/guidance-for-system-design-architects.md) follows elicited meaning into system structure. When a requirement risks turning a membership, appointment, role, assignment or workflow into one lasting identity, [Entity Lifecycle Patterns](../../../shared/reference/catalogues/entity-lifecycle-patterns.md) offers a more focused explanation.

## The BA's contribution

The BA helps the team move from a request to a designable account of the responsibility:

- **Drivers:** why the change matters, including pressure, opportunity, obligation, risk or failure.
- **Stakeholders and affected people:** who supplies knowledge, has authority, depends on the result or carries consequences without directly using the service.
- **Objectives:** what the organisation intends to achieve.
- **Outcomes:** what should become true or measurably better for people, the organisation or connected systems.
- **Business requirements:** what the organisation must preserve, provide, prevent or prove.
- **User requirements:** what a user or affected person needs from the service in context.
- **System functional requirements:** what the system must do, remember, decide, communicate or prevent.
- **System quality requirements:** how safely, reliably, securely, accessibly, quickly or accurately it must do so.
- **Transitional requirements:** what is needed to move from the current arrangement to the new one.
- **Operational requirements:** what must be true for the service to be supported, operated, recovered, changed and retired.

These are connected views, not a stack of documents to complete mechanically. The BA helps the team trace them into use cases, flows, capabilities, Domains, contracts, acceptance predicates, deliverable systems, deliverables and evidence.

The BA should ask which concepts are [Enduring](../../../shared/reference/glossary.md#enduring) and which are [Transient](../../../shared/reference/glossary.md#transient) bounded arrangements. When stakeholders say "a student at a school", capture whether they mean a Person, an enduring student classification, a School or Group, a Location, or a time-bounded `StudentAt` membership. This is a requirements question because identity, history, authority, reporting, transition and retention depend on the answer.

## What the BA must not silently absorb

The BA should not invent missing policy, speak for every stakeholder, approve technical risk, choose the physical architecture alone or turn an unresolved conflict into a false requirement. When the evidence is incomplete, the correct output is a visible assumption, open decision, disagreement, exclusion or deliberate deferral.

Technical analysis is a capability, not an automatic part of the BA title. A BA may perform Technical Analyst work when they have the demonstrated technical knowledge, capacity and accountability for the relevant API, event, data or integration contracts. A BA should not be expected to do that work merely because no technical analyst has been assigned. An architect may perform it when appropriate, but should not become the default owner of every technical contract or specialist detail. For substantial or high-risk technical analysis, assign a suitably capable Technical Analyst or technical team member and keep ownership of each contract with the responsible boundary.

The BA also does not hand off meaning once and disappear. Developers may discover that a requirement is ambiguous or unsafe. Testers may expose a missing condition. Operators may identify a lifecycle need. The BA returns to the relevant stakeholders and helps refine the meaning while the architect protects the wider system relationships.

## Useful output

A useful BA output lets another role answer:

- What problem or obligation led to this requirement?
- Whose need or authority does it represent?
- What outcome should change?
- What must the system do and what qualities must it provide?
- What changes during transition and operation?
- Which capability and Domain carry the meaning?
- What is still uncertain, disputed or deliberately deferred?
- What evidence will show that the requirement is satisfied?

## Related guidance

- [Elicitation](./elicitation.md)
- [Drivers, Stakeholders, Objectives and Outcomes](./drivers-stakeholders-objectives-outcomes.md)
- [Functional and Quality Requirements](./functional-and-quality-requirements.md)
- [Transitional and Operational Requirements](./transitional-and-operational-requirements.md)
- [Use Cases and Flows](./use-cases-and-flows.md)
- [Traceability and Evidence](./traceability-and-evidence.md)
- [BUST Requirements](./bust-requirements.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Stakeholder Roles](../../../shared/reference/catalogues/stakeholder-roles.md)
- [Liberation Through Clarity](../../../shared/liberation-through-clarity.md)
- [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md)
- [Deliverables](../../../shared/reference/catalogues/deliverables.md)
- [Engineering Checklists](../../../shared/reference/checklists/readme.md)
