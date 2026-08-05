[Up](./readme.md)

# Deliverable Systems


A deliverable system is a system that must be produced, operated or used to make the intended service outcome possible. It has its own execution environment, boundary, dependencies, identity, lifecycle and failure behaviour.

The team may deliver several systems as one product experience. That does not make them one system. Shared ownership, a shared repository or a shared release train does not remove the boundaries between their execution environments or responsibilities.

The [System Perspectives](../../../deliverables/systems/readme.md) provides the corresponding reader entry routes. It does not replace this catalogue or imply that every system perspective has equal implementation depth.

A codebase can itself be a system when it has a distinct purpose, owner, lifecycle, boundary, dependencies and evidence. The codebase that defines an environment is therefore not merely a file beside the pipeline. It is a named delivery constituent that the pipeline executes or applies. The resulting environment is a separate execution context and is not the same thing as its definition code.

## Relationship to deliverables

[Deliverables](./deliverables.md) names the wider things that must exist around these systems: data, content, registrations, discovery, dependencies, operational material and evidence. The [Deliverables Checklist](../checklists/deliverables.md) turns both views into review prompts. Use all three together: systems describe distinct execution and information boundaries; deliverables describe what must be produced, configured, published or maintained across those boundaries.

## The primary deliverable systems

### 1. Delivery system

The delivery system compiles, qualifies, packages, promotes and deploys the other deliverables. It may include source control, build agents, static analysis, security scanning, test execution, artifact and package registries, infrastructure automation, approval controls and deployment pipelines.

The delivery system is not the service runtime. It may be needed to release, repair, secure, recover or decommission the service without receiving the service's normal user requests.

Its design must define source and artifact provenance, identity and permissions, environment separation, secret handling, approvals, evidence, rollback, recovery and what can happen when the pipeline is unavailable or compromised.

### Delivery system constituents

The delivery system is often composed of several related systems. They may share a repository or team, but their responsibilities remain distinguishable:

- **Pipeline Definition System:** the versioned codebase that defines delivery flows, triggers, gates, approvals, runner selection, inputs, outputs and evidence handling.
- **Pipeline Execution System:** the runners, agents, orchestrators, credentials, logs and control services that execute the pipeline definitions. This is the system that performs the work; it is not the flow definition itself.
- **Environment Definition System:** the versioned codebase that defines desired environments, infrastructure resources, networks, identities, policies, configuration scaffolding and deployment targets. It may use ARM/Bicep, CloudFormation, Terraform or another infrastructure language.

The Pipeline Execution System runs the Pipeline Definition System and applies the Environment Definition System. It may also build, test, package and deploy the service, client and testing codebases. The actual development, test, business-test, production or recovery environment is the resulting execution context, not another name for the codebase that defines it.

Deployment definitions may belong to the Environment Definition System, the Service or Client codebase, or a separate codebase when their owner, lifecycle and evidence genuinely differ. The classification follows responsibility rather than a preferred repository layout.

### 2. Service system

The service system is the server-side system that owns and enforces the service capabilities. It normally includes the service runtime, application and domain behaviour, interfaces, persistence and external integrations required to serve requests or process durable work.

It has its own execution environment, such as a server process, container or managed runtime. It owns service-side authorisation, data rules, state transitions, diagnostics, operational behaviour and recovery responsibilities.

The service system is not the delivery system, the consumer system or the testing system. The System LDM is an application-owned logical structure inside the service system; it is not a name for the whole set of systems delivered around the service.

### 3. Service consumer system

The service consumer system is the browser-side or client-side system through which a consumer reaches the service. For a single-page application, it includes the SPA assets, browser execution, client-side state, views, interaction flows and calls to the service interfaces.

The [Front-end Developer Guidance](../../../stakeholders/deliverers/developers/front-end.md) follows the responsibility for building this consumer system, including its client-side flow, component assemblies, accessibility, usability and browser security.

The consumer system runs in a distinct execution environment from the service system. A browser has different memory, storage, trust, update, network and failure properties from a server runtime. The service must therefore enforce its own security and authorisation rather than trusting the SPA to do so.

The same team may deliver both the service system and the consumer system, and they may be released together. They are still distinct systems with distinct boundaries, deployments, failure modes and security responsibilities. They are not one system merely because they form one user experience, and neither is the System LDM.

### 4. Testing system

The testing system is the system used to qualify the service system and the service consumer system. It is operated by the delivery system or by an associated controlled process, but it is not merely a collection of test files.

