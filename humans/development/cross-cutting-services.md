[Up](readme.md)

# Cross-Cutting Services

A cross-cutting service is a shared capability that many parts of the building may need. In a physical building, power, lighting, heating, ventilation, water, access control, communications and maintenance support many rooms without becoming the purpose of every room.

In an information system, configuration, diagnostics, tracing, settings, identity, authorisation, storage, mapping, caching, audit and messaging can play a similar role. They are commonly provided by the System LDM so that business slices do not each invent a private version.

The name can sound vague. The precise meaning is: **a [contract](./contracts.md)-bearing service with a shared technical or system responsibility, an owning LDM, known consumers and an explicit lifecycle**. Cross-cutting does not mean global, static, invisible or free.

## Shared utilities are not shared ownership

A business slice may use diagnostics, settings, identity or storage. It does not thereby transfer its business meaning to the System LDM.

The System LDM may provide:

- an authenticated actor context;
- permission evaluation;
- audit recording;
- durable queueing;
- trace and correlation propagation;
- typed configuration binding;
- settings declarations and value resolution;
- mapping infrastructure;
- storage and persistence contracts; and
- readiness, health and startup diagnostics.

The business LDM still owns what a business approval means, which state transition is valid, which evidence is required and which records it stewards. A shared service supplies ability. The consuming slice supplies domain meaning and authority.

## The building comparison

| Building system | System capability | What the shared service must decide |
| --- | --- | --- |
| Power and lighting | Configuration, startup and diagnostics | What is required, how it is connected, when the system is ready and how failure is reported |
| Heating and air conditioning | Caching and performance support | Which values may be reused, for how long, under what classification and with what degradation policy |
| Water and drainage | Storage, persistence and recovery | What is durable, who owns it, how it is retained, restored, migrated and removed |
| Lifts and stairwells | Routing, identity and authorisation | Who may reach which capability and how access remains safe during failure |
| Fire and alarm systems | Diagnostics, health, audit and monitoring | What must be detected, recorded, escalated and shown to operators |
| Communications cabling | Mapping, events, queues and integration | Which information crosses the boundary, in what shape, with what delivery and retry rules |
| Maintenance access | Support, reconciliation and operational tooling | Which actions are allowed, evidenced, reversible and visible to responsible operators |

The comparison is about responsibility, not implementation. A building may use one physical network for many services. An application may use one library for many capabilities. Neither fact removes the need for ownership, contracts and failure policy.

## Common cross-cutting services

### Configuration

Configuration supplies typed values needed to assemble and operate the service. It identifies dependency targets and environment references. It is not automatically a user-managed setting, persisted business data or a secret.

### Diagnostics, tracing and health

Diagnostics explains composition, startup, readiness, failure and operational state. Tracing connects work across boundaries with correlation and timing. Health and readiness answer whether a dependency or capability can safely serve its purpose.

These services must control sensitive data. A trace that includes credentials, personal data or full request bodies is not useful evidence; it is an exposure.

### Settings

Settings describe choices that users, workspaces, organisations, modules or environments may manage. The service should define declarations, scope, defaults, validation, classification, effective-value calculation, change history and fallback behaviour.

Keep deployment configuration, setting declarations and persisted setting values separate. They may be related, but they have different owners and lifecycles.

### Secrets

Secret resolution protects credentials, tokens, keys and certificates. Production integration credentials belong only in Key Vault, never in ordinary system configuration, source control, generated artifacts, URLs or logs. Production values are retrieved by the executing workload identity only as required; the delivery pipeline may retrieve values only when required for delivery. Humans must not retrieve or copy production secret values, although they may manage access, rotation, expiry and metadata without seeing the values. Local development should use an approved local development secret store, such as .NET User Secrets backed by a local `secrets.json` outside the project directory. The service must still define access identity, scope, rotation, expiry, redaction, startup failure and recovery.

### Identity and authentication

Authentication establishes who or what is acting. The shared service may resolve a local identity, validate an external identity provider assertion or establish service-to-service identity.

It must define issuer, audience, claims, key rotation, session or token lifecycle, logout, provisioning, deprovisioning, outage and account recovery behaviour where applicable.

### Authorisation

Authorisation decides whether an authenticated actor may perform an action on a classified resource in a particular context. A shared policy service can provide evaluation mechanics, common permission vocabulary and decision evidence.

The owning business or technical boundary still defines the resource, action, context and meaning of the decision. A role name alone is not a complete authorisation model.

### Audit

