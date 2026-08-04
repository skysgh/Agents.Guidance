# Human Guidance Completeness Audit Findings

## Scope

This is the first findings pass for the [Human Guidance Completeness Audit](HUMAN-GUIDANCE-AUDIT-PLAN.md). It covers route coverage and cold-start reader journeys across the human root, orientation pages and stakeholder routes. It does not yet establish that the conceptual model, full lifecycle, serious-system controls, vocabulary, examples or all links are complete.

The findings distinguish a missing route from a missing responsibility. A role may be handled by a shared page, catalogue entry or subsection rather than needing a dedicated folder.

## Current strengths

- The core routes for Business Analysts, Product Owners, Architects, Technical Leads, Developers, Testers, Support, Operators, Maintainers and Service Providers are coherent enough to provide a viable starting point.
- [Shared Requirements](../../humans/shared/requirements.md) gives the routes a common requirement chain and names important handoffs.
- [Stakeholder Roles](../../humans/reference/catalogues/stakeholder-roles.md) provides a broad candidate vocabulary and makes several non-absorption boundaries visible.
- [Liberation Through Clarity](../../humans/shared/liberation-through-clarity.md) explains personal benefit rather than presenting structure only as organisational control.
- The recent introduction and navigation work has removed the strongest reading gates from the route README files.
- An opening-level fresh-eyes review now covers the root, engineering, human, orientation, delivery, stakeholder, role, development, example, reference, catalogue and checklist indexes. The story-led bridge is available before deeper naming, and the Development index was corrected so it begins with the reader's problem before exposing catalogues or checklists.
- The system-route voice pass now gives Client, Service, Shared, Pipeline and Testing readers a recognisable situation and a place to contribute before the technical vocabulary, catalogue or evidence prompts arrive.

## Cold-start review of the revised front door

The revised root and engineering entry pages were checked from four perspectives: a developer implementing a prepared capability, a Product Owner ordering outcomes, an operator looking for live-service guidance and a reader arriving from the repository assessment's gap list. Each can find a first destination without being required to follow a sequence. The assessment now explains its status labels and links the gap-led reader back to the relevant perspective.

The review also removed the remaining optional "follow the progression in order" wording from the orientation index. The deeper human routes remain substantial after the first click; that is appropriate for their subject, but the entry pages now make the choice and stopping point visible before asking the reader to invest more attention.

The entry pages now also offer [A Short Way Into the Guidance](../../humans/orientation/ways-into-guidance.md), which starts with a recognisable delivery problem, offers human role and problem routes, then explains when catalogues and checklists become useful. This is an initial navigation improvement, not evidence that every perspective has passed a full cold-start usability review.

The opening-level review found that the catalogue and checklist indexes are appropriately direct because they are reference surfaces, while narrative and role routes need explanation before deeper tools. Most role routes already provide that explanation. The Development index was the notable exception and now begins with the problem of placing a capability before naming its catalogues and checklists.

The Client, Service, Pipeline, Testing and Shared system routes have now received a route-level cold-start check. Each names its execution or responsibility boundary, gives a next destination and states whether it provides a foundation route or project-specific evidence. The worked SPA example supplies the first concrete cross-system story. This remains a documentation usability check, not evidence that a real project's systems are ready.

## Cold-start journey completed: Product Manager

The Product Manager route was tested as a reader entry point without relying on an assumed prior reading order. The route can lead a reader from:

1. product purpose and objectives within constraints;
2. the distinction between Product Manager objectives and Product Owner outcomes;
3. complete elicitation and the authority needed for decisions;
4. visible conceptual requests into enduring responsibilities and logical design;
5. investment, sequencing, deferral and evidence; and
6. lifecycle, specialist obligations, operational responsibility and whole-service success.

The route links to the relevant catalogue, shared requirements, lifecycle, modelling, Product Owner and evidence guidance. Its relative links and diagnostics pass. This is a navigation and content check, not evidence that real Product Manager readers agree with every boundary; that remains a later usability check.

