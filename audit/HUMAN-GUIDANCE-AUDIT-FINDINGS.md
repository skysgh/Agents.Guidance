# Human Guidance Completeness Audit Findings

## Scope

This is the first findings pass for the [Human Guidance Completeness Audit](HUMAN-GUIDANCE-AUDIT-PLAN.md). It covers route coverage and cold-start reader journeys across the human root, orientation pages and stakeholder routes. It does not yet establish that the conceptual model, full lifecycle, serious-system controls, vocabulary, examples or all links are complete.

The findings distinguish a missing route from a missing responsibility. A role may be handled by a shared page, catalogue entry or subsection rather than needing a dedicated folder.

## Current strengths

- The core routes for Business Analysts, Product Owners, Architects, Technical Leads, Developers, Testers, Support, Operators, Maintainers and Service Providers are coherent enough to provide a viable starting point.
- [Shared Requirements](../engineering/humans/shared/requirements.md) gives the routes a common requirement chain and names important handoffs.
- [Stakeholder Roles](../engineering/humans/reference/catalogues/stakeholder-roles.md) provides a broad candidate vocabulary and makes several non-absorption boundaries visible.
- [Liberation Through Clarity](../engineering/humans/shared/liberation-through-clarity.md) explains personal benefit rather than presenting structure only as organisational control.
- The recent introduction and navigation work has removed the strongest reading gates from the route README files.

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
- **Source:** [Business Analyst Guidance](../engineering/humans/stakeholders/business-analysts/readme.md), [Developer Guidance](../engineering/humans/stakeholders/developers/readme.md), [Shared Requirements](../engineering/humans/shared/requirements.md).
- **Issue:** Technical Analyst is named as a distinct responsibility, but the role is not intended to have a dedicated human route in this guidance. Its boundary is slightly less discoverable than the core routes.
- **Consequence:** A reader may need to infer the responsibility from shared requirements, the stakeholder catalogue and neighbouring architecture or technical-lead guidance.
- **Recommended treatment:** Keep Technical Analyst as a catalogue and shared-responsibility treatment. Preserve the existing boundary around technical contracts, integrations, data, feasibility and handoff without creating a route for a responsibility that is not a stable stakeholder journey here.
- **Status:** Accepted deliberate non-route; minor discoverability improvement may be made during vocabulary and navigation refinement

### H-02: Product Manager treatment needed a fuller route or shared treatment

- **Severity:** High
- **Affected reader:** Product Manager, Product Owner, sponsor, business owner or reader trying to understand strategic versus near-term product authority.
- **Source:** [Product Owner Guidance](../engineering/humans/stakeholders/product-owners/readme.md), [Stakeholder Guidance](../engineering/humans/stakeholders/readme.md), [Product Manager Guidance](../engineering/humans/stakeholders/product-managers/readme.md).
- **Issue:** Product Manager was previously distinguished from Product Owner in catalogue and stakeholder material without a coherent reader route for far-seeing objectives within budget, schedule, organisational capacity, obligations and risk.
- **Consequence:** Without that perspective, the organisation can lose the strategic context that makes near-term Product Owner outcomes meaningful, feasible and worth pursuing.
- **Recommended treatment:** A dedicated route now explains Product Manager stewardship, the boundary with Product Owner, influence over complete elicitation, the move from visible concept to logical design, investment and deferral, authority, handoffs and whole-service success.
- **Status:** Implemented; cold-start route check passed; reader feedback remains open

### H-03: Specialist control responsibilities needed a route decision and purpose-led explanation

