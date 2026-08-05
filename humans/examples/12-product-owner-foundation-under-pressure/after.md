[Up](../readme.md)

# Product pressure protects the foundation

The Product Owner starts by naming the outcome and the minimum dependable boundary. The first release may be staged, but it cannot silently promise behaviour that has no authority, test evidence, support route or recovery path.

The team separates the work into visible decisions:

- The form and status journey are the first user-facing slice.
- Duplicate submission handling and the status contract are required for the slice to be meaningful.
- Audit, authorisation, accessibility, dependency failure and recovery are required conditions for acceptance.
- Reporting for a later cohort is deferred. The deferred responsibility, affected users, owner, trigger and temporary control are recorded.
- Migration of existing records is a separate transitional deliverable with its own mapping, reconciliation and rollback evidence.
- Support receives known symptoms and supported responses. Operations receives readiness, dependency and alert information. Maintenance receives the technical design, data consequences and repair procedure.

Testing then exercises successful submission, retry, duplicate work, dependency timeout, recovery and accessible use with controlled and cross-system test data. Operations rehearses the degraded and recovery paths in the target environment. The Product Owner accepts the first slice only when the stated functional, quality, transitional, operational and evidence conditions hold.

The later reporting cohort is still real work, but it is responsible deferral rather than hidden omission. It has a work item, an owner, a trigger, a target condition and a visible effect on scope and acceptance. If the trigger is reached without capacity, the Product Owner must make a new scope decision rather than pretending the obligation disappeared.

## Evidence

- A recorded foundation and scope decision names what is included, deferred and protected.
- Contracts distinguish status meaning, duplicate handling and recovery outcomes.
- Test results cover normal, invalid, duplicate, degraded and recovered paths.
- Support, Operational and Maintenance Manuals or Information are reachable and versioned.
- Migration and reporting work have separate owners, conditions and evidence.
- The deferred work has a repayment path; the shipped slice does not transfer an unacknowledged known cost to future users or teams.

## What changed afterwards

The Product Owner changed the release conversation from "Can we show the screen?" to "What can we responsibly promise, and what must exist for that promise to hold?" The team could still stage delivery, but the cost, authority, evidence and future work remained visible. That preserved speed without turning omission into a permanent obligation for someone else.
