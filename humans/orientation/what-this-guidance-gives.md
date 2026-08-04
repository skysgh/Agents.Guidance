# What the Guidance Gives Each Stakeholder

## Purpose

This paper explains how the guidance helps different people contribute to the same system design. It is not a request for every person to become an architect or programmer.

The guidance is a shared way to see the system before implementation details scatter across projects. It is not asking every stakeholder to become an architect or a programmer. Each role needs a different answer from the same structure, and no single role can see the whole system alone.

Business analysts contribute domain meaning and decisions. Developers test whether the design is implementable. Testers expose whether the claimed boundaries hold. Operations contributes lifecycle, readiness and recovery knowledge. Security and assurance contribute protection and evidence requirements. Architects preserve coherence across the views. The guidance is the meeting surface between these contributions, not architecture speaking over them.

Imagine a team receiving a request to introduce a new service capability. The request begins with a useful outcome, but it does not yet explain the whole system. Someone must clarify what the outcome means, someone must give it a responsible place, someone must build it, someone must test whether the claimed boundaries are real and someone must keep it dependable after release. Other people may use it, fund it, regulate it or carry the consequences when it fails.

The work becomes difficult when each person answers only the question nearest to their role. The business description becomes a screen, the screen becomes a model, the model becomes a persistence contract and the first implementation becomes the only explanation of what the capability means. The guidance gives these contributors a shared picture before those local decisions harden into different interpretations.

## The short version

The guidance gives the team a shared picture before each role adds its part. It helps the team agree what a capability means, where it belongs, how it is protected, what is built first and what is deliberately deferred.

That shared picture includes the wider systems around the service. [Systems Within Systems](./systems-within-systems.md) explains why a digital system must be understood as part of wider enterprise, physical, policy, regulatory, legal and international arrangements, each carrying obligations, duties, capabilities and evidence.

## The change story

Imagine one business unit running one restaurant. It is the only customer the team has today. That does not mean its current menu, kitchen process or organisation will stay fixed. Over time it may change how it serves people, add catering, alter its ordering route or take on new responsibilities. The organisation around it may also merge departments, split teams or move responsibilities between groups. Those changes happen at different speeds and for different reasons, but both should be possible without rebuilding the whole system.

The building analogy makes the role handoff visible. The architect designs the durable restaurant-capable structure rather than freezing one current arrangement into it. The technical lead recognises that design, checks whether the available team, technology, dependencies and constraints can achieve it, and plots the construction path. The developer builds the agreed part of the structure and keeps its responsibility intact. A different tenant is only a later resilience test: could the building be adapted for another restaurant without making the current design ruinously expensive to change?

This is why abstraction matters even when there is one customer. The first responsibility is to help that customer change safely. The second is to help the organisation change around the capability. A possible future tenant simply tests whether the design has preserved enough durable structure to keep that option open.

## For everyone

