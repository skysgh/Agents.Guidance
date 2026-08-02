# A broad contract is replaced by responsible boundaries

The team maps each existing operation to its real consumer, Domain, LDM, authority, data classification, lifecycle and failure behaviour. It does not split the interface merely by method count. It separates relationships that have different meanings.

The replacement contracts are narrow and explicit:

- a request query contract for the browser's status view;
- an application command contract for submission and its validation or duplicate outcome;
- an approval contract owned by the approval capability for state transitions;
- a notification contract for publishing an approved event to the responsible delivery boundary; and
- an export or reporting contract with its own projection, classification and access policy.

The application and domain layer owns capability meaning. Persistence and provider adapters implement the relevant contracts. The consumer-facing layer maps its request and response shapes. Each contract states its inputs, outcomes, denied paths, retry or idempotency behaviour, diagnostics and compatibility obligations.

The team introduces the new contracts behind adapters so existing consumers can move in stages. It records which old methods map to which new boundary, adds focused and integration tests, monitors both paths during migration and removes the broad contract only after its consumers and operational evidence have moved.

The browser can now change its status presentation without changing approval or notification behaviour. A notification outage no longer changes the meaning of submission. Approval rules can evolve with their responsible authority. Export can protect fields that the browser must never receive. Tests use the smallest environment that proves each claim.

## Evidence

- Each replacement contract has a named consumer, owner, Domain or LDM and lifecycle.
- Contract tests cover valid, invalid, denied, duplicate, retry and dependency-failure outcomes at the relevant boundary.
- Consumer and provider mappings are recorded during migration.
- Telemetry shows old and new paths during the transition, with a removal condition for the old contract.
- The broad interface is removed only after compatibility, support, operational and maintenance consequences are understood.

## What changed afterwards

The team stopped treating reuse of a type as proof that the responsibilities belonged together. The replacement contracts made the real relationships visible, so a change could remain local when its meaning was local. The migration required work, but it prevented every future change from paying for the same accidental coupling.
