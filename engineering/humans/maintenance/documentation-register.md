# Human Documentation Register

The original human-guidance rewrite is complete. This register records future changes that affect the meaning, audience, terminology or navigation of the guidance.

Use it when a change needs to remain visible beyond the file being edited. Small wording fixes and routine link repairs do not need a register entry.

## What to record

Record a short entry when a change:

- introduces or changes a shared term;
- changes the relationship between human and agent guidance;
- changes a design principle or implementation invariant;
- adds, removes or moves a route entry point; or
- leaves a deliberate unresolved question or deferred decision.

## Review checks

Before closing an entry, check the affected human explanation, agent routing, links, terminology and examples. Mark the entry complete only when the relevant checks have passed.

## Human and agent authority

Human guidance is the canonical explanation of meaning, consequences, role perspective and adoption. Agent guidance is the canonical expression of precise implementation rules, invariants, task routing and validation requirements. Neither layer silently replaces the other.

When the two layers appear to conflict:

1. identify whether the difference is explanation versus rule, or a genuine contradiction;
2. record the conflict and affected responsibility in this register;
3. preserve the human explanation of the problem and consequence while checking the precise agent convention with the responsible engineering owner;
4. update both layers when the decision changes shared meaning or implementation obligation; and
5. validate links, diagnostics, conventions and examples before closing the entry.

An unresolved conflict is a visible decision or risk. It is not resolved by making one page harder to find.

## Entries

