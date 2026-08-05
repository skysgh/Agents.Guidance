# API Lifecycle Conventions

Apply these conventions to HTTP, event, RPC and other externally consumed contracts.

For the accessible explanation of why published contracts need a managed life, read [API Lifecycle](../../../IT/foundations/api-lifecycle.md). This document states the precise portable rules.

## Contract design

- Define the consumer-facing contract before implementing the transport.
- Use standard HTTP semantics, status codes and machine-readable error responses for HTTP APIs.
- Define pagination, filtering, ordering, expansion and maximum request limits for collection reads.
- Make commands idempotent where clients may retry them. Use explicit idempotency keys when necessary.
- Return stable problem types and correlation information without leaking implementation details.
- Keep transport models separate from domain and persistence models.

## Change management

- Treat published contracts as compatibility surfaces.
- Prefer additive changes. Record and review every breaking change.
- Define versioning, deprecation, migration and removal dates before introducing incompatible behaviour.
- Validate OpenAPI, event schemas or generated contracts in CI where applicable.
- Test authentication, authorisation, validation, concurrency conflict, rate limit and dependency-failure responses.
- Do not expose an internal query or persistence surface merely to avoid designing a consumer contract.

## Stewardship

Every published contract needs a stewarding boundary, compatibility policy, security classification and support path. A contract is not complete when only its success response is documented.
