# Startup Conventions

Read this document when adding or changing application startup, module initialisation, service registration, configuration binding, registries, schema discovery, settings, seed initialisation, middleware composition or startup diagnostics.

## Startup is object assembly

Startup is the deliberate assembly of the system from objects that represent configuration, capabilities, policies, registries, schema definitions, settings, initialisers and pipeline components. Prefer an object with a clear contract, lifecycle, owner, order and diagnostic identity over spare arguments passed through unrelated methods or assembled only when a later caller happens to need them.

Create and validate these objects as early as their dependencies permit. Early object assembly makes the system's composition visible, allows conflicts and missing dependencies to be rejected before requests arrive, and gives diagnostics something meaningful to report. It does not mean every object must be instantiated before configuration or dependency injection is available; it means the required lifecycle phase should be explicit.

## Contract-based reflection

Reflection is a discovery mechanism, not a design model. Discover types because they satisfy a capability contract, lifecycle contract or explicit discovery attribute. Do not rely on a class name, filename or namespace as the meaning of the capability.

A discovery contract should make the following answerable:

- what capability the object provides;
- which lifecycle phase may invoke it;
- how dependencies are obtained;
- whether it is stateful and what lifetime it requires;
- how execution order or dependencies are determined;
- how ambiguity and duplicates are handled; and
- how discovery, activation, failure and completion are reported.

Concrete repositories may call these contracts configuration-object, registry, schema-definition, service-configurer, initialiser, middleware or setting contracts. Those names are bindings, not the portable architecture. The portable concept is a contract-bearing startup participant.

Do not use reflection to discover arbitrary methods and infer their meaning from method names when a contract can express the capability. If a compatibility bridge must inspect a legacy shape, keep it scoped, visible, deterministic and temporary.

## Lifecycle phases

A host commonly needs phases with these responsibilities. The exact names may vary, but the dependency order must remain observable:

1. **Preflight and host configuration**: establish environment, dependency targets, secrets/configuration sources and safe startup diagnostics.
2. **Assembly and module discovery**: identify eligible assemblies, group them by logical module, apply exclusions, load them and establish deterministic order.
3. **Contract discovery**: collect startup participants into a module-owned composition record. Discover configuration objects, services, registries, schema definitions, contexts, maps, middleware, settings and initialisers without invoking work prematurely.
4. **Pre-build registration**: bind configuration objects, register services and registries, add framework services, and invoke only operations that need the service collection rather than a built provider.
5. **Container build and validation**: build the provider, validate required registrations and publish the discovered composition and diagnostics.
6. **Schema and persistence readiness**: apply or migrate schemas and make required persistence infrastructure available before hooks that query or write it.
7. **Post-build initialisation**: invoke objects that require resolved services, such as registry population, definitions loaded from persistence, cache preparation or module hooks.
8. **Ordered service configuration**: run configuration objects that require the built provider in declared dependency order. Reject ambiguous or duplicate ordering where it affects correctness.
9. **Runtime seeding and external preparation**: run idempotent initialisers that depend on databases, object storage, identity providers or other external infrastructure.
10. **Pipeline composition and finalisation**: compose middleware and endpoints in security-sensitive order, expose readiness only when required phases have completed, and emit a final startup record.

A phase may fail, degrade or be skipped only under an explicit policy. Startup must report the phase, participant, reason, impact and recovery path.

## Object categories

Use these conceptual categories when deciding what belongs in startup:

