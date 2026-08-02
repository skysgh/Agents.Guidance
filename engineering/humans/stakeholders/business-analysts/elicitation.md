# Elicitation

Elicitation is the disciplined work of drawing out the knowledge needed to understand a service and its consequences. It is not asking someone to approve a screen, collecting a list of feature preferences or turning the loudest person's explanation into a requirement.

The [IIBA](https://www.iiba.org/) and [BABOK Guide](https://www.iiba.org/standards-and-resources/babok/) are the authoritative external sources for Business Analysis practice. This page applies that practice to the serious-system engineering route used by this repository. Here, the person doing this work may be called a Stakeholder Analyst because the required scope includes all material stakeholder and user groups, not only business owners.

## What the Stakeholder Analyst is trying to learn

A useful elicitation conversation discovers more than the happy path. It seeks:

- the driver, obligation, risk or opportunity behind the request;
- the outcome that should become true;
- the people and systems affected, including people who never use the interface;
- the decisions made, who may make them and what authority they rely on;
- the concepts, identities, relationships, states and transitions that matter;
- the information needed, produced, changed, retained, shared or protected;
- rules, policies, timing, thresholds, exceptions and prohibited actions;
- workarounds, manual steps, duplicate records and unofficial sources of truth;
- what happens when information is missing, contradictory, late or wrong;
- accessibility, language, safety, trust and error-recovery needs;
- operational, support, recovery, migration and retirement consequences; and
- the evidence that would show the outcome and its constraints are satisfied.

The aim is not to capture every statement. It is to identify the meaning, responsibility and consequence that the wider team must preserve.

## Find the right people and systems

A job title is not proof that someone can represent a requirement. Identify the responsibility and then find people with the relevant knowledge, authority and lived experience.

Include the people and connected systems that:

- perform or receive the service outcome;
- own the business decision, policy or obligation;
- are affected by a decision without operating the service;
- understand exceptions, safeguarding, accessibility or support consequences;
- operate, recover, maintain or secure the service;
- own a connected system, data source or external dependency; and
- must provide evidence to an auditor, regulator, customer or other authority.

Use the [Users to Consider](../../reference/catalogues/users.md) catalogue to check direct users, represented subjects, affected people, beneficiaries, applicants, providers, intermediaries, support users, operators, maintainers, assurance users and connected systems. Use the [System Roles](../../reference/catalogues/system-roles.md) catalogue to distinguish those real-world responsibilities from the access contexts the service must enforce. Use the [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md) catalogue to record each representative's purpose, knowledge, authority, inputs, outputs, consequences, boundaries and representation. One person may provide several perspectives, but do not assume one confident SME speaks for every affected group.

The architect can help find gaps and integrate the resulting map. The architect is not a substitute for specialist SMEs in Operations, Maintenance, Monitoring, Change Control, Security, Privacy, Records, assurance, Support, Supplier or Delivery responsibilities. Ask those roles to provide or validate their own knowledge and evidence.

## Draw out tacit knowledge

People often know how work really happens without having a complete formal description. They may describe a workaround, a special case or an informal phrase that reveals an important rule.

Useful prompts include:

- “What happens when the normal path cannot be followed?”
- “Who notices that this is ready, incorrect or unsafe?”
- “What must be true before this decision can be made?”
- “What do you check that the system does not currently record?”
- “What do you do when another person or system disagrees?”
- “What must remain available years later, and why?”
- “What would make you stop trusting this result?”
- “Who is affected even though they never see this screen?”
- “What do you do today that the proposed change might remove?”
- “What would support, recovery or maintenance staff need to know at 2 a.m.?”

Treat examples as evidence, not automatically as the final model. One example may reveal a general rule, a local exception, a policy violation, a temporary workaround or a genuinely different Domain. Ask what makes the example the same or different from other cases.

## Separate kinds of statements

During elicitation, distinguish what has been said before deciding what it means:

- **Desire:** something someone would like to have.
- **Need:** something required to achieve a goal or avoid a consequence.
- **Obligation:** something the organisation must do because of law, policy, contract, authority or duty.
- **Assumption:** something currently believed but not yet evidenced.
- **Constraint:** a condition the solution must respect.
- **Requirement:** an agreed statement of what must be achieved, provided, prevented, preserved or proved.
- **Decision:** an authorised choice between alternatives.
- **Open question:** a material uncertainty that still needs evidence or authority.
- **Exclusion:** something deliberately outside the current responsibility or scope.
- **Deferral:** something understood enough to place responsibly, but intentionally not constructed yet.

A desire may become a requirement after its purpose, authority, consequence and acceptance condition are understood. An assumption must not quietly become a system rule. An unresolved disagreement must not be polished into a sentence that falsely suggests agreement.

## Expose disagreement

Conflict is useful evidence. Two stakeholders may use the same word differently, want incompatible outcomes, have different authority or describe different states as though they were one.

When accounts differ:

1. Record the competing statements in the language each person recognises.
2. Identify whether the difference is vocabulary, fact, policy, priority, authority, timing, risk or desired outcome.
3. Find the person or body authorised to resolve the difference.
4. Record the decision, rationale, affected people, assumptions and evidence required.
5. Keep the unresolved conflict visible when no authorised decision has been made.

The BA facilitates understanding and makes the conflict usable by the people who can decide. The BA should not resolve a policy dispute by choosing the easiest implementation, and should not give a Product Owner authority they do not possess.

## From conversation to designable evidence

After elicitation, organise the material so another role can examine it without attending the original conversation. A useful record can include:

- source, date, participants and representation;
- driver, objective and intended outcome;
- concepts, terms and distinctions used by the participants;
- stakeholders, affected people and authority;
- rules, examples, exceptions and prohibited outcomes;
- business, user, system and transitional requirements;
- operational, security, privacy, accessibility and recovery concerns;
- assumptions, dependencies, exclusions, conflicts and open questions;
- candidate capabilities, Domains, use cases and flows;
- acceptance predicates and evidence ideas; and
- the owner and review condition for each unresolved item.

This record is not a demand for a large document. It may be a decision record, structured requirement, model, workshop output or linked set of artefacts. The test is whether the meaning, authority, uncertainty and consequence remain visible to Product Owners, architects, developers, testers, operators and maintainers.

## What elicitation does not decide alone

Elicitation does not allow the BA to:

- invent policy or regulatory interpretation without the responsible authority;
- declare one stakeholder representative of people they cannot represent;
- choose the physical architecture, database, framework or deployment model alone;
- accept an unsafe quality compromise on behalf of security, operations or affected people;
- turn a current workaround into a permanent Domain rule without examination; or
- declare a requirement complete without an owner, acceptance condition or evidence path.

The BA does help the team make those decisions possible by identifying the missing knowledge, the responsible decision-maker and the consequences of waiting.

## Handoff questions

Before handing elicited material into product ordering or architecture, ask:

- Can another person explain why this matters and for whom?
- Are the relevant users, affected people, SMEs and authorities represented?
- Are the important concepts, states, decisions, rules and exceptions distinguishable?
- Are contradictions, assumptions, exclusions and unresolved questions visible?
- Are quality, transitional and operational consequences included?
- Can the material be traced into a capability, Domain, use case or flow without inventing technical structure?
- What predicate and evidence could show that the intended outcome is true?
- Which question must the Product Owner, business owner, policy owner, architect, tester or operator answer next?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [BUST Requirements](./bust-requirements.md)
- [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md)
- [Users to Consider](../../reference/catalogues/users.md)
- [System Roles](../../reference/catalogues/system-roles.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Conceptual, Logical and Physical Models](../../reference/catalogues/conceptual-logical-physical-models.md)
- [Domains and Capabilities](../../reference/catalogues/domains-and-capabilities.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