## Lifecycle trace completed

The first lifecycle trace is recorded in [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md). It follows request submission and processing status from recognition through retirement. The trace confirms that the guidance can connect ambiguity, authority, contracts, testing, Support, Operations, recovery, maintenance and decommissioning, while recording these verification implications:

- Product Owner to Architect readiness needs a visible stopping point and return path.
- Specialist control evidence now has a shared responsibility treatment; the reader journey still needs testing.
- Cross-system test data, receipt reconciliation and retention or deletion evidence now have a canonical deliverable-systems treatment; the capability trace still needs testing.
- Capability-specific retirement evidence has not yet been demonstrated by an example.

## Findings

### L-01: Technical Analyst is a minor discoverability oversight

- **Severity:** Low
- **Affected reader:** Technical Analyst, Business Analyst, Product Owner, architect, developer or reader discovering a contract or integration question.
- **Source:** [Business Analyst Guidance](../../humans/stakeholders/business-analysts/readme.md), [Developer Guidance](../../humans/stakeholders/developers/readme.md), [Shared Requirements](../../humans/shared/requirements.md).
- **Issue:** Technical Analyst is named as a distinct responsibility, but the role is not intended to have a dedicated human route in this guidance. Its boundary is slightly less discoverable than the core routes.
- **Consequence:** A reader may need to infer the responsibility from shared requirements, the stakeholder catalogue and neighbouring architecture or technical-lead guidance.
- **Recommended treatment:** Keep Technical Analyst as a catalogue and shared-responsibility treatment. Preserve the existing boundary around technical contracts, integrations, data, feasibility and handoff without creating a route for a responsibility that is not a stable stakeholder journey here.
- **Status:** Accepted deliberate non-route; minor discoverability improvement may be made during vocabulary and navigation refinement

### H-02: Product Manager treatment needed a fuller route or shared treatment

- **Severity:** High
- **Affected reader:** Product Manager, Product Owner, sponsor, business owner or reader trying to understand strategic versus near-term product authority.
- **Source:** [Product Owner Guidance](../../humans/stakeholders/product-owners/readme.md), [Stakeholder Guidance](../../humans/stakeholders/readme.md), [Product Manager Guidance](../../humans/stakeholders/product-managers/readme.md).
- **Issue:** Product Manager was previously distinguished from Product Owner in catalogue and stakeholder material without a coherent reader route for far-seeing objectives within budget, schedule, organisational capacity, obligations and risk.
- **Consequence:** Without that perspective, the organisation can lose the strategic context that makes near-term Product Owner outcomes meaningful, feasible and worth pursuing.
- **Recommended treatment:** A dedicated route now explains Product Manager stewardship, the boundary with Product Owner, influence over complete elicitation, the move from visible concept to logical design, investment and deferral, authority, handoffs and whole-service success.
- **Status:** Implemented; cold-start route check passed; reader feedback remains open

### H-03: Specialist control responsibilities needed a route decision and purpose-led explanation

- **Severity:** High
- **Affected reader:** Security, Privacy, Records and Information Governance, Monitoring, Change Control, Assurance or Audit specialist.
- **Source:** [Stakeholder Roles](../../humans/reference/catalogues/stakeholder-roles.md), [Operator Guidance](../../humans/stakeholders/operators/readme.md), [Product Owner Scope and Deferral](../../humans/stakeholders/product-owners/scope-and-deferral.md).
- **Issue:** The catalogue named these responsibilities without a shared route decision or purpose-led explanation. Their authority, evidence, handoffs and failure consequences were unevenly discoverable, and the material risked presenting specialists as external approval obstacles rather than contributors to completeness and protection.
- **Consequence:** A specialist reader may find a role definition but not the path from obligation to design decision, implementation evidence, operation and assurance. Other readers may misunderstand the specialist as an infuriating gatekeeper instead of someone helping bring the organisation's full force behind completeness and evidence, or protecting it when careless work could spill into real harm.
- **Recommended treatment:** Build a control-responsibility matrix first. For each responsibility, explain the positive contribution, the conditions that create defensive intervention, its authority, the evidence it needs and the handoff it makes. Group roles with genuinely shared concerns where possible; do not create routes merely to mirror titles.
- **Status:** Closed as an implementation finding in [Shared Requirements](../../humans/shared/requirements.md); cold-start and lifecycle verification remain tracked separately.

