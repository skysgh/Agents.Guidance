# Developers Need to Know

Read this document before planning a new capability, module, service, endpoint, persistence model or cross-cutting integration. It explains the order in which the system becomes buildable and the questions that must be answered before implementation accelerates.

The default stance is **design the knowable, discover the novel**. Enterprise engineering has decades of repeated solutions for boundaries, contracts, objects, services, persistence, security, startup and operations. Do not make developers rediscover those structures feature by feature. The domain vocabulary, conceptual relationships, decisions and presentation shape may need exploration; the formwork that lets those things become a reliable service should already be deliberate.

The intended system may be designed before the whole system is built. Every known capability should have a rightful place in the model, even when its implementation is deferred by budget, sequencing or evidence. Establish the structure that proves the design and leave later capabilities as explicit, stewarded work. Do not leave future teams to infer the intended system from unrelated partial implementations.

## The common mistake

Teams often begin with the visible business requirement and treat configuration, settings, startup, mapping, storage schema and access control as details to fill in later. That reverses the dependency order. A business capability can only be made reliable when the platform knows how to construct it, secure it, map it, persist it, discover it and report its lifecycle.

The right mental model is a building:

- **Contracts are the structural frame.** They state what a participant provides, which boundary stewards it, when it is available, what it may depend on and how failure is reported.
- **Objects are the contract-bearing parts.** Configuration objects, setting declarations, policy definitions, schema definitions, mappings and domain objects hold meaning and policy.
- **Services are the working systems.** They compose objects into application operations, provider integrations and infrastructure behaviour.
- **Registries and discovery are the building services.** They collect participants, validate duplicates, establish ordering and make the assembled system visible.
- **Vertical slices are shafts.** A slice carries one stewarded capability from its external contract through application rules to persistence or an external effect.
- **Horizontal flows are routes between rooms.** A flow coordinates slices, actors, decisions and hand-offs into an outcome without taking stewardship away from the slices.

This is a shared design, not a hierarchy. The architect does not see everything and hand a finished structure to developers. Business analysts contribute meaning, developers test implementability, testers challenge the claimed boundaries, operations exposes lifecycle and recovery needs, security roles expose protection obligations, and architecture preserves coherence across the views. Each role supplies evidence that the others cannot reliably supply alone.

Do not begin by asking only, "Which endpoint and table do I need?" First ask:

1. What contract makes this capability explicit?
2. Which boundary or module stewards each responsibility, regardless of which person is available today?
3. Which foundational platform contracts does it depend on?
4. How will startup discover, order, validate and report it?
5. Which data may this actor see or change, and where is that enforced?
6. Which mapping protects the boundary between internal and external models?
7. What is the vertical slice, and which horizontal flows will use it?
8. Which failure, retry, audit, recovery and operational paths must exist before the happy path is considered complete?

## Design patterns before persons

Do not block design because a named business owner, product owner or future operator cannot yet be identified. People and organisational assignments change. The design must first establish concrete responsibility:

- which contract is being provided;
- which boundary or module stewards the contract;
- which data and decisions it is responsible for;
- which services and registries support it;
- which lifecycle phase makes it available;
- which security and audit rules apply; and
- which team or role must be consulted when the responsibility is exercised.

This is stewardship, not dependence on a particular person. A person may later accept operational accountability, approve a policy or act as a user, but the architecture should remain intelligible and deliverable before that person is known. The absence of a named stakeholder may leave a business decision to resolve; it must not leave the technical boundary, contract or safe default undefined.

## Foundational areas

Treat these as first-class design work, not administrative preparation:

- **Configuration**: typed values needed to construct or operate the service.
- **Settings**: declared and potentially scope-managed choices with metadata, validation and effective-value rules.
- **Startup**: the lifecycle that discovers, assembles, validates and prepares the platform.
- **Access and security**: identity, authorisation, classification, visibility, audit and protected transitions.
- **Storage schema**: the durable shape, ownership and readiness of persisted state.
- **Caching**: key, expiry, invalidation, provider, fallback and consistency policy.
- **Mapping**: the intentional translation between transport, application, domain, persistence and query projection models.

These areas are related, but they are not one undifferentiated mechanism. Their contracts should be assembled through startup and diagnosed together while retaining clear ownership.

## Readiness before speed

Hard-wired setup can be useful while a platform contract is still being proven. Reflection does not make a system organised: contracts do. Mature platform code should prefer contract-based discovery and reflection when the scope, ordering, activation, duplicate handling, diagnostics and tests are in place, because that wiring expresses an already-organised composition model. The answer to discomfort about reflection is better contracts and evidence, not a permanent return to scattered host calls. Explicit registration remains correct when the participant set is intentionally closed or discovery cannot be made safe and observable.

