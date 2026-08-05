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

## Delivery Perspective Increment

This increment creates an explanatory delivery perspective without moving or duplicating the existing reference catalogues.

- [x] Add `engineering/humans/deliverables/readme.md` as the narrative entry for system delivery.
- [x] Explain how delivery differs from development and how software becomes usable, operable, supportable and maintainable.
- [x] Connect the delivery perspective to deliverable systems, deliverables, registries, lifecycle, stakeholder responsibilities, assurance and enduring-value structures.
- [x] Link the perspective from the engineering and human entry pages and record the new route in the documentation register.
- [x] Validate links, formatting and the choice-preserving tone.

## Cold-Start Welcome Increment

This increment makes the first contact useful before asking a reader to absorb the full guidance map. It keeps the assessment honest about the difference between a strong foundation and production-complete serious-system guidance.

- [x] Give the repository root a short explanation of purpose, scope and the current limits of the material.
- [x] Offer practical question-based routes without imposing a reading order.
- [x] Keep the detailed engineering perspectives and distinct Quality, Assurance and Operating routes available after the first orientation.
- [x] Reframe the repository assessment as an evidence-based scope statement rather than an unsupported comparative verdict.
- [x] Re-test cold-start journeys with a developer, Product Owner, operator and a reader who only knows the assessment's substantive gap list.
- [x] Remove the remaining optional reading-sequence wording from the orientation index and add a short explanation of the assessment's status labels and reader routes.
- [x] Review the opening of the human root, engineering, orientation, delivery, stakeholder, role, development, example, reference, catalogue and checklist indexes; add the story-led bridge and correct the Development index's early catalogue/checklist drop.
- [x] Rework the Client, Service, Shared, Pipeline and Testing system routes and their core catalogues so recognisable situations and contribution come before terminology, prompts or imperative language.

## Sponsor Perspective Increment

This increment gives the Sponsor a decision-focused route for holding the organisational commitment to account without duplicating Product Manager, Product Owner or specialist authority.

- [x] Add Sponsor guidance covering purpose, constraints, whole-life value and cost, relevant qualities, focused interaction, bounded self-correction and internal specialist groups.
- [x] Explain the comparison between promise, actual delivery, evidence, variance, owner and escalation.
- [x] Connect Sponsor handoffs to Product Management, Product Ownership, business meaning, architecture, implementation, testing, operation, support, maintenance and specialist controls.
- [x] Link the route from stakeholder navigation and Product Manager guidance.
- [x] Perform the initial Sponsor cold-start and lifecycle review; retain the broader all-perspectives cold-start review as follow-up.

## Front-end Developer Perspective Increment

This increment recognises the browser SPA as a distinct service consumer system and gives the developer responsible for it a human route into its flows, component assemblies and quality responsibilities.

- [x] Add Front-end Developer to the glossary and the stakeholder developer-family catalogue.
- [x] Add a focused Front-end Developer route covering the consumer system, client-side horizontal flows, component assemblies, accessibility, usability and browser security.
- [x] Explain the boundary between client-side experience coordination and server-side authority for capabilities, authorisation, durable state and audit.
- [x] Link the route from the developer, stakeholder, engineering and story-led entry pages.
- [x] Add a worked SPA consumer-system example and perform the initial complete Front-end Developer route check; broader reader usability and project-specific evidence remain open.

## Human Systems Boundary Migration Increment

This increment introduces system-oriented human routes without claiming that the client, service, pipeline or testing systems have equal documentation depth.

- [x] Add the controlled [Human Systems Boundary Migration Plan](SYSTEMS-BOUNDARY-MIGRATION-PLAN.md).
- [x] Add client, service, pipeline, testing and shared system indexes.
- [x] Move the client Palette into a canonical client-system first-look page, UX palette catalogue and implementation-vocabulary page.
- [x] Leave compatibility routes at the former Palette paths and converge agent, glossary, orientation and entry-point links on the new client authority.
- [x] Mark current Development material as staged service/shared migration content rather than moving mixed pages by filename alone.
- [x] Migrate the coherent Service implementation group of LDMs, layers, System LDM services and vertical slices, with compatibility routes at the former paths.
- [x] Migrate the coherent Shared group of Contracts and Common Flows, with compatibility routes at the former paths.
- [x] Migrate the remaining lifecycle, quality, model and data-protection material into Shared System Concerns after confirming its consumers and authority, with compatibility routes at the former paths.
- [x] Develop substantive Pipeline and Testing System foundation routes covering lifecycle, ownership, security, environments, qualification and evidence; project-specific routes and evidence remain open.

