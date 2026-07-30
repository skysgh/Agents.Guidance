# What the Guidance Gives Each Stakeholder

The guidance is a shared way to see the system before implementation details scatter across projects. It is not asking every stakeholder to become an architect or a programmer. Each role needs a different answer from the same structure.

No single role can see the whole system alone. Business analysts contribute domain meaning and decisions. Developers test whether the design is implementable. Testers expose whether the claimed boundaries hold. Operations contributes lifecycle, readiness and recovery knowledge. Security and assurance contribute protection and evidence requirements. Architects preserve coherence across the views. The guidance is the meeting surface between these contributions, not architecture speaking over them.

## For everyone

The guidance gives a common vocabulary:

- **contract**: what a boundary promises and what it requires;
- **object**: a thing that carries meaning, state or policy;
- **service**: a thing that composes objects into useful behaviour;
- **registry**: an owned place that collects and governs participants;
- **vertical slice**: one complete owned capability;
- **horizontal flow**: a journey that coordinates capabilities; and
- **deferred capability**: something not built yet but designed well enough that its future place and stewarding boundary are known.

This vocabulary lets people discuss the same system without assuming that a ticket, model, endpoint or table is the whole design.

The guidance also separates two planning questions:

- **DBB: Design Before Build** asks whether the known structure and contracts are clear enough to support implementation.
- **WGF: What Goes First?** asks which already-designed capability or part should be constructed first.

These reminders prevent two opposite mistakes: building without a shared design, and treating design as a reason to delay all useful construction.

WGF is not a label for an intuition that something feels important. For each inclusion, deferral or omission, record the consequence of doing it and the consequence of not doing it. Then record the stewarding boundary, dependency, evidence needed and condition that would change the decision.

The relevant design question is usually not "Which person owns this?" It is "Which boundary or module stewards this responsibility, what contract expresses it, and which role must be consulted when a decision is needed?" That keeps design achievable even while organisational assignments are changing.

## For business analysts and product people

The guidance does not ask a business analyst to design database tables or write service classes. It asks for a clearer description of the business meaning that developers need:

- What outcome is wanted?
- Who owns the decision or record?
- Who may see, change, approve or withdraw it?
- What is the difference between a draft, submitted, approved, published or closed state?
- What must be remembered for audit or history?
- Which other capabilities does this outcome depend on?
- What is the business meaning, separate from the first screen that displays it?

A ticket is an important input, but it is not a complete logical design. The guidance helps the team turn a ticket into a shared capability description without blaming the person who wrote the ticket for not being an engineer.

## For developers

The guidance tells developers where to put work and what not to couple together:

- begin with a stewarded contract rather than a convenient concrete model;
- keep transport, application, domain and persistence responsibilities distinct when their meanings differ;
- use governed queryability for flexible reads and explicit commands for writes;
- map deliberately at boundaries;
- keep access and classification rules close to the boundary that owns them;
- make startup participants contract-bearing and observable; and
- build a complete vertical slice through the prepared structure.

It reduces the number of architectural decisions that each developer has to reinvent while coding.

It also gives a practical answer to "I already do all that." The claim is tested against one real capability, not against familiarity with individual words. The capability should be able to point to its contract, owner, implementation, security decision, lifecycle, mapping, persistence policy, startup participation, tests and explicit deferrals. Where one of those is absent, the work may contain the idea but has not yet assembled the complete pattern.

## For testers and people learning automation

The guidance turns architecture into observable checks. A tester does not need to understand every implementation detail to ask useful questions:

- Does the controller call the application boundary rather than persistence directly?
- Can an unauthorised actor see or change the record?
- Does the query return only mapped and permitted fields?
- Are invalid state transitions rejected?
- Is a duplicate command safe to retry?
- Does startup discover and invoke each required participant in the correct phase?
- Does a schema or dependency failure affect readiness as intended?
- Does a deferred capability have a documented stewarding boundary and technical contact path?

These questions can become unit tests, integration tests, contract tests, startup tests and review checks. The guidance gives automation a structure to verify rather than limiting testing to whether the screen appears to work.

## For technical leads and architects

The guidance provides a way to review design without reviewing every line first:

- Is ownership clear?
- Are contracts narrower than implementations?
- Are dependencies crossing declared boundaries?
- Is the known whole designed even where construction is staged?
- Are security, lifecycle, persistence and operational obligations explicit?
- Is reflection being enabled by contracts, or is it hiding poor wiring?
- Is a flow coordinating slices or absorbing their rules?
- Is deletion retiring a capability deliberately, with its consequences understood?

It also provides a place to record deliberate divergence when the standard structure is not suitable.

## For delivery and programme stakeholders

The guidance separates three different questions that are often confused:

- **What is designed?** The intended structure, contracts and ownership are known.
- **What is built?** A selected part has been implemented and tested.
- **What is deferred?** The intended place and boundary are known, but construction is staged by budget, sequencing or evidence.

This makes architectural risk visible without pretending that every designed capability must be delivered in the first release.

WGF gives delivery discussions a consequence record rather than a contest of preferences. It makes clear what is being included, what is being deferred, what risk is accepted, who owns the next decision and what evidence will justify changing priority.

## For operators and support teams

The guidance treats startup and lifecycle as operational concerns, not just developer wiring. It asks the system to make visible:

- which configuration and settings were accepted;
- which modules and participants were discovered;
- which schema and storage dependencies are ready;
- which mappings, cache providers and registries were registered;
- what failed, degraded or was excluded; and
- why the service is or is not ready.

This is more useful than reconstructing startup from scattered console lines or asking the original developer what order the host calls must run in.

## For security, privacy and assurance roles

The guidance makes access, classification, audit and recovery design inputs. It asks:

- what is the protected resource;
- who is acting and in what context;
- which boundary enforces visibility and mutation rights;
- which fields may be queried or projected;
- what must be recorded;
- what happens when a dependency or authorisation decision fails; and
- whether cache, settings, diagnostics and exports can leak protected information.

Security is not a final inspection of a feature that was designed without it.

## For platform and framework teams

The guidance distinguishes reusable platform contracts from product-specific domain behaviour. Platform teams can provide stable capabilities for:

- configuration and settings;
- startup discovery and diagnostics;
- mapping and query projection;
- persistence and schema contribution;
- caching and storage;
- identity and access context; and
- registries and lifecycle participants.

Product teams can then use those capabilities without reimplementing their foundations, while retaining ownership of their domain concepts and flows.

## The shared outcome

The guidance does not guarantee that every design decision will be correct. It does something more practical: it makes the intended structure, current construction, deferrals, ownership and evidence visible to more than one role.

That is how a system becomes maintainable across people and generations. A person should be able to join later, understand where a capability belongs, see why a boundary exists, test the important invariants and continue construction without guessing what the previous team imagined.

## Learn by recognition

The guidance is intended to be recognised in working situations, not admired as an abstract framework. The [example gallery](./examples/README.md) presents several common starting points and shows how different roles contribute to the improvement. A reader does not need to agree with every example before learning from the one that matches a problem they have experienced.

## Related reading

- [Human Start Here](./HUMAN-START-HERE.md)
- [The Current State](./HUMAN-CURRENT-STATE.md)
- [Developers Need to Know](./conventions/developers-need-to-know.md)
- [Development Principles](./conventions/principles.md)
