# Guidance Glossary

This glossary gives the plain meaning first. The technical label is included so people can recognise it in code and documentation. You do not need to memorise the labels to understand the ideas.

## Action

A request for the system to do something, such as add, edit, submit, approve, return or cancel. An action is not automatically the same as a state change.

See [Palette Elements](../palette/elements.md).

## Action Zone

A group of actions that belong together because of a record, step, state or permission context. For example, applicant actions and approver actions may be shown in different zones.

## Agent guidance

Compact instructions that tell an AI agent what rules apply to a task. Agent guidance should be precise and task-selective. It links to human explanations rather than copying them.

See [Agent Guidance](../../agents/readme.md).

## Application boundary

The part of the service that turns a request into an application capability. It coordinates use-case behaviour without exposing transport or persistence details to every caller.

## Broker

A component that knows how to reach another capability or external system. It hides the details of the call from the visible experience. In technical language, it is a boundary connector.

See [Palette Relationships](../palette/relationships.md).

## Registry

An owned and governed collection of records used for lookup, decision, control, handoff or lifecycle. A registry has a defined scope, authority, maintainer, record shape, status, review condition and stale-entry treatment. An enterprise-referred registry informs or constrains projects; a project-produced registry records the project's own dependencies, commitments, assignments, schedules, risks or evidence. A software registry building block may implement lookup and lifecycle for participants or definitions, but a governance registry is not automatically a repository or a general-purpose collection.

