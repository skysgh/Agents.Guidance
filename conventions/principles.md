# Development Principles

Read this document for every engineering task; use it as the rationale for the more specific conventions selected by the task.

These principles are portable engineering priorities. They are not product requirements, project management preferences or a list of framework names. They explain why the more specific constraints and conventions exist.

## 1. Optimise the whole service life

A system spends far longer in operation, support and maintenance than in initial delivery. Optimise for the total cost of ownership, not only for the first successful build. A shortcut is not cheap if it creates a permanent operational dependency, repeated support work, or a difficult migration after the original developers have moved on.

This does not justify speculative complexity. It requires recording foreseeable directions of change, then choosing the smallest design that keeps those directions open.

**Source:** The ISO/IEC 25010 quality model treats maintainability, performance efficiency, reliability, security and portability as product quality characteristics, not as post-delivery decoration. See the [ISO/IEC 25010 overview](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010).

## 2. Preserve evolvability at boundaries

Design boundaries so that future consumers can ask for more than the first user interface required, without forcing a new endpoint shape or a rewrite of the persistence path. This is the reason queryability is valuable.

Where a read is queryable, a repository should expose a governed `IQueryable` surface, the application service should compose the use-case query, and the controller should invoke the application service. The repository owns the source, visibility policy and provider boundary. Queryability does not mean exposing `DbContext` or permitting arbitrary persistence operations.

This supports reuse that was not fully imaginable during development: new screens, exports, integrations, support tools, reporting, accessibility needs, filtering, projection, ordering and paging can often be added by composing an existing governed read path. It also reduces the pressure to preserve brittle fixed endpoint shapes after the original developers are gone.

