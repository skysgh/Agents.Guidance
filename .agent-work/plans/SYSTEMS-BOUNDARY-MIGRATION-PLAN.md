# Human Systems Boundary Migration Plan

## Purpose

This plan separates human guidance by the systems whose execution environment, authority, dependencies, lifecycle and failure behaviour differ. It is a documentation-structure change, not a claim that every planned system already exists as a built or fully documented implementation.

The immediate reason for the change is that the repository has begun to describe a browser-based service consumer, a server-side service, a delivery or pipeline system and a testing system as distinct systems. The human guidance should let a reader follow the constraints and responsibilities of each one without treating the visible client, the service runtime, the delivery path and the testing environment as one undifferentiated application.

## Decision

Concur with a systems-oriented human structure. Resist a blind folder move.

The boundary should be based on responsibility, execution environment, authority, dependencies, lifecycle, failure behaviour and evidence. A role or filename alone is not enough. A concept belongs in `systems/shared` only when both or all participating systems need the same meaning or contract. `systems/shared` must not become a home for material that has not been classified.

The move is staged so that:

- the browser or client guidance can become a real client-system route now;
- server-side LDM, layer, service and slice guidance can become a service-system route without being confused with the client;
- contracts, cross-system flows, quality and lifecycle material can be separated where their shared meaning is demonstrated;
- pipeline and test systems have visible future homes without being represented as complete; and
- existing links remain usable until each canonical page has moved and its references have been repaired.

## Target shape

The intended human route is:

```text
engineering/humans/systems/
  readme.md
  client/
    readme.md
    first-look.md
    ux-palette.md
    implementation-vocabulary.md
  service/
    readme.md
  pipeline/
    readme.md
  tests/
    readme.md
  shared/
    readme.md
```

These folders describe human perspectives and system boundaries. They do not require one repository, project, deployment or team per folder. A real product may deliver several systems together, and one person or team may work across several perspectives.

The existing [Deliverable Systems](engineering/humans/reference/catalogues/deliverable-systems.md) catalogue remains the authority for the relationship among Delivery, Service, Consumer and Testing systems. The new indexes explain how to enter the human guidance for those systems; they do not duplicate that catalogue.

The delivery system itself has important constituents: Pipeline Definition, Pipeline Execution and Environment Definition Systems. The [Deliverables](engineering/humans/reference/catalogues/deliverables.md) catalogue also records the codebases, resulting environment instances, runner support and baselines that connect those constituents. This is a correction to the earlier assumption that environment-definition code was merely one infrastructure file within the pipeline.

## Ownership map

### Client system

The client system includes browser or client execution, published assets, client-side state, views, components, interaction flows, client-side failure behaviour and calls to service contracts.

| Current material | Target treatment | Decision |
| --- | --- | --- |
| `engineering/humans/palette/first-look.md` | `systems/client/first-look.md` | Move and retain as the narrative introduction to the client experience. |
| `engineering/humans/palette/elements.md` | `systems/client/ux-palette.md` | Merge into the client UX catalogue rather than preserving an unqualified `elements` page. |
| `engineering/humans/palette/relationships.md` | `systems/client/ux-palette.md` | Merge the relationship map and example into the same catalogue so definitions and relationships have one authority. |
| `engineering/humans/palette/technical-terms.md` | `systems/client/implementation-vocabulary.md` plus glossary links | Keep code-specific correspondence out of the general glossary; add concise glossary definitions only for terms used across human guidance. |
| `engineering/humans/palette/readme.md` | `systems/client/readme.md` | Replace the Palette index with a client-system entry that explains the boundary and routes to the first look and UX palette. |
| `engineering/humans/reference/catalogues/sites-flows-views-components.md` | Existing catalogue, linked from client guidance | Keep as the broader shared catalogue for sites, flows, views and components. The client UX palette must complement it, not create a second conflicting definition. |

### Service system

The service system is the server-side runtime and its application, domain, persistence, integration, diagnostic, authorisation and recovery responsibilities. The initial service index will classify current development pages before any broad relocation.

| Current material | Initial treatment | Later decision |
| --- | --- | --- |
| `development/ldms.md` | Service candidate | Move or canonicalise under `systems/service` after link impact is mapped. |
| `development/layers.md` | Service candidate | Move or canonicalise under `systems/service`; keep the distinction between implementation layers and model types. |
| `development/services.md` | Service candidate | Move or canonicalise under `systems/service`; it describes System LDM technical capabilities. |
| `development/cross-cutting-services.md` | Service candidate | Keep service ownership where the material concerns System LDM capabilities; split genuinely cross-system contracts later. |
| `development/vertical-slices.md` | Primarily service candidate | Keep the capability slice distinct from the client journey and shared horizontal flow. |
| `development/constants.md` | Service implementation candidate | Keep ownership with the LDM or service boundary; move shared vocabulary only when a real cross-system consumer exists. |
| `development/readme.md` | Service entry candidate | Replace with or redirect to the service-system index once detailed pages have stable homes. |

### Shared systems and cross-boundary guidance

Shared guidance must describe a relationship that crosses system boundaries or is needed by several system perspectives.

