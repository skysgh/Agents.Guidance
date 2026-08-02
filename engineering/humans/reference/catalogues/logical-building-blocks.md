# Logical Building Blocks

A logical building block is a named unit of responsibility within an LDM and its layers. The term describes what a part must do before deciding whether the physical implementation is a class, record, module, function, provider binding or framework object.

Building blocks are scale-dependent. At architecture scale, components describe meaningful parts of a site, flow, view or LDM. At technical-lead scale, logical building blocks describe the kinds of responsibility needed inside those components and layers. At developer scale, code types and design patterns express those responsibilities in a language and framework.

The scale does not make the levels interchangeable. An architectural component is not automatically a UI class. A logical service is not automatically one physical class. A coding pattern is not a substitute for deciding which responsibility exists. Always name the responsibility and boundary alongside the building-block term.

## Service

A service is cohesive behaviour or application orchestration provided through a contract. An application service coordinates a use case across validation, authorisation, mapping, repositories and external capabilities. A domain service expresses an important domain rule that does not naturally belong to one entity, value object or aggregate.

A service is not automatically the owner of every rule in a journey and is not the same thing as an LDM, deployment or external provider.

## State-management coordinator

A state-management coordinator composes a use case, establishes context, invokes domain behaviour, calls contracts and maps the result for a consumer. It helps keep logical state transitions and application sequencing distinct from transport and physical storage.

It should not become a general-purpose service that absorbs unrelated rules. The name is useful when the responsibility is coordination of logical state; use application service or another more specific name when that is clearer.

## Repository

A repository provides governed access to domain or persisted information in terms useful to the application. It owns the persistence source and its query, visibility, classification and execution policies where the repository boundary is responsible for them.

A repository is not a general-purpose database shortcut, and it is not a domain merely because it reads a table. It should not expose provider detail or unrestricted persistence access to consumers.

## Broker and adapter

A broker or adapter crosses a boundary to an external system, provider or infrastructure mechanism. It translates between contracts and hides transport or vendor detail from the logical consumer.

It connects calls; it does not absorb the business rules owned by the capability it reaches. The exact term depends on whether the emphasis is communication, translation or compatibility.

## Provider

A provider supplies a physical or technical capability behind a contract, such as storage, caching, notifications, identity, mapping or messaging. Provider choice is a physical implementation decision unless the provider itself is an explicit architectural constraint.

A provider is not a policy. The logical boundary decides what may happen, what data may cross it and how failure is handled. The provider implements the allowed mechanism.

## Registry

A registry is a stateful place that registers, indexes, looks up and sometimes manages the lifecycle of participants or definitions. Examples include mapping, schema, cache, handler or startup registries.

A registry is not a general-purpose collection and should not become an ungoverned service locator. Its key, lifecycle, uniqueness, replacement and diagnostic rules should be explicit. For governance records that inform or constrain a project, read [Registries](./registries.md); it distinguishes enterprise-referred registries from project-produced registries.

## Mapping and projection

A mapping or projection translates one representation into another, such as a persistence record into a logical model or a logical result into a consumer response. It protects meaning, classification, security and future change at the boundary.

A mapper does not decide the business rule or the destination contract on its own. The consuming capability decides what shape is needed and what may cross the boundary.

## Validator and policy

A validator checks input, shape or state conditions at a defined boundary. A policy expresses a rule about what may happen, often using actor, resource, context or lifecycle information.

Validation does not replace domain invariants, and a policy should not be hidden in a screen, provider or generic utility when it controls a consequential decision.

## Handler

A handler carries one defined command, query, event, message or request responsibility. It can make a vertical slice easier to locate and test when the operation is genuinely distinct.

A handler should not become a miscellaneous dispatch point for unrelated work. Its contract, identity, retry and failure behaviour should be explicit when it processes durable messages or deferred work.

## Model and contract

A model represents information for a defined responsibility: domain concepts, value objects, aggregates, requests, responses, commands, queries, results, events, messages, options, projections or physical records. The word model is incomplete without its layer and consumer.

A contract is an agreement between a provider and consumer. It describes what is offered, what may be relied on, what is required and how failure is expressed. A type named `IThing` is not automatically a useful contract.

## Choosing a building block

Start with the responsibility, consumer, boundary, lifecycle and failure behaviour. Then choose the smallest building block that makes that responsibility clear. Do not create one of every category, and do not rename a class to make an unclear responsibility sound designed.

A logical building block may be implemented by several physical types. Several building blocks may share one physical type only when their responsibilities, lifecycle and reasons for change genuinely align. When a physical class starts carrying interface, state management, persistence, provider and registry responsibilities at once, the layers have probably collapsed.

Read [Patterns](./patterns.md) for developer-scale design patterns, [Logical Layers](./logical-layers.md) for layer placement and [LDM Layers and Contents](../../development/layers.md) for the detailed categories used in development.
