# Repository Assessment Implementation Plan

## Purpose

This plan turns the 2026 repository assessment into a controlled implementation record. It separates improvements that belong in the current guidance experience from larger capability areas that need their own evidence, examples and review.

## Definition of Done

This implementation cycle is complete when:

- the repository root introduces the human guidance without making the reader pass through audit material;
- human-facing entry pages explain the value of destinations without imposing a reading order;
- agent-facing conventions retain conditional routing where an agent must apply a rule;
- the navigation and imperative-language scan has been repeated and its remaining matches are classified;
- the assessment and documentation register describe the resulting state honestly;
- all relative Markdown links resolve, the diff has no whitespace errors, and the changes are committed and pushed.

## Work Items

### 1. Improve the repository entry point

- [x] Replace the audit-first root opening with a welcoming explanation of the guidance.
- [x] Give human readers a clear route to the human guidance.
- [x] Keep audit evidence available as supporting material rather than the first destination.
- [x] Keep agent readers able to reach the agent conventions.

### 2. Preserve choice in human navigation

- [x] Remove ordered-reading commands from human entry pages.
- [x] Replace introductory "Start with", "Read in this order" and similar gates with reasons and optional routes.
- [x] Keep imperative language where it expresses a technical rule, design warning, checklist prompt or agent convention.
- [x] Re-scan for sequencing language and classify any remaining matches.

### 3. Record the implementation boundary

- [x] Record the completed entry and tone work in the documentation register.
- [x] Keep the assessment's substantive operations, security, governance, evidence, performance and cross-system gaps visible for a later capability-focused implementation cycle.
- [x] Do not claim that navigation improvements make the corpus production-complete for regulated systems.

## Deferred Capability Backlog

The assessment identifies these substantive areas that require dedicated design and evidence rather than superficial additions to this cycle:

1. Operations depth: observability contracts, runbooks, failure modes, readiness, capacity, degradation and recovery evidence.
2. Access control: authorization models, delegation, cross-system authorization, credential lifecycle and negative-path testing.
3. Security architecture: threat modelling, cryptographic and certificate lifecycle, secrets, security testing and dependency supply chain controls.
4. Governance: decision authority, quality gates, escalation, release/change control and conflict resolution.
5. Evidence and verification: claim-to-evidence strategies, audit verification, compliance testing and evidence preservation.
6. Cross-system coordination: versioning, deployment coordination, contract testing, consistency, tracing and failure propagation.
7. Performance and cost: load and soak testing, cost modelling, degradation thresholds and operational measurement.
8. Schema and migration safety: physical evolution, compatibility, zero-downtime migration and historical data handling.
9. Diagnostic contracts: health, readiness, correlation, metrics, alerting and structured logging without sensitive leakage.
10. Discovery: problem-to-example indexing, specialist routes and a decision-record format.

These remain explicit backlog items. They are not marked complete by the entry-point and tone work above.

## Validation Record

- Markdown relative links: passed repository-wide validation after edits.
- Formatting: passed `git diff --check`.
- Tone scan: human-facing reading gates are removed; remaining matches are ordinary explanatory prose, technical advice, or the style register describing the rule.
- Publication: this completed implementation slice is being committed and pushed now.