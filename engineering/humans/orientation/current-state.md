# The Current State: How Enterprise Systems Drift

## Purpose

This paper helps people recognise common ways that a large system becomes harder to change. It is for business analysts, developers, testers, operations staff, security roles, delivery leads and architects. You do not need to know the technical terms before reading it.

## The short version

People usually do not create difficult systems through one careless decision. They make a series of locally reasonable decisions without a shared picture of how the parts should fit together. A screen becomes a data model. A model becomes a service interface. A framework default becomes an unstated rule. A missing boundary is repaired in several different places. Over time, the system becomes difficult to explain and expensive to change.

The guidance provides the shared picture. It asks the team to design the known structure before implementation spreads different assumptions, while allowing the new business concepts and user experiences to develop within that structure.

This paper describes common development conditions that the guidance is intended to improve. It is not an accusation against developers, testers, business analysts or delivery leaders. Most of these problems come from reasonable people working under pressure, using the nearest visible pattern and trying to make progress with incomplete shared design.

The problem is systemic: the organisation asks people to build large structures while leaving too much of the formwork implicit.

## The visible feature takes over

A ticket usually describes a business outcome or a screen. That is useful, but it is not a complete engineering design.

When the visible ticket is treated as the whole design, the screen can shape the controller, the controller action can shape the service, the service's first query can shape the persistence model and today's fields can harden into the database schema. Each step feels close to the work in front of the team, but the accumulated shape quietly decides responsibility, security, lifecycle, mapping and future query behaviour without discussing them.

The result may satisfy the ticket while silently deciding responsibility, security, lifecycle, mapping and future query behaviour without discussing them. Those decisions then become difficult to change because they are spread across code rather than named as contracts.

A business description tells us what someone wants to achieve. It does not, by itself, tell us the logical objects, the boundary contracts, the storage model, the access rules or the operational lifecycle needed to achieve it safely. The business analyst is not at fault when implementation invents the wrong logical object; the team is responsible for carrying the conceptual request into a deliberate logical design. [What the Guidance Gives Each Stakeholder](./what-this-guidance-gives.md) explains how business analysts, developers and testers can protect that distinction together.

## Common drift patterns

### Controllers that carry too many jobs

A controller begins with receiving a request and returning a response. It gradually acquires validation, permission decisions, query construction, mapping, state transitions, persistence calls and notification behaviour. The code is easy to start because everything is nearby. It becomes hard to test, reuse, secure and change because one boundary has taken on many jobs.

In technical language, this is often called a thick controller. The name is less important than the idea: each part should have a clear job so that the parts can change independently.

The remedy is not to create more classes mechanically. The remedy is to name the contracts and responsibilities: transport invokes application capability; application logic composes use cases; repositories govern persistence access; domain rules make meaningful state decisions; mappings protect model boundaries.

### The ticket becomes the stored object

A screen or ticket describes a shape, and that shape is implemented directly as the database entity. There is no deliberate step between what the user sees, what the service means and what the database stores. There is no boundary that lets each part evolve independently.

In technical language, that missing separation is often described as a missing brokering layer. The concept is more important than the term: storage should not silently decide the meaning of the business concept. A tester may notice the smell when test cases, fixtures and assertions can only describe the behaviour through table names or persistence entities. That does not prove the design is wrong, but it is a useful reason to ask whether the logical capability has been defined independently of its physical storage.

This makes storage constraints decide the conceptual model too early. It also makes a later screen, report or integration negotiate with the first screen's schema instead of using a reusable capability.

Document models and aggregate-oriented stores can make this drift feel natural because the application object is serialised as one document. That convenience does not remove the need to distinguish external representation, logical meaning and physical storage. It can hide the distinction until change becomes expensive.

Event sourcing can amplify the problem when events are treated as accidental serialisations of an early conceptual model. Keeping every historical representation forever does not, by itself, create a sound domain model. Event shape, semantic meaning, versioning, migration and projection responsibilities must be designed deliberately. This is a specialised consequence, not a prerequisite for using the guidance.

### Objects are created before shared agreements

A developer creates a model, then writes services directly against its concrete methods and properties. No shared agreement states what consumers may rely on. Other services then depend on the model's accidental shape.

In technical language, the shared agreement is a [contract](../development/contracts.md). The contract is not a ceremony added beside the model. It is the part that tells different contributors what may safely be relied upon.

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

YAGNI is useful against speculative features and unjustified infrastructure. It becomes harmful when it is used to remove a known contract, relationship, lifecycle state or extension point because the first release does not use it. [YAGNI versus WGF](./design-before-build-and-wgf.md) explains how to defer construction without losing the structure needed for a later change.

A deferred capability should have a known place, responsible boundary and intended contract. Otherwise each later team must guess whether the missing structure was forgotten, rejected, postponed or assigned elsewhere.

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
- developers are asked to code before responsibilities and contracts are agreed;
- framework defaults provide an attractive path of least resistance;
- tests may cover the happy path without testing boundary responsibilities;
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

- [The Structure Before the Feature](./the-structure-before-the-feature.md)
- [What the guidance gives each stakeholder](./what-this-guidance-gives.md)
- [Systems Within Systems](./systems-within-systems.md)
- [Developer Architecture Route](../../agents/conventions/development/guidance-for-developers.md)
- [Design the knowable; discover the novel](../../agents/conventions/foundations/principles.md)
- [IQueryable and Governed Queryability](../../agents/conventions/foundations/iqueryable.md)
