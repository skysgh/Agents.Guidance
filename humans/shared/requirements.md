[Up](readme.md)

# Shared Requirements

A [requirement](./reference/glossary.md#requirement) is an agreed statement of something a serious system must achieve, provide, prevent, preserve or prove. It is not merely a request, feature label, screen description or implementation task.

Requirements are shared engineering objects. A Stakeholder Analyst may elicit and clarify them. A Product Manager or Product Owner may provide direction, priority and scope decisions within authority. Business, Domain, policy and specialist SMEs provide meaning and constraints. Architects place responsibilities and boundaries. Technical Analysts help make technical contracts precise when that capability is assigned. Developers implement. Testers challenge predicates and produce evidence. Operations, support and maintainers establish readiness, recovery and lifecycle conditions.

No single role should silently absorb the authority or knowledge of all the others.

Specialists in Security, Privacy, Records, Monitoring, Change Control or Assurance can use this page as their shared entry point. The [specialist controls](#specialist-controls-enable-the-outcome-and-protect-it-when-needed) section names each responsibility's contribution, bounded authority, evidence and return path; [Stakeholder Roles](./reference/catalogues/stakeholder-roles.md) supplies the broader role definitions.

## The requirement chain

A useful requirement chain preserves the reason for work as it becomes more precise:

```text
Driver
  -> Stakeholders, users and affected people
    -> Objective
      -> Outcome and measure
        -> Business, User, System and Transitional requirements
          -> Operational, quality and lifecycle conditions
            -> Use case or flow
              -> Capability and Domain
                -> Contract and acceptance predicate
                  -> Work item with acceptance criteria
                    -> Test Suite and implementation
                      -> Deliverables and evidence
```

The chain is not a mandatory document sequence. It is a way to find missing meaning, authority, ownership or evidence. New evidence may send the team back to an earlier point. That is responsible correction, not failure.

The chain connects a [Capability](./reference/glossary.md#capability) to its responsible [Domain](./reference/glossary.md#domain) before contract, implementation, deliverables and evidence are chosen.

Acceptance criteria are the bridge between meaning and evidence. They describe the conditions under which the outcome can be recognised as true, including relevant success, failure, authority, data, quality and recovery conditions. A work item that contains only a business concept or feature label has not yet given the Test Suite or the developer enough to prove what ÔÇ£doneÔÇØ means.

## Requirement views

The useful requirement views depend on the responsibility being clarified, and they work best when they remain connected rather than becoming disconnected documents created only to satisfy a classification. A **Business** view describes what the organisation must achieve, preserve, provide, prevent or prove. A **User** view describes what direct users, represented subjects, affected people or connected systems need in context. A **System functional** view describes what the system must do, remember, decide, communicate or prevent. A **System quality** view describes how safely, securely, accessibly, reliably, quickly, accurately, recoverably or maintainably it must behave. A **Transitional** view describes what is needed to move from the current arrangement to the intended one, including migration, training, staged release, fallback and retirement. An **Operational** view describes what must be true for the service to be supported, observed, operated, recovered, changed and maintained.

BUST is a useful reminder for Business, User, System and Transitional requirements. It is not an IIBA or BABOK term and it does not replace operational, quality or lifecycle analysis.

## Make a requirement usable

A requirement should be understandable to the people who must decide, implement, test, operate or accept it. Its meaning becomes more usable when the affected subject, actor or system is visible, together with the outcome, action, state, information or constraint. The [Domain](./reference/glossary.md#domain), [capability](./reference/glossary.md#capability) or boundary responsible for it should be recognisable, as should the authority, policy, obligation or evidence behind it. Timing, quality, security, privacy, accessibility and recovery conditions may shape the requirement, alongside assumptions, exclusions, conflicts and deliberate deferrals. An acceptance predicate or other testable evidence connects the statement to proof, while the responsible authority and the person or team able to change or accept it keep its future life clear.

ÔÇ£The system shall support requestsÔÇØ is not enough. A useful statement distinguishes the relevant request, actor, state, authority, result and failure conditions without prescribing a physical design prematurely. The acceptance criteria can then express the examples and boundaries that a tester can automate and a developer can implement against.

## Requirements and contracts

A requirement expresses what must be true. A contract expresses the dependable relationship at a boundary: what a participant may ask, what it means, what it receives, what conditions apply and what happens when the normal path fails.

A requirement may lead to a user, API, event, data, operational or delivery contract. The contract owner must be explicit. A Technical Analyst, architect or developer may document the contract, but documentation activity does not transfer authority from the responsible Domain, product, security, privacy, operational or technical boundary.

The Test Suite does not invent the acceptance meaning after implementation. It makes the agreed acceptance criteria executable where that is useful and returns ambiguity to the responsible product, business, Domain or specialist authority.

## Requirements and acceptance

Acceptance is evidence-based. The person who explains a need, records a requirement, orders an outcome, implements a contract, produces a test or accepts product scope may be different people.

These distinctions remain important throughout acceptance. Evidence is not authority, and a test pass is not policy approval. Product Owner acceptance does not erase specialist obligations, just as architectural coherence does not prove operational readiness. A deployed feature is not a complete deliverable when the required data, trust, content, manuals, support, operation, maintenance or evidence is absent.

## Requirements and change

When a requirement changes, its consequences reach across users, stakeholders, Domains, capabilities, contracts, systems, deliverables, tests, operations, support, maintenance and retirement. The change record can describe whether the change is an addition, correction, conflict resolution, exclusion, deferral or replacement.

A deliberate deferral retains its intended place, owner, trigger, risk and evidence condition. An unowned omission that transfers known cost or risk to future people is technical theft, not ordinary technical debt.

## Role handoffs

The **Stakeholder Analyst** identifies relevant stakeholder and user groups, elicits meaning, checks representation and makes uncertainty visible. The **Product Manager** may set broader product direction, purpose, value and lifecycle decisions, while the **Product Owner** orders near-term outcomes and decides scope and priority within delegated authority. **Business, Domain and policy authorities** establish meaning, rules, obligations and decisions within their authority.

The **Architect** maps boundaries, dependencies, responsibilities and system structure without impersonating specialist SMEs. The **Technical Analyst** makes technical meaning, contracts, mappings and conditions precise when explicitly assigned and competent. **Technical leads and developers** turn the prepared meaning into implementable structure and behaviour, raising contradictions and unsafe assumptions. The **Tester and Test Developer** turn acceptance criteria into appropriately scoped automated, exploratory or manual evidence, then return ambiguity or failed predicates to the responsible decision.

The **Front-end Developer** turns prepared consumer meaning and service contracts into an accessible, usable and secure browser or client experience while preserving server-side authority for business rules, authorisation, durable state and audit. **Testers and assurance roles** challenge predicates and produce evidence for the claims within their responsibility. **Operations, support and maintainers** define and verify readiness, observability, recovery, supportability, changeability and retirement conditions. The **Scrum Master or flow facilitator** helps the work move and improve without becoming the authority for product meaning, priority or technical decisions.

### Specialist controls: enable the outcome and protect it when needed

Specialist responsibilities are part of the design, not a final approval queue. Their constructive contribution is to make an obligation, risk or quality condition understandable early enough for the team to design and test it. Defensive intervention is appropriate when a proposed shortcut could create material harm, breach an obligation or leave the service unable to prove or recover its behaviour.

| Responsibility | Contribution and authority | Evidence and handoff |
| --- | --- | --- |
| Security | Makes actors, trust, protected resources, threats, controls and safe failure visible. Security authority decides or advises within the organisation's security governance; it does not own product meaning or the whole architecture. | Supplies control objectives, threat and access evidence, and conditions for development, testing, operation and privileged recovery. |
| Privacy | Connects people, purpose, classification, lawful handling, access, sharing, retention and deletion to the design. Privacy authority identifies privacy consequences and required safeguards; it does not replace business, records or product decisions. | Supplies privacy impact, data-handling and incident evidence, then returns unresolved consequences to the responsible product, data, legal or architecture decision. |
| Records and information governance | Protects provenance, official evidence, retention, legal hold, correction, archival and defensible disposal. Records authority determines the applicable recordkeeping conditions. | Supplies retention, provenance, disposal and audit evidence to product, data, operations, migration and retirement decisions. |
| Monitoring and Operations | Makes health, performance, behaviour, dependency condition, diagnosis and recovery visible. Operations owns live-service action within its authority; monitoring signals do not decide business meaning by themselves. | Supplies alerts, diagnostics, incident, recovery and actual-behaviour evidence to the service, product, maintenance and assurance boundaries. |
| Change Control | Makes impact, authorisation, compatibility, migration, rollback and timing visible for an occupied service. It coordinates the relevant authorities rather than absorbing their decisions. | Receives the change case and evidence, then returns readiness, residual risk, rollback or follow-up conditions to the responsible decision-maker. |
| Assurance and audit | Tests whether obligations, controls, decisions and evidence are credible, and whether residual risk is visible. Assurance should be independent enough to expose gaps without becoming the owner of the control. | Returns findings and evidence gaps to the responsible authority, with a clear condition for closure, acceptance or escalation. |

These responsibilities may be held by specialists, teams or people with several assignments. The assignment does not remove the boundary. When a specialist finds a contradiction, missing evidence or unsafe assumption, the issue returns to the requirement, design, implementation, operational or product decision that owns it. A specialist challenge is neither a veto without explanation nor a problem for another role to silently absorb.

### Product Owner and Architect: protect the delivery sequence

The Product Owner's responsibility is to manage and prioritise the tickets against the delivery strategy. They do not elicit architecture or take it over. They listen to the architect's logical blocking of the problem into a sequence and make that sequence visible in product decisions.

The [System LDM](../development/ldms.md#the-system-ldm-and-business-ldms) is prioritised before attention moves to the next business LDM where its shared foundations are needed. The [System LDM service sequence](../development/services.md#dependency-led-service-sequence) gives the dependency shape. The architect decides the logical boundary, what is coherent enough to hand forward, and when unresolved ambiguity must return to the responsible product, business or analysis decision; the Product Owner ensures the corresponding foundation tickets are not displaced by the next visible interface.

This is the minimum formwork for staged delivery. It is not a demand for perfect up-front design. The team may build a small slice, learn from it and change the design. The Product Owner holds the strategy against two tactical pressures: business demands for a visible feature before its foundations are ready, and developers' temptation to skip unfamiliar rigour. Skipping the sequence moves the cost into repeated reinterpretation, mistrust, defensive testing, rework and risk carried into every later change. The Product Owner protects the order, while architecture owns the design and development owns implementation.

## Related guidance

The [Shared Human Guidance](./readme.md) gives the wider route. [BUST Requirements](../stakeholders/deliverers/business-analysts/bust-requirements.md) and [Traceability and Evidence](../stakeholders/deliverers/business-analysts/traceability-and-evidence.md) develop the analyst perspective. [Product Purpose and Outcomes](../stakeholders/deliverers/product-owners/product-purpose-and-outcomes.md), [Acceptance and Evidence](../stakeholders/deliverers/product-owners/acceptance-and-evidence.md) and [Stakeholder Conflict and Authority](../stakeholders/deliverers/product-owners/stakeholder-conflict-and-authority.md) follow the product decisions. The [Stakeholder Roles](./reference/catalogues/stakeholder-roles.md), [Users to Consider](./reference/catalogues/users.md), [System Roles](./reference/catalogues/system-roles.md), [Domains and Capabilities](./reference/catalogues/domains-and-capabilities.md) and [Deliverables](./reference/catalogues/deliverables.md) catalogues provide the surrounding vocabulary and delivery context.
