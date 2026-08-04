# Software Development Lifecycle

A software development lifecycle (SDLC) is the set of activities through which a service is understood, discussed, decided, defined, designed, developed, delivered, operated, maintained and eventually decommissioned. It is a lifecycle, not a mandatory project methodology and not a claim that work happens once in a straight line.

Each SDLC phase is useful because it asks a different question. The phases can overlap, repeat and run at different levels. A whole service may be in Operations while a new capability is in Design and another is in Development. A production incident may return an existing capability to Discovery or Definition. A small change may pass through all ten phases quickly; a regulated or long-lived service may need substantial evidence in each.

The order is a reasoning frame:

```text
Discovery -> Discussion -> Decision -> Definition -> Design
     ^                                                          |
     |                                                          v
Decommissioning <- Maintenance <- Operations <- Delivery <- Development
```

The arrow back to Discovery is intentional. Evidence from design, construction, delivery or operation can change what the team understands. [Incident learning and corrective change](../../../stakeholders/deliverers/operators/incident-learning-and-corrective-change.md) explains how operational evidence becomes a recorded question, an authorised decision and verifiable lifecycle work. The phases do not remove the need for iterative delivery; they make the different kinds of work and evidence visible.

## Discovery

Discovery finds out what situation, opportunity, obligation, problem or change is actually present. It asks who is affected, what outcome matters, what already exists, what evidence is available, which constraints apply and what is still unknown.

BAs identify stakeholder groups and suitable SMEs. Product and business roles explain purpose and consequence. Architects identify the wider systems and major boundaries. Developers, testers, operations, security, data and assurance roles expose technical, quality, lifecycle and evidence conditions that a purely business description may miss.

Useful discovery outputs include a problem or opportunity statement, stakeholder map, initial capability and obligation map, existing-system context, known constraints, risks, assumptions, unanswered questions and a plan for further elicitation. Discovery should not pretend that a preferred solution is already proven.

A discovery may return to this phase when an incident, test, user observation, audit finding or new dependency shows that the original understanding was incomplete. A discovery output is ready to move forward when the team can explain what it is trying to understand and what evidence would change the direction.

## Discussion

Discussion brings the relevant perspectives together so that differences in language, needs, authority, risk and consequence become visible. It is where stakeholders and SMEs explain their conceptual desires and needs, and where the team tests whether apparently similar words mean the same thing.

The BA facilitates elicitation and records definitions, examples, exceptions, conflicts and decisions still needed. Architects, product and business roles discuss purpose and boundaries. Developers and testers challenge ambiguity and testability. Operations, security, data, privacy, records, audit and supplier roles add the constraints and evidence their responsibilities require.

Discussion is not a vote in which the loudest participant wins. It is also not a request for every participant to solve every technical detail. Its output is a clearer shared account of the concepts, outcomes, tensions, alternatives and questions that require a decision.

Discussion may continue after a decision when new evidence exposes a conflict or when implementation reveals that a term was understood differently. It is ready to support a decision when the relevant alternatives, affected groups, consequences and missing authority are visible.

## Decision

Decision chooses a direction within the authority available to the participants. It may decide purpose, priority, scope, policy, architecture, dependency, risk acceptance, quality target, delivery order, deferral or retirement. A decision should identify who made it, what evidence supported it, which alternatives were considered, what consequences are accepted and when it should be revisited.

Different roles decide different things. A sponsor may decide investment or escalation. A business owner may decide an outcome or business trade-off. A product owner may order product work. An architect may decide or recommend a structural boundary within their authority. A security, data, privacy, operations or audit role may own specialist acceptance conditions. A technical lead may decide implementation structure within the architecture. The decision record should not imply authority that the role does not possess.

Decision is not the same as agreement by everyone. A responsible decision can record disagreement, residual risk and a review condition. It is ready to move into Definition when the chosen direction and its authority are clear enough for the team to state what must be true.

## Definition

Definition turns the chosen direction into precise concepts and conditions that can be designed, built and checked. It defines the capabilities, actors, information, relationships, states, rules, obligations, contracts, quality outcomes, lifecycle conditions, boundaries and acceptance evidence that matter.

