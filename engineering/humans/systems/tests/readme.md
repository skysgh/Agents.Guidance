# Testing System Guidance

The objective of the Testing System is to develop and run automated quality assurance for the delivered Service and Client systems, their boundaries and their integrations with other systems. The tests give the organisation repeatable evidence that an accepted behaviour and its important quality conditions remain true as the systems change.

The browser test is green, but a person still cannot complete the task with a keyboard. A service test is green, but a duplicate submission created two provider requests. The result is not evidence that testing failed; it shows that different claims need different boundaries, conditions and kinds of evidence.

The Testing System runs within the wider Pipeline System. The pipeline protects the branches and release paths of the Service, Client, test and environment-definition codebases, then provides the environments and execution needed to qualify the delivered result. This makes automated assurance part of delivery rather than a manual inspection waiting at the end.

This route is now the human foundation for a system that the repository has not yet developed with one project's concrete environments and retained evidence. Testing is still a system boundary now: it has its own environments, data, trust assumptions, credentials, lifecycle and evidence-retention consequences.

The tests themselves are another useful distinction. A Test Suite groups tests and their supporting code around a claim, boundary, flow, risk or quality concern. The Testing System runs the suite. Test Data supplies its controlled inputs. A Test Plan explains its scope. A result or evidence record shows what happened on a particular execution.

## Why automate quality assurance

Manual testing remains valuable when exploration, human judgment, accessibility, usability or a novel situation matters. It cannot by itself provide a dependable answer every time a developer changes a contract, mapping, state rule, client flow, dependency or environment.

Automation makes the agreed evidence repeatable. It gives a developer and tester a quick way to see whether a change has preserved the acceptance criteria, and it gives maintainers a safer way to change an occupied system without relying on memory or repeating every check by hand. The value is not the number of tests. The value is maintainable change with less avoidable risk.

Automation also has limits. A test can repeat an incorrect expectation very efficiently. The acceptance criteria still need meaning, authority, representative examples and a route back when the test exposes an ambiguity.

## Work items become testable before they become buildable

A work item that names only a business concept or desired feature is incomplete. It tells the team what someone wants, but not what must be true for the result to be accepted. The work item becomes more useful when its acceptance criteria describe the outcome, actors, state, authority, data, failure behaviour and relevant quality conditions.

The handoff becomes a constructive conversation. A Subject Matter Expert explains the need, meaning, exceptions and consequence. A Business Analyst helps express that meaning clearly and keeps unresolved questions visible. The tester and relevant authorities then make the acceptance criteria and the evidence that would make them credible more explicit. A Test Developer can turn suitable criteria into automated checks, fixtures, suites or supporting test contracts, while the tester considers whether those checks represent the intended claim, boundary and risk. Developers then have a concrete target for the Service or Client behaviour, alongside the prepared design and contracts. Testing, Product, business and specialist authorities can interpret the result and decide whether the evidence supports acceptance, correction, deferral or escalation.

This ordering gives the implementation a clearer answer to “what does passing mean?” It can reduce the disagreement that arises when a story is handed to developers and testers in parallel with important meanings left unstated. The exact people may overlap, and the sequence may loop when implementation reveals a misunderstood requirement, but the acceptance meaning and executable evidence should become visible before the work is called complete.

This is not a demand for a large test project before useful learning begins. A small representative check may be enough to expose the first ambiguity. The important change is that acceptance criteria and evidence are part of the work item, not a separate promise made after coding.

## The testing-system lifecycle

The Testing System turns a claim into evidence that can be understood, repeated, challenged and returned to the responsible boundary:

```text
claim, risk and predicate
	-> test scope and scenario context
		-> environment, identity and data preparation
			-> execution across the relevant boundary
				-> result, diagnostics and evidence capture
					-> interpretation and independent challenge
						-> retained evidence and finding handoff
							-> correction, re-test and closure or escalation
```

Testing does not own product meaning or accept a business risk merely because a test passes. It makes the claim and its conditions visible, challenges the boundary and returns evidence or uncertainty to the authority that can decide it.

## What the Testing System qualifies

The Testing System can provide evidence about the service system's capabilities, data rules, state transitions, integrations, recovery and diagnostics. It can provide evidence about the client system's views, component contracts, flows, accessibility, usability, browser security and failure behaviour. It can examine the contract between client and service, including authentication, authorisation, mapping, versioning, retries and stale data. Where the release path is in scope, it can also examine the pipeline's source, artifact, environment and deployment evidence. Cross-system scenarios involving providers, messages, files, payments, notifications, reconciliation or durable work may require the same connected view.