- **Severity:** High
- **Affected reader:** Security, Privacy, Records and Information Governance, Monitoring, Change Control, Assurance or Audit specialist.
- **Source:** [Stakeholder Roles](../engineering/humans/reference/catalogues/stakeholder-roles.md), [Operator Guidance](../engineering/humans/stakeholders/operators/readme.md), [Product Owner Scope and Deferral](../engineering/humans/stakeholders/product-owners/scope-and-deferral.md).
- **Issue:** The catalogue named these responsibilities without a shared route decision or purpose-led explanation. Their authority, evidence, handoffs and failure consequences were unevenly discoverable, and the material risked presenting specialists as external approval obstacles rather than contributors to completeness and protection.
- **Consequence:** A specialist reader may find a role definition but not the path from obligation to design decision, implementation evidence, operation and assurance. Other readers may misunderstand the specialist as an infuriating gatekeeper instead of someone helping bring the organisation's full force behind completeness and evidence, or protecting it when careless work could spill into real harm.
- **Recommended treatment:** Build a control-responsibility matrix first. For each responsibility, explain the positive contribution, the conditions that create defensive intervention, its authority, the evidence it needs and the handoff it makes. Group roles with genuinely shared concerns where possible; do not create routes merely to mirror titles.
- **Status:** Closed as an implementation finding in [Shared Requirements](../engineering/humans/shared/requirements.md); cold-start and lifecycle verification remain tracked separately.

### H-04: Product Owner sequencing needs explicit System LDM priority

- **Severity:** High
- **Affected reader:** Product Owner handing over an outcome; architect receiving the material.
- **Source:** [Product Owner Guidance](../engineering/humans/stakeholders/product-owners/readme.md), [Shared Requirements](../engineering/humans/shared/requirements.md), [Guidance for System Design Architects](../engineering/humans/orientation/guidance-for-system-design-architects.md).
- **Issue:** The guidance previously characterised the Product Owner as eliciting architecture. The correct responsibility is to manage tickets against the architect's delivery strategy, prioritise the System LDM before the next dependent LDM or interface, and listen to the architect's logical blocking of foundations before furniture.
- **Consequence:** If the Product Owner yields to tactical business pressure or developers' avoidance of rigour, the visible feature can arrive before its shared foundations. Repeated reinterpretation, mistrust, defensive testing and rework then spread through every later ticket.
- **Recommended treatment:** Keep the canonical explanation focused on Product Owner sequencing and System LDM priority. Architecture owns the logical design and its stopping point; the Product Owner protects the order in product decisions without becoming an architect or a development gatekeeper.
- **Status:** Implemented and cold-start verified in [Shared Requirements](../engineering/humans/shared/requirements.md) and the Product Owner route; capability lifecycle verification remains in Increment 2

### M-01: Specialist routes are not consistently discoverable from shared requirements

- **Severity:** Medium
- **Affected reader:** Any reader following a requirement into security, privacy, records, monitoring, change or assurance evidence.
- **Source:** [Shared Requirements](../engineering/humans/shared/requirements.md).
- **Issue:** Specialist responsibilities are named in the shared chain, but the reader's next destination is not always obvious when no dedicated route exists.
- **Consequence:** The shared page can identify a responsibility without providing a useful route into its treatment.
- **Recommended treatment:** Add purposeful links to the chosen canonical control pages or record the deliberate catalogue-only treatment once Phase 4 decides it.
- **Status:** Shared destination and direct role-entry links now exist in [Shared Requirements](../engineering/humans/shared/requirements.md), Architect, Product Owner, Developer and Technical Lead guidance; cold-start discoverability passed, while capability lifecycle verification remains in Increment 2

### M-02: Example discovery is organised by case, not reader question

- **Severity:** Medium
- **Affected reader:** A reader looking for an example relevant to a role, handoff or decision.
- **Source:** [Human Examples](../engineering/humans/examples/readme.md).
- **Issue:** The examples are grouped as a sequence of cases, but the index does not yet help a reader find examples by role, problem, lifecycle stage or design question.
- **Consequence:** Strong examples are harder to retrieve when the reader is stuck on a particular kind of decision.
- **Recommended treatment:** Add a small cross-index by reader question or role after the audit has classified the examples. Avoid duplicating the examples themselves.
- **Status:** Open

### M-03: Decision-record format is implied but not provided

