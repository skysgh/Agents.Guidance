# Logical Layers

Logical layers distinguish kinds of implementation responsibility within an LDM. They are architectural concepts before they are projects or folders. They help people keep the consumer-facing representation, the application and domain responsibilities and the physical mechanisms that execute them from becoming one accidental model. They are not the same thing as the Conceptual, Logical and Physical model types.

The three principal implementation areas are:

1. **Consumer-facing interface**: physical interface code that presents the language and interaction recognised by people or connected systems.
2. **Application and domain responsibility**: physical code that coordinates use cases and expresses or implements the logical model of things, identities, relationships, states, rules and transitions.
3. **Persistence and external effects**: physical code and resources that represent information through records, files, providers, transports, messages and runtime mechanisms.

A shared vocabulary and contracts area may support these layers. It is not a fourth business layer and must not become a dumping ground for types that have no clear responsibility.

## Consumer-facing interface

The consumer-facing interface is physical code that presents an interaction in the language a stakeholder or connected system understands. It may use familiar terms that are locally useful even when those terms are imprecise or have different meanings elsewhere. It carries a conceptual representation; it is not itself the whole conceptual model.

A screen, endpoint or integration contract belongs to this layer when its responsibility is to represent an interaction for a consumer. It should not become the authority for domain rules, persistence or substantial application orchestration merely because it is the first place a request appears.

## Application and domain responsibility

Application and domain code is the physical implementation of the logical model. It identifies the things, identities, relationships, states, rules and transitions that must be distinguished, then coordinates the use cases that change or read them. The logical model is the responsibility and meaning; classes, records and services are physical representations of it.

This layer may contain application coordination, domain concepts, commands, queries, requests, responses, results, projections, policies and logical models. It should express the service's meaning rather than mirror one screen, transport payload, database table or vendor API.

This implementation area may use many code types, but its responsibility is not defined by the programming language. Several classes may express one logical responsibility, and one class may be a warning sign when it mixes several responsibilities.

## Persistence and external effects

Persistence and external effects are physical representations and behaviours through databases, files, caches, indexes, queues, provider resources, transports, frameworks and runtime mechanisms. This area contains schemas, records, mappings, migrations, provider configuration, adapters and operational integration.

This area may know its provider and framework. Application and domain code should not reach outward to call those details directly. Contracts and mappings keep the dependency direction visible and allow the physical representation to change without silently changing the service meaning.

## Why the separation matters

Without a consumer-facing representation, the service may be logically sound but unintelligible to its consumers. Without a logical model, a screen or database structure can become the meaning by accident. Without physical implementation, the team may have a sound idea without deciding how to persist, recover, query, integrate or operate it.

The implementation areas are connected, not isolated. A consumer-facing contract maps to application and domain behaviour. Logical responsibilities map to persistence and external effects. The mapping is part of the design. It is not disposable plumbing. See [Conceptual, Logical and Physical Models](./conceptual-logical-physical-models.md) for the model-type distinction.

## Scale and handoff

The architect uses these implementation areas to show the major kinds of responsibility inside an LDM. The tech lead decides which logical building blocks are needed within them and how their contracts and dependencies are arranged. The developer chooses code types and patterns that express those responsibilities without collapsing the logical and physical models.

The same physical class may be close to a logical object when the responsibilities genuinely align. Similarity is not proof that the layers have collapsed. The test is whether the logical meaning can be explained and changed without being forced to follow a storage, transport or framework detail.

Read [Logical Deployment Modules](./ldms.md) for the package boundary, [Logical Building Blocks](./logical-building-blocks.md) for the implementation-design vocabulary and [Logical and Physical Models in ORM](../../development/logical-and-physical-models.md) for the closer relationship between logical and physical representations.

For implementation responsibilities, read [LDM Layers and Contents](../../development/layers.md). For review prompts, use the [LDM and logical layers checklist](../checklists/ldms-and-logical-layers.md).
