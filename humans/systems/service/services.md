# System LDM Services

The System LDM is normally the first LDM developed because it gives later business LDMs dependable shared capabilities. This list is a starting catalogue, not a demand to build every service before any business value appears.

A new business capability may need configuration, diagnostics, storage, identity, permissions and audit before its own rules can be trusted. Those foundations are easy to treat as incidental framework wiring until a dependency fails or a second capability needs the same behaviour. The System LDM gives those shared technical responsibilities a visible home without taking business meaning away from the business LDM.

A service is a capability with a [contract](../../development/contracts.md) and a responsible boundary. It is not the LDM itself. The [Service glossary entry](../../reference/glossary.md#service) distinguishes this designed service from the wider organisational service system and the technical web-service representation. The System LDM contains services alongside domains, layers, constants, models, registries, repositories, mappings and infrastructure implementations.

## The first System LDM shape

A service will commonly establish these related system domains first:

- **Configuration:** typed construction values, dependency targets and environment references.
- **Diagnostics:** composition, health, correlation, failure and operational evidence.
- **Secrets:** protected material, resolution, rotation and redaction.
- **Storage:** durable resource contracts, media storage and recovery boundaries.
- **Settings:** declared choices, scope, validation and effective values.
- **Identity:** local or remote users and service identities where the system owns or integrates identity.
- **Roles and permissions:** reusable access concepts and policy evaluation contracts.
- **Audit:** accountable records of protected access, decisions and changes.
- **Startup and discovery:** lifecycle participants, ordering, readiness and diagnostics.

Person and Group may be part of this first LDM when they are shared system concepts. They may become a separate LDM when their administration, relationships, reuse or lifecycle is substantial.

## Dependency-led service sequence

Develop and assess the services in this broad order. Mark a capability **Available**, **Planned**, **Not applicable** or **Missing** rather than pretending every service exists:

1. Configuration
2. Diagnostics
3. Key Vault and secret resolution
4. Storage foundations
5. Settings
6. Routing
7. Mapping
8. Startup reflection and contract-based discovery
9. Schema and persistence-model contribution
10. Local caching
11. Remote caching
12. Templating
13. Notifications and SMTP
14. Local user authentication
15. Remote user authentication
16. Remote service authentication
17. Authorisation
18. Auditing
19. Queuing
20. Workflow

The sequence expresses dependencies and readiness. It does not mean that all work is strictly sequential. A service may be developed in parallel once its contract and lower-level dependencies are understood.

## Why the framework is not the service design

A framework can bind configuration, validate a token, match a route, map an object, open a database connection, enqueue a message or run a workflow step. Those mechanisms are useful, but they do not decide:

- which LDM owns the capability and its data;
- what the capability means in this service;
- which actors may use it and which information is classified;
- what happens during outage, timeout, duplication, partial success or provider change;
- how readiness, diagnostics, tests, audit and recovery prove it works; or
- how the organisation migrates, replaces or exits the provider.

The System LDM provides an application-owned contract around those decisions where shared responsibility exists. It may wrap a framework, expose a deliberately narrow part of it or reject it as unsuitable. The point is not to hide every framework type. The point is to prevent a default configuration from silently becoming the architecture.

## Service boundary rule

The System LDM may provide technical ability. Business LDMs retain business meaning.

For example, Sys may provide authentication context, permission evaluation, audit recording and durable queuing. A business LDM still owns who may approve a request, what approval means, which state transition is valid and what business evidence is required.

A workflow engine in Sys may provide durable execution, retries and resumption. The business LDM owns the business workflow definition and the meaning of its decisions. Do not move business rules into Sys merely because several business areas currently use a similar-looking process.

## Minimum evidence for an adopted service

For each service that the System LDM provides, record:

- the owning domain and LDM;
- the contract and consumers;
- dependencies and startup phase;
- configuration and secret requirements;
- readiness, diagnostics and shutdown behaviour;
- security, classification and data handling;
- timeout, retry, fallback and recovery behaviour;
- tests and failure evidence; and
- whether the service is available, planned, not applicable or missing.

Do not hide a missing shared service in a feature-local helper. Name the gap, assign responsibility and record the temporary arrangement and its convergence condition.

## Detailed readiness questions

The [System LDM Service Readiness Reference](../../reference/platform-services.md) gives the detailed purpose and readiness question for each service. Use it when a team needs to decide whether a framework capability is sufficient or whether an application-owned contract and boundary are still required.

## The human and agent views

This paper gives people the service catalogue and the reasoning behind it. The [agent platform inventory](../../../agents/conventions/development/platform-services.md) gives the task-time enforcement rules and status protocol.

## Related guidance

- [Service System Guidance](./readme.md)
- [Logical Deployment Modules](./ldms.md)
- [LDM Layers and Contents](./layers.md)
- [Guidance for Tech Leads](../../orientation/guidance-for-tech-leads.md)
- [Guidance for Developers](../../orientation/guidance-for-developers.md)
- [System LDM Service Readiness Reference](../../reference/platform-services.md)
- [Platform Service Inventory](../../../agents/conventions/development/platform-services.md)
