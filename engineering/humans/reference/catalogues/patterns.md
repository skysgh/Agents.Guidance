# Patterns Catalogue

A pattern is a named response to a problem that appears repeatedly in a particular context. The name helps people recognise a useful structure and discuss its consequences. A pattern is not a command to use a particular class shape, framework or project layout. It is a starting point for reasoning.

Patterns are useful when a problem has enough repetition that the team benefits from a shared language. They are harmful when the name replaces understanding. Before applying one, understand the responsibility, the forces acting on it and the cost the pattern introduces. A pattern should reduce confusion, coupling or repeated design effort; it should not add ceremony merely because it is familiar.

The patterns in this catalogue are related. Separation of concerns, high cohesion and low coupling are broad structural principles. OOP, GRASP and SOLID help preserve those principles in object-oriented code. GoF patterns name recurring object collaborations. DDD patterns help the team model a problem domain. Architectural patterns describe larger arrangements of boundaries and dependencies. The same word can therefore appear at different levels and should be read in its context.

## Structural principles

Separation of concerns keeps responsibilities that change for different reasons from becoming one tangled decision. High cohesion keeps responsibilities that belong together close enough to understand and change together. Low coupling keeps relationships between separate responsibilities small, explicit and replaceable.

These principles apply to stakeholder sites, flows, views, components, domains, capabilities, LDMs, logical layers and code. They are the first pattern language to use because they help decide whether a more specific pattern is needed at all.

## Object-oriented programming

Object-oriented programming organises behaviour and state around objects that have responsibilities and relationships. Encapsulation protects the state and rules that must change together. Abstraction exposes what a consumer needs without requiring it to know physical detail. Polymorphism allows a consumer to rely on a contract while different implementations provide the behaviour. Composition builds a responsibility from collaborating objects rather than forcing inheritance to represent every variation.

OOP is a code and design approach. It does not decide which stakeholder needs a site, which domain gives a capability its meaning or which LDM contains a component. Those larger decisions should already be understood before OOP is used to express them.

## GRASP

GRASP, or General Responsibility Assignment Software Patterns, helps a developer decide where an object responsibility should go and how objects should collaborate. Information Expert gives a responsibility to the object with the information needed to fulfil it. Creator gives creation responsibility to a type with a strong relationship to the thing being created. Controller gives an entry-point object responsibility for receiving a system operation and coordinating the appropriate application work.

Low Coupling and High Cohesion in GRASP are the same structural concerns used throughout this guidance. Polymorphism places variation behind a common contract. Pure Fabrication introduces a focused technical object when a responsibility does not belong naturally to a domain object. Indirection places an intermediate object between responsibilities that should not depend directly on each other. Protected Variations puts a stable boundary around a point likely to change.

GRASP is most useful when a class or component is becoming difficult to understand. It helps answer which object should carry a behaviour, which object should coordinate it and where a variation should be isolated. It does not replace domain evidence or the larger boundary decisions made by an architect or tech lead.

## SOLID

SOLID is a group of object and component design principles. The Single Responsibility Principle keeps a class or component focused on one coherent reason to change. The Open-Closed Principle encourages extension through stable contracts rather than repeated modification of unrelated callers. The Liskov Substitution Principle requires an implementation to honour the expectations of the contract it replaces. The Interface Segregation Principle keeps consumers from depending on methods they do not need. The Dependency Inversion Principle keeps high-level policy dependent on stable abstractions rather than physical details.

SOLID is not a demand for an interface beside every class or an abstraction for every possible future. Applied without judgement, it creates indirection and makes simple code harder to follow. Applied to a real boundary, it helps prevent a view, provider adapter, domain rule and persistence mechanism from becoming one inseparable component.

## GoF patterns

The Gang of Four patterns catalogue recurring object collaborations. Creational patterns such as Factory Method, Abstract Factory, Builder and Prototype address how objects are created when construction has meaningful variation or complexity. Structural patterns such as Adapter, Decorator, Facade, Composite, Proxy and Bridge address how objects or boundaries are composed without exposing every detail to their consumers. Behavioural patterns such as Strategy, Command, Observer, State, Template Method, Mediator, Chain of Responsibility and Iterator address how behaviour, variation, notification or sequencing is organised.