Likewise, queryability should not be rejected because unrestricted entity exposure is unsafe. Use a governed, mapped and bounded `IQueryable` read contract, and keep writes as explicit commands with explicit authorisation and state rules. See the [IQueryable guidance](./iqueryable.md).

Before calling a capability ready, confirm that:

- its contracts have a defined stewarding boundary and a lifecycle;
- its startup participants are discovered or registered deliberately;
- configuration and settings have not been conflated;
- access decisions and classification are enforced at the correct boundary;
- mappings do not expose internal persistence shape;
- schema and external dependencies have a readiness and failure policy;
- cache behaviour is bounded and observable where caching is used;
- the slice can be tested independently; and
- every flow using it has explicit hand-offs, retries, permissions and recovery.

Only then is it reasonable to accelerate the visible business work. The foundations are the work that allows the business work to survive.

## Design completeness and build completeness

These are different completion states:

- **Design complete** means the intended capability has a stewarding boundary, boundary contracts, participating objects and services, dependencies, lifecycle, security rules, data and persistence intention, mappings, related slices and flow participation, and an explicit deferral record where implementation is postponed.
- **Build complete** means the selected part has been implemented, integrated, tested and made operational.

A release may be build-incomplete for capabilities that are deliberately deferred while still being design-complete for the architecture. That is controlled sequencing. An unbounded gap in the design is not controlled sequencing; it is a future invention disguised as a backlog item.

Physical deletion is not the same as deferral. Before removing a relational field, relationship, state, contract or other structural element, check historical meaning, dependants, migrations, referential integrity, security, recovery and future composition. Retire deliberately or preserve an explicit extension point. Do not remove a structural element merely because the capability is not being built in the current delivery stage.

## The delivery balance

Do not turn this guidance into an indefinite architecture exercise. Do not turn it into feature-first improvisation either.

Before coding, observe the problem domain, identify recurring structures, categorise the capabilities, name ownership and design the boundary contracts. Then put developers to work building one real vertical slice through the formwork. Let that slice challenge the abstractions. Refine the domain concepts and presentation where the evidence is new. Keep the known platform structure stable unless the slice proves that an assumption is wrong.

The practical split is:

- **Waterfall of the knowable**: the complete intended contracts, boundary responsibilities, access rules, lifecycle phases, mapping policy, persistence conventions, diagnostics and operational obligations, with implementation staged by value and capacity.
- **Agility of the unknown**: domain language, conceptual objects, relationships, user decisions, workflow detail and presentation shape.

YAGNI applies to speculative features and unjustified infrastructure. It does not excuse omitting a known boundary and making every future capability pay for the omission.

Use **DBB: Design Before Build** as the design reminder, and **WGF: What Goes First?** as the sequencing reminder. DBB protects the known structure. WGF allows construction to proceed in a deliberate priority order. Neither says that every implementation must be completed before the first useful capability is delivered.

For each WGF decision, record:

- what is included, deferred or omitted;
- the consequence of including it now;
- the consequence of omitting or deferring it;
- the affected contracts, dependencies, security and lifecycle;
- the stewarding boundary for the decision and deferred work;
- the evidence currently available; and
- the condition that would change the priority.

Do not accept "we already do that" as completion evidence. Check one real capability across the whole chain: contract, ownership, objects, services, registry or startup participation, access control, mapping, persistence, tests and explicit deferrals. The purpose is not to catch people out. It is to distinguish a shared, assembled pattern from several familiar practices that happen to exist in different places.

Read this orientation document when joining the project, making a cross-cutting architectural decision, creating a module, or deciding where a new capability belongs. Skip it for a narrow local change unless the task crosses one of these boundaries.

For worked recognition rather than more explanation, use the [example gallery](../../humans/examples/readme.md). Choose the case that resembles the problem in front of you, read the `before.md` account, then read the matching `after.md` account.

## 1. Principles come first

Principles are the durable reasons behind the engineering rules. When a local shortcut conflicts with a principle, do not silently accept the shortcut. Identify the trade-off and record a **Deliberated Divergence** as a Decision.

A divergence decision should state:

- the principle or constraint being departed from;
- the alternatives considered;
- the reason the normal rule is unsuitable here;
- the security, data, operational, performance and maintenance consequences;
- the scope and owner of the exception; and
- the review, expiry or replacement condition.

