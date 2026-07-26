# Developers Need to Know

Read this orientation document when joining the project, making a cross-cutting architectural decision, creating a module, or deciding where a new capability belongs. Skip it for a narrow local change unless the task crosses one of these boundaries.

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
