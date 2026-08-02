# Logical and Physical Models in ORM

Logical and physical models are often close in shape. That is not automatically a problem. An ORM can make it convenient to express a logical object with a class and map it to a relational record, while adding physical keys, relationships, indexes, concurrency markers and provider-specific configuration underneath.

The important question is not whether the classes and records look similar. It is whether the physical model is allowed to redefine the meaning, lifecycle, security or rules of the logical model without a deliberate decision.

## Visible physical artefacts

Some database facts are also meaningful to the logical model. An identity that the application uses to distinguish a concept may need a visible logical property. A relationship that the application reasons about may need a logical association. Other facts exist only to make storage work: a surrogate key, a join-table key, an index, a concurrency token, a provider discriminator or a foreign-key value that is not itself part of the domain meaning.

When a physical artefact has no logical use, exposing it in the logical model makes the lower layer's concerns visible to developers and can encourage accidental coupling. It may also make a storage migration look like a domain change.

## Shadow and mapped properties

ORMs such as Entity Framework Core can keep some persistence-only properties in the model used by the ORM without adding them to the application-facing class. These shadow properties can be useful for foreign keys, audit metadata, concurrency markers or other storage concerns that the logical layer does not need to manipulate directly.

Shadow properties are not a rule to hide every key or relationship. Use a visible logical property when the identity or relationship is part of the behaviour, contract, authorisation, lifecycle or meaningful state of the domain. Use a persistence-only property when it exists to support storage and the logical model can remain correct without knowing it.

The physical layer still owns configuration, migrations, indexes, constraints and provider behaviour. Keeping a property out of the logical class does not remove the physical obligation; it keeps that obligation in the layer that understands it.

## Enduring identity and transient relationships

Use the [Enduring](../reference/glossary.md#enduring) versus [Transient](../reference/glossary.md#transient) distinction before deciding whether a physical property belongs on an entity record. An enduring identity such as Person, Group or School should not acquire a current membership, appointment or assignment as though that arrangement were its identity. A relationship such as `StudentAt` may require its own record or aggregate when it has effective dates, state, authority, history, reporting, classification or recovery consequences.

For example, a nullable `SchoolId` on Person may represent the current view, but it cannot by itself preserve a person's historical memberships, overlapping rules, withdrawal reason or as-at-date query. Map the logical relationship deliberately into tables, documents, events or projections, and keep the contract that defines the relationship separate from the physical representation. See [Entity Lifecycle Patterns](../reference/catalogues/entity-lifecycle-patterns.md).

## When models resemble each other

A simple capability may legitimately have a logical model and a persistence model that are nearly identical. Explicit mapping can still be valuable because it records the relationship and leaves room for the models to diverge when the service grows. A one-to-one shape is not proof of a collapsed architecture, just as a different shape is not proof of good separation.

The warning signs are stronger: a table name becomes the business vocabulary, a migration changes a rule without a logical decision, a provider type appears in a domain contract, a screen field dictates persistence state or developers cannot test the logical behaviour without constructing an ORM context.

## Building blocks and classes

Logical building blocks are responsibilities. Classes are one physical way to implement them. A repository, service, registry or mapping building block may be represented by one class, several classes or a framework composition. Conversely, one class may accidentally combine several building blocks because the framework makes the first implementation convenient.

The developer's job is to keep the physical implementation faithful to the logical responsibility and to expose mappings where the representations differ. The tech lead's job is to identify whether the logical building blocks and layer boundaries remain coherent. The architect's job is to have set enough boundary and meaning for those decisions to be made without rediscovering the whole system from ORM types.

Read [Logical Layers](../reference/catalogues/logical-layers.md), [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md), [Contracts](./contracts.md) and [LDM Layers and Contents](./layers.md) together when deciding whether a physical property or type belongs in the logical model.
