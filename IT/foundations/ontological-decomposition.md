[Up](./readme.md)

# Ontological Decomposition


Ontological decomposition is the deliberate work of recognising what kinds of things exist in a problem space, what makes them the same or different, how they relate, which states and events matter, which rules constrain them and which responsibilities belong together.

It is a north-star abstraction for engineering. It helps a team avoid treating a screen, table, endpoint, organisation chart or current process as the whole truth. It does not require a universal vocabulary, a single database shape or a final model that every person must read directly.

## What is being decomposed

A team begins with stakeholder language, observations, obligations, examples and existing evidence. It asks questions such as:

- What enduring things or identities must remain recognisable as their information changes?
- What transient relationships, memberships, assignments, decisions or interactions connect them?
- Which attributes are values, and which deserve identity, history or authority of their own?
- What states, events, rules, permissions, obligations and evidence distinguish one situation from another?
- Which concepts belong together because they share meaning, lifecycle, authority and change?
- Which words are polysemous across Domains, and which apparent differences are only local wording?
- What must a consumer recognise, what must a logical model preserve and what must a physical representation store or execute?

The answers are hypotheses supported by evidence. They are not extracted mechanically from nouns in a requirements document.

## Ontological, logical and physical

**Ontological** concerns the kinds of things, relationships, distinctions, identities, states and rules that the system needs to recognise as meaningful. It is concerned with what is the same, what is different and what can happen.

**Logical** expresses those distinctions independently of one particular transport, vendor, framework or storage engine. A logical model may describe entities, value objects, relationships, state transitions, responsibilities, contracts and invariants.

**Physical** is the code, configuration, schema, message, view, infrastructure or other representation that executes or carries the design.

These are model types and semantic perspectives, not LDM layers. Every LDM layer is physicalised. A consumer-facing DTO or view model is physical code shaped close to business or stakeholder language. Application and domain entities are physical code shaped closer to ontological and logical distinctions. Persistence models are physical code shaped for logical meaning plus storage requirements such as primary keys, foreign keys, indexes, concurrency and provider constraints. Mappings keep the differences visible.

## Primitives are a north star, not a universal list

An ontological primitive is a basic distinction used to build or explain a model in a particular context. Examples may include identity, thing, person, organisation, place, time, relationship, state, event, action, rule, authority, value, information and evidence. The useful set depends on the problem, the purpose of the model and the distinctions that must survive change.

Natural Semantic Metalanguage and its commonly discussed inventory of 65 semantic primes are relevant background for thinking about irreducible real-world meaning. They are not an engineering requirement and they are not a universal target for reducing every domain model. Engineering models need enough distinctions to preserve obligations, behaviour, lifecycle, security, evidence and change, not merely a small list of words.

The north star is therefore directional: move toward stable distinctions that explain more cases and survive more kinds of change. Do not pretend that the direction ends in one fixed list or that greater abstraction is always better.

## The abstraction trade-off

A model closer to stable ontological distinctions can absorb more changes in screens, processes, vendors, teams and storage. It can also become harder for a person to understand if it is presented without the consumer language and examples that gave it meaning.

A model closer to a current consumer is often easier to recognise and use immediately. It can also preserve accidental details of one screen, organisation or workflow and make future change expensive.

The engineering decision is to preserve the durable meaning at the logical boundary while providing physical representations that are understandable to their consumers. A good design may therefore contain several mapped models rather than one supposedly pure model:

```text
stakeholder concepts and language
  -> conceptual recognition
  -> logical ontological distinctions
  -> physical application/domain representations
  -> physical consumer, integration and persistence representations
```

The arrows are translations and evidence-bearing boundaries. They are not a claim that one layer is conceptual, another logical and another physical.

## A worked example

Suppose stakeholders speak about a student attending a school. A first screen may show a `Student` DTO with a school name. That is useful consumer language, but it may hide several distinctions:

- `Person` identifies the enduring person;
- `School` or `Organisation` identifies the enduring institution;
- `StudentAt` represents the relationship that says the person held student status at that institution during a period;
- the relationship may have state, authority, effective dates, evidence and a reason for ending; and
- a persistence model may add keys, indexes, uniqueness, concurrency and retention rules needed to store and query that history.

The interface model can remain recognisable as ÔÇ£student at school.ÔÇØ The application and domain model can preserve the relationship and its lifecycle. The persistence model can add the storage constraints. None of these is the whole ontology, and none should silently redefine it.

## Choosing the stopping point

Decomposition should stop when the model is clear enough for the decision and change risk in front of the team. Ask:

- Can the responsible people explain the concept, boundary, lifecycle and authority?
- Can the design distinguish the cases that have different rules, consequences or evidence?
- Can the physical representations serve their consumers without redefining the logical meaning?
- Can the team test, operate, migrate, secure and retire the result?
- Would another split clarify a real responsibility, or merely create indirection and vocabulary cost?
- Is an unresolved question recorded with an owner, evidence needed, trigger and review condition?

Under-decomposition hides important identity, lifecycle, policy or authority. Over-decomposition creates fragments that no person can understand or no boundary can own. The right level is a decision, not a universal endpoint.

## Common failure modes

- **Screen-first modelling:** treating a DTO or view model as the domain truth because it is visible.
- **Table-first modelling:** treating columns, keys or ORM classes as the logical meaning without examining lifecycle and responsibility.
- **Layer-as-model confusion:** describing interface, application/domain and persistence positions as conceptual, logical and physical model types.
- **Under-decomposition:** storing a relationship, event or decision as attributes on an enduring entity and losing its history or authority.
- **Over-decomposition:** splitting every word into an object without a distinct rule, lifecycle, owner or evidence need.
- **False universalism:** treating one organisation's names, one framework's patterns or one fixed primitive list as the truth for every Domain.
- **Consumer erasure:** making the logical model so abstract that people cannot recognise how their work, outcome or obligation is represented.

## Relationship to other guidance

Ontological decomposition supports [Conceptual, Logical and Physical Models](../shared/reference/catalogues/conceptual-logical-physical-models.md), [LDM Layers and Contents](../development/layers.md), [Entity Lifecycle Patterns](../shared/reference/catalogues/entity-lifecycle-patterns.md), [Domains and Capabilities](../shared/reference/catalogues/domains-and-capabilities.md), [Contracts](../development/contracts.md) and [Domain-Driven Design](../shared/reference/glossary.md#domain-driven-design-ddd).

It does not replace elicitation, domain authority, architecture, contracts, testing or operational evidence. It gives those responsibilities a clearer object of discussion: the distinctions the system must preserve, the representations it may choose and the evidence that would show the choice remains sound.