It may include test runners, static and dynamic test hosts, browsers, devices, test environments, stubs, simulators, seeded data, reference data, test identities, observability and result storage. Its execution environment and trust assumptions must be understood because test systems can access real interfaces, data and credentials if they are poorly isolated.

The testing system must prove the required behaviour and qualities of both the service and its consumer. It should test the contract between them as well as each system's own behaviour. Its Test Suites, Test Plans, Test Data and retained evidence are separate deliverables within the testing work. Test evidence is a deliverable, not only an activity that disappears when the pipeline finishes.

## Supporting information system: cross-system test context

The cross-system test context system is a shared information system that supplies portable context to the testing system. It is not test data owned by one service and it is not the testing system itself. Its purpose is to let several systems be tested together using the same meaningful people, organisations, institutions, relationships, states, events and scenarios.

For example, it may define a neutral person, student, university, course, application, assessment or payment context. The service system, consumer system and provider systems can each translate that context into their own input, storage or API representation while preserving the identity and relationships needed for the scenario. The neutral context is the shared test meaning; each system-specific fixture is a generated representation of it.

This system should be portable across environments and projects. It should not require one application's schema, database, API or vendor model to be authoritative. Its model needs stable identifiers, relationships, lifecycle states, scenario composition, expected outcomes, versioning and provenance. Translators or adapters then turn the neutral context into system-specific seeds, requests, messages, files or provider setup.

The cross-system test context system is a deliverable to which multiple projects contribute. Contributions need ownership, review, compatibility rules, change history, deprecation, scenario coverage and a process for resolving conflicting meanings. A project must not privately fork the shared context merely because its local representation is different.

Production data must not leave production environments. Generate synthetic context for non-production environments. If an exceptional need requires a separately governed transformation, the resulting dataset must be formally approved as a new non-production dataset with its own minimisation, de-identification, access, retention, deletion and audit evidence; it must not be treated as a casual copy of production. Test, development, integration, qualification and recovery environments receive only synthetic or explicitly approved non-production data, with credentials, media and personal information controlled separately.

### Cross-system evidence and reconciliation

A cross-system test is not complete because one request received a successful network response. The scenario must carry enough identity and evidence to show what each boundary received, accepted, rejected, delayed, retried, replayed or applied, and whether the resulting states agree.

For each material scenario, preserve:

- a stable scenario and correlation identity;
- the source and receiving boundary, including which system is authoritative for each fact;
- the versioned context and translated representations used in each system;
- the request, acknowledgement, receipt, processing and outcome evidence;
- duplicate, timeout, retry, replay, quarantine and reconciliation results;
- the owner and condition for resolving any mismatch; and
- the classification, retention, deletion and reset treatment for the test data and its evidence copies.

The testing system produces qualification evidence, while the participating service, consumer and provider boundaries remain responsible for their own contracts and behaviour. Reconciliation evidence belongs with the scenario rather than disappearing into a test-run summary. When a mismatch is found, return it to the owning contract, logical model, integration mapping, operational procedure or data-lifecycle decision. Do not hide it by changing the expected result after the fact.

## System relationships

```text
                         operates
Delivery System ------------------------------+
      |                                         |
      | qualifies, packages and deploys         v
      +------------------------------> Service System
      |                                         ^
      | qualifies and publishes                  |
      +---------------------> Consumer System --+
      |
      +---------------------> Testing System
                                  |
                                  +-- tests Service System
                                  +-- tests Consumer System
Cross-System Test Context System -- generates inputs for Testing System
```

The diagram is a responsibility map, not a required topology. A pipeline may run tests in several environments, and a consumer may be deployed through a different hosting mechanism from the service. The cross-system context system may be versioned and published separately from the testing system. The important point is to keep the boundaries and relationships visible.

## Minimum description

For each deliverable system, record:

- its purpose and intended consumers;
- its execution environment and deployment boundary;
- its owner, operators and support route;
- its interfaces and dependencies;
- its data, credentials and classification;
- its availability, failure and recovery behaviour;
- its qualification and acceptance evidence;
- its release, versioning and compatibility relationship with the other systems; and
- its maintenance and decommissioning conditions.

For the cross-system test context system, also record the neutral model, contributing projects, translators, generated representations, scenario identifiers, data classification, reset process and the rule that prevents production data from entering non-production environments.

These systems are one part of the wider delivery picture. [Deliverables](../../../deliverables/readme.md) explains how they join with people, responsibilities, material and evidence to make an outcome usable and supportable. From here, [Deliverables](./deliverables.md) covers the wider things produced around the systems, while [External Dependencies](./external-dependencies.md) covers boundaries the systems rely on rather than contain.
