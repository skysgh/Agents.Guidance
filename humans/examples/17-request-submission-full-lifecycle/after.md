# A request submission capability is carried through its whole life

The team treats request submission and processing status as a capability with a lifecycle, not as a form and a screen. The example is illustrative: an actual service must still record its own authorities, decisions and evidence.

## Recognition and decision

The Product Manager frames the objective: applicants need a trustworthy way to submit a request and understand whether the organisation has received it and accepted it for processing. The Product Owner orders the first slice around the System LDM foundations before the next dependent interface. The business or policy authority decides the organisational meaning of each state.

The decision record names:

- affected applicants, processors, Support, Operations and connected consumers;
- the difference between `Submitted`, `Received` and `Accepted for processing`;
- constraints, risks, acceptance predicates and the condition for revisiting the decision;
- included work, deferred work, owners, triggers and temporary controls; and
- the architect's stopping point for unresolved logical or dependency questions.

The Product Owner owns priority and scope. The architect owns the logical boundary and decides whether the model is coherent enough to hand to technical design. An unresolved question returns to the responsible product, business or analysis authority instead of being hidden in implementation.

## Logical design and contracts

The architect separates applicant action, organisational receipt and processor authority. The logical model does not use a screen label, database row or provider payload as the meaning of the capability.

The contracts distinguish:

- submission and validation, including idempotency and duplicate outcomes;
- receipt acknowledgement, correlation and timeout behaviour;
- processing acceptance and permitted state transitions;
- notification delivery and failure behaviour; and
- status queries for applicants, Support and authorised internal users.

Each contract names its owner, consumers, data classification, denied paths, retry or replay rules, diagnostics and compatibility obligations. Connected systems receive a stable scenario or correlation identity, source and receiving boundary, contract version and reconciliation outcome.

## Build, test and release

The first vertical slice includes the System LDM responsibility, one dependable submission path, receipt evidence, duplicate handling, status meaning, Support information and operational signals. Deferred reporting is recorded with an owner, trigger and repayment condition.

Testers use controlled data with an explicit classification, retention period and deletion or anonymisation method. Cross-system tests preserve scenario identity across submission, receipt, notification and status query. They test delayed receipt, duplicate submission, retry, rejection, inaccessible use, notification failure, partial completion and reconciliation.

Release evidence includes:

- contract and mapping versions;
- compatibility tests for existing consumers;
- migration mapping for existing status values, if applicable;
- rollback or forward-correction limits;
- Support responses and escalation conditions;
- readiness, alerts, protected diagnostics and recovery procedures; and
- Product, business, testing, operational and relevant specialist acceptance evidence.

## Service, support and recovery

Support records the applicant's language, affected request, correlation identity, known status, classification, action taken and escalation condition. Support does not declare business meaning or perform an operational recovery outside its authority.

Operations distinguishes technical intake delay from a legitimate business state. It may retry or replay only where the recovery contract permits it. Business, product, data, records and specialist authorities decide consequential correction or reconciliation. The outcome returns to Support with a clear owner and user-facing explanation.

Security, Privacy, Records, Monitoring, Change Control and Assurance contribute bounded conditions and evidence. They do not become an unexplained approval gate, and other roles do not silently absorb their responsibilities.

## Maintenance, migration and retirement

A status definition or contract change records affected consumers, current and target versions, data mapping, compatibility behaviour, migration order, rollback limits, monitoring, Support communication and post-change verification. Existing and new paths may run together until the removal condition for the old path is met.

If the capability is replaced or retired, the service records the end state for request and status data, including retention, archive, transformation, deletion or anonymisation authority. It closes notification and status contracts, communicates with consumers and affected people, removes access, credentials, routes, queues and monitoring, and records provider and support closure. Retirement is complete only when those residual obligations have owners and evidence.

## Evidence

- Decision, logical design and contract records preserve authority and stopping points.
- Test, reconciliation and release records prove behaviour across system boundaries.
- Support, Operational and Maintenance Information preserve the live-service handoffs.
- Migration records prove compatibility, mapping, rollback or forward correction.
- Retirement records prove the disposition of data, access, dependencies, contracts and support commitments.

## What changed afterwards

The team still staged delivery, but the first visible slice carried the foundations needed to make its promise true. Later change remained possible because the meaning, authority, dependencies and evidence were explicit. The lifecycle did not become ceremony; it became a way to keep responsibility visible as the capability moved through time.