The BA and SMEs clarify conceptual language. Architects place responsibilities in the system landscape. Data, security, privacy, records, accessibility, operations, finance and assurance roles define the conditions relevant to their concerns. Developers and testers check that the definitions can be represented and verified without silently choosing an unsafe implementation.

A definition is not automatically a database schema, API payload or user-interface design. Those may be physical representations of the definition. Keep the meaning independent enough that different consumers, stores and integrations can be mapped to it when their responsibilities differ.

Definitions can remain deliberately incomplete where the uncertainty is explicit and the boundary, owner and next evidence are known. Definition is ready for Design when the team can distinguish required behaviour from assumptions, identify the responsible boundary and state what evidence will show that the definition has been met.

## Design

Design turns definitions into a coherent solution structure. It decides how stakeholder responsibilities, capabilities, domains, sites, flows, components, Logical Deployment Modules, layers, contracts, dependencies, data representations, security controls, quality measures and operational responsibilities fit together.

System design architects map the whole service and its wider relationships. Enterprise, business, data, integrations, security, platform and domain architects contribute the concerns within their authority. Technical leads shape implementable logical building blocks and delivery boundaries. Developers, testers and operations review whether the design can be built, checked, run, recovered and maintained.

Design should make dependencies, authority, lifecycle, failure behaviour, quality targets, evidence and deliberate deferrals visible. It does not need to decide every class or provider option before development begins. It does need to prevent the first implementation from becoming the accidental owner of unresolved meaning.

Design is iterative. A vertical slice may reveal that a contract is too narrow, a domain boundary is wrong, a quality target is unmeasurable or an external dependency cannot provide the assumed authority. That evidence returns the relevant question to Discussion, Decision or Definition rather than being hidden in code.

## Development

Development constructs the solution through code, configuration, infrastructure, tests, mappings, schemas, documentation and operational material. It also constructs the wider deliverables that make the outcome usable, trusted, reachable and discoverable. Developers implement the contracts and responsibilities that design established, while preserving the difference between conceptual meaning, logical behaviour and physical representation.

System developers build capabilities and application behaviour. Integration developers implement cross-boundary contracts. Environment and pipeline developers make construction and deployment repeatable. Test developers create automated evidence. Maintenance-minded developers identify compatibility and migration consequences even when the capability is new. BAs, SMEs, architects, technical leads, operations, security and data roles remain available when construction reveals a question the design did not settle.

Development is not complete when code compiles or a screen appears. The relevant slice must show its security, data, lifecycle, failure, quality, audit and recovery behaviour, together with the tests and diagnostics that make those claims credible.

Development may overlap Delivery for one capability while another is still being built. A defect or unexpected test result can return work to Definition or Design. That is learning, not a failure of the lifecycle model.

## Delivery

Delivery moves a tested and approved set of deliverables into the environments, registries, domains, corporate surfaces and other boundaries where intended consumers, operators or dependent systems can use or find it. It includes packaging, migration, configuration, infrastructure, release controls, compatibility checks, communication, readiness evidence and rollback or recovery arrangements. The [Registries](./registries.md) catalogue distinguishes enterprise registries consulted during delivery from project registries updated by the delivery itself.

Delivery roles coordinate timing and risk. Environment and pipeline developers automate repeatable movement. Operations checks the target environment and recovery route. Testers and product or business roles confirm the evidence appropriate to the change. Architects and technical leads confirm that the deployed shape still respects the intended boundaries and dependencies.

Delivery is not merely copying binaries or clicking a release button. A change may alter schema, queues, caches, indexes, permissions, configuration, data classification, downstream contracts, support procedures or audit evidence. Those effects belong in the delivery decision.

A delivery is ready for Operations when the service or capability has a known version, its dependencies and configuration are resolved, readiness and diagnostics are meaningful, the responsible people can support it and the effect of failure or rollback is understood.

## Operations

Operations provides the live service and keeps it observable, available, secure and recoverable. It includes monitoring, alerting, incident response, capacity, dependency management, access management, routine intervention, backup and restore, scheduled work, support, communications and evidence of actual behaviour.

Operations staff use the signals and controls the development and delivery teams provide. They need to know what healthy and degraded states mean, which dependencies are required or optional, how work is retried or reconciled, what data may appear in diagnostics and who may perform a consequential action. A service is not operationally complete merely because its happy path works.

