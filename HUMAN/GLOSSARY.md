# Guidance Glossary

This glossary gives the plain meaning first. The technical label is included so people can recognise it in code and documentation. You do not need to memorise the labels to understand the ideas.

## Action

A request for the system to do something, such as add, edit, submit, approve, return or cancel. An action is not automatically the same as a state change.

See [Palette Elements](./PALETTE-ELEMENTS.md).

## Action Zone

A group of actions that belong together because of a record, step, state or permission context. For example, applicant actions and approver actions may be shown in different zones.

## Agent guidance

Compact instructions that tell an AI agent what rules apply to a task. Agent guidance should be precise and task-selective. It links to human explanations rather than copying them.

See [Agent Guidance](../AGENTS/README.md).

## Application boundary

The part of the service that turns a request into an application capability. It coordinates use-case behaviour without exposing transport or persistence details to every caller.

## Broker

A component that knows how to reach another capability or external system. It hides the details of the call from the visible experience. In technical language, it is a boundary connector.

See [Palette Relationships](./PALETTE-RELATIONSHIPS.md).

## BREAD/ST

A common baseline for a managed item:

- Browse;
- Read;
- Edit;
- Add; and
- Delete or another controlled lifecycle operation, plus State Transitions.

It is a recognition aid, not a command to force every operation into generic CRUD.

See [Common Flows](./FLOWS.md).

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

## Capability

A useful ability the system provides, such as creating a request, reviewing evidence, approving a decision or producing a report. A capability belongs to a **Domain**: the area of business meaning and responsibility that gives the capability its purpose. The Domain enables the capability by providing its concepts, rules, states and relationships.

A capability contains one or more **Functions**. A Function is a smaller operation or responsibility within the capability, such as adding Evidence, submitting a Request, returning it for information or approving it. Functions should not be mistaken for the whole capability or for unrelated technical helper methods.

The same word may describe different capabilities in different Domains. This is an example of [polysemy](#polysemy). The name alone is not enough; the Domain and the surrounding contract give the word its meaning.

## Domain

The area of business meaning in which concepts, rules, decisions and capabilities make sense together. A Domain is not only a database area or a folder. It gives a capability its vocabulary and boundaries.

In technical language, a Domain-Driven Design (DDD) team tries to keep the software language close to the language and rules of the relevant Domain.

## Function

A focused operation within a Capability. For example, a Request capability may contain Functions to prepare answers, add Evidence, submit, return for information and approve. Functions can be reused or composed, but they remain part of the capability that gives them meaning.

## Polysemy

Polysemy means that one word has more than one related meaning, often depending on the Domain in which it is used. For example, **Request** may mean a funding application in one Domain, a customer service ticket in another, and a technical HTTP request in a software boundary.

The word is not wrong in each case. The surrounding Domain, contract, state and rules explain which meaning is intended. When designing a capability, do not assume that a familiar word means the same thing everywhere.

### Role is polysemous

**Role** can mean different things at different layers:

- a **real-world business role** describes what a person or organisation does in a business or service, such as applicant, assessor, approver or finance officer;
- an **access-context role** describes the position or context in which someone is acting for a particular resource, workspace, organisation or situation;
- a **system authorisation role** is a configured permission grouping used by software to allow or deny operations; and
- an **implementation role** describes what a component does in the software, such as Coordinator, Presenter, Player or Broker.

These roles may be related, but they are not interchangeable. A person acting as an assessor in the real world does not automatically have every system permission called `Assessor`. A user may hold a system role in one context and not another. A software component's implementation role is not a human business role.

### System is polysemous

**System** can mean different layers of a wider arrangement. There are two useful views, and they should not be confused.

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

## Contract

A shared agreement about what a boundary provides, what it needs and what callers may rely upon. A contract can be implemented by an object or service and can be used for mapping, schema, validation, discovery or policy.

## Coordinator

A component that manages movement between surfaces or steps. It sequences, transitions and gates a journey. It should coordinate the journey without absorbing every business rule.

See [Palette Technical Terms](./PALETTE-TECHNICAL-TERMS.md).

## Design completeness

The intended structure is known: boundaries, contracts, lifecycle, security, persistence intention, mappings, relationships and deferrals are described. This does not mean every implementation has been built.

## Deferred capability

A capability that is not being built now but has a known place, responsible boundary, contract direction, dependencies, lifecycle and condition for future construction.

## Event

A statement that something happened. The producer owns the fact. A consumer may respond, retry its own handling or explicitly emit another event. An event is not automatically a command.

## Flow

A repeated journey that coordinates capabilities, actions, decisions or state changes into an outcome. A flow gives the journey a recognisable shape. It is not a replacement for the capabilities beneath it.

See [Common Flows](./FLOWS.md).

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

See [Human Guidance](./README.md).

## Lifecycle responsibility

The responsibility for keeping a capability coherent as it is created, changed, operated and eventually retired. The first explanation should use “responsible boundary” rather than assuming that Owner or Steward is understood.

See [Responsible Boundaries and Deferred Design](./STEWARDSHIP-AND-DEFERRED-DESIGN.md).

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

See [Vertical Slices](../conventions/slices.md).

## Stewardship

The technical term for lifecycle responsibility. It means keeping a capability coherent across its contract, state, security, dependencies, tests, operation and change. Use the plain phrase first when writing for a wide audience.

## State

The current lifecycle position of a capability, such as draft, submitted, under assessment, approved, published, suspended or closed.

## State Change

A deliberate move from one state to another. Submission, approval, publication, suspension and closure usually need explicit rules rather than being hidden inside a general field update.

## View

The experience a person recognises, such as a page, form, list, tree, workspace, report or sequence. A View is not necessarily the boundary that owns every behaviour visible within it.

See [The Palette: First Look](./PALETTE-FIRST-LOOK.md).

## WGF: What Goes First?

A planning reminder that asks what happens if a part is included, deferred or omitted, and which designed structure must remain so later construction can continue without guessing.

See [YAGNI versus WGF](../HUMAN-YAGNI-VERSUS-WGF.md).