See [Registries](./catalogues/registries.md) and [Logical Building Blocks](./catalogues/logical-building-blocks.md#registry).

## Business Analysis

The discipline of identifying needs, understanding stakeholders and determining solutions that deliver value in a business or organisational context. This guidance uses the [International Institute of Business Analysis (IIBA)](https://www.iiba.org/) and its [BABOK Guide](https://www.iiba.org/standards-and-resources/babok/) as the authoritative external source for Business Analysis terminology and practice. This repository adds engineering guidance for carrying that work into Domains, capabilities, contracts, deliverables and evidence; it does not replace the IIBA body of knowledge.

## Business Analyst (BA)

A person who helps a team understand needs, stakeholders, requirements, constraints, decisions and consequences, then carries that understanding into a form the wider team can use. A BA does not silently become the Product Owner, Domain authority, architect, developer, tester or operator. The BA brings the right knowledge together and makes the meaning and unresolved questions visible.

This guidance follows IIBA terminology and practice as its authoritative external reference. Its BUST mnemonic was developed by the BA contributors to this guidance as a practical way to keep Business, User, System and Transitional requirements visible.

## Stakeholder Analyst

The working role name used in this repository for analysis that must cover the full stakeholder and user landscape, not only business owners or organisational sponsors. A Stakeholder Analyst identifies stakeholder and user groups, finds representative SMEs, elicits their knowledge and consequences, and carries the resulting meaning into requirements, design, acceptance and evidence.

Stakeholder Analyst is not presented as an IIBA or BABOK replacement term. Business Analysis remains the recognised discipline and external reference. A Stakeholder Analyst may be a Business Analyst, or another person carrying the same analysis responsibility, but the local name makes the required breadth explicit: consumers, represented subjects, providers, support, Operations, Maintenance, Monitoring, Change Control, Security, Privacy, Records, assurance, suppliers and connected systems may all hold material knowledge.

## Stakeholder

A person, group, organisation or connected system that can affect a service, be affected by it, depend on its result, supply knowledge or evidence, or hold authority over an obligation the service must fulfil. A stakeholder need not use the service directly. See [Stakeholder Roles](./catalogues/stakeholder-roles.md).

## User

A person, group or connected system that directly uses a site, capability, information or result. A user may also be an affected person or stakeholder, but those terms are not interchangeable: someone may be represented in a service, hold authority or carry consequences without operating it. See [Users to Consider](./catalogues/users.md).

## Product Owner

A Product Owner is the person accountable for ordering product work and making product decisions within delegated authority. They connect stakeholder and organisational needs to valuable, testable outcomes, make scope and sequencing visible, and bring the right decision-makers and SMEs into unresolved questions. The title and authority vary by organisation; it does not automatically include business ownership, policy authority, architecture, technical leadership or delivery-process facilitation.

## Product Manager

A Product Manager is commonly responsible for the broader product direction and lifecycle: understanding the market or organisational context, product purpose, users, value, viability, strategic positioning, investment and longer-term outcomes. In some organisations the Product Manager also acts as Product Owner; in others, the Product Owner turns that direction into near-term ordered outcomes for a delivery team.

These titles overlap and are not universal standards. The useful question is which person has authority for strategy, product purpose, investment, priority, scope, acceptance and day-to-day ordering. Do not assume that a Product Owner can make Product Manager decisions, or that a Product Manager has the detailed authority or availability needed for every backlog decision.

## Scrum Master and Kanban flow facilitator

A Scrum Master helps a Scrum team understand and improve its way of working, removes or escalates impediments, supports effective events and protects useful collaboration. A Kanban team has no mandatory Scrum Master role; it may assign a flow facilitator, delivery manager, service delivery manager or another named person to help manage flow, policies, feedback, blockers and improvement.

Neither role owns product priority, business meaning, architecture or implementation merely because they facilitate delivery. If no person is assigned, the accountability still exists: the team and its sponsoring organisation must explicitly name who will perform the necessary facilitation, or record that the responsibility is currently unassigned as a delivery risk. It should not silently default to the Product Owner, architect or most senior developer. A person may hold both product and flow responsibilities in a small team, but the two accountabilities and their conflicts must remain visible.

## Technical Analyst

A Technical Analyst is a responsibility profile for making technical meaning precise enough for architecture, implementation, testing and operation. Depending on the organisation, the role may analyse API and event contracts, message and data structures, integration mappings, technical constraints, non-functional requirements, error and retry behaviour, compatibility, traceability and technical acceptance conditions. They help connect stakeholder and Domain meaning to the interfaces and technical boundaries that must preserve it.

Technical Analyst is not a universal job title or a claim that one person owns every technical decision. The analyst should work with the relevant architect, Domain authority, developers, testers, security and privacy specialists, data and integration owners, Operations, Maintenance and other SMEs. They may propose or document a contract, but the responsible boundary owns its meaning and authority, and specialist roles must validate the conditions they own. A Technical Analyst does not silently become the system architect, API owner, security authority, operational SME or developer.

Business Analysts are not automatically unsuitable for this work, and architects are not automatically the best people to perform it. Either may carry the Technical Analyst responsibility when they have the demonstrated knowledge, capacity and accountability for the particular contracts and technical boundaries involved. Where the work is substantial, specialised or high-risk, assign it explicitly to a suitably capable Technical Analyst or technical team member rather than assuming that a BA will fill the gap or that an architect must absorb it.

## Solution Architecture Document (SAD)

A Solution Architecture Document (SAD) is a controlled, pre-market description of the problem space, intended outcome, desired solution shape, boundaries, constraints, responsibilities, quality expectations and response conditions. It gives vendors, delivery partners and development shops a common basis from which to prepare a Solution Design Document (SDD) or other response.

A SAD is not a living document. Because it may be used as the basis of a procurement, proposal, statement of work or contract, its released versions must remain stable and identifiable. A material change requires a new version, an explicit amendment or a new market exercise, with the effect on responses and commitments made visible. A SAD may point to separately governed definitions or decisions, but it must not silently absorb later design detail.

SAD is a local abbreviation in this guidance. Some organisations use it for System Architecture Document or Software Architecture Document; use the expansion and authority defined for the particular engagement rather than assuming the acronym has one universal meaning.

## Solution Design Document (SDD)

A Solution Design Document (SDD) is a respondent's or solution provider's proposed design for satisfying the SAD. It explains the proposed solution structure, capabilities, boundaries, integrations, data, delivery approach, quality characteristics, assumptions, dependencies, exclusions, risks and responsibilities. Multiple vendors or delivery partners may produce different SDDs in response to the same SAD.

An SDD is not automatically a commitment or a contract. The relevant authority must evaluate and accept the proposal, and the accepted scope, obligations and changes must be carried into the agreement and controlled delivery records. After acceptance, the SDD remains a solution-level reference; it does not replace the more detailed Technical Design Documents (TDDs) needed to implement particular work.

## Technical Design Document (TDD)

A Technical Design Document (TDD) describes how an accepted solution or a specific change will be implemented at the technical boundary concerned. It may cover components, interfaces, schemas, mappings, algorithms, configuration, infrastructure, security controls, observability, migration, testability, rollout, rollback, recovery and compatibility. TDDs are developed as the relevant work becomes sufficiently understood and are referenced from the work items, contracts, decisions, tests and evidence they support.

A TDD must remain consistent with the accepted SDD and SAD. If implementation reveals that the solution or requirement must change, the change returns to the responsible decision or approval path; it is not hidden by quietly changing the TDD. TDD means Technical Design Document in this guidance. Do not confuse it with Test-Driven Development, which is a development practice rather than a deliverable.

## IIBA

The **International Institute of Business Analysis (IIBA)** is the professional body and authoritative external reference used here for Business Analysis practice. Refer to IIBA and the BABOK Guide when a Business Analysis term, role or practice needs a recognised definition. Local delivery guidance may extend the application of that practice to serious-system architecture, implementation, operations and maintenance, but should not quietly redefine the underlying Business Analysis discipline.

See [IIBA](https://www.iiba.org/) and the [BABOK Guide](https://www.iiba.org/standards-and-resources/babok/).

## BREAD/ST

A common baseline for a managed item:

- Browse;
- Read;
- Edit;
- Add; and
- Delete or another controlled lifecycle operation, plus State Transitions.

It is a recognition aid, not a command to force every operation into generic CRUD.

See [Common Flows](../orientation/flows.md).

## BREAST

A request-preparation variation of the baseline:

- Browse;
- Read;
- Edit;
- Add;
- Submit; and
- Transition.

Submit is important because it usually freezes or versions information and moves the request into assessment. Delete or withdrawal remains a separate lifecycle decision.

See [Request, assessment, approval and payment](../examples/11-request-offer-approval/after.md).

## Requirement

An agreed statement of something a serious system must achieve, provide, prevent, preserve or prove. A requirement is not merely a request, feature label, screen description or implementation task. It carries enough meaning, authority and context to be placed in a responsible Domain, capability, contract, acceptance predicate or lifecycle condition. See [Shared Requirements](../shared/requirements.md).

## Capability

A useful, owned ability the system provides, such as creating a request, reviewing evidence, approving a decision or producing a report. A capability belongs to a **Domain**: the area of business meaning and responsibility that gives the capability its purpose. The Domain enables the capability by providing its concepts, rules, states, relationships and authority.

A capability contains one or more **Functions**. A Function is a smaller operation or responsibility within the capability, such as adding Evidence, submitting a Request, returning it for information or approving it. Functions should not be mistaken for the whole capability or for unrelated technical helper methods.

**Functionality** is an aspect of a Capability: the observable behaviour or outcome that the capability makes available to its consumer. Functionality describes what can happen or be achieved; Capability also includes the Domain meaning, ownership, contract, lifecycle, security and evidence that make that behaviour dependable.

The same word may describe different capabilities in different Domains. This is an example of [polysemy](#polysemy). The name alone is not enough; the Domain and the surrounding contract give the word its meaning.

## Conceptual

Conceptual describes how people or connected systems recognise, name and talk about something. A conceptual model uses the language, distinctions, relationships and outcomes that make sense to the people using or depending on the service. That language may be incomplete, locally understood or polysemous. Conceptual does not mean scientifically perfect; it means recognisable to the consumer. See [Conceptual, Logical and Physical Models](./catalogues/conceptual-logical-physical-models.md) for the distinction between model type and implementation position.

## Logical

Logical describes the engineering work of breaking a recognised problem into ontological categories, identities, relationships, states, rules and transitions. A logical model decides what the system must distinguish and what it may combine so that behaviour remains dependable across changes in consumer, process, organisation or technology. It is not automatically the same as a conceptual interface, physical code, storage model, framework model or vendor model.

## Physical

Physical describes the representation and execution required to make the service real. It includes consumer-facing interfaces, application and domain objects, mappings, database records, schemas, files, cache entries, search indexes, queue messages, provider resources and framework objects. Physical representations are necessary, but they do not automatically define the logical meaning or the conceptual language of the service. A physical representation may be close to the conceptual language at an interface, or close to the logical model in application and domain code, depending on its responsibility.

## Ontological

Ontological concerns the kinds of things, identities, relationships, states, events, rules and responsibilities that a problem space needs the system to recognise as meaningful. It asks what is the same, what is different and what can happen. Ontological is a north-star abstraction, not a claim that one universal vocabulary or fixed primitive list fits every Domain. See [Ontological Decomposition](../orientation/ontological-decomposition.md).

## Ontological primitives

Ontological primitives are basic distinctions used to build or explain a model in a particular context, such as identity, thing, person, organisation, relationship, state, event, action, rule, authority, value, information or evidence. The useful set depends on purpose and the distinctions that must survive change. They are not an engineering requirement to reduce every domain to the 65 Natural Semantic Metalanguage primes. See [Ontological Decomposition](../orientation/ontological-decomposition.md).

## Enduring

**Enduring** describes a concept whose identity and responsibility persist beyond one transaction, workflow, appointment, membership, provider or physical representation. An enduring concept may change attributes, states or affiliations and may eventually be retired, but it remains the same kind of thing for the purposes that own it. Examples include a Person, Organisation, Group or Location. Enduring does not mean unchanging, immortal or globally authoritative.

See [Entity Lifecycle Patterns](./catalogues/entity-lifecycle-patterns.md).

## Transient

**Transient** describes a concept bounded by a time, context, process, decision, appointment, membership, assignment or interaction. A transient concept may have its own identity, state, authority, audit history and evidence. It is not disposable or merely in-memory. Examples include a StudentAt membership, access grant, team assignment, subscription, enrolment, booking or decision. Transient concepts often need effective dates and historical queries.

See [Entity Lifecycle Patterns](./catalogues/entity-lifecycle-patterns.md).

## Enduring and Transient modelling

Enduring versus Transient is a foundational logical-modelling distinction. It asks which concepts must retain identity and meaning across changing circumstances and which concepts record bounded relationships or participation involving them. It helps translate conceptual language into logical concepts without making a current role, membership or workflow the accidental identity of a person or organisation.

This distinction works alongside Domain-Driven Design (DDD), bounded contexts, entities, aggregates, value objects and domain events. It is a lifecycle question, not a claim that every Enduring concept is an aggregate or every Transient concept is a value object. See [Entity Lifecycle Patterns](./catalogues/entity-lifecycle-patterns.md).

## Domain

The area of meaning in which concepts, rules, decisions and capabilities make sense together. A Domain is not only a database area, project or folder. It gives a capability its vocabulary and boundaries.

A **business domain** describes the people, records, decisions, relationships and outcomes the service exists to support. A **technical or platform domain** describes a coherent technical problem, such as identity, settings, persistence, startup or diagnostics. Both need explicit concepts, contracts, lifecycle rules and responsible boundaries.

A **domain model** is the logical ontological model of one domain. It describes the things, identities, relationships, states and rules that the system must understand. It is not automatically a storage model, transport model or framework model.

In technical language, a Domain-Driven Design (DDD) team tries to keep the software language close to the language and rules of the relevant Domain.

## Logical Deployment Module (LDM)

An LDM is a logical package whose components are delivered together as one package. It is not automatically independently deployable, and it may be deployed at the same time as other LDMs in a whole-system deployment. It is not automatically a DDD bounded context, aggregate or single domain. One LDM may contain one or more explicit domains when those domains are related and their deployment, responsibility and contracts justify keeping them together. When the domains no longer share a coherent purpose, lifecycle or responsibility, the team should consider a separate LDM.

For example, a Systems LDM may contain related User, Role, Permission and Settings domains because they support the operation of the same service foundation. A business LDM may then contain Request and Evidence domains for the organisation's business need. Person and Group may belong in the Systems LDM or a separate LDM depending on their complexity, reuse, responsibility and lifecycle. The example is a way to reason about structure, not a mandatory decomposition.

## Function

A focused operation within a Capability. For example, a Request capability may contain Functions to prepare answers, add Evidence, submit, return for information and approve. Functions can be reused or composed, but they remain part of the capability that gives them meaning.

## Technical debt

## Capabilities and Functions

A Capability is an owned, dependable ability provided within a Domain. A Function is a focused operation or responsibility within that capability. A Function describes part of what can happen; a Capability also carries the Domain meaning, ownership, contract, lifecycle, security and evidence that make the ability dependable. See [Capabilities and Functions](../stakeholders/business-analysts/functional-and-quality-requirements.md#capabilities-and-functions).

## Objectives and Outcomes

An Objective is an intended direction or condition that guides investment and choice. An Outcome is the observable change or result that should become true for identified people, systems or the organisation. An objective may lead to several outcomes; an outcome needs measures, constraints and evidence. Neither is the same as a feature or implementation task. See [Drivers, Stakeholders, Objectives and Outcomes](../stakeholders/business-analysts/drivers-stakeholders-objectives-outcomes.md).

## Technical debt

A deliberate temporary compromise made to achieve a necessary outcome sooner, with an identified owner, a repayment condition, a credible source of repayment capacity and a visible account of the cost and risk. A compromise is not responsible technical debt merely because the team intends to revisit it someday. If there is no realistic path to repayment, it is [technical theft](#technical-theft).

## Technical theft

An unpaid technical compromise whose cost, risk or rework is knowingly transferred to future developers, operators, users or the organisation. Calling it theft makes the responsibility visible: the original decision consumed a benefit while leaving other people to pay. Technical theft includes omitted foundations, hidden exceptions and knowingly fragile implementations that are described as debt without an owner, trigger or capacity to correct them.

Technical theft is not a judgement about a person who makes a difficult emergency decision. A critical incident may justify temporary simplification. The theft occurs when the compromise is concealed, normalised or left without a credible route back to a dependable design.

## BUST

A practical reminder developed by the BA contributors to this guidance to consider **Business, User, System and Transitional** requirements together. BUST is used here as an engineering-facing mnemonic for applying Business Analysis thinking to a serious system. It is not presented as an IIBA or BABOK term, a replacement for IIBA terminology or the BABOK Guide, and it should not be treated as four isolated documents.

The Transitional part is frequently misunderstood or omitted. It covers the requirements and deliverables needed to move from the current arrangement to the intended one, such as migration, training, parallel running, staged release, fallback, legacy integration and decommissioning. Transitional requirements are temporary in subject, but they are still real requirements and must have ownership, readiness evidence and a retirement condition.

See [BUST Requirements](../stakeholders/business-analysts/bust-requirements.md).

## Polysemy

Polysemy means that one word has more than one related meaning, often depending on the Domain in which it is used. For example, **Request** may mean a funding application in one Domain, a customer service ticket in another, and a technical HTTP request in a software boundary.

The word is not wrong in each case. The surrounding Domain, contract, state and rules explain which meaning is intended. When designing a capability, do not assume that a familiar word means the same thing everywhere.

## Homonymy and Monosemy

**Homonymy** is the relationship between forms that are the same or very similar while their meanings are unrelated or historically distinct. **Polysemy** concerns related meanings of one word. The distinction is useful but not always settled by the word alone; Domain evidence and usage determine whether the meanings should be treated as related, separate or merely ambiguous.

**Monosemy** is the condition in which a term has one established meaning within the relevant context. **Monosemous** describes that term. A monosemous term in one bounded context may still be polysemous across the wider system, so local clarity does not remove the need to state the Domain.

### Role is polysemous

**Role** can mean different things at different layers:

- a **real-world business role** describes what a person or organisation does in a business or service, such as applicant, assessor, approver or finance officer;
- an **access-context role** describes the position or context in which someone is acting for a particular resource, workspace, organisation or situation;
- a **system authorisation role** is a configured permission grouping used by software to allow or deny operations; and
- an **implementation role** describes what a component does in the software, such as Coordinator, Presenter, Player or Broker.

These roles may be related, but they are not interchangeable. A person acting as an assessor in the real world does not automatically have every system permission called `Assessor`. A user may hold a system role in one context and not another. A software component's implementation role is not a human business role.

### System is polysemous

**System** can mean different layers of a wider arrangement. There are two useful views, and they should not be confused.

For the wider relationship between those layers, see [Systems Within Systems](../orientation/systems-within-systems.md). That paper uses **polysystem** as a reminder that a digital system can participate in several wider systems of obligations, duties and capabilities at once.

#### The organisational and service view

This view describes what the organisation and its surrounding environment are trying to achieve:

```text
legal and regulatory context
  -> sector or industry system
	  -> wider organisational system
		  -> business service system
			  -> digital solution
				  -> digital system
					  -> web service or application capability
```

- A **wider organisational system** includes people, responsibilities, processes, information, physical resources, partners and digital solutions used to operate an organisation.
- A **business service system** is the people, capabilities, processes, information and supporting resources through which an organisation provides a service or performs an operating function.
- A **digital solution** combines one or more digital systems with data, processes, configuration and user experience to solve a problem.
- A **digital system** is a coordinated set of software and technical services that provides part of that solution.
- A **web service** is a network-accessible software capability within a digital system or solution. It is not automatically the whole business service system.

#### The technical execution view

This view describes what makes the digital system run:

```text
web service or application process
  -> runtime and web server
	  -> operating system
		  -> virtual machine, container or managed runtime
			  -> host, cloud or physical infrastructure
```

A web service can therefore be **part of** an organisational digital solution while also **running on** an operating-system and infrastructure stack. “Part of” describes a design or business relationship. “Runs on” describes a technical execution relationship.

The boundaries are not always physical containers. They may be connected networks of people, organisations, rules, processes and technology. The word System must therefore be qualified when it matters: system for whom, at which layer, with which boundary, purpose, authority and lifecycle?

## Service

A **service** is a capability with a contract and a responsible boundary. The word has related meanings at different layers and should be qualified when the distinction affects authority or lifecycle.

- A **business service system** is the people, capabilities, processes, information and resources through which an organisation provides a service or performs an operating function. See [Systems Within Systems](../orientation/systems-within-systems.md#the-organisational-and-service-view).
- A **service capability** is an agreed ability provided to consumers and stakeholders, with a promise, owner, evidence, support, operation and route for change or retirement. See [Service Provider](./catalogues/stakeholder-roles.md#service-provider).
- A **designed service** is a capability with a contract and boundary in the logical and delivery model. See [System LDM Services](../development/services.md) and [Contracts](../development/contracts.md).
- A **web service** is a network-accessible software capability within a digital system or solution. It is one physical or technical representation, not automatically the whole business service system. See the [System polysemy](#system-is-polysemous) entry above.

When reading **Service Provider**, **service capability** or **service** in a deployment context, check which layer is intended. The organisation's service promise, logical capability and technical service may be related without being the same boundary or authority.

## Contract

A shared agreement about what a boundary provides, what it needs and what callers may rely upon. A contract can be implemented by an object or service and can be used for mapping, schema, validation, discovery or policy.

## Coordinator

A component that manages movement between surfaces or steps. It sequences, transitions and gates a journey. It should coordinate the journey without absorbing every business rule.

See [Palette Technical Terms](../palette/technical-terms.md).

## Design completeness

The intended structure is known: boundaries, contracts, lifecycle, security, persistence intention, mappings, relationships and deferrals are described. This does not mean every implementation has been built.

## Deferred capability

A capability that is not being built now but has a known place, responsible boundary, contract direction, dependencies, lifecycle and condition for future construction.

## Event

A statement that something happened. The producer owns the fact. A consumer may respond, retry its own handling or explicitly emit another event. An event is not automatically a command.

## Flow

A repeated journey that coordinates capabilities, actions, decisions or state changes into an outcome. A flow gives the journey a recognisable shape. It is not a replacement for the capabilities beneath it.

See [Common Flows](../orientation/flows.md).

## Domain-Driven Design (DDD)

A way of designing software around the important meanings, rules and decisions of a business or problem area. DDD is not a requirement to use a particular database or framework. Its terms help a team discuss which concepts belong together and where rules should live.

## Ubiquitous language

The agreed words used by the people who understand a Domain and by the software that represents it. The aim is not to force one word across every Domain. The aim is to make the meaning of each word clear in its context and to avoid accidental polysemy.

## Bounded context

A boundary within which a set of terms and rules has one consistent meaning. The same word may legitimately mean something different in another bounded context. Contracts and mappings make the relationship between contexts explicit.

## Entity

A concept whose identity remains important as its information changes. An Entity may have a lifecycle and state. Identity is not the same as an email address, display label or database row number.

## Value Object

A concept defined by its values rather than by an independent identity. Examples may include a money amount with currency, an address or a date range. A Value Object should express the rules that make its values valid.

## Aggregate

A group of related domain objects treated as one consistency boundary for particular changes. An Aggregate is not automatically the same as a database document or a screen model.

## Aggregate Root

The entry point through which an Aggregate is changed. It protects the rules that must remain consistent within the boundary. Other parts of the system should not modify the Aggregate's internals directly.

## Repository

A boundary that provides access to domain or persisted information in terms useful to the application. In this guidance, a repository also carries governed query and visibility policy where it owns the persistence source. It is not a general-purpose shortcut to the database.

## Domain Service

An operation that expresses important Domain rules but does not naturally belong to one Entity, Value Object or Aggregate. It should remain focused on Domain meaning rather than becoming a general utility or application coordinator.

## Application Service

A service that coordinates an application use case across contracts, validation, authorisation, mapping, repositories and external capabilities. It does not replace the Domain rules owned by Entities, Value Objects, Aggregates or Domain Services.

## Domain Event

An Event that records a meaningful fact in a Domain, such as a Request being submitted or an approval being granted. It is a fact, not a command. Consumers decide whether and how to respond.

## Human guidance

Explanations written for people from different roles and levels of technical experience. Human guidance explains the problem and concept before the technical term.

See [Human Guidance](./readme.md).

## Lifecycle responsibility

The responsibility for keeping a capability coherent as it is created, changed, operated and eventually retired. The first explanation should use “responsible boundary” rather than assuming that Owner or Steward is understood.

See [Responsible Boundaries and Deferred Design](../orientation/responsible-boundaries-and-deferred-design.md).

## Mapping

The deliberate translation between representations, such as a stored record, a domain object, an application model and a response shown to a consumer. Mapping protects meaning, security and future change.

See [Object mapping example](../examples/06-object-mapping/after.md).

## Player

A component that presents and operates one capability or focused record. It may load, validate, track changes, submit or cancel.

## Presenter

A component that frames and coordinates a collection, page, tree or ordered group. It may manage selection, filtering, ordering and paging.

## Renderer

A component that turns a model, definition or state into visible output. It concentrates on representation rather than application orchestration.

## Responsible boundary

The part of the system or team where a capability belongs and where its lifecycle responsibility is maintained. It does not require a particular named person to be available before design can proceed.

## Slice

A complete capability carried from an external boundary through application rules to stored state or an external effect. A vertical slice is a way to keep the capability complete and testable across the building.

See [Vertical Slices](../../agents/conventions/capabilities/slices.md).

## Stewardship

The technical term for lifecycle responsibility. It means keeping a capability coherent across its contract, state, security, dependencies, tests, operation and change. Use the plain phrase first when writing for a wide audience.

## State

The current lifecycle position of a capability, such as draft, submitted, under assessment, approved, published, suspended or closed.

## State Change

A deliberate move from one state to another. Submission, approval, publication, suspension and closure usually need explicit rules rather than being hidden inside a general field update.

## View

The experience a person recognises, such as a page, form, list, tree, workspace, report or sequence. A View is not necessarily the boundary that owns every behaviour visible within it.

See [The Palette: First Look](../palette/first-look.md).

## WGF: What Goes First?

A planning reminder that asks what happens if a part is included, deferred or omitted, and which designed structure must remain so later construction can continue without guessing.

See [YAGNI versus WGF](../orientation/design-before-build-and-wgf.md).