| Current material | Shared candidate | Guardrail |
| --- | --- | --- |
| `development/contracts.md` | Shared contract guidance | Explain client-service, service-provider and internal contracts without making every contract client material. |
| `foundations/flows.md` | Shared flow language | Keep the general flow shape shared; add client and service interpretations rather than duplicating one flow definition. |
| `development/data-deletion-guidance.md` and `detailed-data-deletion-considerations.md` | Shared lifecycle and data-protection guidance | Keep authority with privacy, records, business and system owners; do not make deletion a client-only or service-only concern. |
| `development/availability-capacity-and-resilience.md` | Shared quality outcome with service evidence | Separate common quality meaning from service operational targets and client experience evidence when needed. |
| `development/logical-and-physical-models.md` | Shared model guidance | Preserve conceptual, logical and physical distinctions across client, service and infrastructure models. |
| `shared/requirements.md` and `reference/catalogues/qualities.md` | Existing shared authorities | Do not duplicate their meaning inside system indexes. Link to them from client and service routes. |

### Pipeline and testing systems

The repository has not yet invested equally in these perspectives. The foundation routes now explain their boundaries and responsibilities, while project-specific evidence and deeper examples remain future work.

- `systems/pipeline/readme.md` explains source, build, qualification, packaging, promotion, deployment, release evidence, artifact integrity, environment separation, secrets and recovery. It connects to the existing Delivery System material.
- `systems/tests/readme.md` explains the Testing System, browser and device execution, test data, environments, stubs, qualification evidence, accessibility evidence, cross-system contracts and result retention. It connects to the existing Testing System material and tester routes.
- These are foundation routes, not project-specific evidence packs. They must not be presented as proof that a particular service's pipeline or testing system is ready.

## Migration sequence

### Phase 1: Establish the map

1. Add this plan as the controlled migration record.
2. Add `systems/readme.md` with the system-boundary explanation.
3. Add client, service, pipeline, tests and shared entry indexes.
4. Link the indexes from the story-led jump route, human guidance and relevant stakeholder routes.
5. Record that pipeline and testing guidance are reserved and foundational rather than complete.

### Phase 2: Move the client Palette

1. Create the client first-look page and client index.
2. Merge Palette Elements and Palette Relationships into `ux-palette.md`.
3. Move the implementation-specific terms into `implementation-vocabulary.md`.
4. Add or refine short glossary entries only where the terms are used as shared human vocabulary.
5. Update all incoming and outgoing links, including agent-facing links to the human explanation.
6. Remove the old Palette files only after the repository-wide link check passes. Do not leave two competing canonical Palettes.

### Phase 3: Establish service and shared ownership

1. Add service and shared indexes that classify the current Development pages.
2. Move one coherent page or small group at a time, beginning with LDMs, layers, services and vertical slices for the service route. **The first Service implementation group is now complete, with compatibility routes at the former paths.**
3. Treat contracts, flows, lifecycle, quality and model material as shared candidates only after checking their actual consumers and authority. **The current identified Shared group is now relocated; newly identified material must follow the same classification rule.**
4. Update links in orientation, role, catalogue, example, audit and agent guidance as each page moves.
5. Leave compatibility pages or deliberate redirects when a broad external or internal reference would otherwise break.

### Phase 4: Develop pipeline and testing perspectives

1. Build the pipeline foundation route from the existing Delivery System, delivery guidance and agent delivery conventions. **Complete for the foundation route.**
2. Build the testing foundation route from the existing Testing System, tester guidance, cross-system test context and evidence requirements. **Complete for the foundation route.**
3. Add worked examples before expanding either route into detailed catalogues or checklists. **The worked SPA example now provides the first cross-system example.**
4. Record project-specific evidence that remains absent rather than treating the foundation routes as an implementation proof.

### Phase 5: Verify and consolidate

1. Run the repository-wide Markdown link check and `git diff --check` after every migration increment.
2. Search for stale `palette/` and `humans/development/` links after each move.
3. Check that every canonical concept has one authority and every system route links to shared requirements, quality and deliverable-system guidance where relevant.
4. Review cold-start routes so stories and human explanations precede catalogues and checklists.
5. Update the implementation plan, audit findings, coverage matrix and documentation register. **The initial structural migration is now complete; project-specific system evidence remains a separate workstream.**

## Link and compatibility policy

The migration must not silently break readers or agent instructions.

- Use relative Markdown links and preserve exact anchors where they remain meaningful.
- Update links in human guidance, agent conventions, assessments, audit records, examples and handover material.
- Prefer one canonical page with short compatibility content over two full copies that can diverge.
- Do not rewrite unrelated links or reformat unrelated pages during a move.
- Do not claim that a new folder represents a complete system until its purpose, owner, dependencies, lifecycle, evidence and known limits are described.

## Acceptance criteria

The migration increment is acceptable when:

- the target system indexes explain the boundaries in plain language;
- the client Palette has one canonical UX vocabulary and one implementation-correspondence location;
- client, service and shared responsibilities are not silently conflated;
- pipeline and test systems have visible but honest future entry points;
- all changed relative Markdown links resolve;
- no stale canonical Palette links remain;
- `git diff --check` passes; and
- the audit and implementation records state which pages moved, which compatibility routes remain and what project-specific evidence is still missing.

This plan does not require a commit or push. Publication remains a separate explicit decision.
