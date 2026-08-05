[Up](./readme.md)

# System LDM Service Readiness Reference


This reference is the detailed readiness table supporting the human [System LDM Services](../../development/services.md) paper. It describes the services and domains that commonly belong in a System LDM. It is a dependency and readiness guide, not a mandatory feature list. The System LDM provides reusable technical foundations and shared system capabilities. A business LDM remains responsible for its business concepts, rules, state transitions and business workflow.

The list is deliberately more explicit than a framework or hosting template. Frameworks can provide useful mechanisms, but they do not decide the application's responsibilities, data classification, lifecycle, recovery, audit, portability or operating concerns. The System LDM turns those responsibilities into contracts that the rest of the application can use without repeating provider-specific assumptions.

## What belongs in the System LDM

The System LDM is a useful home for related technical and system-wide domains. A service may begin with only a subset, but the modular structure should remain visible from the beginning.

Common system domains include:

- **Configuration:** values needed to assemble and operate the service.
- **Diagnostics:** composition, health, failure and operational evidence.
- **Secrets:** protected material and its resolution, rotation and redaction rules.
- **Storage:** durable resource contracts, media or object storage and recovery boundaries.
- **Settings:** declared choices and their effective, scoped values.
- **Identity:** users, service identities and authentication context where the system owns or integrates identity.
- **Roles and permissions:** reusable access concepts and policy evaluation contracts.
- **Audit:** accountable records of protected access, decisions and changes.
- **Startup and discovery:** the contracts and ordering that make a running service ready.

Person and Group may also belong in the System LDM when they are shared system concepts. They may deserve a separate LDM when their complexity, reuse, responsibility or lifecycle becomes substantial. Do not force them into the System LDM merely because they sound foundational.

The System LDM can provide the technical ability to authenticate, authorise, audit, queue or coordinate work. It must not silently become responsible for a business concept just because that concept uses one of those services. For example, the System LDM can provide permission evaluation; a business LDM remains responsible for what approving a request means.

| Order | Capability | Purpose | Readiness question |
| --- | --- | --- | --- |
| 1 | Configuration | Supplies typed construction values, environment references and dependency targets. | Are sources, classification, defaults and validation rules known before dependent services activate? |
| 2 | Diagnostics | Reports composition, health, failure, correlation and operational evidence. | Can the service explain what it tried to assemble and why readiness succeeded or failed? |
| 3 | Key Vault and secret resolution | Retrieves protected secrets, credentials, tokens and keys without treating them as ordinary source-controlled configuration. The pipeline and the executing workload use identities to access values only when required; humans do not retrieve or copy production secret values. | Can protected material be resolved, classified, rotated and redacted safely, with human administration separated from value retrieval? |
| 4 | Storage foundations | Provides contracts for durable storage, object or media storage and other persistent resources. | Are responsibility, readiness, failure, retention and recovery policies explicit? |
| 5 | Settings | Defines available choices and effective values for users, workspaces, modules or environments. | Are declarations separate from persisted values, with validation, scope, responsibility and classification? |
| 6 | Routing | Connects external requests to the responsible interface and capability boundary. | Are routes stable, authorised, observable and free from business responsibility that belongs deeper in the system? |
| 7 | Mapping | Translates between external, application, domain, persistence and query projection models. | Are mappings explicit, safe for query translation and independent of accidental storage or UI shape? |
| 8 | Startup reflection and contract-based discovery | Finds eligible platform and module participants, orders them and invokes their lifecycle contracts. | Is discovery scoped, deterministic, observable, duplicate-safe and tested for execution as well as presence? |
| 9 | EF schema and model contribution | Discovers and applies persistence model contributions, migrations and provider-specific schema behaviour. | Is schema responsibility clear, is design-time/runtime discovery consistent and is persistence ready before dependent work? |
| 10 | Local caching | Reuses rebuildable values within one process. | Are keys, expiry, invalidation, classification and restart loss acceptable for a per-instance cache? |
| 11 | Remote caching | Shares values across processes or instances and can survive an individual process restart. | Are network failure, consistency, security, availability, invalidation and provider cost understood? |
| 12 | Templating | Produces controlled messages, documents or presentation content from approved data and templates. | Are template responsibility, escaping, versioning, localisation, sensitive data and failure behaviour explicit? |
| 13 | Notifications, including SMTP | Delivers outbound email or other notifications through a governed capability. | Are recipient authority, consent or policy, redaction, delivery status, retry and provider failure handled? |
| 14 | Local user authentication | Establishes identity using credentials or identity records owned by the service or platform. | Are credential storage, recovery, session/token lifecycle, lockout and sensitive diagnostics safe? |
| 15 | Remote user authentication | Establishes user identity through an external identity provider. | Are issuer, audience, claims, key rotation, clock tolerance, logout and provider outage behaviour defined? |
| 16 | Remote service authentication | Establishes service-to-service identity and trust. | Are credentials or workload identities scoped, rotated, audited and rejected safely when invalid? |
| 17 | Authorisation | Decides whether an authenticated actor may perform an action on a classified resource in its context. | Is the decision enforced at the responsible boundary and tested for both allow and deny paths? |
| 18 | Auditing | Records protected access, decisions, changes, commands and operational events that require accountability. | Is the audit record trustworthy, minimised, protected, correlated and retained for the required period? |
| 19 | Queuing | Records durable work for later processing, retry, throttling and recovery. | Are identity, correlation, status, idempotency, retry, poison handling, expiry and operator visibility defined? |
| 20 | Workflow | Coordinates capabilities, actors, decisions and durable state across a business or technical journey. | Are slice responsibility, transitions, compensation, permissions, recovery and resumption explicit? |