- **Severity:** Medium
- **Affected reader:** Any team told to record an unresolved boundary, assumption, deferral or authority gap.
- **Source:** [Responsible Boundaries and Deferred Design](../engineering/humans/orientation/responsible-boundaries-and-deferred-design.md), [Human Guidance Audit Plan](HUMAN-GUIDANCE-AUDIT-PLAN.md).
- **Issue:** The guidance repeatedly values visible decisions and unresolved questions, but does not yet provide a lightweight format or location convention for maintaining them.
- **Consequence:** Teams may record important uncertainty inconsistently or leave it in transient conversation.
- **Recommended treatment:** Add a small decision-record example or shared template only after confirming the repository's intended governance format. Do not introduce process ceremony without evidence that it is needed.
- **Status:** Open

### L-02: Support and Operations depth is intentionally staged but remains uneven

- **Severity:** Low
- **Affected reader:** Support or Operations reader looking for the same depth available to development roles.
- **Source:** [Support Guidance](../engineering/humans/stakeholders/support/readme.md), [Operator Guidance](../engineering/humans/stakeholders/operators/readme.md).
- **Issue:** These routes are coherent but lighter than the Business Analyst and Developer routes. Support explicitly identifies substantive guidance as future work.
- **Consequence:** Readers may need to infer more from shared catalogues and agent conventions.
- **Recommended treatment:** Keep as an explicit deferred increment unless a cold-start journey shows a material operational gap. Add owner, trigger and review condition to the backlog.
- **Status:** Deferred

### L-03: Orientation pages do not share a uniform stopping-point convention

- **Severity:** Low
- **Affected reader:** Any reader unsure whether to continue orientation, move to a role route or use a checklist.
- **Source:** Orientation pages under [Human Orientation](../engineering/humans/orientation/readme.md).
- **Issue:** Pages vary in how they describe their relationship to the next route and where the reader can stop.
- **Consequence:** Navigation remains workable but depends on local page style and reader inference.
- **Recommended treatment:** During the usability pass, add a light convention for “what this explains” and “where related questions continue” without turning every page into a mandatory route.
- **Status:** Open

### M-04: Lifecycle evidence is connected in principle but not yet in one discoverable path

- **Severity:** Medium
- **Affected reader:** Product, architecture, testing, Operations, Support, maintenance, records, privacy and assurance participants following a capability beyond first delivery.
- **Source:** [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md), [Software Development Lifecycle](../engineering/humans/reference/catalogues/sdlc.md), [Deliverables](../engineering/humans/reference/catalogues/deliverables.md).
- **Issue:** The lifecycle guidance names the necessary stages and evidence, and canonical pages now connect specialist responsibilities and cross-system scenario evidence. The first trace still needs to prove that a reader can follow those destinations at the point of need, including capability-specific retirement evidence.
- **Consequence:** A team may understand each responsibility separately while still missing evidence at the transitions between delivery, service, recovery, change and retirement.
- **Recommended treatment:** Re-run the trace with the [Specialist controls](../engineering/humans/shared/requirements.md) and [Cross-system evidence and reconciliation](../engineering/humans/reference/catalogues/deliverable-systems.md) destinations in view. Add a focused example only if the reader still cannot follow the evidence. Keep the lifecycle model shared rather than creating role-specific copies.
- **Status:** Canonical treatment, cold-start discoverability and an illustrative full-lifecycle application are verified through [Example 17](../engineering/humans/examples/17-request-submission-full-lifecycle/after.md); real capability evidence remains contingent on an actual service change or retirement

## Audit limits

This report does not yet establish:

- that every specialist responsibility has the correct route, subsection or catalogue-only treatment;
- that one capability can be traced through every lifecycle and deliverable stage;
- that security, privacy, records, resilience, monitoring and recovery controls have complete authority and evidence;
- that every incident pattern is converted into a governed learning decision and corrective-change trail; and
- that all vocabulary uses have been classified; or
- that every example has sufficient evidence and a clear claim type.

Those remain later audit phases. The report should be updated rather than silently replaced as those phases complete.
