# Testing Evidence and Boundaries

Testing provides evidence about whether stated behaviour and quality conditions hold under stated conditions. Testing is not merely a final inspection after development, and it is not the same responsibility as Support, Operations or Maintenance.

## The claim under examination

A useful test starts with a claim that can be examined. The claim may come from a requirement, contract, predicate, quality target, state rule, operational condition, security decision, migration rule or acceptance condition.

For a new work item, the acceptance criteria are a natural starting point. The tester helps clarify whether each criterion is meaningful, observable and assigned to the right boundary. The Test Developer can then shape the repeatable criteria into a Test Suite, while exploratory or manual testing remains available for human judgment and novel risk.

The claim becomes useful when its subject, capability or boundary is recognisable, along with the actor, resource, state and authority involved. Its input, context and preconditions need enough shape for another person to understand the scenario. The expected result or invariant, the evidence that would support it, and the environment and dependencies required to produce that evidence belong to the same account. So does the consequence of failure: the effect on users, systems or the organisation gives the claim its priority and helps determine how much evidence is appropriate. The [deliverables checklist](../../reference/checklists/deliverables.md) provides a more formal completeness check for the surrounding testing deliverables.

A test that only repeats an implementation detail may pass while the intended meaning is wrong. A test that only checks a screen may miss the contract, persistence, security, integration or recovery boundary that makes the outcome dependable. The automated check is evidence of a prepared claim, not a substitute for the authority that gave the claim meaning.

## Match the test to the boundary

The narrowest test that can prove a claim usually gives the clearest evidence, while broader evidence becomes important when the boundary itself is part of the claim. Domain tests can examine rules, identities, relationships and state transitions. Application tests can examine orchestration, validation, mapping and permission composition. Repository and persistence tests can examine query policy, classification, history, schema and recovery behaviour. Contract and endpoint tests can examine externally reachable meaning, errors, authentication and authorisation.

The same reasoning extends across system boundaries. Service interop API tests can examine published meaning, compatibility, mapping, validation, limits, idempotency and safe failure for consuming systems. Where a Backend for Frontend exists, its tests can examine client-specific aggregation, shaping, session boundaries and failure behaviour without making the BFF the authority for business rules. Dynamic tests can examine a running host, deployed component or real infrastructure dependency. Cross-system tests can examine translation, ordering, duplication, reconciliation, compatibility and failure between systems. Exploratory and manual testing remains important for human journeys, accessibility, confusing states and credible combinations that scripted checks may not anticipate.

A green project is therefore only one piece of evidence. The result becomes meaningful when it shows which claim and boundary it protects, under which conditions, and what remains outside its reach.

## Test the paths people rely on

The paths people rely on often include more than successful behaviour and meaningful results. Depending on the capability and its consequences, evidence may need to cover invalid input, rejected state transitions, unauthenticated and forbidden access, missing records, conflicting updates, duplicate requests, retries, idempotency, dependency timeouts, outages, quotas, partial success, startup, readiness, shutdown and recovery. Migration, reconciliation, rollback, compatibility, data classification, deletion, anonymisation, protected copies, accessibility, quality in use, performance and representative capacity can matter just as much.

The exact set depends on the capability and its consequences. A test plan gives the reasoning for what is in scope and explains what is not applicable, rather than silently leaving a material condition unexamined.

Data tests can show that a boundary parses, validates, classifies, maps, transforms, filters, rejects, accepts, exports or reconciles information as intended. They do not make the Test Suite the authority for the truth of the incoming business data. That truth comes from the responsible business, Domain, data, policy, privacy, records or external-system authority. The test supplies a known scenario and checks the system's behaviour against the agreed predicate.

## Testing and the other routes

Testing does not accept the product outcome alone. Product, business, domain, security, privacy, records, technical and operational authorities may each have a decision or evidence responsibility.

Testing does not operate the live service. Operations uses readiness, health, alerting, diagnostics and recovery procedures; Testing supplies evidence that those behaviours work under the tested conditions.

