# LDM Layers and Contents

An LDM contains more than services. It contains logical layers that give different responsibilities a safe place to live. The layers are architectural responsibilities first and projects or folders second. They are not necessarily separate deployments, projects or folders.

A useful implementation shape is:

```text
consumer-facing interface implementation
        |
        v
application and domain implementation
        |
        v
persistence and external effects implementation
```

A shared or substrate area supplies narrow vocabulary and structural contracts used by the LDM. It must not become a fourth business layer or a dumping ground for types that have no clear responsibility.

These are implementation responsibilities, not three model types. A consumer-facing interface is physical code that carries conceptual language. Application and domain code is physical code that implements logical ontological distinctions. Persistence and external effects are physical representations and behaviours needed for execution. The [Conceptual, Logical and Physical Models](../reference/catalogues/conceptual-logical-physical-models.md) catalogue explains the model types separately.

## The layers

### Shared vocabulary and contracts

This area contains stable LDM vocabulary, constants and contracts that must be known by more than one layer. It should remain narrow. It may identify the LDM, compose route or permission names and define contracts for discovery or boundary use.

A shared contract is not automatically a domain model. Keep business meaning in the domain layer when that is where the responsibility belongs.

### Consumer-facing interface layer

The consumer-facing interface layer adapts an external consumer to an application contract. It physically represents the language and interaction the consumer recognises and owns transport, protocol and presentation concerns such as HTTP metadata, request shapes, response shapes and boundary validation.

It should not own logical domain rules, physical persistence access or substantial application orchestration. A screen or endpoint is a consumer of a capability, not the source of its meaning.

### Application and domain layer

The application and domain layer physically implements and coordinates the logical model. It composes contracts, validates the application request, establishes the relevant actor and context, invokes domain behaviour, calls repositories or brokers through contracts and maps the result for the consumer.

It may contain application coordination, domain concepts, commands, queries, requests, responses, results, projections and application view models where those shapes serve a use case. It should not force the logical model to mirror one client, screen or organisational process.

### Persistence and external implementation layer

The persistence and external implementation layer implements contracts against frameworks, providers, storage, external systems and runtime mechanisms. It contains adapters, brokers, provider-specific services, registrations and operational integration.

This layer is allowed to know the framework or provider. Inner logical contracts should not reach outward to call those implementations directly.

### Physical storage

Physical storage contains physical records, ORM configuration, schema contribution, migrations and storage mappings. A persistence record may resemble a logical entity, but it remains physical until an explicit mapping shows otherwise.

Physical storage must not make a table, ORM entity or provider document the definition of the business concept.

## What lives inside a layer

Layers commonly contain these code-purpose categories:

- **Constants:** immutable shared meaning, not runtime settings or persisted reference data.
- **Contracts:** behavioural or structural agreements used by a real consumer, policy, schema, mapper, discovery rule or generic constraint.
- **Models:** entities, value objects, aggregates, DTOs, requests, responses, commands, queries, results, events, messages, options, projections and physical records according to responsibility.
- **Services:** cohesive stateless behaviour or application orchestration.
- **Registries:** stateful registration, lookup and lifecycle of participants or definitions.
- **Repositories:** persistence access expressed in domain or application terms.
- **Brokers:** communication with external systems or infrastructure mechanisms.
- **Maps and mappers:** declarative or procedural translation between representations.
- **Validators:** validation of input or state, without replacing domain invariants.
- **Handlers:** one defined command, query, event, message or request responsibility.
- **Controllers or endpoint handlers:** thin boundary adapters in the interface layer.

These categories are not a licence to create one class of every kind. Create a category when a responsibility exists and the boundary benefits from naming it.

## Contracts before implementations

A contract should be visible before its implementation when another part of the system needs to rely on it. Consumers depend on the contract. Composition, framework integration, persistence, serialisation and relevant tests may refer to the implementation.

The [Contracts](./contracts.md) paper explains how to decide whether an agreement is meaningful rather than creating empty interfaces beside every class.

## The dependency direction

The consumer-facing interface may depend on application and domain contracts. The logical model must not depend on transport, physical storage, infrastructure, vendors or frameworks. Physical and external implementations implement ports defined by the application and domain responsibilities.

A vertical slice travels through these layers, but responsibility does not move with the request. The business capability remains the responsibility of its domain and LDM while each layer contributes the work it was designed to carry.

## Related guidance

- [Human Development Guidance](./readme.md)
- [Logical Deployment Modules](./ldms.md)
- [Constants](./constants.md)
- [Contracts](./contracts.md)
- [System LDM Services](./services.md)
- [Logical Layers](../reference/catalogues/logical-layers.md)
- [Logical Building Blocks](../reference/catalogues/logical-building-blocks.md)
- [Logical and Physical Models in ORM](./logical-and-physical-models.md)
- [Guidance for Developers](../orientation/guidance-for-developers.md)
- [Code Conventions](../../agents/conventions/development/code-csharp.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
