[Up](../readme.md)

# Enduring identity is separated from bounded membership

The BA records that "student" has several meanings. It may be a person's enduring classification in one context, a current membership in another and a reporting label for anyone who held that membership during a period. The architect and Technical Analyst make the lifecycle and authority explicit before choosing storage.

The logical model distinguishes:

- **Person**, whose identity endures when affiliations change;
- **School**, **Group** or **Organisation**, according to which authority owns the institution's meaning;
- **Location**, where place has its own identity and lifecycle; and
- **StudentAt**, a transient membership connecting a Person to a School or Group with effective dates, status, authority, history and permitted transitions.

The physical model may use tables, documents, events and projections. A consumer can still use the familiar word **Student**, and each system can map its local representation through a contract. No local schema is made the universal cross-system authority merely because it was designed first.

A current membership query is evaluated from the relationship's state and temporal bounds. A historical query uses the membership evidence, for example:

```text
EffectiveFrom <= date
and (EffectiveTo is null or EffectiveTo >= date)
```

The contract defines who may create, amend, withdraw or reinstate a membership, how overlapping memberships are handled, what happens when a Person or School is retired or merged, and which system is authoritative for each meaning.

## A worked boundary, contract and storage choice

This example uses an **Enrollment** capability as the owner of `StudentAt`. That is a worked choice, not a universal rule. In another organisation, a School domain, Student Records domain or membership service may own the relationship. The durable question is whether one authority is named for membership meaning, while Person and School authorities remain responsible for their own identities.

The Enrollment boundary owns the relationship facts:

- it accepts an authorised request to create, amend, withdraw or reinstate `StudentAt`;
- it rejects overlapping active memberships when the policy does not permit them;
- it preserves the effective dates, status transitions, actor, reason and provenance;
- it publishes a stable relationship identity and version for connected consumers; and
- it does not rename, merge or redefine the Person or School identities it references.

A contract can make those promises visible without prescribing the implementation:

```text
CreateStudentAt
	personId, schoolId, effectiveFrom, authority, correlationId
	-> studentAtId, status, version

GetCurrentStudentAt
	personId, asAt
	-> zero or more memberships with effective bounds and status

ChangeStudentAt
	studentAtId, requestedTransition, effectiveAt, reason, expectedVersion
	-> new status, version, audit reference
```

The contract rejects an unknown identity, an unauthorised transition, an overlapping period that policy forbids and a stale `expectedVersion`. A retry with the same correlation or idempotency identity returns the original outcome rather than creating a second membership. Consumers may rely on the relationship identity, temporal meaning, permitted transitions and failure conditions; they may not rely on a particular table, ORM type or provider payload. See [Contracts](../../development/contracts.md) for the wider contract questions.

One possible relational representation is:

```text
StudentAt
	StudentAtId       stable relationship identity
	PersonId          reference to the Person authority
	SchoolId          reference to the School authority
	EffectiveFrom     inclusive start
	EffectiveTo       nullable inclusive end
	Status            governed relationship state
	Version           optimistic concurrency value
	Authority         creating or changing authority
	Reason            transition explanation
	CorrelationId     request or cross-system identity
	CreatedAt         provenance timestamp
```

Indexes and constraints support current and as-at-date queries, duplicate detection, permitted overlap rules and concurrency. An event stream or document model could represent the same logical responsibility. The storage choice is correct only if it preserves the relationship identity, temporal evidence, authority, history, classification, recovery and translation rules.

## Retirement and deletion

When a Person changes school, the old `StudentAt` ends and a new relationship begins. When a School closes or merges, the Enrollment authority records the effective transition and maps the affected relationships; it does not silently rewrite history. Support and Operations can therefore distinguish an identity correction, an institution change and a membership transition.

If the Person's identifiable representation must be deleted, the responsible privacy and records authorities decide what must remain. The service may retain a legally required or useful historical membership only after removing the person-linked route back and applying the approved retention, anonymisation or destruction method across copies, indexes, exports, logs and backups. The surviving record must not be presented as an anonymous Person. See [Data Deletion Guidance](../../development/data-deletion-guidance.md) for the decision and verification questions.

Retirement evidence names the final active memberships, downstream consumers, contract and access closure, retained or transformed history, removed identifiers, recovery implications and the authority that accepted completion. This is a relationship lifecycle, not merely a row deletion.

## Evidence

- A school change ends one `StudentAt` relationship and creates another without changing the Person identity.
- Historical membership, current membership, withdrawal and as-at-date queries are independently testable.
- Tests cover duplicate and overlap rules, authority, expiry, school change, withdrawal, identity mapping and cross-system translation.
- Support and Maintenance can distinguish correcting a Person from correcting a membership or institution mapping.
- Operations can preserve audit, backups, recovery and retention for both enduring records and transient evidence.

## What changed afterwards

The team did not reject the stakeholder phrase "student at a school". It decomposed that phrase into durable identities and a bounded relationship before implementation. DDD decisions, vertical slices, contracts, ORM mappings and tests now follow the lifecycle responsibilities instead of allowing the first screen or table to define them.
