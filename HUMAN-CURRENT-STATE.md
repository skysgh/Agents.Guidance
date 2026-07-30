# The Current State: How Enterprise Systems Drift

This paper describes common development conditions that the guidance is intended to improve. It is not an accusation against developers, testers, business analysts or delivery leaders. Most of these problems come from reasonable people working under pressure, using the nearest visible pattern and trying to make progress with incomplete shared design.

The problem is systemic: the organisation asks people to build large structures while leaving too much of the formwork implicit.

## The visible feature takes over

A ticket usually describes a business outcome or a screen. That is useful, but it is not a complete engineering design.

When the visible ticket is treated as the whole design, the team may build:

- a controller shaped around the screen;
- a service shaped around the controller action;
- a persistence model shaped around the service's first query; and
- a database schema shaped around today's fields.

The result may satisfy the ticket while silently deciding ownership, security, lifecycle, mapping and future query behaviour without discussing them. Those decisions then become difficult to change because they are spread across code rather than named as contracts.

A business description tells us what someone wants to achieve. It does not, by itself, tell us the logical objects, the boundary contracts, the storage model, the access rules or the operational lifecycle needed to achieve it safely.

## Common drift patterns

### Thick controllers

A controller begins with transport handling and gradually acquires validation, permission decisions, query construction, mapping, state transitions, persistence calls and notification behaviour. The code is easy to start because everything is nearby. It becomes hard to test, reuse, secure and change because one boundary has become responsible for many others.

The remedy is not to create more classes mechanically. The remedy is to name the contracts and ownership: transport invokes application capability; application logic composes use cases; repositories govern persistence access; domain rules own meaningful state decisions; mappings protect model boundaries.

### The ticket becomes the persisted object

A screen or ticket describes a conceptual shape, and that shape is implemented directly as the database entity. There is no deliberate step through a logical model, no brokering boundary and no discussion of which parts are presentation convenience versus durable domain meaning.

This makes storage constraints decide the conceptual model too early. It also makes a later screen, report or integration negotiate with the first screen's schema instead of using a reusable capability.

Document models and aggregate-oriented stores can make this drift feel natural because the application object is serialised as one document. That convenience does not remove the need to distinguish external representation, logical meaning and physical storage. It can hide the distinction until change becomes expensive.

Event sourcing can amplify the problem when events are treated as accidental serialisations of an early conceptual model. Keeping every historical representation forever does not, by itself, create a sound domain model. Event shape, semantic meaning, versioning, migration and projection responsibilities must be designed deliberately. This is a specialised consequence, not a prerequisite for using the guidance.

### Objects are created before contracts

A developer creates a model, then writes services directly against its concrete methods and properties. No capability contract states what consumers may rely on. Other services then depend on the model's accidental shape.

The consequences cascade:

- the model gains methods for unrelated consumers;
- application services become coupled to persistence details;
- mappings become inconsistent or disappear;
- schema changes produce many small failures;
- tests need concrete infrastructure when a contract would have sufficed; and
- replacement or discovery becomes difficult because there is no stable capability to discover.

The point of a contract is not to add ceremony before useful work. It is to make the intended responsibility visible before implementation details spread.

### Framework dependency becomes invisible architecture

A framework is a dependency even when it is supplied by the platform. ORM behaviour, web conventions, configuration providers, identity libraries, serialisers, UI frameworks and messaging libraries all carry assumptions about lifecycle, querying, security, performance and failure.

When those assumptions leak through every layer, replacing or governing the dependency becomes difficult. The code may appear simple while the real architecture is controlled by framework defaults nobody has named.

The answer is not to hide every framework type. It is to isolate the framework where its semantics belong, expose application-owned contracts where policy matters and document deliberate leaks where isolation would add more cost than value.

### YAGNI removes structure instead of features

YAGNI is useful against speculative features and unjustified infrastructure. It becomes harmful when it is used to remove a known contract, relationship, lifecycle state or extension point because the first release does not use it.

A deferred capability should have a known place, owner and intended boundary. Otherwise each later team must guess whether the missing structure was forgotten, rejected, postponed or owned elsewhere.

Physical deletion is especially risky in relational systems. Removing a field or relationship can affect historical meaning, migrations, referential integrity, reports and future composition. Deletion may be correct, but it is an architectural decision that needs evidence, not merely tidying.

### Startup becomes a list of host calls

Services, mappings, schema participants, settings, cache providers and module initialisers are registered through scattered calls. The system works while the original author remembers the unwritten order. Later, a participant is omitted, registered twice, invoked too early or never diagnosed.

Reflection is not a cure by itself. The underlying problem is missing contract organisation. Once participants have clear contracts, scope, lifecycle, ordering and diagnostics, discovery can reduce repetitive wiring and make the composition model more visible.

### Queryability is rejected because exposure is unsafe

Some teams reject `IQueryable` because exposing persistence entities would be unsafe. That correctly identifies a bad implementation, but rejects a valuable capability along with it.

A governed queryable read can let consumers shape filtering, projection, ordering and paging without requiring a new endpoint for every future need. The safe boundary is an authorised, mapped and bounded query surface. The answer to unsafe exposure is policy and mapping, not the removal of composable reads.

## Why these patterns persist

These patterns are reinforced by normal pressures:

- delivery measures visible features more readily than preserved structure;
- tickets often describe outcomes without enough logical design;
- developers are asked to code before ownership and contracts are agreed;
- framework defaults provide an attractive path of least resistance;
- tests may cover the happy path without testing boundary ownership;
- architecture documents may be too abstract, too long or too disconnected from code; and
- deferred work is recorded as a vague backlog item rather than a designed future capability.

No role is solely responsible. Business analysis, architecture, development, testing, delivery and operations each see only part of the structure unless the organisation provides a shared model.

## The cost of drift

Drift does not always produce an immediate outage. More often it produces a long series of small costs:

- repeated endpoint and mapping work;
- inconsistent security decisions;
- schema changes that break unrelated features;
- fragile migrations and difficult historical reporting;
- hidden startup dependencies;
- tests that require too much infrastructure;
- cache and configuration behaviour that differs between modules;
- integrations coupled to internal models; and
- new teams spending weeks reconstructing why the system is shaped as it is.

The individual error may be small. The accumulated structure becomes the problem.

## The corrective question

Before adding a class, endpoint or table, ask:

> What known structure is this work meant to occupy, and which contract tells the next person how to extend it?

That question does not prevent delivery. It prevents delivery from becoming a sequence of unrelated local interpretations.

## Related guidance

- [Human Start Here](./HUMAN-START-HERE.md)
- [What the guidance gives each stakeholder](./HUMAN-WHAT-GUIDANCE-GIVES.md)
- [Developers Need to Know](./conventions/developers-need-to-know.md)
- [Design the knowable; discover the novel](./conventions/principles.md)
- [IQueryable and Governed Queryability](./conventions/iqueryable.md)