## Pipeline Developer Language Increment

This increment gives Pipeline Developers a human entry into infrastructure languages and imperative orchestration without confusing them with service-side application languages.

- [x] Explain declarative infrastructure, typed infrastructure frameworks and imperative PowerShell or Bash orchestration.
- [x] Cover Azure ARM/Bicep, AWS CloudFormation and AWS CDK, including the distinction between AWS CDK's TypeScript implementation and its supported authoring languages.
- [x] Connect pipeline language choice to provenance, permissions, secrets, repeatability, preview, rollback, recovery and evidence.
- [x] Link the route from Pipeline System Guidance, language selection, the developer-family catalogue and agent development conventions.
- [x] Add a provider-neutral learning path for Azure, AWS, Terraform, Linux/Bash and PowerShell so an Azure-focused contributor can enter unfamiliar pipeline platforms through shared concepts first.
- [x] Reorder the Pipeline Developer route so Delivery, Restoration, Fail-over Switching, Rollback and Environment Rebuild objectives and technology-neutral steps precede provider and language detail; leave the later flow-depth work explicitly noted in the page.
- [x] Correct the Deliverables catalogue and checklist so pipeline definitions, environment definitions, service/client/test codebases, pipeline execution, resulting environments and their baselines are distinct deliverables and systems.
- [x] Separate the Delivery Guidance delivered-whole list into distinct systems, codebases, environments, data, branding, media/accessibility, reachability, interfaces, optional event/message flows, operations and decisions; remove the ambiguous data-contract grouping.
- [x] Distinguish Test Suites from the Testing System, Test Data, Test Plan and execution evidence in the tester route, glossary, Deliverables catalogue and Deliverables Checklist.
- [x] Define the Testing System's separate test areas for service behaviour, service interop APIs, BFF behaviour, client experience, data ingress/egress and external-system integration, including the boundary between testing data validation behaviour and deciding data truth.
- [x] Reframe Testing System guidance around automated quality assurance of the delivered Service and Client systems within the Pipeline System, with acceptance criteria and Test Suites becoming part of the work item before implementation evidence.
- [x] Connect the work-item handoff from SME and Business Analyst meaning, through tester acceptance criteria and Test Developer automation, to Service or Client implementation and iterative interpretation.
- [x] Add Pipeline protection of code branches, quality checks, identifiable artifacts and controlled promotion without making the Pipeline the acceptance authority.

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
11. Project-specific consumer-system depth: real SPA component contracts, client/server horizontal-flow evidence, WCAG task evidence, browser security testing and consumer-system release or cache behaviour.

These remain explicit backlog items. They are not marked complete by the entry-point and tone work above.

## Validation Record

- Markdown relative links: passed repository-wide validation after edits.
- Formatting: passed `git diff --check`.
- Tone scan: human-facing reading gates are removed; remaining matches are ordinary explanatory prose, technical advice, or the style register describing the rule.
- Cold-start review: root, developer, Product Owner, operator and assessment-led routes each have a usable first destination; the orientation index no longer presents a reading progression as an option to follow in order.
- Opening-level perspective review: story-led bridge added; narrative and role routes reviewed for explanation before tools; catalogue and checklist indexes remain intentionally direct reference surfaces; full reader usability and worked SPA example remain open.
- Systems boundary migration: client Palette, Service implementation guidance and Shared Contracts, Flows, lifecycle, model, data-protection and availability guidance now have canonical system locations with compatibility routes; Pipeline and Testing foundation routes are established.
- Systems foundation routes: worked SPA example added; Pipeline and Testing foundation routes explain lifecycle, ownership, security, environments, qualification and evidence; project-specific pipeline/testing/consumer evidence remains open.
- System-route cold-start review: Client, Service, Pipeline, Testing and Shared routes checked for boundary clarity, next destination, story/tool ordering and honest stopping points; project-specific usability and evidence remain open.
- Voice review: canonical system and Shared pages now lead with inclusive situations and contribution, then move to boundaries and catalogues; checklist-style prompts remain in their reference boundary.
- Publication: pending an explicit commit and push request.
