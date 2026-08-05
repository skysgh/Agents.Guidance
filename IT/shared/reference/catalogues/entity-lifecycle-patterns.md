[Up](./readme.md)

# Entity Lifecycle Patterns


Enduring versus Transient is a foundational classification for logical data modelling. It helps the team decide what should retain identity and meaning across time, what represents a bounded arrangement, and how conceptual language should be translated into a logical model without losing either real-world recognition or durable responsibility.

This classification works alongside Domain-Driven Design (DDD). DDD helps identify bounded contexts, aggregates, entities, value objects, domain events and responsibilities. Enduring versus Transient asks an additional lifecycle question: which concept remains the same kind of thing across changing circumstances, and which concept records a time-bounded participation, appointment, membership, assignment, state or event involving it?

## Enduring concepts

An **Enduring** concept has an identity and responsibility that persist beyond one transaction, workflow, appointment, period, provider or physical representation. It may change attributes, enter different states or be retired, but it remains the same kind of thing for the purposes that own it.

Examples may include:

- a **Person**, whose identity persists even when their name, contact details, role or affiliations change;
- an **Organisation** or **Group**, whose identity persists even when its members, purpose, structure or location changes;
- a **Location**, whose identity and meaning may persist while its address, use or associated group changes; and
- a **School**, where that is the enduring organisation or institution the relevant Domain owns.

Enduring does not mean immortal, unchanging, globally authoritative or necessarily stored in one database. It means the identity and responsibility should not be recreated merely because a transient arrangement changes.

## Transient concepts

A **Transient** concept records something bounded by a time, context, process, decision, appointment, membership, assignment or interaction. It may have its own identity, state, audit history, authority and evidence, but its meaning depends on the enduring things or context it connects.

Examples may include:

- **StudentAt**, a person's bounded student membership or affiliation with a School or Group;
- an access grant for a person in an organisation and resource context;
- a team assignment for a person during a period;
- a subscription, enrolment, booking or appointment; and
- a request, assessment or decision whose lifecycle is bounded even when the people and organisations involved endure.

Transient does not mean unimportant, disposable or merely in-memory. A transient relationship may be the most important evidence in the system. It often needs effective dates, state, authority, audit, classification, reporting and a lifecycle of its own.

## The modelling question

When stakeholders say "a student at a school", do not immediately create one `Student` record with a `SchoolId` and treat the current association as the identity. Ask:

- What endures if the person changes school?
- What endures if the school changes location, name or membership?
- Is Student an enduring classification, a current role, or a transient membership?
- Is the relationship historical evidence that must answer "was this person a student here on date X?"?
- Who owns the person, group, school, location and membership meanings?
- What happens when either end is retired, merged, renamed or translated into another system?

A useful logical model may therefore be:

```text
Person --------------------< StudentAt >-------------------- School
   |                              |                              |
   | enduring identity            | transient membership        | enduring organisation
   |                              | effective from/to          |
   |                              | status, authority, evidence |
   |                              v                              |
   +-------------------------- Group / Location context --------+
```

The exact entities depend on the Domain. The important point is not the names or table count. The important point is that the enduring identities are not confused with the transient relationship that joins them. A **Group** may be the enduring organisational concept, while a **Location** is a distinct enduring place or address; a School may be a Group, an Organisation, a Location, or a composition of those concepts depending on the authority and lifecycle being modelled.

## Translation from conceptual to logical

Different stakeholders may use "student" to mean different things:

- a teacher may mean a person currently assigned to their teaching group;
- admissions may mean a person with an enduring student identifier in the institution's records;
- a report may mean a person who had an active `StudentAt` relationship during a period;
- a cross-system test scenario may mean a neutral person, student context and institution that several systems translate into local records; and
- a person may mean the enduring identity that continues after study ends.

Do not force these meanings into one universal `Student` object. Record the conceptual language, identify the durable logical responsibilities, then map each consumer to the appropriate logical concept and contract. A consumer-facing label may remain **Student** while the logical and physical representations distinguish `Person`, `Student`, `StudentAt`, `Group`, `School` and `Location`.

This is not needless abstraction. It prevents a current membership, role or workflow from becoming the accidental identity of the person or institution. It also allows systems with different local schemas to preserve shared identity and relationships without making one physical schema the universal authority.

## Temporal and relationship evidence

A transient relationship commonly needs:

- `EffectiveFrom` and `EffectiveTo`, or another explicit temporal bound;
- a status and permitted transitions;
- the authority that creates, changes or ends it;
- duplicate and overlap rules;
- audit and provenance;
- classification and retention;
- behaviour when either enduring end is retired or merged; and
- query contracts for current, historical and as-at-date views.

For example, an historical membership query means:

```text
EffectiveFrom <= date
and (EffectiveTo is null or EffectiveTo >= date)
```

The physical representation may use tables, documents, events, projections or an external provider model. The representation must preserve the logical distinction and temporal evidence required by the Domain; a nullable `SchoolId` on `Person` is not enough when membership has history, authority or reporting meaning.

## Relationship to DDD and vertical slices

Enduring versus Transient does not replace DDD. It is evidence for DDD decisions:

- an enduring concept may be an Entity or Aggregate root when it owns identity and lifecycle;
- a transient relationship may be an Entity, Aggregate, value-bearing association or domain event depending on its authority and behaviour;
- a transient concept may deserve its own bounded context or vertical slice when it has independent permissions, state, history, reporting or recovery; and
- a value object may still be enduring or transient in use, so the classification is about lifecycle responsibility, not merely class inheritance or database shape.

A relationship shaft is often the implementation path for a transient relationship. It should be treated as a real capability when the relationship has its own lifecycle rather than hidden inside one enduring entity's record. See [Vertical Slices](../../../development/vertical-slices.md).

## Responsibilities by role

- **Business Analysts and Stakeholder Analysts** expose when stakeholder language conflates an enduring identity with a current role, membership, assignment or workflow. They elicit temporal meaning, authority, history and consequences.
- **Architects** use the distinction to derive logical boundaries, ownership, bounded contexts, integration mappings and durable responsibilities from conceptual language.
- **Technical Analysts** make the identity, relationship, effective-date, contract, mapping and query consequences precise.
- **Technical Leads** ensure the implementation path can preserve the distinction through LDMs, layers, schemas, migrations, tests and operational evidence.
- **Developers** implement the prepared model and raise a design question when a physical representation would make a transient arrangement the accidental identity of an enduring concept.
- **Testers** verify current and historical queries, transitions, overlap, retirement, translation and cross-system identity preservation.
- **Operations and Maintenance** preserve the data, audit, migration, recovery and decommissioning consequences of both enduring identities and transient evidence.

## Related guidance

- [Conceptual, Logical and Physical Models](./conceptual-logical-physical-models.md)
- [Domains and Capabilities](./domains-and-capabilities.md)
- [Vertical Slices](../../../development/vertical-slices.md)
- [Contracts](../../../development/contracts.md)
- [Logical and Physical Models in ORM](../../../development/logical-and-physical-models.md)
- [Deliverable Systems](./deliverable-systems.md)
- [Glossary](../glossary.md)