The guidance gives the team a common vocabulary for following that capability through the system. A [**contract**](../shared/reference/glossary.md#contract) says what a boundary promises and requires. An **object** carries meaning, state or policy. A **service** composes objects into useful behaviour. A [**registry**](../shared/reference/catalogues/logical-building-blocks.md#registry) is an owned place that collects and governs participants. A [**vertical slice**](../development/vertical-slices.md) carries one complete owned capability, while a [**horizontal flow**](../shared/reference/glossary.md#flow) coordinates several capabilities into a journey. A **deferred capability** is not built yet, but its future place and responsible boundary are known.

[Liberation Through Clarity](../shared/liberation-through-clarity.md) explains the personal benefit of this shared structure for developers, Business Analysts, Product Managers, Product Owners, architects, technical leads, testers, operators and maintainers.

This vocabulary lets people discuss the same system without assuming that a ticket, model, endpoint or table is the whole design.

The central architectural act is to decompose a stated problem until the things, relationships, states, decisions and rules that matter can be recognised. Those are the ontological elements of the relevant business or technical domain. Contracts protect their boundaries so they can be isolated and tested. Services, registries, startup, persistence and other infrastructure provide the dependable building in which those elements can operate. This is why the guidance treats technical structure and Domain thinking as one connected responsibility, not as two competing schools.

The guidance also separates two planning questions. **Design Before Build**, or **DBB**, asks whether the known structure and contracts are clear enough to support implementation. **What Goes First?**, or **WGF**, asks which already-designed capability or part should be constructed first.

These reminders prevent two opposite mistakes: building without a shared design, and treating design as a reason to delay all useful construction.

WGF is not a label for an intuition that something feels important. When the team includes, defers or omits part of the design, it records the consequences in both directions, the responsible boundary, the dependency, the evidence needed and the condition that would change the decision.

The relevant design question is usually not "Which person owns this?" It is "Which boundary or module carries this responsibility, what contract expresses it, and which role must be consulted when a decision is needed?" That keeps design achievable even while organisational assignments are changing.

## When governance is thin

Do not wait for a perfect governance structure before making responsible decisions. A team can begin with a short decision record and review it with the people who will build, operate, secure and depend on the result. Mature governance can later provide a stronger route; the questions remain useful even when the team has to govern itself.

For a new capability, ask:

- What does the capability mean, and who depends on it?
- Which boundary or module can keep its contract, data, security and lifecycle coherent?
- What must be true before construction or operation is safe?
- What is deliberately deferred, and what would cause that decision to change?
- Who will review the decision when the dependency, risk or ownership changes?

The record can be a small markdown page, issue or register entry. The point is to make responsibility and uncertainty visible without creating a process larger than the decision requires.

## The foundation: keep the meaning intact

This is the most important distinction in the guidance. A business request is usually **conceptual**. It describes what people mean, what outcome they need, which decisions matter and what they recognise as a useful result. It is allowed to use business language and remain incomplete as an implementation design.

The service still needs a **logical** design before construction spreads assumptions. In this guidance, that logical domain design is the **ontological model of the business domain**. In plain language, it is the system's answer to what kinds of things exist, how they relate, which identities and states matter and which rules should remain meaningful when today's client organisation or process changes. It is an abstraction from real business evidence, not a copy of one current screen or team structure. It does not need to name database tables or framework classes.

The **physical** design is how those responsibilities are represented and executed through interfaces, application and domain code, mappings, persistence, infrastructure and deployment. Physical code appears at every position in that stack. An endpoint or user-facing label may stay close to the conceptual language, while application and domain objects may use more abstract names to implement the logical ontological model. A table, ORM entity or framework component may be a good physical implementation, but it is not automatically the logical object or business concept that gave rise to it. When any physical representation becomes the only explanation of the business concept, the system may still run, but its ability to change without losing meaning is already in serious danger.

ANSI/SPARC gives related separations a formal vocabulary through external, conceptual and internal views. The practical lesson is simpler: Conceptual, Logical and Physical are model types, while interface, application/domain and storage are implementation positions. Do not let a screen become the ontological domain model, do not let that model become a storage schema by accident and do not ask one role to carry all three model types alone. [Conceptual, Logical and Physical Models](../shared/reference/catalogues/conceptual-logical-physical-models.md) develops this distinction. We are not following layering lore for its own sake. We are doing the harder work of abstracting on behalf of customers so that the system can carry durable meaning into future needs. The whole team must keep asking whether the implementation still expresses that meaning, and must carry it forward as the system grows. The [Quality Perspectives](../shared/reference/catalogues/qualities.md) catalogue follows that meaning through system qualities, data qualities and the outcomes people experience in use.

## For business analysts and product people

Product Managers steward objectives within considered context: purpose, users, value, viability, strategic fit, investment, budget, schedule, capacity, obligations and risk. [Product Manager Guidance](../stakeholders/product-managers/readme.md) explains how that longer view connects to Product Owner outcomes, complete elicitation, logical design, evidence and the whole service lifecycle.

The guidance does not ask a business analyst to design database tables or write service classes. It asks for the business meaning that developers need: the outcome, the responsible decision or record, who may see or change it, the difference between states such as draft, submitted, approved, published and closed, what must be remembered for history and audit, which capabilities it depends on and how its meaning differs from the first screen that displays it.

A ticket is an important conceptual input, but it is not a complete logical design. A business analyst is not responsible for a developer choosing the wrong object or allowing storage tables to define the service. The useful contribution is to make the conceptual decomposition visible: name the meaningful things, decisions, states, relationships, actors, evidence and outcomes, and distinguish them from the first screen or current process. That gives the team enough material to develop the logical design without pretending that the ticket already contains it.

The team should be able to carry the ticket forward and show how each important concept becomes a logical capability, contract, state or relationship. That conversation is not a demand for the business analyst to design classes or tables. It is a way to make sure that the business meaning does not disappear when implementation begins.

## For developers

Developer is a family name rather than one uniform role. The [Builders Metaphor](../shared/reference/builders-metaphor.md) describes platform and DevOps developers, integration developers, maintenance developers, test developers and system developers. Those roles overlap, but their experience gives them different strengths and different questions to ask. The dedicated [Guidance for Developers](./guidance-for-developers.md) paper follows the developer route from problem decomposition through domains, contracts, slices, flows and operation.

The guidance tells developers where to put work and what not to couple together. They begin with a contract that has a responsible boundary rather than a convenient concrete model. They keep transport, application, domain and persistence responsibilities distinct when their meanings differ, use governed queryability for flexible reads and explicit commands for writes, map deliberately at boundaries, keep access and classification rules close to the boundary that owns them, make startup participants contract-bearing and observable and build a complete vertical slice through the prepared structure.

It reduces the number of architectural decisions that each developer has to reinvent while coding. A developer should recognise that a ticket is conceptual. If the request is genuinely trivial and the conceptual and logical shapes are safely the same, the developer may carry it through directly and be able to explain why. Otherwise, implementation should pause before the first model or table is created until the logical thing to build is defined: its boundary, contract, state, relationships, mappings and persistence intention.

That pause is not asking the business analyst to finish the developer's design. It is asking the developer not to make an unreviewed logical decision by encoding the conceptual request directly into physical structure. The developer owns the responsibility to raise the gap and help make the logical design implementable.

It also gives a practical answer to "I already do all that." The claim is tested against one real capability, not against familiarity with individual words. The capability should be able to point to its contract, responsible boundary, implementation, security decision, lifecycle, mapping, persistence policy, startup participation, tests and explicit deferrals. Where one of those is absent, the work may contain the idea but has not yet assembled the complete pattern.

## For testers and people learning automation

The guidance turns architecture into observable checks. A tester does not need to understand every implementation detail to examine whether the controller calls the application boundary rather than persistence directly, whether an unauthorised actor can see or change the record, whether queries return only mapped and permitted fields, whether invalid state transitions are rejected, whether duplicate commands are safe to retry, whether startup discovers and invokes each required participant in the correct phase, whether schema or dependency failure affects readiness as intended and whether a deferred capability has a responsible boundary and technical contact path.

These questions can become unit tests, integration tests, contract tests, startup tests and review checks. The guidance gives automation a structure to verify rather than limiting testing to whether the screen appears to work.

Testers also help protect the layers. They test the conceptual outcome people care about, but they should keep asking what logical capability and boundary the behaviour belongs to. If a test can only describe the feature through table names, ORM entities or storage columns, that may be a smell that the logical design has collapsed into the physical one. Matching names are not proof of a problem; the concern is an unexplained one-to-one dependence in which storage structure dictates business meaning, state or behaviour. Test evidence should help expose that dependence rather than quietly treating it as inevitable.

## For technical leads and architects

The guidance provides a way to review design without reviewing every line first. A technical lead or architect can follow responsibility across the lifecycle, compare contracts with implementations, see whether dependencies cross declared boundaries, check that the known whole is designed even when construction is staged and ask whether security, lifecycle, persistence and operational obligations are explicit. They can also distinguish contract-led discovery from reflection that hides poor wiring, check whether a flow coordinates slices or absorbs their rules and examine whether deletion retires a capability deliberately with its consequences understood. [Guidance for Tech Leads](./guidance-for-tech-leads.md) adds the platform service sequence and the questions to ask when a required capability is missing.

It also provides a place to record deliberate divergence when the standard structure is not suitable. [Guidance for System Design Architects](./guidance-for-system-design-architects.md) develops the wider system map that technical leads need to understand: stakeholder interfaces, access within those interfaces, external dependencies and distinct downstream obligations. Those maps should also make important quality outcomes and evidence visible; [Quality Perspectives](../shared/reference/catalogues/qualities.md) explains how system, data and quality-in-use concerns connect without collapsing into one measure.

## For delivery and programme stakeholders

The guidance separates three different questions that are often confused. What is designed means that the intended structure, contracts and responsibilities are known. What is built means that a selected part has been implemented and tested. What is deferred means that the intended place and boundary are known, but construction is staged by budget, sequencing or evidence.

This makes architectural risk visible without pretending that every designed capability must be delivered in the first release.

WGF gives delivery discussions a consequence record rather than a contest of preferences. It makes clear what is being included, what is being deferred, what risk is accepted, which person, role or boundary is responsible for the next decision and what evidence will justify changing priority.

## For operators and support teams

The guidance treats startup and lifecycle as operational concerns, not just developer wiring. The service should make visible which configuration and settings were accepted, which modules and participants were discovered, which schema and storage dependencies are ready, which mappings, cache providers and registries were registered, what failed, degraded or was excluded and why the service is or is not ready.

This is more useful than reconstructing startup from scattered console lines or asking the original developer what order the host calls must run in.

## For security, privacy and assurance roles

The guidance makes access, classification, audit and recovery design inputs. Security, privacy and assurance roles help the team identify the protected resource, the actor and context, the boundary that enforces visibility and mutation rights, the fields that may be queried or projected, what must be recorded, what happens when a dependency or authorisation decision fails and whether cache, settings, diagnostics and exports can leak protected information.

Security is not a final inspection of a feature that was designed without it.

## For platform and framework teams

The guidance distinguishes reusable platform contracts from product-specific domain behaviour. Platform teams can provide stable capabilities for configuration and settings, startup discovery and diagnostics, mapping and query projection, persistence and schema contribution, caching and storage, identity and access context and registries and lifecycle participants.

Product teams can then use those capabilities without reimplementing their foundations, while retaining responsibility for their domain concepts and flows.

## The shared outcome

The guidance does not guarantee that every design decision will be correct. It does something more practical: it makes the intended structure, current construction, deferrals, responsibility and evidence visible to more than one role.

That is how a system becomes maintainable across people and generations. A person should be able to join later, understand where a capability belongs, see why a boundary exists, test the important invariants and continue construction without guessing what the previous team imagined.

## Learn by recognition

The guidance is intended to be recognised in working situations, not admired as an abstract framework. The [example gallery](../examples/readme.md) presents several common starting points and shows how different roles contribute to the improvement. A reader does not need to agree with every example before learning from the one that matches a problem they have experienced.

## Related guidance

- [The Structure Before the Feature](./the-structure-before-the-feature.md)
- [The Current State](./current-state.md)
- [Guidance for Developers](./guidance-for-developers.md)
- [Guidance for Tech Leads](./guidance-for-tech-leads.md)
- [Platform Services Reference](../shared/reference/platform-services.md)
- [Human Development Guidance](../development/readme.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