### H-04: Product Owner sequencing needs explicit System LDM priority

- **Severity:** High
- **Affected reader:** Product Owner handing over an outcome; architect receiving the material.
- **Source:** [Product Owner Guidance](../../humans/stakeholders/product-owners/readme.md), [Shared Requirements](../../humans/shared/requirements.md), [Guidance for System Design Architects](../../humans/orientation/guidance-for-system-design-architects.md).
- **Issue:** The guidance previously characterised the Product Owner as eliciting architecture. The correct responsibility is to manage tickets against the architect's delivery strategy, prioritise the System LDM before the next dependent LDM or interface, and listen to the architect's logical blocking of foundations before furniture.
- **Consequence:** If the Product Owner yields to tactical business pressure or developers' avoidance of rigour, the visible feature can arrive before its shared foundations. Repeated reinterpretation, mistrust, defensive testing and rework then spread through every later ticket.
- **Recommended treatment:** Keep the canonical explanation focused on Product Owner sequencing and System LDM priority. Architecture owns the logical design and its stopping point; the Product Owner protects the order in product decisions without becoming an architect or a development gatekeeper.
- **Status:** Implemented and cold-start verified in [Shared Requirements](../../humans/shared/requirements.md) and the Product Owner route; capability lifecycle verification remains in Increment 2

### H-05: Sponsor accountability needed a distinct reader route

- **Severity:** High
- **Affected reader:** Sponsor, Product Manager, Product Owner, business owner or delivery participant trying to understand who checks delivery against the organisational promise.
- **Source:** [Stakeholder Guidance](../../humans/stakeholders/readme.md), [Sponsor Guidance](../../humans/stakeholders/sponsors/readme.md), [Stakeholder Roles](../../humans/reference/catalogues/stakeholder-roles.md).
- **Issue:** Sponsor was defined as organisational backing and investment authority, but the guidance did not give the Sponsor a clear way to examine delivery against promise, constraints, qualities, evidence, whole-life cost and unresolved variance.
- **Consequence:** Delivery could appear successful through status, tickets or deployment while unmet outcomes, specialist responsibilities or lifecycle ownership remained without a visible escalation path.
- **Recommended treatment:** Provide a decision-focused Sponsor route that preserves the Product Manager's product stewardship and the Product Owner's near-term ordering authority, while making commitment, evidence, variance, intervention and whole-life accountability explicit.
- **Status:** Implemented; initial Sponsor cold-start and lifecycle check passed; broader cold-start perspective review remains to be performed.

### H-06: Front-end Developer responsibility was hidden inside generic development

- **Severity:** High
- **Affected reader:** Front-end Developer, technical lead, architect, tester, accessibility specialist, security specialist or Product Owner responsible for a browser SPA.
- **Source:** [Deliverable Systems](../../humans/reference/catalogues/deliverable-systems.md), [Stakeholder Roles](../../humans/reference/catalogues/stakeholder-roles.md), [Developer Guidance](../../humans/stakeholders/developers/readme.md).
- **Issue:** The service consumer system was already identified as a distinct deliverable system, and agent conventions already contained accessibility and browser-security rules, but the human guidance did not identify Front-end Developer as a distinct developer-family responsibility or provide a route into client-side flows, component assemblies and quality-in-use evidence.
- **Consequence:** The SPA could be treated as presentation furniture attached to the server, leaving accessibility, usability, browser security, client-side failure behaviour and consumer-system evidence without a clear owner.
- **Recommended treatment:** Add Front-end Developer to the glossary, stakeholder developer-family catalogue and stakeholder navigation, then provide a human route that preserves the boundary between consumer-side experience coordination and service-side authority.
- **Status:** Implemented; focused link and topic validation passed; worked SPA example and broader cold-start perspective review remain open.