A pattern name should describe a problem the code actually has. An Adapter is useful when one contract must be translated to another. A Decorator is useful when behaviour can be added around a stable contract. A Strategy is useful when an algorithm varies behind a common policy. A Facade is useful when a consumer needs a simpler boundary over a complex subsystem. Creating these shapes before the variation or boundary exists adds ceremony rather than clarity.

## Domain-Driven Design

Domain-Driven Design, or DDD, gives a team a way to keep software close to the important meanings, rules and decisions of a problem domain. Ubiquitous language records the terms used by the people who understand the domain and by the software that represents it. A bounded context protects one consistent meaning when the same word has different meanings elsewhere.

Entities have identity that remains important as their information changes. Value Objects are defined by their values and the rules that make those values valid. Aggregates provide a consistency boundary for related domain objects and an aggregate root is the controlled entry point for changing that boundary. Repositories provide governed access to domain or persisted information. Domain Services express important rules that do not naturally belong to one entity, value object or aggregate. Domain Events record meaningful facts that have happened. Application Services coordinate a use case without replacing the domain rules.

DDD patterns support the logical model. They do not require a particular database, transport or deployment topology. A domain model is not a copy of a screen, table or vendor API. It is the logical account of the concepts, identities, relationships, states and rules that the service must understand.

## Enduring versus Transient

Enduring versus Transient is a logical modelling pattern for separating concepts that retain identity and responsibility across changing circumstances from bounded memberships, appointments, assignments, decisions, states or interactions involving them. It is especially useful when conceptual language makes a current relationship look like the identity of a person, organisation or other enduring concept.

For example, the phrase "a student at a school" may be decomposed into an enduring **Person**, an enduring **School**, **Group** or **Organisation**, a distinct **Location** where location has its own responsibility, and a transient **StudentAt** relationship. The relationship may need effective dates, status, authority, audit, history, overlap rules and as-at-date queries. It is not disposable merely because it is transient.

This pattern works alongside DDD. It provides lifecycle evidence for deciding whether a concept should be an Entity, Aggregate, value-bearing association, Domain Event, bounded context or vertical slice. It does not prescribe one class, table or schema. The logical distinction must survive whichever physical representation the service uses. See [Entity Lifecycle Patterns](./entity-lifecycle-patterns.md) for the full modelling questions and role consequences.

## Architectural patterns

Layered, onion and ports-and-adapters patterns protect dependency direction by keeping conceptual interfaces and physical infrastructure from redefining the logical model. Vertical slices organise a complete capability through the relevant boundaries so that it can be delivered and tested as a meaningful unit. A flow coordinates several capabilities into a journey while allowing each capability to retain its own rules and state.

Other patterns may be useful when the problem warrants them. CQRS separates command and query responsibilities when their models, scaling or consistency needs genuinely differ. Event-driven architecture uses events to communicate facts between decoupled participants. A modular monolith keeps logical packages separate while deploying them together. Microservices introduce independently deployable boundaries when the operational and organisational consequences justify that cost. None of these patterns repairs unclear business responsibility by itself.

## Finding the right level

Start with the smallest pattern language that makes the problem clearer. Use Separation of Concerns, High Cohesion and Low Coupling to test the boundary. Use DDD when the domain meaning and rules need protection. Use OOP, GRASP and SOLID to place and separate responsibilities in code. Use GoF patterns when a recurring object collaboration is present. Use architectural patterns when the relationship between larger boundaries needs a known shape.

The [Guidance Glossary](../glossary.md) provides short definitions for many of these terms. [Domains and Capabilities](./domains-and-capabilities.md), [Logical Deployment Modules](./ldms.md), [Logical Layers](./logical-layers.md), [Logical Building Blocks](./logical-building-blocks.md), [LDM Layers and Contents](../../development/layers.md), [Vertical Slices](../../development/vertical-slices.md) and [Contracts](../../development/contracts.md) show how the patterns fit this guidance. The [Domains and Capabilities Checklist](../checklists/domains-and-capabilities.md) helps review whether a pattern is serving a real responsibility rather than decorating the design.
