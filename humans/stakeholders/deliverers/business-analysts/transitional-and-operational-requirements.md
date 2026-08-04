# Transitional and Operational Requirements

Transitional and operational requirements describe how a service becomes usable, remains dependable and eventually changes or retires. They are not optional project administration. They are requirements whenever the intended outcome depends on moving from the current arrangement or running the service over time.

## Transitional requirements

A transitional requirement supports movement from the current arrangement to the intended one. It may be temporary in subject, but it is still a real requirement, responsibility and deliverable.

Examples include:

- discovering, mapping, cleansing, migrating and reconciling data;
- training users, support staff, operators and maintainers;
- assisted operation for people or groups who need help during change;
- parallel running of old and new arrangements;
- staged release, pilot, rollout and communication;
- identity, access and consent transition;
- temporary reports, exports, adapters or compatibility routes;
- legacy integration and source-system retirement;
- rollback, fallback, reconciliation and recovery arrangements; and
- decommissioning, archival, disposal or anonymisation of the replaced capability.

The requirement should explain:

- what current condition is changing;
- what future condition it enables;
- who owns the transition;
- which people, systems and records are affected;
- what must be ready before the transition starts;
- what evidence proves that it is safe and complete;
- how failure, rollback or partial completion is handled; and
- when the temporary arrangement can be retired.

A migration that copies rows but does not reconcile authority, rejected records, permissions, history, reports and downstream consumers is not complete. A training plan without evidence that people can perform the changed responsibility is not complete. A temporary adapter without an owner and retirement condition is likely to become an unexamined permanent dependency.

## Why Transitional requirements are often missed

Transitional work is easy to omit because it sits between delivery and operation. It may not appear in the new screen, and the people who understand the current arrangement may not be in the build team.

Common omissions include:

- assuming that clean test data represents the condition of live records;
- treating an import as successful because the row count matches;
- forgetting historical meaning, attachments, permissions, references or reconciliation;
- assuming users will discover a changed process without training or support;
- leaving old and new systems with conflicting authority during parallel running;
- releasing a new identity or access model without handling existing accounts;
- keeping a legacy integration alive without monitoring or a retirement decision; and
- calling a known migration, fallback or decommissioning gap ÔÇ£technical debtÔÇØ without a funded repayment path.

Ask the people who operate the current arrangement what cannot be seen in the formal process description. Their workarounds and manual checks often reveal the most important transition conditions.

## Operational requirements

Operational requirements state what must be true for the service to be supported, operated, observed, secured, recovered, changed and retired. They cover the service after the first successful deployment and the conditions around every release.

They may include:

- ownership, support hours, escalation and incident responsibilities;
- readiness, health, dependency and capacity signals;
- deployment, configuration, access and secret-management procedures;
- monitoring, alerting, logs, audit records and diagnostic identity;
- backup, restore, recovery time, data-loss and continuity expectations;
- routine operations, reconciliation, correction and controlled replay;
- maintenance, patching, dependency renewal and compatibility;
- privacy, retention, deletion, anonymisation and legal-hold handling;
- support content, operational manuals and maintenance information;
- release, rollback, feature compatibility and deprecation procedures; and
- retirement, replacement, archival, disposal and exit arrangements.

An operational requirement should identify the operator or responsible boundary, the condition to maintain, the trigger or frequency, the permitted action, the evidence produced and the consequence when the condition is not met.

Weak:

> The service must be monitored.

Stronger:

> The service exposes readiness for required dependencies, records structured failures with module and capability identity, alerts the operational owner when the defined recovery threshold is at risk, and provides a runbook for restoring the affected capability without bypassing authorisation or data-protection controls.

The exact thresholds belong to the product, business, operations, security and technical authorities. The BA helps ensure that the operational need and consequence are represented early enough to shape the design.

## Transition and operation are connected

A transitional decision often creates an operational condition:

- migrated data needs reconciliation and ongoing ownership;
- a temporary compatibility route needs monitoring and retirement;
- staged access needs support and audit;
- parallel running needs a rule for authority and disagreement;
- new training needs support material and feedback; and
- decommissioning needs evidence that consumers, records and recovery paths have moved.

Trace each transition into the operational arrangements it creates. Do not hand a temporary system to operators without explaining its remaining purpose, limits, failure behaviour and end condition.

## Requirements across the service life

Ask these questions at each stage:

### Before transition

- Is the current arrangement understood, including manual workarounds and hidden dependencies?
- Are data authority, classification, retention and history clear?
- Are affected people, support, operations, security and recovery roles represented?
- What must be ready, rehearsed and evidenced before movement begins?

### During transition

- Which system or person is authoritative at each point?
- How are duplicates, rejected records, partial completion and disagreement handled?
- Can people recover from interruption without losing or duplicating work?
- Are support, communication, access and audit arrangements active?
- Who can pause, reverse or continue the transition, and on what evidence?

### During operation

- Can operators tell whether the service is ready and what has failed?
- Can support staff explain expected symptoms and safe responses?
- Can maintainers change the service without losing compatibility or evidence?
- Can the service meet backup, recovery, privacy, security, accessibility and capacity expectations?
- What evidence proves the service remains dependable under normal and degraded conditions?

### Before retirement

- Which consumers, records, reports, integrations and people still depend on the capability?
- What must be transferred, archived, anonymised or destroyed?
- How are links, credentials, certificates, scheduled jobs and support routes retired?
- What evidence shows that the replacement is authoritative and the old path is no longer required?
- Who authorises the retirement and owns residual risk?

## Handoff questions

Before transitional and operational requirements move into product ordering or architecture, ask:

- Is the current-to-future change stated clearly?
- Are temporary requirements treated as deliverables with owners and retirement conditions?
- Are migration, training, assisted operation, access transition, fallback and decommissioning considered where relevant?
- Can operators, support staff and maintainers describe what they must do and what evidence they need?
- Are readiness, incident, recovery, data protection, compatibility and maintenance expectations visible?
- Which requirements need Product Owner, business owner, records, privacy, security, operations or technical authority?
- Which manuals, information, data, content, trust, testing and evidence deliverables follow?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [BUST Requirements](./bust-requirements.md)
- [Functional and Quality Requirements](./functional-and-quality-requirements.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [Deliverables Checklist](../../reference/checklists/deliverables.md)
- [Operations Conventions](../../../agents/conventions/development/operations.md)
- [Data Deletion Guidance](../../development/data-deletion-guidance.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Guidance for System Design Architects](../../orientation/guidance-for-system-design-architects.md)
