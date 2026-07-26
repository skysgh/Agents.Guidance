# Horizontal Flows

Read this document only when a task coordinates multiple capabilities, actors, decisions or stateful steps into one outcome.

A horizontal flow is an outcome-oriented path that coordinates multiple vertical slices. It describes how actors, information, decisions and state changes move through the system. A flow is not a replacement for the slices that implement its steps.

## How to recognise a flow pattern

A candidate is a flow pattern when that coordination shape recurs: it coordinates two or more independently meaningful capabilities, or its outcome depends on ordering, decisions, hand-offs, compensation, waiting or multiple actors. The flow owns orchestration policy and outcome criteria. The participating slices retain their own validation, state transitions, permissions and data ownership.

Do not create a flow for a single resource CRUD operation. Do not make a slice responsible for a journey merely because it starts or ends there.

Use the same recurrence test as for slice patterns. Compare real journeys, identify the stable orchestration invariant, and abstract only what remains true across them. Recursive composition is legitimate when a flow contains subflows or when a slice invoked by the flow has its own internal lifecycle, but the boundary and ownership must remain visible.

## Common flow families

These are common outcome patterns. They are not a fixed acronym and they do not all belong in every product.

### Discover and select

Find, compare, qualify and choose one or more available items.

Typical slices: catalogue, search projection, eligibility, selection or request, identity and access.

Implementation: define the discovery snapshot and eligibility authority. Keep search projections queryable but non-authoritative. Recheck suitability and availability when the selection is committed. Make duplicate selection and withdrawal explicit.

### Prepare and submit

Gather information, validate completeness and commit a formal submission for consideration.

Typical slices: managed item, identity/profile, document/evidence, submission and notification.

Implementation: distinguish draft from submitted state. Define who may prepare, who may submit, what is frozen at submission, what can be corrected, and how resubmission is versioned. Use an idempotency key for retryable submission commands.

### Assess and decide

Review a submission or evidence set, request clarification, recommend, escalate, approve, reject or defer.

Typical slices: submission, evidence, assessment, decision, access grant and audit.

Implementation: capture the evidence version and decision authority. Enforce separation of duties where required. Model clarification and appeal paths. Record reasons and immutable decision history; do not overwrite an earlier decision to simulate correction.

### Publish and maintain

Prepare an item, make it discoverable, manage changes, supersede or withdraw it, and keep its public representation accurate.

Typical slices: managed item, catalogue, media/document, search projection, notification and audit.

Implementation: separate draft, published and withdrawn representations. Define publication validation, effective dates, cache or projection invalidation, rollback and supersession. A published item must not change invisibly beneath a consumer's recorded selection.

### Onboard and establish participation

Identify a person or organisation, collect required information, establish membership or affiliation, grant initial access and confirm readiness.

Typical slices: identity profile, membership, access grant, evidence, notification and audit.

Implementation: make prerequisites and consent explicit. Separate identity proofing from authorisation. Make invitations, expiry, rejection, withdrawal and partial completion recoverable. Do not grant broad access as a side effect of creating a profile.

### Provision and fulfil

Turn an approved request or order into an allocated resource, service, entitlement or delivered outcome.

Typical slices: decision, request, allocation, managed item, integration and notification.

Implementation: define reservation, allocation, fulfilment, partial fulfilment, cancellation and compensation. Use an orchestration record or durable state machine when the process can pause or retry. Make external side effects idempotent and reconcile uncertain outcomes.

### Change, renew and close

Manage a live relationship, entitlement, contract or case through renewal, amendment, suspension, expiry and closure.

Typical slices: managed item, relationship, access grant, notification, audit and billing or integration where applicable.

Implementation: define effective dates and the source of truth for time. Separate an amendment from an overwrite when history matters. Schedule reminders from durable state, handle missed timers, and make closure safe to retry.

### Import, synchronise and reconcile

Receive or send data across a boundary, map it, apply accepted changes, detect conflicts and reconcile differences.

Typical slices: import/export, integration endpoint, managed resource, audit and notification.

Implementation: version the external contract and mapping. Validate before mutation, quarantine bad records, checkpoint progress, use idempotency and correlation, and provide replay and reconciliation reports. Never assume a successful network response proves the external state was applied.

### Report and export

Assemble an authorised view or extract for a person, organisation, regulator, operator or downstream system.

Typical slices: search projection, audit, data protection, export and notification.

Implementation: define the point-in-time meaning, classification, row and file limits, redaction, authorisation, expiry and delivery channel. Avoid using an export as an ungoverned second database. Record who requested it, what scope was used and whether delivery succeeded.

### Notify and respond

Detect an event, select recipients, deliver a message, accept a response and update the owning capability.

Typical slices: notification/subscription, managed resource, access grant and audit.

Implementation: keep delivery at-least-once and deduplicate with a notification identity. Treat a response as a command into the owning slice, not as an edit to notification history. Define opt-out, quiet hours, escalation, bounce and sensitive-content rules.

### Detect, contain and recover

Detect an incident, restrict impact, investigate, restore service or data, and record follow-up actions.

Typical slices: monitoring/alert, access grant, audit, managed resource, integration and notification.

Implementation: define authority to contain, evidence preservation, safe-mode behaviour, recovery checkpoints, communication and post-incident actions. Keep operational recovery state separate from the business record unless the business itself owns the incident.

## Implementing a flow

Use this sequence for a new flow:

1. State the outcome, trigger, completion condition and non-goals.
2. Draw the participating slices and name the owner of every decision, record and external effect.
3. Define the flow state: current step, correlation identity, retry count, deadlines, cancellation and compensation state.
4. Define commands and events between slices. Pass stable identifiers and versioned facts rather than shared mutable objects.
5. Define transaction boundaries. Use one transaction only where ownership and infrastructure make it valid; otherwise use durable orchestration, idempotency and reconciliation.
6. Define permissions, separation of duties, audit events, notifications and data classification at each hand-off.
7. Define waiting, clarification, timeout, retry, rejection, cancellation, partial success and recovery paths before implementing the happy path.
8. Implement orchestration that invokes slice contracts. Do not duplicate slice rules in the coordinator.
9. Test the complete outcome, each hand-off, restart/resume, duplicate delivery, timeout, compensation and failure recovery.
10. Monitor flow duration, stuck instances, retries, failures and manual interventions in production.

## Flow record

Document each adopted flow with:

1. outcome, trigger, completion condition and non-goals;
2. actors, permissions and separation-of-duty rules;
3. slices consumed and the versioned data passed between them;
4. read models, query boundaries and presentation needs;
5. commands, transitions and transaction boundaries;
6. flow state, deadlines, clarification, retry, cancellation and compensation paths;
7. audit, notification and integration effects; and
8. completion, failure, recovery, monitoring and operator intervention criteria.

Flows should reuse slices without duplicating their rules. If a flow needs a special rule, place it at the owning slice or domain boundary and document why the flow-specific policy exists.

Further reading: [BPMN 2.0.2 specification](https://www.omg.org/spec/BPMN/2.0.2/), [Microsoft, saga distributed transactions pattern](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga), and [Martin Fowler, Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html).

## Flow record

Document each adopted flow with:

1. outcome and triggering event;
2. actors, permissions and separation-of-duty rules;
3. slices consumed and the data passed between them;
4. read models, query boundaries and presentation needs;
5. commands, transitions and transaction boundaries;
6. validation, clarification, retry and cancellation paths;
7. audit, notification and integration effects; and
8. completion, failure and recovery criteria.

Flows should be allowed to reuse a slice without duplicating its rules. If a flow needs a special rule, place the rule at the owning slice or domain boundary and document why the flow-specific policy exists.