A decision record is not permission to ignore a rule. It is the evidence that the conflict was understood and consciously governed.

## 2. The system is modulithic

The default architecture is a modulith: one deployable system composed of separately owned, bounded modules with explicit contracts and controlled dependencies.

A modulith is not a Big Ball of Mud. The distinction is not the number of processes. It is whether boundaries are real:

- a module owns a coherent capability and its data;
- dependencies cross declared contracts rather than reaching into implementation details;
- access follows the approved application path;
- module changes have an identifiable owner and test boundary; and
- deployment may be combined today without making future separation impossible.

Do not split a module into a service merely to conceal unclear ownership. First make the boundary explicit and measure whether separate deployment solves a real operational or organisational problem.

## 3. A module is a unit of ownership

A Logical Deployment Module, also called a Logical Deployment Unit in older material, is a coherent deployable boundary with an identifiable purpose, owner, contracts, data and operational responsibilities. In this project, the normal rule is one module per repository.

The repository boundary supports ownership, history, dependency review, release management and future separation. It does not mean every module must run as a separate process immediately. The binding document supplies the repository's concrete project and assembly arrangement.

Keep framework code distinct from client or organisation-specific code. A module may depend on lower-level public contracts, but it should not casually depend on another module's infrastructure implementation.

## 4. Models exist at different levels

Use ANSI/SPARC's three-schema idea as a useful mental model, not as a demand to reproduce a database textbook literally:

- external models describe what a consumer or interface needs;
- the conceptual model describes domain meaning and rules; and
- the internal model describes storage and infrastructure concerns.

In implementation terms, an interface contract, application DTO, domain model and persistence record may be different types because they have different consumers, lifecycles and security responsibilities. Map deliberately where meanings differ. Reuse a type only when its responsibility genuinely matches at both boundaries.

Prefer logical abstraction before presentation shaping. Preserve reusable capability, relationship, lifecycle and query meaning until the consumer boundary is known. This protects evolvability and avoids inventing a new conceptual model for every screen or first-use endpoint. It does not permit exposing domain entities or persistence records directly; use application-owned contracts and explicit mappings at the edge.

## 5. Vertical slices go through the layers

A vertical slice is one complete capability. It travels through the relevant layers from an external boundary to the state or external effect it reads or changes. A slice normally includes its contract, application orchestration, domain rules, persistence or integration policy, mapping, authorisation, audit behaviour and tests.

The slice is the unit of delivery and testability. Layers still matter, but a feature should not be scattered into disconnected technical work with no end-to-end owner.

For the standard service access path, use:

`Controller -> Application Service -> Repository -> DbContext`

Repositories provide governed query surfaces. Application services compose use-case queries and policy. Controllers do not bypass the application boundary.

## 6. Flows cross slices

A horizontal flow coordinates multiple slices to achieve an outcome. It describes actors, information, decisions and state transitions across capabilities. Examples include browse and select, prepare and submit, assess and decide, and publish and maintain.

A flow is conceptual orchestration, not a replacement for the slices beneath it. Define its permissions, transaction boundaries, audit effects, failure paths and recovery behaviour before implementing it.

## 7. How to choose where work belongs

Ask these questions in order:

1. Which principle, quality characteristic or constraint governs the decision?
2. Which module owns the capability and its data?
3. Is this one vertical slice or a cross-slice flow?
4. Which model and layer owns the decision or transformation?
5. Which contract crosses the boundary?
6. What evidence and validation could disprove the proposed design?
7. Does the decision need a recorded divergence?

When the answers are unclear, stop and clarify the boundary before adding another class, project, service or dependency.

## 8. Startup is the composition root

Startup assembles the application from typed participants before the runtime serves requests. Configuration objects, registries, schema and model participants, service contributors, middleware, settings declarations and initialisers should each have an explicit owner, capability contract, lifecycle phase, dependency rule and diagnostic identity.

Use contract-based discovery when it is safe and observable. Keep the discovery scope, ordering, exclusions, ambiguity policy and design-time/runtime parity explicit. A contract that is discovered but never invoked is not an implemented lifecycle; test both discovery and execution. Read [Startup and discovery](./startup.md) for the detailed phase model and implementation rules.

## Related guidance

- [Development Principles](./principles.md)
- [Development Constraints](./constraints.md)
- [Logical Deployment Modules](./ldms.md)
- [Vertical Slices](./slices.md)
- [Horizontal Flows](./flows.md)
- [Repository bindings](./bindings.md)
- [Agent Workflow](./agent-workflow.md)