Operational evidence can change the design. Repeated timeout, confusing support work, unexpected load, inaccessible interaction, data-quality failure or an audit gap may require new Definition, Design, Development or Delivery work. Operations is therefore part of the lifecycle's learning loop, not the final destination after engineering stops.

## Maintenance

Maintenance preserves and improves an occupied service. It includes defect correction, security updates, dependency renewal, compatibility work, performance improvement, data correction, schema evolution, supportability improvements, refactoring, migration, capacity adjustment and controlled enhancement.

Maintenance starts from what existing people and systems already rely upon. The maintenance developer and operations team investigate consumers, historical behaviour, contracts, data copies, deployment conditions, recovery options and hidden dependencies before changing them. Testers preserve existing evidence while adding coverage for the new risk. Product, business, BA and SME roles confirm whether the changed behaviour still represents the intended outcome.

Maintenance is not a lesser version of Development. It has a different risk posture because the service is occupied and its existing behaviour may be relied upon even when it was poorly documented. A small code change can have a large operational or contractual consequence. Controlled scope, compatibility, rollback, observability and evidence matter more than the apparent size of the edit.

Maintenance may discover that the service needs a new design, a replacement capability or retirement. That is a legitimate return to Discovery and Decision, not a reason to keep extending a boundary that can no longer carry its obligations.

## Decommissioning

Decommissioning retires a service, capability, dependency, data representation or delivery boundary deliberately. It asks who still depends on it, what contracts and records must be migrated or preserved, what access must be removed, what data must be deleted, anonymised or archived, which downstream copies exist, how consumers are notified and what evidence proves that retirement is complete.

Decommissioning needs business, product, architecture, data, security, operations, maintenance, records, privacy, audit, finance, supplier and affected-user perspectives as applicable. A service may be technically stopped while its data, backups, reports, integrations, credentials, domains, certificates, queues or support commitments remain active.

The retirement decision should name the replacement or end state, transition conditions, dependency and data inventory, communication plan, rollback or contingency period, final evidence, ownership of residual records and the date on which remaining access and infrastructure will be removed. Do not treat deleting the main application or database as proof that the service's obligations have ended.

A decommissioning activity may discover an unexpected consumer or obligation and return to Discovery or Discussion. Retirement is complete only when the intended service boundary has ceased operation, remaining obligations have an owner and the evidence can show what was retained, transformed, transferred or removed.

## Iteration and evidence

The phases form a loop around a living service:

- Discovery identifies what is present and what matters.
- Discussion makes different perspectives and meanings visible.
- Decision selects a direction and records authority and consequence.
- Definition states what must be true.
- Design places responsibilities and relationships.
- Development constructs and tests the solution.
- Delivery makes a controlled change available.
- Operations provides and observes the live service.
- Maintenance preserves and improves it under real reliance.
- Decommissioning retires it with its remaining obligations understood.

At every phase, record what is known, what is assumed, what is decided, what is deferred, who is responsible and what evidence supports the next move. The [Stakeholder Roles](./stakeholder-roles.md) catalogue explains the different perspectives that contribute to that evidence. The [Qualities](./qualities.md) catalogue explains how quality targets connect system behaviour, data and human outcomes.

The [Deliverable Systems](./deliverable-systems.md) catalogue distinguishes the delivery, service, consumer and testing systems. The [Deliverables](./deliverables.md) catalogue records the wider set of data, content, addressing, discovery, corporate surfaces, operational material and evidence that must exist around them.

## Related guidance

[Delivery Guidance](../../../delivery/readme.md) keeps the lifecycle connected to the wider delivered service and its continuing responsibilities. The orientation paper [Phases, Roles and Stakeholders](../../../orientation/phases-roles-and-stakeholders.md) introduces the distinction between time, responsibility and affected groups. [Guidance for System Design Architects](../../../orientation/guidance-for-system-design-architects.md), [Guidance for Tech Leads](../../../orientation/guidance-for-tech-leads.md) and [Guidance for Developers](../../../orientation/guidance-for-developers.md) show how the lifecycle concerns become architecture, delivery and code.
