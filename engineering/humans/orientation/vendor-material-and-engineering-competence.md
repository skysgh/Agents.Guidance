# Vendor Material and Engineering Competence

Vendor material is useful, but it has a commercial purpose. It is usually written to help a reader understand, adopt and use a vendor's product or paid service quickly. It is not normally a complete education in software engineering, system design, operations, security, law or architecture.

That is not necessarily deceptive. The vendor is explaining its product and reducing the effort required to become a customer or successful user. The organisation and the engineering team remain responsible for learning how that product fits into the whole system they are creating.

## Product fluency is not system competence

A developer may become very good at configuring a cloud service, calling an API, defining a framework model or following a reference sample. An architect may become very good at arranging the vendor's products into a familiar diagram. Those are useful skills, but they do not by themselves demonstrate competence in designing the service that depends on them.

Product fluency answers questions such as:

- Which setting enables this feature?
- Which API call creates the resource?
- Which framework type represents the record?
- Which deployment template starts the service?
- Which vendor-supported integration is easiest to configure?

System engineering must also answer:

- What responsibility does this capability have in the whole service?
- Which boundary owns its data, policy, lifecycle and failure behaviour?
- What must happen when the vendor service is slow, unavailable, changed or retired?
- How are access, classification, retention, erasure, audit and recovery enforced?
- What evidence proves that the service remains safe and dependable?
- How will the organisation operate, migrate, replace or exit the dependency?

Knowing how to use a product is not the same as knowing whether the resulting system is well designed.

## The commercial system around the team

A team works inside a commercial system that includes vendor documentation, tutorials, quickstarts, sample repositories, reference architectures, training, certification, marketing, sales material, support plans, product roadmaps and pricing. These materials can be accurate and valuable while still presenting the vendor's product boundary as the natural centre of the solution.

The team must therefore ask what the material leaves outside its frame. A quickstart may omit multi-user authorisation, data classification, retention, backup and restore, regional processing, tenant isolation, cost controls, monitoring, incident response, accessibility, legal obligations and long-term change. A reference architecture may describe how to assemble the vendor's services without deciding whether those services are appropriate for the business responsibility, risk level or operating capacity of the organisation.

Vendor material is one input to engineering judgment. It is not an independent architecture review, a complete threat model, a service operating model or proof that the proposed design satisfies the organisation's obligations.

## Out of the box is a baseline

Out-of-the-box behaviour is usually designed to make a product usable with reasonable initial effort. That is valuable for learning, evaluation and early construction. It is not proof that the service is ready for its real audience, data, load, failure conditions, legal context or operational consequences.

The first usable configuration often provides just enough to demonstrate the product:

- a default identity or access model;
- a convenient storage shape;
- a happy-path request flow;
- default network exposure;
- basic logs or metrics;
- a single-region or single-instance assumption;
- provider-selected retention and backup behaviour; or
- a framework default that is safe only for a narrow context.

Stopping at that point usually produces the minimum product usage path, not a dependable production service. The result may break under scale, concurrency, provider outage, partial failure, recovery, upgrade, data growth, support intervention or a change in the people who must use it. It may also make later security, accessibility, retention, migration or compliance work expensive because the default has already become an unexamined architecture.

Vendor defaults are decisions. Treat them as hypotheses to verify, not as neutral facts, and not as the objective.

## What the engineering team must add

Before adopting a vendor capability, separate the vendor's product contract from the service's responsibility. Record:

- the business or technical capability the dependency supports;
- the owning domain and Logical Deployment Module;
- the data, policy and decision boundaries around it;
- the identity, authorisation and classification model;
- the required availability, performance, capacity and recovery behaviour;
- the retention, export, correction, erasure, audit and evidence obligations;
- the monitoring, alerting, support and operational ownership;
- the cost, quota, rate, region and usage assumptions;
- the upgrade, compatibility, migration and exit conditions; and
- the tests that prove the service remains correct when the dependency is degraded or unavailable.

Then verify which parts are provided by the product, which parts are configured by the team, which parts require additional code or another service and which parts remain an organisational or human duty. Do not count a vendor feature as a fulfilled obligation until its behaviour, boundary and evidence are understood in the actual service context.

## Architecture must remain independent

The architecture should begin with the responsibility and outcome the service must preserve. The team can then evaluate whether a vendor product is an appropriate implementation, one option among several or only a temporary accelerator.

Do not let a vendor API define the domain model, or let a product's resource names become the organisation's business concepts without deliberate mapping. Keep vendor-specific behaviour behind the boundary that owns the integration. Expose a service-owned contract where policy, security, lifecycle, failure or replacement matters.