### H-07: Human guidance mixed system boundaries in Palette and Development folders

- **Severity:** High
- **Affected reader:** Front-end Developer, service-side Developer, architect, technical lead, tester, operator or reader trying to understand which constraints belong to the client, service or shared boundary.
- **Source:** [Deliverable Systems](../../humans/reference/catalogues/deliverable-systems.md), [Palette](../../humans/systems/client/palette/readme.md), [Human Development Guidance](../../humans/development/readme.md).
- **Issue:** The repository described distinct client, service, delivery and testing systems, but the Palette was located outside a system route and the Development folder mixed service implementation guidance with contracts, flows, lifecycle and other cross-boundary material.
- **Consequence:** A reader could treat the SPA as presentation attached to the service, or treat a service implementation rule as a shared system contract, without seeing the different execution environments, authority, failure modes and evidence.
- **Recommended treatment:** Introduce system-oriented human indexes, relocate the client Palette into a canonical client route, preserve compatibility links, and classify service versus shared Development material before moving it. Reserve honest future routes for Pipeline and Testing Systems.
- **Status:** Initial system map, client Palette migration, Service implementation-group relocation and Shared Contracts, Common Flows, lifecycle, model, data-protection and availability relocation are implemented with compatibility routes. Project-specific system evidence remains separate.

### H-08: Pipeline and Testing Systems needed human foundation routes

- **Severity:** High
- **Affected reader:** Sponsor, Product Manager, Technical Lead, Front-end Developer, service Developer, Tester, Operations or Release participant trying to understand what the delivery and qualification systems must prove.
- **Source:** [Pipeline System Guidance](../../humans/systems/pipeline/readme.md), [Testing System Guidance](../../humans/systems/tests/readme.md), [Deliverable Systems](../../humans/reference/catalogues/deliverable-systems.md).
- **Issue:** Delivery and Testing Systems were named in the catalogue, but their human routes did not yet explain lifecycle, ownership, environment, security, qualification, evidence or failure responsibilities.
- **Consequence:** The organisation could treat a build, deployment, browser test or green pipeline as proof of the complete service without distinguishing artifact evidence, client/service behaviour, test-system assumptions and operational readiness.
- **Recommended treatment:** Provide foundation routes for Pipeline and Testing Systems, then add project-specific environments, identities, data, evidence retention, release, rollback and recovery material when a real service requires it.
- **Status:** Foundation routes implemented; project-specific evidence and deeper examples remain open.

### H-09: Pipeline Developers needed a language and infrastructure entry point

- **Severity:** Medium
- **Affected reader:** Environment and Pipeline Developer, Technical Lead, Architect, service Developer or reviewer choosing how infrastructure and delivery automation should be expressed.
- **Source:** [Pipeline Development and Infrastructure as Code](../../humans/systems/pipeline/development-language.md), [Selecting a Language and Framework](../../humans/orientation/language-and-framework-selection.md), [Stakeholder Roles](../../humans/reference/catalogues/stakeholder-roles.md).
- **Issue:** The guidance distinguished C#, TypeScript and Python for browser, service and bounded work, but did not provide a human entry for declarative infrastructure languages, typed infrastructure frameworks or the PowerShell/Bash orchestration around them.
- **Consequence:** Pipeline work could be treated as incidental scripting, or AWS CDK's TypeScript origins could be mistaken for a universal AWS requirement, leaving resource authority, provider templates, permissions, rollback and pipeline evidence underexplained.
- **Recommended treatment:** Provide a provider-aware Pipeline Developer route that separates resource declaration from imperative orchestration and records the support, security, repeatability and evidence consequences of the language choice.
- **Status:** Implemented; provider-reference links, provider-neutral learning path, objective-first flow structure and focused route validation passed. Project-specific pipeline evidence and deeper flow definitions remain open.

