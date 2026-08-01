# What Tech Leads Need to Know

Technical leadership is the responsibility of keeping the whole service coherent while different specialists build its parts. A tech lead does not need to personally implement every service. They do need to know which platform capabilities the service depends on, which boundary owns each one, how the capabilities become ready and what the team must do when one is missing.

The service also sits inside wider systems of enterprise process, policy, regulation and law. Read [Systems Within Systems](./systems-within-systems.md) and [Legal and Regulatory Context](./legal-context.md) to understand why privacy, data protection, storage, audit, retention and recovery are obligations carried into technical delivery rather than optional features of the local codebase. For a local service, the offering and delivery jurisdictions may be the same; the tech lead should still check whether access, hosting, processing, support or suppliers widen the map. The architect defines what those obligations require; the tech lead guides the team in making them technically real and does not treat them as negotiable implementation preferences.

For digital lifecycle decisions, start with [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md). It makes irreversible anonymisation or de-identification the preferred preservation outcome where the applicable rule allows it, while keeping technical erasure available for rules, orders, failed risk assessments and other cases where preservation cannot remain lawful. Use the [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md) paper for deeper analysis.

## The platform is a sequence of capabilities

The platform is not a bag of shared utilities. Its capabilities have relationships and readiness dependencies. A service should establish the lower-level capabilities that make later capabilities possible, then expose a consistent contract to business and technical domains.

The default sequence is:

1. Configuration
2. Diagnostics
3. Key Vault and secret resolution
4. Storage foundations
5. Settings
6. Routing
7. Mapping
8. Startup reflection and contract-based discovery
9. EF schema and model contribution
10. Local caching
11. Remote caching
12. Templating
13. Notifications, including SMTP
14. Local user authentication
15. Remote user authentication
16. Remote service authentication
17. Authorisation
18. Auditing
19. Queuing
20. Workflow

This list is the tech lead's short route. Read [System LDM Services](../development/services.md) for the human explanation of the System LDM and [System LDM Service Readiness Reference](../reference/platform-services.md) for the detailed purpose and readiness questions for each capability.

This is a dependency-led default, not a demand that every service implement every item or that all work happen in one irreversible pass. A small service may not need remote caching, templating, SMTP, queues or workflow. A capability may also be developed in parallel once its contract and required lower-level dependencies are understood. The sequence tells the team what must be established before a dependent capability can be safely treated as a platform service.

## What the sequence protects

Configuration gives the service typed values and dependency references. Diagnostics make composition and failure visible. Key Vault resolves protected material without turning secrets into ordinary configuration. Storage provides durable and transient resource contracts. Settings distinguish declared choices from their effective values.

Routing and mapping protect the external boundaries. Routing decides how a request reaches a capability. Mapping translates between external, application, domain, persistence and projection models without allowing one view to redefine another.

Startup reflection and contract-based discovery make the platform assembled rather than scattered through host code. EF schema and model contribution make persistence shape deliberate, discoverable and ready before code that depends on it runs.

Caching, templating and notifications are reusable runtime capabilities. Authentication establishes who or what is acting. Authorisation decides what that actor may do. Auditing records the protected decisions and changes that need accountability. Queuing makes durable deferred work possible. Workflow coordinates capabilities and stateful steps without taking ownership away from the slices that own them.

The ordering is therefore about responsibility and evidence. It is not merely about which NuGet package or framework service is registered first.

## The tech lead's job at each boundary

For every platform capability, identify:

- the contract it provides;
- the owning platform domain or LDM;
- the capabilities it depends on;
- the capabilities it enables;
- its startup, readiness and shutdown behaviour;
- its security, classification and data-handling rules;
- its local, remote, provider-specific or fallback choices;
- its failure, retry, degradation and recovery policy; and
- the tests and diagnostics that prove it is available and safe.

Do not allow a feature team to create a private copy of a platform concern because the shared capability is inconvenient or not yet ready. First establish whether the capability exists, who owns it, what contract it exposes and what evidence is missing. A deliberate local exception may be correct, but it should be recorded as a divergence with a replacement or convergence condition.

## Ask for the platform status

When a new capability is proposed, ask the team to walk the relevant part of the service sequence. For every required item, the answer should be one of:

- **Available**: the contract, owner, registration, readiness signal and tests are known.
- **Planned**: the owner, contract and delivery condition are recorded.
- **Not applicable**: the reason is explicit and fits the service's consequences.
- **Missing**: the gap is visible, assigned and treated as a dependency rather than hidden in feature code.

The tech lead should be able to answer where the first missing capability sits in the sequence and what later work it puts at risk. This makes platform debt visible without pretending that every capability must be built before any business value can be delivered.

## Review a real slice

Use one vertical slice to test the platform design. Follow it from route and external contract through mapping, authentication, authorisation, application and domain rules, storage or an external effect, audit, diagnostics and recovery. If it queues work or participates in a workflow, follow the durable identity, status, retry, correlation and operator visibility as well.

The slice should prove that platform services are actually invoked. A discovered mapping, schema contributor, cache policy or notification provider that is never used is not a working platform capability. A startup log that says only "started" is not evidence that the required composition succeeded.

## Keep the service list alive

The catalogue is a reference point, not a frozen architecture diagram. When BASE introduces or retires a platform capability, update the service purpose, dependency position, owning boundary and agent inventory together. When a repository adopts the guidance, its binding document should name the concrete implementations and any deliberate omissions.

The tech lead protects the sequence by making change visible. They do not protect it by blocking every change until the ideal platform exists.

## Related guidance

- [What Architects Need to Know](./architects-need-to-know.md)
- [Legal and Regulatory Context](./legal-context.md)
- [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md)
- [System LDM Services](../development/services.md)
- [System LDM Service Readiness Reference](../reference/platform-services.md)
- [LDM Layers and Contents](../development/layers.md)
- [Cross-Cutting Services](../development/cross-cutting-services.md)
- [Vertical Slices: Common Shafts](../development/vertical-slices.md)
- [Constants](../development/constants.md)
- [Contracts](../development/contracts.md)
- [What Developers Need to Know](./developers-need-to-know.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Startup and discovery](../../agents/conventions/foundations/startup.md)
- [Operations](../../agents/conventions/development/operations.md)
- [Data Protection](../../agents/conventions/foundations/data-protection.md)
- [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md)
- [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md)