- **Configuration object**: a typed, owned set of settings bound from a source and validated before dependent services use it.
- **Definition object**: metadata describing a resource, setting, permission, schema element, capability or other thing that the system must know about.
- **Registry object**: a stateful, usually singleton index or broker that collects providers, handlers, descriptors or runtime entries and exposes governed lookup or invocation.
- **Cache policy/object**: a typed description of a cacheable capability, key policy, expiry/timeout behaviour and refresh or fallback operation. A timeout callback is part of the policy object, not a loose delegate floating through startup.
- **Schema definition**: a contract-bearing description of persistence shape or configuration that the persistence boundary can discover and apply. Keep provider-specific details in the persistence binding.
- **Initialiser**: a lifecycle operation that prepares a module or external state. It must declare whether it runs before or after provider build, whether it is idempotent and what it requires.
- **Service configurer**: an ordered operation that configures a service after the required provider or dependency exists.
- **Pipeline component**: a contract-bearing middleware, endpoint, handler or tool contribution with a declared placement and order.
- **Setting declaration**: a typed definition of a setting's key, data type, default, validation, classification, ownership and presentation metadata. A setting declaration is not the same thing as a user's setting value.
- **Startup diagnostic record**: structured phase, participant, timing, status, metrics, exception and child-step information. Do not make operators reconstruct startup from unstructured console text.

These categories may overlap in a concrete implementation, but the lifecycle responsibility must remain unambiguous.

## Configuration and settings

Bind configuration into typed objects before dependent services are registered or activated. Validate required values, defaults, sources, classification and cross-property rules at the earliest phase that has enough information.

Keep these concepts separate:

- host configuration used to assemble the application;
- module configuration used by a service or infrastructure adapter;
- declared settings that describe available user or workspace choices; and
- persisted setting values owned by a user, workspace or other actor.

Do not pass raw configuration keys, optional values and fallback delegates through many constructors. Give the owning object a contract and let startup bind, validate and register it once.

## Registries and timeout operations

A registry is an owned runtime object, not a static bag of global functions. It should define its state, lifetime, registration rules, lookup semantics, duplicate policy, thread-safety, maximum size and diagnostic identity.

For cache or registry entries that need timeout, expiry or refresh behaviour, keep the operation with the object that owns the policy. The object should express the key, value or capability, expiry semantics, cancellation, retry limits, fallback behaviour, observability and failure policy. Startup registers the object or provider through its contract; later code resolves the registry rather than receiving unrelated delegates as spare arguments.

Timeout callbacks must be bounded, cancellation-aware and safe to retry. They must not silently turn a cache miss into an unbounded request fan-out or bypass authorisation and classification policy.

## Schema and model discovery

Discover schema participants by a schema capability contract and scope discovery to the owning module's assemblies. Keep discovery deterministic, report the count and identity of discovered types, reject ambiguous ownership, and ensure design-time and runtime inputs produce the same model where generated schema depends on them.

Schema discovery should collect descriptions before applying provider-specific model operations. The persistence boundary owns the actual model builder, migrations and provider details. Startup owns readiness, ordering, diagnostics and failure handling.

## Ordering and dependencies

Prefer explicit dependency metadata or stable order values over incidental reflection order. A participant that depends on another participant must express that dependency or belong to a later phase.

For each ordered category:

- define the default order range or dependency rule;
- sort with a stable secondary key;
- detect duplicate or contradictory order where it matters;
- log the selected order; and
- make repeated startup safe where the operation may run again.

Do not solve ordering by adding more static calls to the host when a contract can express the lifecycle relationship.

## Failure and observability

Every startup participant should have a meaningful display identity and produce structured success, warning, degraded or failure information. Include phase, module, participant, duration, dependency and impact where appropriate.

Fail before serving traffic when a missing or invalid object makes the service unsafe or functionally false. Degrade only when the degraded capability and operator response are explicit. Readiness must reflect the actual completion of required phases, not merely that a process has opened a port.

## Implementation checklist

When adding a startup participant:

1. State the capability and owning module.
2. Choose the narrowest existing contract that expresses it; create a new contract only when the semantic distinction is real.
3. Declare lifetime, required phase, dependencies, order, idempotency and failure policy.
4. Add it to contract-based discovery or explicit registration when discovery is not safe.
5. Validate configuration and reject ambiguity before dependent work runs.
6. Keep provider, persistence and vendor details behind their owning boundary.
7. Add structured startup diagnostics and a focused discovery/lifecycle test.
8. Verify cold start, repeated start, missing dependency, timeout, duplicate registration and partial failure behaviour.

The goal is not maximum reflection or maximum framework machinery. The goal is visible, contract-led composition that is deterministic, testable and ready at the correct point in the lifecycle.
