# A Short Way Into the Guidance

A team can finish the code, demonstrate the main screen and still discover that nobody can explain who owns the user's failed submission, the operator's missing diagnostic or the next team's unsafe data change. The parts may work locally while the delivered service is still missing the structure, evidence or responsibility that makes the outcome dependable.

This page is a bridge into the guidance. It starts with situations people recognise, then offers a human route. Once the question is clear, the catalogues give shared names to the parts and the checklists help apply those names to a real decision. You do not need to follow every route or learn the vocabulary before finding something useful.

## Begin with recognition

Stories are often a better first teacher than a list of terms. The [Example Gallery](../examples/readme.md) shows ordinary decisions that seem reasonable locally but create wider problems. Each example has a starting situation and an improvement, so a reader can see the consequence before meeting the structure that helps.

The [Current State](./current-state.md) describes how a visible feature, framework default or missing boundary can gradually become the system's accidental architecture. [The Structure Before the Feature](./the-structure-before-the-feature.md) then explains why known responsibilities and dependencies need a place before construction spreads different assumptions.

## Choose the question closest to you

- **I am accountable for whether the organisation gets what it committed to.** [Sponsor Guidance](../stakeholders/sponsors/readme.md) follows promise, delivery, evidence, variance, whole-life value and escalation.
- **I am choosing worthwhile objectives within real constraints.** [Product Manager Guidance](../stakeholders/product-managers/readme.md) follows purpose, value, viability, investment, capacity, risk and longer-term direction.
- **I am deciding what valuable outcome and foundation should come next.** [Product Owner Guidance](../stakeholders/product-owners/readme.md) follows ordering, logical foundations, acceptance and evidence.
- **I am discovering what people, groups and affected subjects actually need.** [Business Analyst Guidance](../stakeholders/business-analysts/readme.md) follows meaning, representation, requirements, uncertainty and handoff.
- **I am deciding where responsibilities, systems and dependencies belong.** [Architect Guidance](../stakeholders/architects/readme.md) follows boundaries, relationships, obligations and coherent structure.
- **I am preparing an achievable implementation and readiness path.** [Technical Lead Guidance](../stakeholders/technical-leads/readme.md) follows contracts, buildability, dependencies, startup, delivery and evidence.
- **I am building the browser-side consumer experience.** [Front-end Developer Guidance](../stakeholders/developers/front-end.md) follows the SPA, client-side horizontal flows, component assemblies, accessibility, usability and browser security.
- **I am implementing a prepared service capability or technical boundary.** [Developer Guidance](../stakeholders/developers/readme.md) follows domains, contracts, LDMs, vertical slices, flows and operation.
- **I am testing whether the claims and boundaries hold.** [Tester Guidance](../stakeholders/testers/readme.md) follows predicates, failures, quality, accessibility, security, recovery and evidence.
- **I am taking responsibility for a live service.** [Service Provider Guidance](../stakeholders/service-providers/readme.md) follows the service promise, people, support, operation, maintenance and lifecycle.
- **I am operating, supporting or changing an occupied service.** [Operator Guidance](../stakeholders/operators/readme.md), [Support Guidance](../stakeholders/support/readme.md) and [Maintainer Guidance](../stakeholders/maintainers/readme.md) follow diagnosis, communication, recovery, compatibility and controlled change.

These are routes into shared work, not separate versions of the system. A front-end developer may need an architect's boundary, a tester's evidence or a Product Owner's acceptance condition. A Sponsor may need to understand the same evidence without becoming the person who produces it.

## Name the parts when the question is ready

When a story has made the problem visible, use the catalogue that gives the next question a stable name:

- [Stakeholder Roles](../shared/reference/catalogues/stakeholder-roles.md) places knowledge, authority, handoffs and responsibility boundaries.
- [Deliverable Systems](../shared/reference/catalogues/deliverable-systems.md) distinguishes delivery, service, consumer and testing systems.
- [Sites, Flows, Views and Components](../shared/reference/catalogues/sites-flows-views-components.md) gives the consumer experience a shape without making a view the owner of every rule.
- [Quality Perspectives](../shared/reference/catalogues/qualities.md) connects system quality, data quality and quality in use to context and evidence.
- [Conceptual, Logical and Physical Models](../shared/reference/catalogues/conceptual-logical-physical-models.md) keeps meaning, logical responsibility and physical implementation distinct.
- [Domains and Capabilities](../shared/reference/catalogues/domains-and-capabilities.md) places behaviour with the problem space and responsibility that give it meaning.

The [Engineering Catalogues](../shared/reference/catalogues/readme.md) index offers the wider shared map. It is more useful after the reader knows which question they are trying to answer.

## Apply the understanding

The [Engineering Checklists](../shared/reference/checklists/readme.md) are practical prompts for a design, review or delivery decision. They are intentionally later in the route. A checklist can remind a team to check a cookie flag, a recovery condition or an accessibility behaviour; it cannot explain why that condition matters or who has authority to decide it.

Use the relevant human route and catalogue first, then choose a checklist such as [Security in Transit](../shared/reference/checklists/security-in-transit.md), [Deliverables](../shared/reference/checklists/deliverables.md) or [Sites and Interfaces](../shared/reference/checklists/sites-and-interfaces.md). Record the answers with the service's requirements, decisions, tests and evidence.

When the question is really about where a responsibility lives, [Human System Guidance](../delivery/systems/readme.md) separates the client, service, pipeline, testing and shared perspectives. It is a boundary map, not a claim that every route has equal depth.

## Keep the route open

The guidance is not a test of endurance. A reader may stop when the current question is answered and return when the work changes. The useful result is not memorising every term. It is being able to name the responsibility, the boundary, the next question and the evidence that would make the decision trustworthy.

## Related guidance

- [Human Orientation](./readme.md)
- [Human Engineering Guidance](../readme.md)
- [Human System Guidance](../delivery/systems/readme.md)
- [Example Gallery](../examples/readme.md)
- [Engineering Catalogues](../shared/reference/catalogues/readme.md)
- [Engineering Checklists](../shared/reference/checklists/readme.md)