## Why framework defaults are not enough

Framework defaults are useful starting points. They are usually designed to make a product easy to run in a narrow or common context. They do not usually answer the whole service question.

For every adopted service, ask what the default leaves undecided:

- **Responsibility:** which LDM is responsible for the contract, data, policy and lifecycle?
- **Meaning:** what does the capability mean to this service rather than to the framework?
- **Security:** who may use it, what may they see or change and how are denied paths enforced?
- **Classification:** which values, logs, cache entries, messages and projections are protected?
- **Failure:** what happens during timeout, outage, partial success, duplicate delivery, quota exhaustion or provider change?
- **Readiness:** how does startup know that the capability is configured, connected and safe to use?
- **Evidence:** what tests, diagnostics, audit records and recovery evidence prove that it works?
- **Change and exit:** how can the organisation upgrade, migrate, replace or stop using the provider without losing meaning or control?

The service contract is the answer to those questions. It may wrap a framework mechanism, deliberately expose a small part of it or decide that the mechanism is unsuitable. The goal is not to hide every framework type. The goal is to prevent an unexamined default from becoming the architecture.

## Service explanations

### Configuration, diagnostics and secrets

**Configuration** establishes the values and dependency targets needed to assemble the service. A framework can bind environment variables, but it does not decide which values are required, which are sensitive, which defaults are safe or when invalid configuration must prevent readiness.

**Diagnostics** makes composition and failure visible to operators and maintainers. A host's startup log is not enough if it cannot say which participants were discovered, which dependencies were checked, which capabilities were excluded and why readiness succeeded or failed.

**Secret resolution** keeps credentials, tokens and keys out of ordinary configuration and source control. A provider may retrieve a secret, but the service still owns classification, rotation, redaction, access scope, failure behaviour and evidence that secret material was not exposed through logs, caches or responses.

### Storage, settings and persistence composition

**Storage foundations** provide application-defined contracts for durable resources, media and other persistent dependencies. A provider client does not decide data responsibility, retention, recovery, consistency, deletion, export or migration policy.

**Settings** are choices that users, workspaces, organisations or modules may manage. They are not the same as deployment configuration. Framework options do not decide scope, validation, inheritance, protection, effective-value calculation or the audit trail for a changed setting.