This does not mean hiding every vendor type or rejecting managed services. It means being able to explain what the service would still mean if the provider, framework, hosting model or product name changed.

## Technology choice is an organisational decision

Choosing a library, persistence technology, framework or platform is not a developer's personal preference. The choice must fit the organisation's maintenance capability, extension needs, security and supply-chain standards, operating environment, approved technology registry and realistic ability to support the result after the original team has moved on.

An approved technology is not automatically the right choice for every problem. It is an organisationally supported option whose lifecycle, ownership, skills, security posture, licensing, interoperability, operational model and replacement path have been considered. The team still has to show that it fits the capability being built.

An unapproved technology is not automatically forbidden forever. It is an exception that needs a documented reason, alternatives considered, consequences, capability-building plan, support owner, security and supply-chain review, operational evidence, exit conditions and a review date. Do not introduce an unfamiliar dependency because one developer prefers it or because its API makes the first implementation shorter.

For example, choosing Marten and event sourcing instead of an established Entity Framework and relational persistence capability may be technically valid, but it is a significant organisational decision. Event schemas, replay, projections, correction, versioning, retention, reporting, operational tooling, training, incident response and migration all become part of the capability the organisation must maintain. For a government enterprise or other organisation that is not primarily a software product company, with no prior Marten or event-sourcing experience, the default risk is high unless the problem genuinely requires the approach and the organisation is prepared to own the additional capability for its full life.

The same caution applies to libraries maintained by a single person or a small, weakly governed community. The concern is not the number of contributors by itself. It is whether the organisation can assess provenance, security response, release continuity, compatibility, succession, support and exit if the maintainer disappears or the project changes direction.

## Keep the registry independent

An approved technology registry is an engineering and organisational control, not a catalogue assembled by sales influence. Its decisions should be based on capability fit, lifecycle, maintainability, extensibility, security, operational support, total cost, interoperability, skills and exit options. Vendor demonstrations, procurement pressure, “enterprise” branding and no-code or low-code claims are inputs to evaluate, not architecture decisions.

The registry must not quietly remove an appropriate custom-code capability merely because a vendor wants the organisation to adopt a product suite. A low-code or managed product may be the right implementation for a bounded responsibility, but the organisation must record what it gives up: control of behaviour, testability, portability, data ownership, custom extension, performance transparency, integration freedom or the ability to continue operating without the vendor.

Separate architecture review from procurement and sales advocacy. Require independent technical review, evidence from comparable operating environments, a clear owner, a support model and a credible exit or replacement path. The registry should record why a technology is approved, where it is appropriate, where it is not, whether it is active or approaching sunset and what conditions trigger reconsideration.

## Role responsibilities

The **architect** challenges the product-shaped view. They identify the service's responsibilities first, compare the vendor's assumptions with the system's obligations and make dependencies, alternatives, failure modes, operating model and exit conditions visible.

The **tech lead** turns that decision into an operable implementation. They check that defaults are explicit, boundaries are enforced, readiness and diagnostics are meaningful, and the team has tested the real limits and failure behaviour of the chosen service.

The **developer** learns the product deeply enough to use it safely, but does not mistake a quickstart or generated configuration for the completed design. They raise gaps around security, data, lifecycle, performance, recovery and support instead of silently accepting the nearest default.

The **organisation** must provide time and access to independent learning, review and assurance. It cannot reasonably demand whole-system competence while providing only vendor tutorials and measuring only visible feature completion.

## Review questions

When a design relies on vendor or framework material, ask:

1. What part of the material teaches product operation, and what engineering questions remain unanswered?
2. Which defaults are active, and what context makes each one safe or unsafe?
3. What happens during outage, timeout, quota exhaustion, partial success, duplicate delivery and provider change?
4. Who owns the data, policy, access decision, retention schedule and recovery outcome?
5. Which obligations apply even though the quickstart does not mention them?
6. What evidence proves the service works beyond the vendor's happy path?
7. Can the dependency be upgraded, migrated, replaced or exited without losing meaning or control?
8. What would an independent reviewer challenge if the vendor product were removed from the diagram?

The goal is not to distrust every vendor or rebuild every managed capability. The goal is to ensure that using a product remains one engineering decision inside a system design, rather than becoming a substitute for system design.

## Related guidance

- [Why Software Needs Engineering](./why-software-needs-engineering.md)
- [The Current State](./current-state.md)
- [Systems Within Systems](./systems-within-systems.md)
- [What Developers Need to Know](./developers-need-to-know.md)
- [What Tech Leads Need to Know](./tech-leads-need-to-know.md)
- [What Architects Need to Know](./architects-need-to-know.md)
- [Dependency and Supply-Chain Conventions](../../agents/conventions/development/dependencies.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