A happy-path browser check is one observation. It does not prove server authority, accessibility, security, recovery, compatibility or quality in use.

## Test areas and suites

The Testing System may run several Test Suites against one delivered outcome. The areas remain distinct because each makes a different claim about a different boundary. A **Service system** suite can examine domain rules, application coordination, persistence behaviour, state transitions, authorisation, audit, diagnostics, failure and recovery within the service boundary. **Service interop API** tests can examine published API meaning, request and response mapping, authentication, authorisation, validation, compatibility, versioning, limits, error contracts, idempotency and safe failure for consuming systems.

Where a **Backend for Frontend (BFF)** exists, its suite can examine client-specific aggregation, shaping, orchestration, caching, session boundaries and failure behaviour. The BFF may adapt service capabilities for the client, but it does not become the authority for business rules or durable state. A **Client system** suite can examine views, component contracts, client-side flows, loading and failure states, accessibility, usability, browser security, stale assets and the way a person experiences the service.

**Data ingress and egress** tests can examine parsing, schema and business validation, classification, mapping, transformation, filtering, export, import, reconciliation, duplicate handling, error reporting and data protection as information crosses a boundary. **External-system integration** tests can examine provider and partner contracts, identity, ordering, retries, timeouts, partial success, receipts, replay, reconciliation and the meaning of what each system accepted or changed.

These areas may share a suite when the claim genuinely crosses boundaries, but a green result in one area does not prove the others. A service test cannot prove that a keyboard user can complete the journey. A client test cannot prove that an external provider applied the intended meaning. An API contract test cannot prove that an exported record is correct for the business purpose without the relevant authority and evidence.

### Data validation without claiming data truth

The Testing System can test whether a system validates data as it is designed to validate it. That includes whether it rejects malformed or unauthorised input, applies the correct business and quality rules, preserves classification, reports useful errors, maps fields correctly, handles missing or duplicate information and reconciles data with the responsible external source.

The test suite does not become the authority for whether the incoming business data is true. That responsibility belongs to the relevant business, Domain, data, policy, privacy, records or external-system authority. Tests can use known fixtures and expected outcomes to check the system's behaviour; they should not silently turn a fixture into a universal definition of reality.

The same distinction applies to data leaving the system. Tests can show that an export contains the permitted fields, correct mapping, required version, classification, recipient, delivery evidence and reconciliation behaviour. The responsible authority still decides whether the export is the right information for its purpose.

## Test data and environments

Test data has a responsible person or team, classification, purpose, version, reset or retention treatment and deletion or anonymisation decision. Production data does not belong in test environments as a convenience. Non-production environments use synthetic or explicitly governed data, with identities, media, credentials and evidence copies controlled separately.

The test environment must make its dependencies and trust assumptions visible. Browsers, devices, stubs, simulators, provider sandboxes, test identities, clocks, queues, caches and observability can all change the result. A test that passes only because an unavailable dependency was silently replaced is evidence about the substitute, not necessarily about the service.

## Evidence and findings

For a material scenario, the evidence story identifies which requirement, quality claim, contract or risk was tested, along with the versions of the client, service, provider, test code and scenario context that ran. It makes the applied identity, permissions, data classification and environment visible. It describes what each boundary received, returned, accepted, rejected, delayed, retried or applied, and connects the conclusion to its diagnostics and supporting artefacts. It also leaves uncertainty and the response responsibility visible, together with the point at which the evidence may be retained, reviewed, deleted or superseded.

An independent finding returns to the responsible product, business, architecture, client, service, security, privacy, operations or pipeline decision. Changing the expected result to make a test pass is not correction; the changed expectation needs its own authority and evidence.

## Project-specific evidence still needed

This route gives the Testing System a durable responsibility model. A real service still needs its own test plan, environments, test identities, data context, browser and device coverage, automation boundaries, accessibility tasks, security tests, performance conditions, evidence store, retention policy and failure-diagnosis route. Those project-specific decisions and records are what turn the general route into credible evidence for a particular service.

## Current entry points

The [Testing System](../../reference/catalogues/deliverable-systems.md#4-testing-system) entry describes the boundary and its relationship to the service and consumer systems. [Tester Guidance](../../stakeholders/testers/readme.md) describes the testing responsibility and its handoffs, while [Testing Evidence and Boundaries](../../stakeholders/testers/evidence-and-boundaries.md) follows test systems, test data, contracts and evidence. [Cross-system test context and reconciliation](../../reference/catalogues/deliverable-systems.md#supporting-information-system-cross-system-test-context) describes portable scenarios and evidence across systems.

A fuller project route belongs here when concrete environments, scenarios, responsible boundaries and retained evidence are known for a real service.