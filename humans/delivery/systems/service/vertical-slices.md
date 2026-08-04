# Vertical Slices: Common Shafts

A vertical slice is one complete capability carried through the relevant layers of an LDM. It begins at a boundary, passes through application coordination and domain rules, and reaches the state, evidence or external effect that the capability owns.

A person submits a request, the service records a durable version, an assessor reviews evidence and a provider receives an approved instruction. A screen, endpoint, domain rule, persistence record and external receipt may all participate, but the journey is not one giant implementation. A vertical slice gives one owned capability a complete path through the service while a horizontal flow connects it to other capabilities.

The building metaphor is useful here. A slice is like a shaft that runs from the upper floors to the foundations. Different shafts carry different loads:

- a **stairwell** carries people and movement between floors;
- an **elevator** carries people or goods quickly between selected floors;
- a **utility shaft** carries water, power, air or communications;
- a **service elevator** carries supplies, waste or maintenance work; and
- a **laundry shaft** carries one specialised kind of material through a controlled route.

Software has the same variety. Every slice travels through the building, but the contract, state, security, evidence, failure behaviour and persistence policy depend on what it carries. A request, a diagnostic feed, an approval decision and a document are not the same shaft merely because each has an endpoint, service and repository.

A slice is therefore more than a folder and less than a whole journey. A horizontal flow may use several slices. The slices retain their own meaning, rules, permissions, data and lifecycle.

## The common record shaft: CRU/ST

The most common enterprise shape manages a record through a controlled lifecycle:

- **Create** a new record or draft;
- **Read** a governed view of it;
- **Update** permitted information; and
- **State Transition** it through meaningful lifecycle states such as draft, submitted, approved, published, suspended or closed.

This is a useful **CRU/ST** baseline. It is deliberately different from generic CRUD. Submission, approval, publication, suspension and closure are decisions or transitions, not ordinary field edits.

A record may also have a controlled retirement, withdrawal, archival or erasure operation. Physical deletion should not be the default shortcut because it can destroy history, relationships, audit evidence and recovery options. It is also wrong to say that records must never be deleted: retention law, privacy law, correction rights, contractual terms or an explicit lifecycle policy may require erasure. Treat deletion as a named, authorised and evidenced state or operation with a clear reason. [Detailed Data Deletion Considerations](../../../development/detailed-data-deletion-considerations.md) explains when preserving the digital record through irreversible anonymisation or de-identification is the stronger outcome.

The read part of this shaft is often useful on its own. The system may first establish a governed read capability, then add commands and transitions as the business need becomes clear. That is a design sequence, not permission to expose persistence records directly.

`CRU/ST` is a mnemonic for a recurring capability shape. It is not a universal base class, generic repository or inheritance hierarchy. Share a stable contract only when more than one real capability has the same invariant and the abstraction preserves responsibility, classification and lifecycle differences.

## Read-only shafts

A read-only shaft carries information from an owned source to an authorised consumer. It may expose a query, projection, feed, health state or diagnostic view without allowing the consumer to change the source.

Common examples include:

- diagnostics and startup evidence;
- health and readiness information;
- monitoring feeds and operational metrics;
- search or discovery projections;
- reporting views;
- audit history;
- reference information; and
- public or partner-facing catalogues.

A read-only slice still needs a contract, responsible boundary, mapping, authorisation, classification, query limits, caching policy, failure behaviour and tests. Read-only does not mean consequence-free. A diagnostic feed may reveal secrets or infrastructure topology. A search projection may expose records that the source boundary would deny. A report may become a regulated statement.

A governed queryable read surface is often more adaptable than a new fixed endpoint for every screen. The query must remain bounded, mapped and authorised. Never make a read-only slice an unrestricted window onto an ORM entity set or database table.

## Append-only evidence shafts

An append-only shaft carries facts that should be added and later read, but not silently edited:

- audit events;
- history records;
- evidence submissions;
- integration receipts;
- delivery outcomes;
- telemetry or measurement observations; and
- immutable decision versions.

The capability may support correction by adding a superseding fact, correction record or new version. It should not rewrite the earlier fact merely to make the current view look tidy. The contract must define ordering, identity, duplication, retention, classification, redaction and access to historical information.

Audit and telemetry are different domains even when both are append-only. Audit proves accountable actions. Telemetry helps operate the service. Do not merge them into one ungoverned event table.

## Command and transition shafts

A command shaft carries an instruction to do something under authority. It may not create a new record at all. Examples include:

- submit a prepared record;
- approve, reject or return a request;
- publish or withdraw an item;
- grant or revoke access;
- send a notification;
- retry or reconcile an integration; and
- start or cancel durable work.

A command has an actor, target, authority, validation, idempotency and result contract. It may produce a state transition, an append-only fact, an external effect or a durable work item. It should not be represented as a generic update merely because the implementation eventually changes a row.

Commands may be synchronous when the caller needs a bounded result. They may be queued when the work is long-running, independently retryable, temporarily unavailable or must survive caller disconnection. Queuing changes the contract: identity, correlation, status, retry, expiry, reconciliation and operator visibility become part of the shaft.