### H-10: Deliverables catalogue under-modelled environment-definition code and execution

- **Severity:** High
- **Affected reader:** Sponsor, Technical Lead, Pipeline Developer, Environment Developer, Service Developer, Front-end Developer, Tester, Operator or maintainer trying to establish what must be delivered for a service to exist and recover.
- **Source:** [Deliverable Systems](../../humans/reference/catalogues/deliverable-systems.md), [Deliverables](../../humans/reference/catalogues/deliverables.md), [Deliverables Checklist](../../humans/reference/checklists/deliverables.md) and [Pipeline System Guidance](../../humans/systems/pipeline/readme.md).
- **Issue:** The earlier model named a delivery system and infrastructure definitions, but did not clearly distinguish the pipeline-definition codebase, pipeline execution system, environment-definition codebase, resulting environment instance, runner support or environment baseline evidence.
- **Consequence:** A team could deliver service and client code while treating environment creation as a side file, or could confuse a successful pipeline run with proof that the resulting environment matches its definition and is recoverable.
- **Recommended treatment:** Treat the definition codebases, execution system, resulting environments and evidence as distinct but connected deliverables. Preserve their ownership, permissions, dependencies, lifecycle, release relationship and recovery evidence even when they share a repository.
- **Status:** Implemented in the Deliverable Systems and Deliverables catalogues and Deliverables Checklist; project-specific environment and pipeline evidence remains open.

### H-11: Delivered-whole list merged unrelated deliverable concepts

- **Severity:** Medium
- **Affected reader:** Sponsor, Product Manager, Architect, Front-end Developer, service Developer, Pipeline Developer, Tester, Operations or content and branding contributor trying to understand what must accompany a usable service.
- **Source:** [Delivery Guidance](../../humans/delivery/readme.md), [Deliverables](../../humans/reference/catalogues/deliverables.md), [Deliverables Checklist](../../humans/reference/checklists/deliverables.md).
- **Issue:** The delivered-whole list grouped data, content, reference values, migrations, derived information, infrastructure, reachability, interfaces, events, media and data contracts as if they were one kind of supporting item.
- **Consequence:** People could lose the distinct responsibility, evidence and lifecycle of branding, media and accessibility, interface contracts, optional event/message flows, data and environment reachability.
- **Recommended treatment:** Separate the delivered-whole categories by the responsibility they protect. Keep data authority in data guidance, interface meaning in contract guidance and event/message concerns as an optional flow with its own delivery and reconciliation evidence.
- **Status:** Implemented; delivered-whole, Deliverables catalogue and checklist validation passed.

### H-12: Test Suite was hidden inside the Testing System and test code

- **Severity:** Medium
- **Affected reader:** Tester, Test Developer, Front-end Developer, service Developer, Pipeline Developer, Product Owner or reviewer trying to understand what a set of tests represents and what evidence its execution produces.
- **Source:** [Testing Evidence and Boundaries](../../humans/stakeholders/testers/evidence-and-boundaries.md), [Testing System Guidance](../../humans/systems/tests/readme.md), [Deliverables](../../humans/reference/catalogues/deliverables.md).
- **Issue:** The guidance distinguished Test Data, Test System and Test Plan, but did not name the coherent set of test cases and supporting code that exercises selected claims, boundaries, flows, risks or qualities.
- **Consequence:** A green suite could be confused with a complete Testing System, a test plan or a result, while failures could be attributed to the wrong boundary.
- **Recommended treatment:** Treat Test Suite as a deliverable within the test codebase and as a user of Test Data, Test System and Test Plan. Keep execution results and retained evidence separate from the suite itself.
- **Status:** Implemented; focused Test Suite link and terminology validation passed.

### H-13: Testing System needed distinct test areas and a data-truth boundary

