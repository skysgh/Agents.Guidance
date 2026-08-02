# Testing Evidence and Boundaries

Testing provides evidence about whether stated behaviour and quality conditions hold under stated conditions. Testing is not merely a final inspection after development, and it is not the same responsibility as Support, Operations or Maintenance.

## The claim under examination

A useful test starts with a claim that can be examined. The claim may come from a requirement, contract, predicate, quality target, state rule, operational condition, security decision, migration rule or acceptance condition.

State:

- what subject, capability or boundary is being tested;
- which actor, resource, state and authority are involved;
- the input, context and preconditions;
- the expected result or invariant;
- the evidence produced;
- the environment and dependencies required; and
- what failure would mean for users, systems or the organisation.

A test that only repeats an implementation detail may pass while the intended meaning is wrong. A test that only checks a screen may miss the contract, persistence, security, integration or recovery boundary that makes the outcome dependable.

## Match the test to the boundary

Use the narrowest test that can prove the claim, then add broader evidence when the boundary itself needs proving:

- domain tests examine rules, identities, relationships and state transitions;
- application tests examine orchestration, validation, mapping and permission composition;
- repository and persistence tests examine query policy, classification, history, schema and recovery behaviour;
- contract and endpoint tests examine externally reachable meaning, errors, authentication and authorisation;
- dynamic tests examine a running host, deployed component or real infrastructure dependency;
- cross-system tests examine translation, ordering, duplication, reconciliation, compatibility and failure between systems; and
- exploratory and manual tests examine human journeys, accessibility, confusing states and credible combinations that scripted checks may not anticipate.

Do not call a test complete merely because the project containing it is green. The evidence must show which boundary and claim it protects.

## Test the paths people rely on

Where applicable, test:

- successful behaviour and meaningful results;
- invalid input and rejected state transitions;
- unauthenticated and forbidden access;
- missing records and conflicting updates;
- duplicate requests, retries and idempotency;
- dependency timeout, outage, quota and partial success;
- startup, readiness, shutdown and recovery;
- migration, reconciliation, rollback and compatibility;
- data classification, deletion, anonymisation and protected copies; and
- accessibility, quality in use, performance and capacity under representative conditions.

The exact set depends on the capability and its consequences. The test plan should explain what is not applicable rather than silently leaving a material condition unexamined.

## Testing and the other routes

Testing does not accept the product outcome alone. Product, business, domain, security, privacy, records, technical and operational authorities may each have a decision or evidence responsibility.

Testing does not operate the live service. Operations uses readiness, health, alerting, diagnostics and recovery procedures; Testing supplies evidence that those behaviours work under the tested conditions.

Testing does not resolve user reports. Support owns the first human conversation and case continuity; Testing may investigate a reproducible claim or recurring pattern when its evidence responsibility is engaged.

Testing does not change the occupied service to make a test pass. Maintenance Developers may investigate and change code, schema, dependencies, configuration or infrastructure under controlled authority, then Testing evaluates the resulting claim.

## Preserve evidence

A test result should identify the test or scenario version, code or contract version, environment, data or cross-system context version, relevant dependency versions, outcome, failure details and retained artefacts. Protect test data, credentials, personal information and diagnostic output according to their classification.

A failed test is information about the claim, the implementation, the test, the environment or the underlying understanding. Record enough context to distinguish those possibilities. Do not weaken the test or suppress the warning merely to obtain a green result.

## Distinct Testing deliverables

Testing contributes to the [Deliverables](../../reference/catalogues/deliverables.md) and [Deliverable Systems](../../reference/catalogues/deliverable-systems.md) required for the service. At minimum, distinguish these deliverables:

- **Test Data:** controlled data used to exercise behaviour, quality and failure paths. Prefer **cross-system test data** for scenarios that cross service, consumer, provider or other system boundaries. The canonical [Cross-System Test Context](../../reference/catalogues/deliverables.md) provides neutral scenario meaning that each participating system can translate into its own inputs and fixtures. See [Deliverable Systems](../../reference/catalogues/deliverable-systems.md#supporting-information-system-cross-system-test-context) for scenario identity, reconciliation and evidence across those boundaries.
- **Test System:** the execution and tooling environment used to qualify the service and consumer systems, including runners, hosts, browsers or devices, stubs, simulators, test identities, observability, result storage and the environments in which tests run. The Test System is not the Test Data and is not the service runtime.
- **Test Plan:** the governed description of what will be tested, why, at which boundary, under which conditions, using which Test Data and Test System, and what evidence is required. It should include automated, exploratory and manual testing where applicable. Manual testing is not an informal substitute for a Test Plan; manual testers need scenarios, preconditions, expected outcomes, risk context and a way to record evidence and observations.

These are related but not interchangeable. Test Data supplies the controlled scenario inputs, the Test System provides the qualification environment and capabilities, and the Test Plan governs scope and evidence. Test results and quality evidence are outputs of their use, not reasons to merge the three deliverables.

Testing deliverables should be reachable by Product, Business, Development, Support, Operations, Maintenance and assurance roles as appropriate. Test evidence is part of the delivered system, not a private by-product of a test run.

## Related guidance

- [Testing Guidance](./readme.md)
- [Testing Conventions](../../../agents/conventions/development/testing.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Shared Requirements](../../shared/requirements.md)
- [Support Guidance](../support/readme.md)
- [Operations Guidance](../operators/readme.md)
- [Maintenance Guidance](../maintainers/readme.md)
