# Human Guidance Completeness Audit Plan

## Purpose

Run a hard-hat review of the complete human guidance after the initial implementation. The review is concerned with omissions, contradictions, weak boundaries, incomplete role routes, unsupported claims, broken navigation and missing evidence. It is not a general rewrite and it is not a popularity contest with other documentation. It asks whether the guidance is coherent, defensible and usable for serious systems.

The audit method and completion criteria are recorded here. The completed audit evidence and continuing decisions are recorded in the [Human Guidance Audit Findings](HUMAN-GUIDANCE-AUDIT-FINDINGS.md), [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md), [Role and Responsibility Coverage Matrix](HUMAN-GUIDANCE-AUDIT-COVERAGE-MATRIX.md) and [Documentation Register](../engineering/humans/maintenance/documentation-register.md).

## Current execution sequence

The review is followed in this order. Each stage leaves a visible artefact before the next stage changes broad guidance.

1. **Establish the baseline.** Keep the route findings in [Human Guidance Completeness Audit Findings](HUMAN-GUIDANCE-AUDIT-FINDINGS.md), confirm the inventory and record what the audit has not yet established.
2. **Classify responsibilities.** Use the [Role and Responsibility Coverage Matrix](HUMAN-GUIDANCE-AUDIT-COVERAGE-MATRIX.md). Decide whether each material responsibility belongs in a dedicated route, an existing route subsection, a shared canonical page, a catalogue or an explicit non-route decision. Include Product Manager, Product Owner and specialist responsibilities as authority-bearing perspectives, not just titles.
3. **Trace one capability.** Follow one representative capability from recognition through logical design, delivery, testing, release, service, support, operation, monitoring, recovery, maintenance and retirement. Record missing handoffs and evidence rather than filling them with assumptions. The first trace is recorded in [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md).
4. **Trace controls and organisational protection.** For Security, Privacy, Records, Monitoring, Assurance and related responsibilities, identify the enabling contribution first, then the defensive response required when obligations, evidence or ownership are missing. Record authority, boundary, evidence and failure consequence.
5. **Review examples, vocabulary and cold-start journeys.** Classify examples by reader question and lifecycle stage, check terminology and links, and test the routes from the perspective of the people who must use them without prior repository knowledge.
6. **Prioritise and implement.** Update canonical guidance first, then route applications, then navigation and editorial material. Every accepted deferral receives an owner, trigger, reason and review condition.
7. **Verify and report.** Run the repository checks and selected reader journeys, update the findings, TODO, register and final evidence report, and state remaining limits plainly.

The sequence is deliberately inspect-before-improve. It prevents the existence of a role name from becoming an automatic new page and prevents attractive prose from hiding an unresolved authority or control gap.

## Audit principles

1. **Inspect before improving.** Record the current state and evidence before rewriting a page.
2. **Canonical first.** Fix shared meaning at its authoritative source before changing role routes.
3. **Meaning before matching.** Search results are candidates for analysis, not permission for global replacement.
4. **Boundary before detail.** Identify responsibility, authority and lifecycle before prescribing documents, classes or folders.
5. **Role routes explain consequences.** Do not duplicate large canonical explanations into role silos.
6. **Evidence scales with consequence.** A serious claim needs a predicate, example, source, decision record or explicit assumption.
7. **Preserve user work.** Do not revert unrelated dirty-worktree changes or rewrite history merely to make the audit easier.
8. **Prefer a visible gap to invented certainty.** Record an unresolved decision, missing authority or unsupported claim instead of smoothing it away.

## Phase 0: Establish the audit baseline

### Work

- Inventory all Markdown files under `engineering/humans/` and all root human-guidance governance files.
- Inventory all human routes, catalogues, checklists, examples, glossary headings and documentation-register entries.
- Inventory relevant agent guidance and compare shared terms, principles, role names and routing assumptions.
- Record file audience, authority, subject, status, owner if known, review date if known and incoming/outgoing navigation links.
- Record pre-existing dirty worktree changes separately from audit changes.

### Evidence

- file inventory;
- route map;
- catalogue and glossary index;
- human/agent alignment notes; and
- baseline diagnostics and link-check results.

### Exit criteria

- Every human page has a known place in the information architecture.
- Every canonical concept has an identified source or is marked unresolved.
- The audit can distinguish an existing issue from an audit-created issue.

## Phase 1: Build the coverage matrix

### Work

Create or maintain the [Role and Responsibility Coverage Matrix](HUMAN-GUIDANCE-AUDIT-COVERAGE-MATRIX.md) with one row per material responsibility and columns for:

- role or stakeholder perspective;
- knowledge required;
- authority and decision rights;
- input and output;
- lifecycle;
- boundary and dependencies;
- contract or handoff;
- deliverable;
- test or acceptance evidence;
- operational evidence;
- maintenance and retirement consequence;
- canonical page;
- route page; and
- known gap or assumption.

Use the catalogue of stakeholder roles as a source of candidates, not as proof that every listed role needs a separate folder.

### Exit criteria

- Every role and responsibility is classified as route, subsection, catalogue-only, shared responsibility or deliberate omission.
- The matrix exposes missing handoffs and overloaded roles.

## Phase 2: Review the reader journeys

### Work

Test at least these journeys from a cold start:

- a developer implementing a prepared capability;
- a Business Analyst discovering ambiguity;
- a Product Owner protecting foundations while ordering work;
- an architect decomposing conceptual language;
- a Technical Analyst making a contract precise;
- a technical lead preparing implementation;
- a Front-end Developer building a browser or client consumer system;
- a tester creating cross-system evidence;
- a Test Developer creating automated evidence;
- an operator diagnosing and recovering a live service;
- a Support person triaging a user report;
- a maintainer changing an occupied service;
- a Service Provider accepting service responsibility; and
- a specialist responsible for Security, Privacy, Records, Monitoring, Change Control or assurance.

For each journey, record whether the reader can find:

- the shared concept;
- the relevant authority;
- the next action;
- the required evidence;
- the preceding and following handoff; and
- the route back when the problem definition changes.

### Exit criteria

- Every journey has a viable start, working route and stopping point.
- Missing routes are recorded with impact and recommended treatment.

## Phase 3: Review the conceptual-to-physical model

### Work

- Trace the same material example, such as "student at a school", through conceptual recognition, logical decomposition and physical representation.
- Check Enduring versus Transient, DDD, polysemy, domains, capabilities, relationships, states, authority and temporal evidence.
- Check that screens, tables, ORM entities, provider APIs and team structures are not silently treated as logical truth.
- Check that the guidance explains when a relationship shaft, aggregate, event, projection, contract or separate capability is justified.
- Check that physical simplification is allowed when it does not erase logical responsibility.

### Exit criteria

- The model distinctions are consistent across catalogues, role routes, development guidance and examples.
- The guidance can explain both over-modelling and under-modelling without collapsing into "it depends".

## Phase 4: Review the role model and new routes

### Work

Start with the current routes:

- Business Analysts;
- Product Owners;
- Architects;
- Technical Leads;
- Developers;
- Testers;
- Operators;
- Maintainers;
- Support; and
- Service Providers.

Then assess catalogue roles that do not yet have equivalent route depth:

- Technical Analyst;
- Product Manager;
- sponsor and business owner;
- enterprise, business, data, integrations, security, solution/application, platform/infrastructure/cloud and domain architects;
- system/application, integration, test and specialist developer families;
- front-end developer responsible for the consumer system and browser experience;
- Monitoring;
- Change Control;
- Security;
- Privacy;
- Records and information governance;
- assurance and audit; and
- supplier and connected-system responsibilities.

This review should preserve the human reason these responsibilities exist. Product roles should be described as stewards who improve the quality of objectives, elicitation, decisions and outcomes, not as backlog clerks or approval gates. Specialist responsibilities should be described as part of the organisation's engineering force: they help completeness, protection, recoverability and evidence travel through the whole endeavour. When preventable sloppiness creates exposure, they may also need to defend the organisation by requiring missing evidence, refusing unsafe assumptions or escalating an unresolved obligation. That defensive response is a consequence of an earlier gap, not the purpose of the specialist person.

For each Security, Privacy, Records, Monitoring and Assurance responsibility, explicitly review:

- what good contribution looks like before design and delivery;
- which objective, obligation, risk or evidence the responsibility protects;
- how the responsibility enables the team rather than merely reviewing it afterwards;
- what authority it has to advise, require, reject, accept or escalate;
- what evidence it contributes and what evidence it needs from others; and
- what conditions cause a shift from enabling the endeavour to protecting the organisation from unsafe or undocumented work.

For each candidate, decide among:

- dedicated route;
- subsection under an existing route;
- shared canonical page;
- catalogue-only treatment; or
- deliberate non-route with reason.

### Exit criteria

- No role is missing merely because its title is less familiar.
- No route is created merely because a title exists.
- Role boundaries distinguish responsibility from title, permission, system boundary and personal identity.

## Phase 5: Review lifecycle, delivery and post-delivery completeness

### Work

Trace one capability through the full lifecycle:

Record the result in the [Human Guidance Lifecycle Trace](HUMAN-GUIDANCE-AUDIT-LIFECYCLE-TRACE.md), or in a later trace that supersedes it with an explicit reason.

```text
recognition -> analysis -> product decision -> architecture -> technical analysis
-> implementation -> testing -> release/transition -> service provision
-> support -> operation/monitoring/recovery -> maintenance/change
-> migration/replacement -> retirement/decommissioning
```

For each stage, check:

- requirements and authority;
- inputs and outputs;
- contracts and mappings;
- data and information lifecycle;
- test data and test system needs;
- manual and automated test evidence;
- operational and maintenance information;
- support and escalation;
- rollback, recovery and reconciliation;
- compatibility, migration and deprecation; and
- retirement evidence.

### Exit criteria

- The guidance does not stop at first delivery.
- Testing, Support, Operations, Monitoring, Maintenance and Service Provider responsibilities remain distinct and connected.

## Phase 6: Review security, privacy, records and resilience

### Work

Review the relevant guidance for explicit boundaries and evidence for:

- authentication and authorisation;
- privileged restoration;
- data protection and privacy;
- retention, deletion and anonymisation;
- records, provenance and audit;
- accessibility and quality in use;
- availability, capacity, performance and resilience;
- monitoring, diagnostics and alerting;
- backup, restore and recovery;
- supplier, provider and dependency failure; and
- incident learning and corrective change.

For each topic, identify the responsible role, system boundary, decision authority, evidence and failure consequence.

### Exit criteria

- No critical control is described as a generic team responsibility without a responsible boundary.
- The guidance distinguishes policy, design, implementation, operation and assurance evidence.

## Phase 7: Review vocabulary, duplication and links

### Work

- Build the glossary and catalogue vocabulary inventory.
- Scan all human guidance uses.
- Classify uses before linking or rewriting.
- Link to the most specific authority and exact heading where appropriate.
- Review terms with multiple meanings, especially Role, System, Service, User, Domain, Capability, Contract, Requirement, Function and Stakeholder.
- Identify duplicated definitions and move meaning to a canonical page where needed.
- Check code blocks, inline code, quotations, headings, navigation labels and examples separately.
- Record deliberate exclusions and unresolved terminology questions.

### Exit criteria

- Shared terms have one source of meaning.
- Links improve retrieval without flattening polysemy.
- Duplicate explanations either add a role-specific consequence or are removed.

## Phase 8: Review examples and evidence

### Work

For every example, check:

- context and affected people;
- decision and authority;
- cost of structure;
- cost of omission;
- result and failure consequence;
- test, operational or maintenance evidence; and
- what changed afterwards.

Identify claims that are illustrative, experience-based, externally sourced or still assumptions. Add missing cases for role boundaries, lifecycle, cross-system identity, operational recovery, support escalation, maintenance and organisational correction.

### Exit criteria

- Examples teach decisions rather than merely repeat principles.
- Important claims have evidence or are honestly marked as assumptions.

## Phase 9: Prioritise and implement findings

### Work

Classify findings as:

- **Critical:** a misleading boundary, missing authority or omitted control could cause serious harm.
- **High:** a role, lifecycle, contract or handoff gap is likely to create material rework or unsafe operation.
- **Medium:** a navigation, terminology, duplication or evidence weakness reduces adoption or confidence.
- **Low:** editorial improvement with no material decision impact.

For each finding record:

- source page;
- exact issue;
- affected reader or system;
- consequence;
- canonical owner;
- proposed change;
- evidence needed;
- dependency;
- status; and
- rationale for deferral if not immediately addressed.

Implement canonical fixes first, then role-route applications, then navigation and editorial improvements. Keep unrelated worktree changes intact.

## Phase 10: Verify and report

### Work

Run:

- repository-wide Markdown diagnostics;
- repository-wide relative link validation;
- `git diff --check`;
- a route and catalogue orphan check;
- a term-link and duplicate-definition review;
- selected cold-start reader journeys; and
- a final changed-file review against the audit findings.

Update the documentation register and final audit report with open risks and deferred work.

### Exit criteria

- Every critical and high finding has been fixed, accepted with evidence or explicitly assigned.
- Remaining gaps have owners, reasons, triggers and review conditions.
- The audit can state what was checked and what it did not establish.
- Human and agent guidance remain aligned.
- Links and diagnostics are clean.

## Definition of complete

The completeness audit is complete when the guidance is not merely extensive but navigable, internally coherent, explicit about authority and lifecycle, connected to evidence and honest about its remaining limits.
