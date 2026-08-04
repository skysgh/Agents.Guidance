# Platform Service Inventory

Agents must use this inventory when planning a new capability, module, service, endpoint, persistence model or cross-cutting integration. The human explanation is [Guidance for Tech Leads](../../../humans/orientation/guidance-for-tech-leads.md), and the detailed human reference is [Platform Services Reference](../../../humans/reference/platform-services.md).

## Canonical sequence

Check the relevant items in this order:

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

This is a dependency-led default. Do not require conditional capabilities when the service does not need them, but record the reason they are not applicable.

## Required agent questions

For each capability required by the task, determine whether it is:

- **Available**: identify the contract, owner, registration, readiness signal and tests.
- **Planned**: identify the owner, contract and delivery condition.
- **Not applicable**: record the reason and the consequence.
- **Missing**: expose the dependency and assign it; do not hide it in feature code.

Ask for the first missing item in sequence before implementing a dependent capability. If a temporary local implementation is justified, record a Deliberated Divergence with its owner, security and operational consequences, expiry or convergence condition and replacement contract.

## Enforcement rules

- Do not create a feature-local substitute for an existing platform contract without evidence that the shared contract is unsuitable.
- Do not proceed as though a platform capability exists merely because a package, registration or class name exists.
- A discovered participant must be invoked, diagnosed and tested; discovery alone is not implementation.
- Mapping, startup discovery and EF schema/model contribution are first-class platform capabilities and must be checked explicitly.
- Do not treat diagnostics as optional when the service must be operated or its startup must be trusted.
- Keep authentication, authorisation and auditing distinct: identity establishes who or what acts, authorisation decides what it may do, and auditing records accountable events.
- Treat local and remote caching as different provider capabilities with different consistency, failure and security consequences.
- Do not add queues or workflows to conceal an unclear capability boundary or an undefined synchronous contract.

## Evidence to request

For every adopted platform service, request:

- contract and owning LDM;
- dependencies and startup phase;
- configuration and secret requirements;
- readiness and diagnostics;
- security and classification policy;
- timeout, retry, fallback and recovery policy;
- focused tests, including failure tests; and
- repository binding or implementation reference.

Use the [Platform Services Reference](../../../humans/reference/platform-services.md) for the purpose and readiness questions of each item.
