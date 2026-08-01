# Engineering Human Orientation

This folder explains why the guidance exists and how different people can contribute to one dependable design.

The pages follow a gradual movement from recognition to action. [The Current State](./current-state.md) begins with the familiar ways that systems become difficult to change. Once that problem is visible, [The Structure Before the Feature](./the-structure-before-the-feature.md) explains why known responsibilities, boundaries and dependencies need a place before implementation spreads assumptions. [What This Guidance Gives](./what-this-guidance-gives.md) then shows how different roles add their knowledge to that shared design. Finally, [Design Before Build and WGF](./design-before-build-and-wgf.md) explains how to choose what to build now while keeping later work possible.

## Choose a starting point

If this is your first visit, read [The Current State](./current-state.md), [The Structure Before the Feature](./the-structure-before-the-feature.md) and [What This Guidance Gives](./what-this-guidance-gives.md). Then choose the route that matches the work in front of you:

- **Developer with a capability:** [What Developers Need to Know](./developers-need-to-know.md), then [Human Development Guidance](../development/readme.md), [Vertical Slices](../../agents/conventions/capabilities/slices.md) and any applicable foundation or development conventions.
- **Technical lead preparing a service:** [What Tech Leads Need to Know](./tech-leads-need-to-know.md), then [Human Development Guidance](../development/readme.md), [Startup and Discovery](../../agents/conventions/foundations/startup.md) and [Operations](../../agents/conventions/development/operations.md).
- **Architect mapping a service:** [Systems Within Systems](./systems-within-systems.md), [Legal and Regulatory Context](./legal-context.md), [Logical Deployment Modules](../development/ldms.md) and [What Architects Need to Know](./architects-need-to-know.md).
- **Team choosing technology:** [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md), then the applicable dependency and registry conventions.

The useful outcome of the first reading is not memorising terms. It is being able to name the capability, its responsible boundary, the next design question and the evidence needed before construction proceeds.

The remaining orientation papers introduce particular foundations when they become useful: [Why Software Needs Engineering](./why-software-needs-engineering.md), [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md), [Phases, Roles and Stakeholders](./phases-roles-and-stakeholders.md), [Systems Within Systems](./systems-within-systems.md), [Legal and Regulatory Context](./legal-context.md), [What Developers Need to Know](./developers-need-to-know.md), [What Tech Leads Need to Know](./tech-leads-need-to-know.md), [What Architects Need to Know](./architects-need-to-know.md), [Configuration and Settings](./configuration-and-settings.md), [Common Flows](./flows.md), [Responsible Boundaries and Deferred Design](./responsible-boundaries-and-deferred-design.md) and [API Lifecycle](./api-lifecycle.md). The building and builder comparisons remain in the shared [reference material](../reference/readme.md), where they can be revisited without interrupting the main progression.

## Which question does each page answer?

- [The Current State](./current-state.md) identifies the recurring drift and failure patterns that make a service difficult to change.
- [Why Software Needs Engineering](./why-software-needs-engineering.md) explains why software teams need deliberate whole-system engineering, especially when a service carries entrusted records, money, access or essential decisions.
- [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md) explains why product fluency and out-of-the-box usage are not substitutes for system-design competence.
- [The Structure Before the Feature](./the-structure-before-the-feature.md) explains what should be understood and placed before construction spreads assumptions through the service.
- [What This Guidance Gives](./what-this-guidance-gives.md) shows how different contributors add knowledge to the shared design.
- [Systems Within Systems](./systems-within-systems.md) explains how digital systems sit inside wider physical, logical, enterprise, regulatory, legal and international systems of obligations and capabilities.
- [Legal and Regulatory Context](./legal-context.md) explains how to identify the jurisdictions where a service is offered and delivered, including wider implications created by access, processing, hosting and connected providers.
- [What Developers Need to Know](./developers-need-to-know.md) explains how developers move from problem decomposition through domains, contracts, slices, flows and operation. [Human Development Guidance](../development/readme.md) explains the LDM, layers and code-purpose categories beneath that route.
- [What Tech Leads Need to Know](./tech-leads-need-to-know.md) explains how technical leads protect platform sequence, ownership, readiness and evidence.
- [What Architects Need to Know](./architects-need-to-know.md) explains how architects map interfaces, dependencies and downstream obligations across the whole service landscape.
- [Phases, Roles and Stakeholders](./phases-roles-and-stakeholders.md) separates when responsibility changes, who contributes and who depends on the result.
- [Design Before Build and WGF](./design-before-build-and-wgf.md) explains how to choose what to build now while keeping later construction possible.
- [Common Flows](./flows.md) and the capability conventions catalogue recurring shapes for journeys and owned capabilities.

The main route is therefore about recognition, structure, contribution and construction choice. The other pages answer narrower questions once that route has given the reader enough context.

## Related guidance

- [Human Engineering Guidance](../readme.md)
- [Human Reference Material](../reference/readme.md)
- [Human Examples](../examples/readme.md)