- **Severity:** High
- **Affected reader:** Tester, Test Developer, service Developer, Front-end Developer, Pipeline Developer, data or integration specialist, Product Owner or reviewer deciding what a test result actually proves.
- **Source:** [Testing System Guidance](../../humans/systems/tests/readme.md), [Testing Evidence and Boundaries](../../humans/stakeholders/testers/evidence-and-boundaries.md), [Deliverable Systems](../../humans/reference/catalogues/deliverable-systems.md).
- **Issue:** The Testing System was described as one qualification environment without a clear map of service, service interop API, BFF, client, data ingress/egress and external-integration test areas. The guidance also risked letting tests appear to certify the truth of business data rather than the behaviour of the system that validates and transforms it.
- **Consequence:** A green test could be overinterpreted as proof of an untested boundary, or a fixture could silently become the authority for real-world data.
- **Recommended treatment:** Use separate Test Suites and evidence for the relevant areas, while keeping the Testing System shared. Test data validation, mapping, classification, reconciliation and error behaviour, but leave business-data truth with the responsible business, Domain, data, policy, privacy, records or external-system authority.
- **Status:** Implemented; test-area, BFF and data-validation boundary validation passed.

### H-14: Automated quality assurance needed to become part of the work item

- **Severity:** High
- **Affected reader:** Sponsor, Product Owner, Business Analyst, Tester, Test Developer, Service Developer, Front-end Developer, Pipeline Developer or reviewer trying to understand how acceptance becomes maintainable evidence.
- **Source:** [Shared Requirements](../../humans/shared/requirements.md), [Acceptance and Evidence](../../humans/stakeholders/product-owners/acceptance-and-evidence.md), [Testing Evidence and Boundaries](../../humans/stakeholders/testers/evidence-and-boundaries.md), [Testing System Guidance](../../humans/systems/tests/readme.md).
- **Issue:** The guidance connected requirements, testing and implementation, but did not make the acceptance-criteria-to-Test-Suite-to-Service-or-Client implementation path explicit. Parallel handoff of an underspecified story could leave testers and developers working from different meanings.
- **Consequence:** Manual checks repeatedly fail for interpretation reasons, while automation arrives after implementation and cannot protect maintainable change as effectively as executable acceptance evidence developed with the work item.
- **Recommended treatment:** Treat acceptance criteria as part of a complete work item. Let testers and Test Developers make suitable criteria executable, then let Service and Client Developers implement against those checks, with iterative return to the responsible meaning authority when the criteria or implementation is wrong.
- **Status:** Implemented; the repository deliberately makes no unsupported numerical claim about the rate of interpretation disagreement. Project-specific workflow evidence remains open.

### M-01: Specialist routes are not consistently discoverable from shared requirements

- **Severity:** Medium
- **Affected reader:** Any reader following a requirement into security, privacy, records, monitoring, change or assurance evidence.
- **Source:** [Shared Requirements](../../humans/shared/requirements.md).
- **Issue:** Specialist responsibilities are named in the shared chain, but the reader's next destination is not always obvious when no dedicated route exists.
- **Consequence:** The shared page can identify a responsibility without providing a useful route into its treatment.
- **Recommended treatment:** Add purposeful links to the chosen canonical control pages or record the deliberate catalogue-only treatment once Phase 4 decides it.
- **Status:** Shared destination and direct role-entry links now exist in [Shared Requirements](../../humans/shared/requirements.md), Architect, Product Owner, Developer and Technical Lead guidance; cold-start discoverability passed, while capability lifecycle verification remains in Increment 2

### M-02: Example discovery is organised by case, not reader question

- **Severity:** Medium
- **Affected reader:** A reader looking for an example relevant to a role, handoff or decision.
- **Source:** [Human Examples](../../humans/examples/readme.md).
- **Issue:** The examples are grouped as a sequence of cases, but the index does not yet help a reader find examples by role, problem, lifecycle stage or design question.
- **Consequence:** Strong examples are harder to retrieve when the reader is stuck on a particular kind of decision.
- **Recommended treatment:** Add a small cross-index by reader question or role after the audit has classified the examples. Avoid duplicating the examples themselves.
- **Status:** Open

### M-03: Decision-record format is implied but not provided

