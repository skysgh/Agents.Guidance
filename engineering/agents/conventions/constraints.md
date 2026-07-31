# Development Constraints

Read this document for every engineering task; apply these portable MUST rules before task-specific conventions or repository bindings.

These are the portable consequences of the development principles. They are stronger than preferences and narrower than product-specific architecture. A repository may add stricter local constraints in its binding document, but it must not silently weaken these constraints.

For the accessible explanation of why these constraints exist, read [Human Guidance](../../humans/README.md).

## Queryable access

- Repositories MUST expose governed `IQueryable` surfaces for queryable reads.
- Application services MUST compose repository queries and own use-case projection, validation and policy composition.
- Controllers MUST invoke application services rather than repositories or persistence contexts directly.
- Repository query surfaces MUST enforce their visibility, classification, share, provider and execution policies.
- No layer may bypass repository policy through direct `DbContext` access.

## Resource discipline

- Do not add a cache, queue, broker, replica, background worker or separate service without a stated operational need, measured benefit or required failure boundary.
- Caching MUST remain optional at the capability level. A cacheable object MAY use in-memory or shared caching according to its consistency, scale, availability and cost requirements; downstream consumers MUST NOT choose or depend on the cache provider.
- Design for horizontal scaling where credible demand requires it, but keep the smallest adequate deployment as the default.
- Treat every additional always-on dependency as an operational cost that requires monitoring, security maintenance, upgrades, capacity planning and failure handling.
- Measure before and after introducing caching or distributed infrastructure.

## Dependency boundaries

- Domain and application code MUST NOT depend directly on web transport, persistence providers, vendor SDKs or infrastructure configuration APIs when an application-owned boundary is responsible for that concern.
- A wrapper MUST own policy, translate a meaningful contract, reduce coupling, or make substitution and testing meaningful. Pass-through wrappers are not justified by abstraction alone.
- EF or another ORM MAY remain visible inside its dedicated persistence boundary where complete shielding would add more complexity than value. It MUST NOT leak beyond that boundary without a documented reason.
- Web concerns MUST remain inside the repository's designated interface boundary.
- Configuration MUST be accessed through typed, purpose-specific options or configuration objects rather than repeated raw key lookups.
- Logging MUST use the application's logging contract where one exists, while retaining structured fields, correlation and integration with the platform logging pipeline.

## Model contracts

- Add a structural interface only when a consumer uses it for a capability, generic constraint, discovery rule, schema rule, mapping rule, validation rule or policy.
- Keep external representations, application models, domain models and persistence records separate when their responsibilities or lifecycles differ.
- Do not force unrelated concepts into a common interface merely to increase reuse.
- Preserve logical capability, relationship, lifecycle and query semantics until a presentation or integration boundary requires a consumer-specific shape.
- Do not shape the logical model around one screen, report, export or endpoint convenience when a governed composition can preserve broader reuse.
- Do not expose domain or persistence models directly merely to delay presentation shaping; use explicit application-owned contracts and mappings.
- Reserve early shaping for cases where security, classification, performance, bandwidth, accessibility, protocol compatibility or cognitive load makes later shaping inadequate. Prefer the least-constraining option, record the alternatives rejected and identify the information intentionally removed or future composition constrained.

## Discovery and startup

- Reflection-based discovery MUST have a defined scope, deterministic ordering, ambiguity handling and startup visibility.
- Reflection MUST NOT be used to compensate for missing contracts, unclear ownership or unorganised startup responsibilities. Contracts organise the system; reflection only discovers contract-bearing participants.
- Before coding a substantial capability, the team MUST identify the applicable known boundaries, stewardship responsibilities, contracts, lifecycle, security and operational obligations. This does not require a named stakeholder to be available; the technical boundary and safe default must be defined. Novel domain concepts and presentation needs MAY remain exploratory.
- Generated schema, registrations, seed data and projections MUST be deterministic between design-time and runtime when they use discovery.
- Explicit registration is permitted when discovery cannot be made safe, deterministic or observable.
- Startup participants MUST be assembled and validated before the lifecycle phase that consumes them.
- Lifecycle behaviour MUST be owned by a typed participant with an explicit capability and phase; do not pass unowned configuration fragments or delegates through unrelated startup methods.
- Stateful registries and cache-policy objects MUST own their lifetime, duplicate policy, timeout, cancellation, retry, fallback and observability rules.
- Required participant discovery or invocation failures MUST prevent readiness and identify the module, contract category and participant. Optional degradation MUST be an explicit policy with a recorded impact.
- Startup tests MUST verify that discovered lifecycle participants are invoked in the declared phase and order, not merely that their types were found.

## Security and completion

- Security, authorisation, privacy, auditability and recovery are boundary requirements, not later hardening tasks.
- Do not present a stub, placeholder, silent fallback or untested path as complete.
- Do not suppress a warning, weaken a test or add infrastructure merely to obtain a green build.