**Sources:** [Microsoft, `IQueryable<T>`](https://learn.microsoft.com/en-us/dotnet/api/system.linq.iqueryable-1) describes a queryable data source whose query is represented as an expression tree; [OData](https://www.oasis-open.org/standards/odata/) defines a standard way to query and represent resources; [Microsoft, DDD and layered architecture](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice) discusses keeping domain and infrastructure concerns behind application boundaries.

## 3. Preserve logical abstraction until the presentation boundary

Keep the logical capability, relationships, state and queryable meaning intact for as long as possible. Delay consumer-specific conceptual shaping until the presentation or integration boundary where the actual need is known.

This does **not** mean exposing domain entities, persistence records or unrestricted queries. It means separating logical meaning from a premature screen model, report shape or endpoint convenience model. Application contracts should preserve useful semantics and compose them through governed projections. The final interface, view, export or integration adapter may then shape that meaning for a particular consumer.

Look for recurring structure before inventing a new conceptual shape. When several capabilities share an invariant, prefer a stable logical abstraction and explicit mapping at the edge. When only one consumer needs a shape, keep it at that consumer boundary rather than allowing it to redefine the underlying capability.

This improves evolvability because later consumers can ask different questions without requiring a new persistence path or a workaround around the first screen. It reduces novel solutions because established resource, relationship, query and lifecycle patterns remain reusable. It also respects long-lived patterns such as separation of concerns, information hiding, abstraction barriers and representation independence instead of rediscovering them as bespoke presentation models.

Presentation shaping may be forced earlier by security, data classification, performance, bandwidth, accessibility, protocol compatibility or cognitive load, but it should be reserved, limited and avoided where the requirement can be met at the presentation or integration boundary. Use early shaping only when no less-constraining option is adequate. Record the reason, the alternatives rejected and the information intentionally removed or future composition constrained.

**Sources:** [Microsoft, DDD-oriented microservice architecture](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice) discusses separation between domain, application and infrastructure concerns; [Martin Fowler, Presentation Domain Data Layering](https://martinfowler.com/eaaDev/PresentationDomainDataLayering.html) describes separating presentation, domain and data responsibilities; [ISO/IEC 25010 overview](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010), especially maintainability, flexibility and functional suitability.

## 4. Prepare for scale; spend as little as needed

Design so horizontal scaling remains possible when demand requires it, but do not buy that scale in advance with unnecessary infrastructure. The default target is the least resource-intensive deployment that satisfies the real workload: a single device or process may be preferable, and caching is not automatically an improvement.

Use shared cache, externalised state, queues or additional replicas when a measured requirement or a resilience boundary justifies them. Treat every always-on service as an operational liability: it needs monitoring, upgrades, security maintenance, capacity planning and failure handling.

The governing trade-off is: **prepare for the worst credible demand; operate at the smallest adequate footprint.** Measure before adding cache or distributed infrastructure, and measure again after adding it.

**Sources:** [AWS Well-Architected, Cost Optimization](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html) and [Azure Well-Architected, Cost Optimization](https://learn.microsoft.com/en-us/azure/well-architected/cost-optimization/) both treat resource efficiency and cost as architectural concerns. [NIST SP 800-160 Volume 1](https://csrc.nist.gov/pubs/sp/800/160/v1/r1/final) frames systems engineering as a lifecycle discipline rather than a one-time construction activity.

## 5. Contain dependencies at deliberate boundaries

Do not wrap a dependency merely to make the code look abstract. Wrap it when the boundary protects the rest of the system from vendor APIs, version churn, persistence semantics, transport concerns, or an operational policy that should be expressed in application language.

The wrapper must earn its existence by reducing coupling, enforcing policy, or making substitution and testing meaningful. It should not be a pass-through layer that adds names without adding ownership.

Persistence frameworks are difficult to contain completely, but containing them in one infrastructure boundary is still valuable when done consistently. The cost is paid once; the resulting boundary can be reused across many domains and maintained by the organisation rather than rediscovered in every feature.

The same principle applies to web frameworks, configuration, logging, caching, storage and external identity systems. Higher layers should depend on app-specific contracts where those contracts protect meaningful decisions.

**Sources:** [Martin Fowler, Inversion of Control Containers and the Dependency Injection pattern](https://martinfowler.com/articles/injection.html) explains dependency inversion and separation of construction from use; [Microsoft, Dependency injection in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection) documents the platform's service composition model; [Microsoft, EF Core overview](https://learn.microsoft.com/en-us/ef/core/) documents EF as a persistence technology whose concerns belong at an infrastructure boundary.

## 6. Keep boundary technologies replaceable

Web transport belongs at the web boundary. Persistence belongs at the persistence boundary. Configuration belongs in typed purpose-specific options. Logging belongs behind the application's diagnostic contract when the application needs stable semantics, correlation, audit or structured events.

Each adopting repository should name its concrete web boundary in its binding document. The portable rule is that web concerns must not leak into domain or application contracts.

**Sources:** [Microsoft, ASP.NET Core overview](https://learn.microsoft.com/en-us/aspnet/core/introduction-to-aspnet-core) describes ASP.NET Core as a framework for HTTP applications; [Microsoft, Options pattern](https://learn.microsoft.com/en-us/dotnet/core/extensions/options) describes strongly typed access to related configuration; [Microsoft, logging in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging) documents structured logging and provider-based logging; [OpenTelemetry Logs](https://opentelemetry.io/docs/specs/otel/logs/) defines a vendor-neutral model for logs.

## 7. Prefer explicit policy over ambient access

Ambient access is convenient during development but difficult to reason about in operations. Prefer an injected, purpose-specific contract over repeatedly reaching for general-purpose `IConfiguration`, a framework logger, a service locator, static state or a database context.

This makes ownership visible, gives policy one home, improves testability, and lets the application reject invalid configuration early. It also reduces the risk that a new caller quietly depends on a setting, log format or persistence behaviour that no one regards as a supported contract.

Configuration values should be bound into typed options or dedicated singleton configuration objects. Logging should use the app-specific logging contract where one exists, while still allowing the implementation to delegate to the platform logger and OpenTelemetry exporters.

The Twelve-Factor App states: “Store config in the environment.” This is a useful reminder to separate deploy-time configuration from code; it does not remove the need for typed options and validation inside the application.

**Sources:** [The Twelve-Factor App, Config](https://12factor.net/config); [Microsoft, Options pattern](https://learn.microsoft.com/en-us/dotnet/core/extensions/options); [Microsoft, logging in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging).

## 8. Use structural contracts where they carry meaning

A model interface is justified when it expresses a capability consumed by something else: identity, title, description, lifecycle, classification, ordering, validation or another generic rule. Such contracts make schema generation, object mapping, validation and policy checking more predictable because the consumer can rely on a named capability instead of repeated type-specific discovery.

Do not add marker interfaces without a consumer. A contract should improve substitution, generic constraints, infrastructure discovery, validation, mapping or another identifiable behaviour.

**Sources:** [Eric Evans, Domain-Driven Design](https://www.domainlanguage.com/ddd/), which established the vocabulary of entities, value objects, repositories and bounded contexts; [Microsoft, DDD-oriented microservice](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice), which describes layering and domain model boundaries; [ISO/IEC/IEEE 42010](https://www.iso.org/standard/74393.html), which treats architecture as the structure and relationships relevant to stakeholder concerns.

## 9. Model different concerns at different levels

The ANSI/SPARC three-schema idea remains useful as a reminder that external views, a logical model and a physical storage model are different concerns. It should not be copied mechanically, but it helps explain why a controller contract, application DTO, domain model and persistence record need not be the same type.

Likewise, domain-driven design distinguishes the domain model from application orchestration and infrastructure implementation. Keep the mapping explicit where the meanings differ; reuse a type only where the responsibility and lifecycle genuinely match.

**Sources:** [ANSI/SPARC three-schema architecture, overview](https://www.ibm.com/docs/en/ida/9.1.2?topic=design-three-schema-architecture); [Microsoft, DDD-oriented microservice](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice); [Eric Evans, Domain-Driven Design](https://www.domainlanguage.com/ddd/).

## 10. Make discovery deterministic and observable

Convention and reflection can remove repetitive registration and make extension predictable, but discovery is infrastructure, not magic. Define the assemblies or namespaces that may participate, make ordering deterministic, reject ambiguity, and report what was discovered. Test that design-time and runtime discovery produce the same result where generated schema, registrations or seed data depend on it.

Explicit registration remains appropriate when discovery cannot be made safe, deterministic or observable. The goal is controlled convention, not reflection for its own sake.

**Sources:** [Microsoft, dependency injection in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection); [Microsoft, .NET assembly loading](https://learn.microsoft.com/en-us/dotnet/standard/assembly/load); [ISO/IEC 25010 overview](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010), especially maintainability and reliability concerns.

## 11. Assemble lifecycle objects early through explicit contracts

Startup is the controlled composition root. Assemble configuration, policy, registry, schema, initialisation and pipeline responsibilities as cohesive objects at the earliest lifecycle phase that has enough information to construct and validate them. An object should own meaningful state, behaviour, invariants, policy or lifecycle; this is not a reason to wrap every scalar in a class.

Discover and invoke those objects through capability contracts rather than arbitrary names or loose delegates. This makes composition visible, supports deterministic ordering and failure handling, improves testability and replacement, and gives operators a structured account of what was discovered and executed. It also prevents lifecycle behaviour from becoming a trail of spare arguments passed between unrelated methods.

Reflection is useful when it is scoped, contract-led, deterministic and observable. Where those conditions cannot be met, use explicit registration. Contracts are only useful when their lifecycle methods are actually invoked, so startup tests must verify execution as well as discovery.

**Sources:** [Microsoft, dependency injection in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection) documents service composition; [Microsoft, options pattern](https://learn.microsoft.com/en-us/dotnet/core/extensions/options) documents typed configuration; [ISO/IEC 25010 overview](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010), especially maintainability, reliability and operability concerns.

## 12. Security and auditability are design inputs

Do not bolt security, privacy, authorisation, auditability or recoverability onto a working path later. Identify the protected resource, actor, permission, classification, state transition and audit event while the boundary is being designed.

A feature that is functionally correct but cannot explain who changed what, why access was allowed, or how failure is recovered is not complete for a serious service.

**Sources:** [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework), [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/), and [ISO/IEC 25010 overview](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010).

## How to use these principles

A principle is not a reason to add architecture automatically. For each proposed abstraction or infrastructure dependency, state:

- which principle or operational risk requires it;
- the smallest boundary that addresses that risk;
- what measurable cost it adds;
- how it can be tested and observed; and
- what evidence would justify removing or simplifying it.
