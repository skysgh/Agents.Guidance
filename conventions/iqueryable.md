# IQueryable and Governed Queryability

Read this document when designing or changing a .NET server-side read contract, repository query, projection, filtering, paging, sorting, expansion or OData-style API surface.

For the accessible explanation and examples, read [The Palette: First Look](../HUMAN/PALETTE-FIRST-LOOK.md) and [IQueryable guidance in the current-state examples](../HUMAN-CURRENT-STATE.md).

## Purpose

This document explains how a service can let different consumers ask useful questions about the same information without creating a new fixed endpoint for every screen, report or integration. It is for business and delivery roles as well as developers, testers, security roles and operations staff.

## The short version

A service can provide one safe read capability and allow each approved consumer to ask for the fields, records, ordering and page it needs. This reduces repeated endpoint work and helps long-lived services respond to needs that were not visible when the first screen was built.

The service must still control what the consumer may see, how much work a request may cause and which internal details remain private. In technical language, the .NET feature that supports this composable read behaviour is called `IQueryable<T>`. The safety comes from the boundary, mapping and policy around it, not from the word itself.

## The capability

`IQueryable<T>` allows a server-side query to remain composable until the boundary that understands the consumer's requested shape. A client can ask for the subset, ordering, projection, page or related data it actually needs without the server team predicting every future combination in advance.

This matters most for long-lived public services. Once a system is in production, a new endpoint is rarely a small technical change. It may require funding, prioritisation, procurement, governance, testing, release coordination and years of operational support. Requiring a new endpoint for every legitimate read shape makes the service less adaptable and makes consumers wait for changes that should have been expressible as safe queries over an existing capability.

A well-governed queryable contract gives consumers useful autonomy:

- user interfaces can request lightweight list projections or detailed views;
- integrations can retrieve only the fields and records they need;
- reporting tools can filter, sort and page without bespoke endpoint proliferation;
- future consumers can use an existing capability without reopening the server contract; and
- the server retains authority over visibility, classification, cost and allowable shape.

The argument against queryability usually attacks unrestricted exposure of persistence objects. That is a valid warning about a bad implementation, not an argument against the capability. Rejecting `IQueryable` because it can be used naively throws away a powerful server-side contract instead of governing it.

## The security boundary

Never expose an internal entity set as an unrestricted public query. Queryability must be applied to a deliberate boundary model, normally a DTO or projection designed for the consumer contract.

The safe shape is:

```text
authorised source
  -> repository-owned query policy
  -> application-owned DTO projection
  -> permitted query composition
  -> bounded transport response
```

The boundary must control at least:

- which records are visible;
- which properties may be selected or filtered;
- which relationships may be expanded;
- which calculated or sensitive values are omitted;
- maximum page size and result cost;
- sort and filter complexity;
- classification and redaction rules;
- cancellation and timeout behaviour; and
- audit or operational evidence where the query is sensitive.

Mapping is not cosmetic. It is the point at which internal persistence shape becomes an intentional external shape. It protects security, prevents accidental coupling to tables and navigation properties, and allows the database model to evolve without silently changing the public contract.

## Layer responsibilities

A queryable read should preserve composability while keeping ownership clear:

- **Repository** owns the governed source, visibility filters, persistence restrictions and queryable policy.
- **Application service** owns use-case composition, authorisation context, DTO projection and application-level restrictions.
- **Controller or transport boundary** owns protocol metadata, query option limits, response semantics and transport-specific validation.
- **Persistence provider** translates the approved expression into database operations and must not receive an unrestricted application escape hatch.

No controller or application service should bypass the repository policy with direct `DbContext` access. No layer should materialise the full entity set merely to avoid understanding query composition.

## Queryable does not mean unlimited

A queryable contract is a controlled language, not a blank cheque. Define and test the supported grammar and its cost limits. At minimum, specify:

- allowed filters and operators;
- allowed ordering fields;
- selectable properties;
- expandable relationships and expansion depth;
- maximum page size and total work;
- whether counts are allowed;
- default ordering and stable pagination;
- maximum request duration;
- behaviour for unsupported or expensive expressions; and
- the error contract when a query is rejected.

Apply access restrictions before consumer shaping. A `$select` option must not be able to select a property that the caller could not otherwise see. A `$filter` must not bypass row-level visibility. An `$expand` must not create an unbounded graph or cross an ownership boundary.

## Read and write asymmetry

Queryability is especially valuable for reads because consumers need different representations of the same governed information. It does not imply that writes should accept arbitrary object graphs or expression trees.

Commands should use explicit contracts with explicit validation, authorisation, idempotency, transaction and state-transition rules. A queryable read and a command may share a resource identity, but they have different safety and evolution requirements.

## Evidence required for adoption

When introducing or changing a queryable contract, document:

1. the consumer capability and expected read shapes;
2. the DTO or projection boundary;
3. visibility and classification rules;
4. supported query operations and cost limits;
5. default ordering and pagination behaviour;
6. mapping and provider-translation constraints;
7. cancellation, timeout and failure behaviour; and
8. tests for allowed queries, denied data, rejected shapes, limits and persistence failures.

The mature position is therefore not "expose everything" and not "ban `IQueryable`." It is: expose a deliberately mapped, authorised and bounded query language over a capability that consumers can safely shape for themselves.
