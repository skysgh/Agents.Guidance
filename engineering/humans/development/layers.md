# LDM Layers and Contents

An LDM contains more than services. It contains layers that give different responsibilities a safe place to live. The layers are architectural responsibilities first and projects or folders second.

A useful shape is:

```text
consumer interface
        |
        v
application layer
        |
        v
logical domain layer
        ^
        |
infrastructure and persistence implementations
```

A shared or substrate area supplies narrow vocabulary and structural contracts used by the LDM. It must not become a fourth business layer or a dumping ground for types that have no clear owner.

## The layers

### Shared vocabulary and contracts

This area contains stable LDM vocabulary, constants and contracts that must be known by more than one layer. It should remain narrow. It may identify the LDM, compose route or permission names and define contracts for discovery or boundary use.

A shared contract is not automatically a domain model. Keep business meaning in the domain layer when that is where the responsibility belongs.

### Interface layer

The interface layer adapts an external consumer to an application contract. It owns transport, protocol and presentation concerns such as HTTP metadata, request shapes, response shapes and boundary validation.

It should not own domain rules, persistence access or substantial application orchestration. A screen or endpoint is a consumer of a capability, not the owner of its meaning.

### Application layer

The application layer coordinates a use case. It composes contracts, validates the application request, establishes the relevant actor and context, invokes domain behaviour, calls repositories or brokers through contracts and maps the result for the consumer.

It may contain commands, queries, requests, responses, results, projections and application view models where those shapes serve a use case. It should not force the domain model to mirror one client, screen or organisational process.

### Domain layer

The domain layer contains the logical ontological model of the relevant business or technical problem. It includes concepts, identities, relationships, states, policies and rules that remain meaningful when transport, storage, vendor or current team structure changes.

Entities, value objects, aggregates and domain services belong here when they express the domain's meaning. A repository contract may also be owned here when the application needs persistence in domain terms.

### Infrastructure layer

Infrastructure implements contracts against frameworks, providers, storage, external systems and runtime mechanisms. It contains adapters, brokers, provider-specific services, registrations and operational integration.

Infrastructure is allowed to know the framework or provider. Inner domain and application contracts should not reach outward to call those implementations directly.

### Persistence layer

Persistence infrastructure owns physical records, ORM configuration, schema contribution, migrations and storage mappings. A persistence record may resemble a domain entity, but it remains physical until an explicit mapping shows otherwise.

The persistence layer must not make a table, ORM entity or provider document the definition of the business concept.

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

The outer layers may depend on inner contracts. The domain must not depend on transport, persistence, infrastructure, vendors or frameworks. Infrastructure and persistence implement ports owned by inner layers.

A vertical slice travels through these layers, but ownership does not move with the request. The business capability remains owned by its domain and LDM while each layer contributes the responsibility it was designed to carry.

## Related guidance

- [Human Development Guidance](./readme.md)
- [Logical Deployment Modules](./ldms.md)
- [Constants](./constants.md)
- [Contracts](./contracts.md)
- [System LDM Services](./services.md)
- [What Developers Need to Know](../orientation/developers-need-to-know.md)
- [Code Conventions](../../agents/conventions/development/code-csharp.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