Testing does not resolve user reports. Support owns the first human conversation and case continuity; Testing may investigate a reproducible claim or recurring pattern when its evidence responsibility is engaged.

Testing does not change the occupied service to make a test pass. Maintenance Developers may investigate and change code, schema, dependencies, configuration or infrastructure under controlled authority, then Testing evaluates the resulting claim.

## Preserve evidence

A test result should identify the test or scenario version, code or contract version, environment, data or cross-system context version, relevant dependency versions, outcome, failure details and retained artefacts. Test data, credentials, personal information and diagnostic output belong under the handling rules for their classification.

A failed test is information about the claim, the implementation, the test, the environment or the underlying understanding. Its surrounding context needs to be rich enough to distinguish those possibilities. A weakened test or suppressed warning may produce a green result, but it no longer gives dependable evidence.

## Distinct Testing deliverables

Testing contributes to the [Deliverables](../../reference/catalogues/deliverables.md) and [Deliverable Systems](../../reference/catalogues/deliverable-systems.md) required for the service. Three distinctions are especially useful. **Test Data** is controlled data used to exercise behaviour, quality and failure paths. Cross-system test data is valuable when a scenario crosses service, consumer, provider or other system boundaries. The canonical [Cross-System Test Context](../../reference/catalogues/deliverables.md) provides neutral scenario meaning that each participating system can translate into its own inputs and fixtures, while [Deliverable Systems](../../reference/catalogues/deliverable-systems.md#supporting-information-system-cross-system-test-context) explains how scenario identity, reconciliation and evidence remain visible across those boundaries.

The **Test System** is the execution and tooling environment used to qualify the service and consumer systems. It includes runners, hosts, browsers or devices, stubs, simulators, test identities, observability, result storage and the environments in which tests run. It is distinct from both Test Data and the service runtime.

The **Test Plan** is the governed account of what will be tested, why it matters, which boundary and conditions apply, which Test Data and Test System are involved, and what evidence is required. Automated, exploratory and manual testing can all belong within that account. Manual testing is therefore not an informal substitute for planning: its scenarios, preconditions, expected outcomes, risk context and observations remain part of the evidence story.

### Test Suite

A **Test Suite** is a coherent set of test cases and supporting test code organised around a claim, boundary, flow, risk or quality concern. It may contain fixtures, scenario setup, generators, helpers, assertions, tags, cleanup and evidence expectations. A test codebase may contain several suites, and one suite may run in several environments.

A Test Suite is not the Test System that runs it, the Test Data it uses or the Test Plan that explains why and when it is in scope. It is also not the result produced after execution. Keeping those distinctions visible helps a tester explain whether a failure belongs to the test, the data, the environment, the implementation or the original claim.

These are related but not interchangeable. Test Data supplies the controlled scenario inputs, the Test System provides the qualification environment and capabilities, the Test Plan governs scope and evidence, and the Test Suite organises the repeatable or exploratory tests that exercise the selected claims. Test results and quality evidence are outputs of their use, not reasons to merge the four deliverables.

The resulting testing deliverables need to remain reachable by Product, Business, Development, Support, Operations, Maintenance and assurance roles as appropriate. Test evidence is part of the delivered system, not a private by-product of a test run.

## Related guidance

The [Testing Guidance](./readme.md) gives the wider route, while [Testing Conventions](../../../agents/conventions/development/testing.md) describes the development practice. The [Deliverables](../../reference/catalogues/deliverables.md) and [Deliverable Systems](../../reference/catalogues/deliverable-systems.md) catalogues place these testing contributions in the delivered whole. [Shared Requirements](../../shared/requirements.md) connects acceptance meaning to evidence. The neighbouring [Support Guidance](../support/readme.md), [Operations Guidance](../operators/readme.md) and [Maintenance Guidance](../maintainers/readme.md) describe the responsibilities that meet testing evidence after or alongside execution.