**Schema and model contribution** makes persistence composition deliberate. An ORM can infer tables or accept registrations, but the System LDM must establish responsibility, discovery, migration responsibility, design-time/runtime consistency and readiness before dependent capabilities run.

### Routing, mapping and discovery

**Routing** gives consumers a stable way to reach the responsible boundary. A web framework can match URLs, but it does not decide which LDM owns the capability, which policy applies, what must be observable or whether a route has accidentally exposed a persistence concern.

**Mapping** protects differences between consumer, application, domain, persistence and projection models. Automatic mapping can save typing, but it cannot safely decide which fields may cross a boundary, whether a state transition is meaningful or whether a provider representation is the business concept.

**Startup discovery** assembles known participants through contracts, ordering, diagnostics and readiness. Reflection can find types; it cannot prove that the participant was invoked, invoked once, invoked in the correct phase or tested under failure.

### Caching, templating and notifications

**Local caching** is a per-process optimisation. The System LDM must define rebuildability, key responsibility, expiry, invalidation, classification and acceptable loss on restart. A framework cache does not know whether the value is safe to reuse or whether stale data changes a decision.

**Remote caching** adds network, consistency, availability, security, cost and invalidation concerns. A provider's distributed-cache API does not make those trade-offs disappear.

**Templating** and **notifications** are governed output capabilities. The service must control template responsibility, escaping, localisation, sensitive data, recipient authority, consent or policy, delivery status, retries and provider failure. An SMTP or template library only supplies mechanics.

### Identity, access and accountability

**Authentication** establishes who or what is acting. Local and remote identity have different credential, issuer, claims, key-rotation, session, logout and outage concerns. The framework can validate a token or credential, but the service still needs a clear identity contract and safe failure behaviour.

**Authorisation** decides whether an actor may perform an action on a classified resource in context. A framework role check is not automatically the correct policy. The responsible boundary must define the resource, action, context, denied path and audit requirement.

**Auditing** records accountable access, decisions, changes and operational events. A logging framework is not an audit design. Audit records need trustworthy identity and correlation, minimisation, protection, retention, review and resistance to accidental alteration.

### Queuing and workflow

**Queuing** provides durable work that can outlive a request. A message broker can deliver messages, but the application must define identity, correlation, status, idempotency, retry, backoff, poison handling, expiry, reconciliation and operator visibility.

**Workflow** coordinates capabilities, actors, decisions and durable state across a journey. A workflow framework can execute steps, but it does not decide which LDM owns each rule, what approval means, how compensation works or which evidence is required. Reusable technical workflow infrastructure may belong in Sys; a business workflow belongs with the business capabilities it coordinates.

## Reading the sequence

The early capabilities make later composition possible. Configuration establishes what the host needs to know. Diagnostics makes the assembly visible. Secret resolution protects sensitive dependencies. Storage and settings establish durable foundations. Routing and mapping protect the boundaries that consumers use. Discovery and schema services make the assembled platform and persistence model deterministic.

The later capabilities build on those foundations but are not all required by every service. Local caching may be enough where a value is cheap to rebuild. Remote caching adds coordination and availability obligations. Templating and notifications are needed only when the service produces governed communications. Authentication, authorisation and auditing must match the actors, resources and consequences of the service. Queuing and workflow are needed when work or coordination must outlive a request or cross several stateful capabilities.

## Minimum contract for an adopted service

For every capability a repository adopts, document:

- the concrete implementation and responsible module;
- the public contract and consumers;
- dependencies and startup phase;
- configuration and secret requirements;
- readiness, health and diagnostics;
- security, classification and data handling;
- timeout, retry, fallback and recovery behaviour;
- test coverage and failure evidence; and
- whether the capability is available, planned, not applicable or missing.

Do not hide a missing shared capability inside a feature-specific helper. Name the gap, assign a responsible boundary and record the deliberate temporary arrangement.