## Relationship shafts

A relationship shaft manages an association between owned things:

- membership or affiliation;
- access grants;
- subscriptions;
- selections;
- assignments;
- dependencies; and
- links between a request and an offer, person, organisation or evidence item.

The relationship deserves its own slice when it has permissions, cardinality, effective dates, state, audit history, classification, reporting or a lifecycle of its own. Do not hide a meaningful relationship inside one side's record merely because the first screen displays it there.

A relationship shaft is often the implementation boundary for a Transient relationship between Enduring concepts. For example, `StudentAt` can preserve the enduring identity of a Person and School while recording the bounded membership, effective dates, status and authority. See [Entity Lifecycle Patterns](../../../shared/reference/catalogues/entity-lifecycle-patterns.md) before deciding whether a relationship belongs inside one entity or deserves its own capability and slice.

The contract must define who owns each end, who may create or change the relationship, how duplicates are handled, what happens when an end is retired and whether the relationship itself is historical evidence.

## Document and media shafts

A document or media shaft carries metadata and content through different physical routes. The metadata may be a normal managed record. The binary content may use secure or open storage, scoped access, scanning, versioning, retention and link expiry.

This shaft commonly includes upload or receipt, classification, validation, versioning, review, replacement, withdrawal, download and retention operations. The UI or API should not become the responsible authority for content classification or storage policy.

Keep the record that describes the content separate from the content bytes when their lifecycle, security or storage needs differ. A document may be evidence in one business slice, a public publication in another and an operational attachment in a third. The domain meaning decides the owning LDM.

## Decision and assessment shafts

An assessment shaft evaluates information against rules and records findings. A decision shaft records an authorised outcome such as recommendation, approval, rejection, escalation or deferral.

They may be separate slices when evidence, assessment and decision have different actors, permissions, separation-of-duty requirements, retention or audit obligations. A decision should identify the authority, evidence version, reason, effective date, reversibility and subsequent state change.

Do not collapse assessment facts and decision outcomes into one editable status field. A status may be useful for the current view, but it is not the complete evidence of how a consequential decision was reached.

## Integration and reconciliation shafts

An integration shaft carries information across a system boundary. It may import, export, synchronise, publish, consume or reconcile data.

The shaft normally needs an external contract version, mapping, correlation identity, idempotency key, checkpoint, quarantine path, retry policy, replay operation and reconciliation evidence. A successful network response does not always prove that the external system applied the change.

Keep the external representation, internal logical model and physical integration record distinct when their responsibilities differ. The integration record may be a slice of its own because delivery, acknowledgement and reconciliation have a lifecycle independent of the business record.

## Notification and subscription shafts

A notification shaft carries a governed message or records a recipient's subscription. It must decide who may receive what, why delivery is allowed, how sensitive information is protected and what happens when delivery fails.

The capability commonly includes subscription, preference, recipient selection, template choice, delivery attempt, retry, suppression, bounce handling and outcome history. A notification response is a command into the owning capability; it is not an edit to notification history.

Delivery is often at least once. Give the notification an identity and make handling retry-safe. Do not make a message's wording the authority boundary for a business decision.

## Identity and access shafts

Identity and access capabilities may look like record management, but their security consequences make their contracts more specific.

Examples include:

- identity profile;
- membership or affiliation;
- access grant;
- role assignment;
- permission evaluation; and
- credential or session lifecycle.

Authentication establishes who or what is acting. Authorisation decides whether that actor may perform an action on a resource in context. Audit records the accountable event. Keep these responsibilities distinct even when one user interface presents them together.

## Recognising the shaft before building it

A strong slice is clear about its own responsibility. As the design takes shape, it helps to be able to name the capability and its non-goals, the owning domain and LDM, the actors and authority, the resource, evidence and classification, the read operations and query restrictions, the commands and state transitions, the persistence or external effect, the audit, retention and recovery obligations, and the contract and tests that will prove the behaviour. Any uncertainty in that picture points to useful design work rather than a failure of the person doing it.

This also helps distinguish a slice from a horizontal flow. A candidate that mainly coordinates several independently meaningful capabilities is a flow; one that owns a capability's rules, state or external effect is a slice.

## Related guidance

- [Service System Guidance](./readme.md)
- [Data Deletion Guidance](../../../development/data-deletion-guidance.md)
- [Detailed Data Deletion Considerations](../../../development/detailed-data-deletion-considerations.md)
- [Logical Deployment Modules](./ldms.md)
- [LDM Layers and Contents](./layers.md)
- [Cross-Cutting Services](../../../development/cross-cutting-services.md)
- [Common Flows](../../../orientation/flows.md)
- [Guidance for Developers](../../../orientation/guidance-for-developers.md)
- [The Building Metaphor](../../../shared/reference/building-metaphor.md)
- [Vertical Slices](../../../../agents/conventions/capabilities/slices.md)
- [Horizontal Flows](../../../../agents/conventions/capabilities/flows.md)