- **Severity:** Medium
- **Affected reader:** Any team told to record an unresolved boundary, assumption, deferral or authority gap.
- **Source:** [Responsible Boundaries and Deferred Design](../../humans/orientation/responsible-boundaries-and-deferred-design.md), [Human Guidance Audit Plan](HUMAN-GUIDANCE-AUDIT-PLAN.md).
- **Issue:** The guidance repeatedly values visible decisions and unresolved questions, but does not yet provide a lightweight format or location convention for maintaining them.
- **Consequence:** Teams may record important uncertainty inconsistently or leave it in transient conversation.
- **Recommended treatment:** Add a small decision-record example or shared template only after confirming the repository's intended governance format. Do not introduce process ceremony without evidence that it is needed.
- **Status:** Open

### L-02: Support and Operations depth is intentionally staged but remains uneven

- **Severity:** Low
- **Affected reader:** Support or Operations reader looking for the same depth available to development roles.
- **Source:** [Support Guidance](../../humans/stakeholders/support/readme.md), [Operator Guidance](../../humans/stakeholders/operators/readme.md).
- **Issue:** These routes are coherent but lighter than the Business Analyst and Developer routes. Support explicitly identifies substantive guidance as future work.
- **Consequence:** Readers may need to infer more from shared catalogues and agent conventions.
- **Recommended treatment:** Keep as an explicit deferred increment unless a cold-start journey shows a material operational gap. Add owner, trigger and review condition to the backlog.
- **Status:** Deferred

### L-03: Orientation pages do not share a uniform stopping-point convention

- **Severity:** Low
- **Affected reader:** Any reader unsure whether to continue orientation, move to a role route or use a checklist.
- **Source:** Orientation pages under [Human Orientation](../../humans/orientation/readme.md).
- **Issue:** Pages vary in how they describe their relationship to the next route and where the reader can stop.
- **Consequence:** Navigation remains workable but depends on local page style and reader inference.
- **Recommended treatment:** During the usability pass, add a light convention for “what this explains” and “where related questions continue” without turning every page into a mandatory route.
- **Status:** Open

### M-04: Lifecycle evidence is connected in principle but not yet in one discoverable path

- **Severity:** Medium
- **Affected reader:** Product, architecture, testing, Operations, Support, maintenance, records, privacy and assurance participants following a capability beyond first delivery.
- **Source:** [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md), [Software Development Lifecycle](../../humans/reference/catalogues/sdlc.md), [Deliverables](../../humans/reference/catalogues/deliverables.md).
- **Issue:** The lifecycle guidance names the necessary stages and evidence, and canonical pages now connect specialist responsibilities and cross-system scenario evidence. The first trace still needs to prove that a reader can follow those destinations at the point of need, including capability-specific retirement evidence.
- **Consequence:** A team may understand each responsibility separately while still missing evidence at the transitions between delivery, service, recovery, change and retirement.
- **Recommended treatment:** Re-run the trace with the [Specialist controls](../../humans/shared/requirements.md) and [Cross-system evidence and reconciliation](../../humans/reference/catalogues/deliverable-systems.md) destinations in view. Add a focused example only if the reader still cannot follow the evidence. Keep the lifecycle model shared rather than creating role-specific copies.
- **Status:** Canonical treatment, cold-start discoverability and an illustrative full-lifecycle application are verified through [Example 17](../../humans/examples/17-request-submission-full-lifecycle/after.md); real capability evidence remains contingent on an actual service change or retirement

## Audit limits

This report does not yet establish:

- that every specialist responsibility has the correct route, subsection or catalogue-only treatment;
- that one capability can be traced through every lifecycle and deliverable stage;
- that security, privacy, records, resilience, monitoring and recovery controls have complete authority and evidence;
- that every incident pattern is converted into a governed learning decision and corrective-change trail; and
- that all vocabulary uses have been classified; or
- that every example has sufficient evidence and a clear claim type.

Those remain later audit phases. The report should be updated rather than silently replaced as those phases complete.