Audit records protected access, decisions, commands, changes and other events that need accountability. It must preserve trustworthy identity and correlation, minimise sensitive data, protect the record, define retention and support review.

Audit is not the same as application logging or telemetry. Logging helps diagnose. Telemetry helps operate. Audit helps prove accountable action.

### Storage and persistence composition

Storage services provide contracts for relational data, media, object storage, queues or other durable resources. Persistence composition discovers and applies schema contributions, mappings and migrations in a controlled lifecycle.

The shared service should not make one provider's table, ORM entity or client object the definition of every business concept. The owning LDM remains responsible for its logical model and data policy.

### Mapping

Mapping translates between interface, application, domain, persistence, integration and projection representations. It protects boundaries when those representations have different consumers, security rules or lifecycles.

Automatic mapping may reduce repetition, but it cannot decide whether a field is safe to expose, whether a state transition is meaningful or whether a provider representation is the business concept.

### Routing and boundary composition

Routing connects consumers to the responsible interface and capability. Shared routing support may provide conventions, metadata, versioning, endpoint discovery and diagnostics.

It must not become an unowned list of paths. The LDM and domain that own the capability still define its contract, permissions, data and lifecycle.

### Caching

Caching provides reusable values when latency, load, availability or provider cost justifies it. Local and remote caches have different consistency, failure, security and operational consequences.

Every cache policy needs an owner, key policy, classification, expiry, invalidation, rebuild strategy, stampede protection, fallback and authorisation rule. A cache is not a second source of truth.

### Messaging and durable work

Queues and messaging carry work or facts beyond the lifetime of one request. The shared service may provide durable identity, correlation, retry, backoff, status, poison handling, cancellation, expiry and operator visibility.

A business slice still owns the meaning of its command or event. A queue does not turn an undefined operation into a well-defined capability.

### Templates and notifications

Templating and notifications provide governed output. They need ownership, escaping, localisation, classification, recipient authority, consent or policy, delivery status, retry and provider failure rules.

Do not allow a template, SMTP library or notification helper to decide what a business message means or who is allowed to receive it.

## A shared service is not a global helper

Avoid making cross-cutting services static bags of functions or ambient state. A service should have:

- a contract and owning LDM;
- a clear set of consumers;
- a lifetime and startup phase;
- dependency and provider choices;
- configuration and secret requirements;
- security and classification rules;
- timeout, retry, fallback and recovery behaviour;
- diagnostics, audit and readiness evidence; and
- a replacement, migration or exit path.

A service may be available to many LDMs without every LDM depending on it directly. Optional capabilities should remain optional, and an unused cross-cutting service should not be pulled into a slice merely because the platform offers it.

## Shared services as slabs and shafts

Cross-cutting services are usually the slabs, utilities and building systems that support many vertical shafts. They are not the shafts themselves.

A vertical slice may call diagnostics, configuration, mapping, storage and authorisation while carrying a managed record. A read-only diagnostic slice may use tracing, health and mapping but not business persistence. A document slice may use storage, scanning, identity and audit. The shared services differ according to the load being carried.

This distinction protects two directions:

- the shared service must not absorb the business rules of every consumer; and
- the slice must not create private substitutes for shared capability without recording why.

## Deciding whether a service belongs in Sys

A capability is a candidate for the System LDM when it has a coherent technical or system purpose, is reused across meaningful boundaries, needs shared lifecycle or operational ownership, and benefits from one governed contract.

Keep it in a business LDM when its meaning, data, decisions or workflow belong to one business domain, even if several domains may eventually need similar mechanics. Similar mechanics are evidence for a reusable implementation; they are not automatically evidence for shared ownership.

Before adopting a cross-cutting service, record:

1. the responsibility and non-goals;
2. the owning LDM and domain;
3. the contract and consumers;
4. the dependencies and lifecycle phase;
5. the security and classification policy;
6. the failure, retry and recovery behaviour; and
7. the tests, diagnostics and audit evidence.

## Related guidance

- [Human Development Guidance](./readme.md)
- [Logical Deployment Modules](./ldms.md)
- [LDM Layers and Contents](./layers.md)
- [System LDM Services](./services.md)
- [Vertical Slices: Common Shafts](./vertical-slices.md)
- [The Building Metaphor](../shared/reference/building-metaphor.md)
- [System LDM Service Readiness Reference](../shared/reference/platform-services.md)
- [Guidance for Developers](../foundations/guidance-for-developers.md)
- [Guidance for Tech Leads](../foundations/guidance-for-tech-leads.md)
- [Platform Service Inventory](../../agents/conventions/development/platform-services.md)