| Date | Subject | Decision or change | Follow-up | Status |
| --- | --- | --- | --- | --- |
| 2026-08-02 | Human guidance foundation and stakeholder routes | Established the human-facing route from liberation through clarity to shared concepts, role routes, development guidance, testing, Support, Operations, Maintenance and Service Provider responsibilities. | Keep route boundaries and shared concepts aligned during future changes. | Complete |
| 2026-08-02 | Enduring versus Transient modelling | Added the canonical Entity Lifecycle Patterns catalogue, glossary terms, Patterns Catalogue entry, logical/physical model guidance, relationship-shaft guidance, role hooks and Example 16. | Apply the distinction to future domain and lifecycle examples without making one physical schema universal. | Complete |
| 2026-08-02 | Meaning-aware vocabulary linking | Added a controlled glossary/catalogue linking pass for high-confidence uses and documented exclusions for polysemous terms such as Role and System. | Continue the pass when new canonical terms or catalogues are added. | In progress |
| 2026-08-02 | Reader navigation links | Added purposeful inline links in major orientation and development routes for contracts, model types, patterns, planning guidance, registries, vertical slices and related concepts. Links explain the destination, use exact anchors where useful and preserve the local explanation. | Refine link coverage as new routes and canonical concepts are added; keep link density subordinate to comprehension. | Complete |
| 2026-08-02 | Narrative voice and page structure | Replaced high-impact "Start here" gates, ordered reading commands and compact implementation lists in narrative routes with connected explanations and choice-preserving invitations. Kept practical prompts in the checklist boundary and treated procedural bullets as reference material rather than the default teaching voice. | Continue the scan across new and existing human pages; preserve directive structure where a document is explicitly a checklist or reference index. | Complete |
| 2026-08-02 | Introduction versus action | Clarified that introductions provide comprehension, links, desire and tools without asking readers to perform the later work. Explicit requests to decide, record, build, test or review belong in the decision, development, testing or checklist guidance that owns the action. | Check new introductions for hidden reading assignments, imperative gates or procedural bullets that belong elsewhere. | Complete |
| 2026-08-02 | Repository entry and choice-preserving navigation | Reworked the root README into a welcoming route for human and agent guidance, moved audit material into supporting context, replaced ordered-reading language in human entry pages with explanatory optional routes, and repaired assessment links exposed by the navigation validation. | Keep the human route invitational while retaining conditional routing in agent conventions; address the substantive operations, security, governance, evidence, performance and cross-system gaps through dedicated future increments. | Complete |
| 2026-08-02 | Completeness audit findings baseline | Recorded the first route and reader-journey findings in [Human Guidance Completeness Audit Findings](../../../audit/HUMAN-GUIDANCE-AUDIT-FINDINGS.md), including open decisions for Technical Analyst, Product Manager, specialist controls, Product Owner to Architect handoff, example discovery and decision records. | Preserve the findings as audit evidence; future changes should update the relevant canonical guidance and register entry rather than recreate the completed work queue. | Complete |
| 2026-08-02 | Product and specialist role framing | Reframed Product Owner as an empowered steward of value, complete elicitation, authoritative decisions and lower-risk logical design. Reframed Product Manager as a far-seeing steward of objectives within budget, schedule, organisational capacity, obligations and risk. Added audit treatment for the enabling and defensive purposes of Security, Privacy, Records, Monitoring and Assurance responsibilities. | Use the audit execution sequence to classify routes and trace authority, evidence and failure consequences before adding specialist route depth. | In progress |
| 2026-08-02 | Product Manager route | Added a dedicated human route for Product Managers, linking strategic objectives within constraints to Product Owner outcomes, complete elicitation, logical design, investment, evidence, lifecycle and whole-service success. | Test the route through a cold-start Product Manager journey and refine its handoffs based on evidence. | In progress |
| 2026-08-02 | Role and responsibility coverage matrix | Classified the material roles and responsibilities by route, subsection, shared canonical guidance, catalogue treatment or open decision. Recorded Product Manager as a dedicated route, Technical Analyst as the next route decision and specialist controls as a shared-treatment-first decision. | Trace one capability through the lifecycle and then review specialist controls, authority and evidence against this matrix. | In progress |
| 2026-08-02 | Technical Analyst deliberate non-route | Accepted that Technical Analyst is an assigned responsibility rather than a stable stakeholder journey requiring dedicated human guidance here. Preserved its boundary in the stakeholder catalogue and shared requirements, with minor discoverability refinement deferred. | Do not create a route solely for this title; revisit only if a real reader journey demonstrates a material gap. | Accepted |
| 2026-08-02 | Lifecycle trace | Traced request submission and processing status from recognition through retirement, confirming strong connections across authority, contracts, testing, Support, Operations, recovery and maintenance. Example 17 now demonstrates the complete lifecycle evidence pattern. | Carry the lifecycle pattern into the conceptual/logical/physical model audit and serious-system controls review. | Complete |
| 2026-08-02 | Product Owner and Architect sequencing | Corrected the canonical guidance so the Product Owner manages tickets against the architect's strategy, prioritises the System LDM before the next dependent LDM or interface, and protects foundation-before-furniture sequencing without owning architecture. Cold-start and lifecycle navigation now directly name the architect's boundary and stopping point. | Preserve the role boundary as later model and controls audits proceed. | Complete |
| 2026-08-02 | Shared specialist controls and cross-system evidence | Added canonical shared guidance for specialist contribution, bounded authority, evidence and return paths, plus cross-system scenario identity, acknowledgement, reconciliation and test-data lifecycle evidence. Example 17 now demonstrates their use across a capability lifecycle. | Carry the specialist evidence pattern into the serious-system controls review; create real service evidence when a project requires it. | Complete |
| 2026-08-02 | Conceptual, logical and physical model audit | Extended Example 16 so the Person, School and `StudentAt` pattern now includes illustrative domain ownership, contract guarantees, temporal storage, cross-system identity and retirement/deletion evidence. | Use the worked model pattern in the examples/claims review and serious-system controls review; preserve the distinction between illustrative choices and project authority. | Complete |
| 2026-08-02 | Examples and claims review | Added role and problem discovery to the Example Gallery and stated the gallery-wide boundary between illustrative patterns and real project authority or legal advice. | Preserve reader-question indexing as new examples are added; continue claims review when the vocabulary and serious-system controls audits expose a specific issue. | Complete |
| 2026-08-02 | Service vocabulary review | Added a canonical Service polysemy entry distinguishing organisational service systems, agreed service capabilities, designed services and web services; linked Service Provider and System LDM guidance to it. | Preserve the distinction between related service meanings as new guidance is added. | Complete |
| 2026-08-02 | Later glossary and ontological decomposition increment | Added glossary entries for Objectives versus Outcomes, Capabilities versus Functions, Polysemy and Homonymy, Monosemy, Ontological and Ontological Primitives, plus the standalone [Ontological Decomposition](../orientation/ontological-decomposition.md) paper. | Preserve the distinction between north-star abstraction and the level that remains understandable and useful for the decision. | Complete |
| 2026-08-02 | Incident learning and corrective change | Added a shared Operations control page that distinguishes response, recording, learning, decision, correction and verification, and assigns each handoff to the responsible boundary. Linked it from SDLC, recovery guidance and the deliverables checklist. | Preserve the incident-to-corrective-change trace in real service evidence when available. | Complete |
| 2026-08-02 | Availability, capacity and resilience control | Added a canonical control path from service-specific availability, capacity, degradation, RTO and RPO decisions through design, implementation, operation and assurance evidence. | Apply service-specific targets in real service evidence; do not treat the guidance as a universal numerical target. | Complete |
| 2026-08-02 | Completeness audit staged | Created the Human Guidance Completeness Audit TODO and plan as the next workstream, covering route coverage, handoffs, lifecycle, evidence, controls and usability. | Do not treat the audit as part of the completed initial implementation; execute it as a separate governed increment. | Deferred |