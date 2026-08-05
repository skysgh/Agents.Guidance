[Up](../readme.md)

# After: Queryable Read Rejected or Exposed Directly

The team defines an intentional read contract and projection. The repository owns visibility and persistence policy. The application service composes the use-case query and maps to a DTO. The transport boundary applies allowed query operations, cost limits and protocol rules.

Consumers can shape filtering, ordering, projection, paging and approved expansion without receiving internal entities or bypassing security. Writes remain explicit commands with explicit validation, authorisation, state and idempotency rules.

The developer proves the boundary with tests for permitted data, rejected shapes, limits, mapping and provider translation. The tester checks denied access and sensitive fields. The business and product roles clarify useful read shapes. Operations watches cost and failure behaviour.

`IQueryable` is neither a blank cheque nor a forbidden technology. It is a governed server-side capability that gives consumers room to ask legitimate questions without multiplying fixed endpoints.
