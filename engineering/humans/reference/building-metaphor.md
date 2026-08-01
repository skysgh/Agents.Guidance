# The Building Metaphor

This page explains the building picture used throughout the guidance. It gives readers a shared way to understand foundations, contracts, objects, services, capabilities, flows and tenant experiences before those ideas are described in implementation vocabulary.

The metaphor is a teaching aid. Software is not literally constructed like a building. The picture helps us see which parts support other parts, where responsibility belongs and what may happen when a known boundary is missing.

## Why buildings help

Most people have some experience of buildings. They know that a temporary shelter, a family home, a shared apartment building and a high-rise have different construction needs. They also understand that the consequences of a failure change when more people rely on the building.

This makes building a useful teaching metaphor for software. A short-lived script can be built like a temporary shelter when its purpose and consequences are limited. An internal application used by one team may be more like a single dwelling. A shared service used by several teams may be more like a multi-unit building, where shared entrances, utilities, maintenance and rules matter. A service used by external people, organisations or systems is closer to a high-rise or commercial building. It needs deliberate foundations, clear boundaries, safety checks, operating services and evidence that it is being managed responsibly.

The larger the audience, the longer the expected service life, the greater the external reliance and the greater the legal, financial or reputational consequence of failure, the more deliberate the construction needs to be. The building size is not a badge of importance. It is a way to think about consequences and the amount of structure needed to manage them.

A building is not successful merely because it was constructed well. Once people move in, it must remain secure, accessible, accurate in the services it provides and usable by the people who depend on it. Building establishes the structure and operating keeps that structure dependable as people, needs, conditions and surrounding services change.

### Boundaries face inward and outward

A property boundary is not the edge of the architect's responsibility. The architect must understand what belongs inside the property, but also what the property must respect and share outside itself.

A building may sit inside a local character or conservation zone, a district planning zone and national building codes. Those wider systems constrain its height, materials, access, drainage, safety, appearance and use. They are not optional decoration added after the design is complete. They are obligations that shape what can responsibly be built.

The building also has neighbours. A shared drive, access route, wall, service connection, drainage path, boundary structure or right of way creates a relationship with another property. The architect cannot design inward from the plot boundary while pretending that the boundary has no outward consequences. The design must state who may use the shared resource, who maintains it, what happens when it is blocked or damaged and how disputes or changes are handled.

Software boundaries work in the same way. A service must protect what belongs inside its domain, but it must also understand the enterprise process, policy, regulation, legal duties, interfaces, dependencies and downstream systems outside the codebase. A shared database, identity provider, storage container, queue, reporting feed or archive is like a shared drive: it has more than one participant and needs an explicit agreement about access, ownership, maintenance, failure and change.

The architect therefore designs from the boundary in both directions. Inward, they define the capabilities, contracts and responsibilities the service owns. Outward, they identify the systems, people, rules and shared resources that constrain or depend on it. See [Systems Within Systems](../orientation/systems-within-systems.md) for the wider obligation model.

## The parts of the building

The building picture gives names to relationships that are easy to lose in a screen, ticket or code file. These names are not a replacement for precise technical terms. They are a route into them.

### Bedrock and foundations

Bedrock represents dependable evidence: what the team has learned about the business, the users, the existing system, the risks and the obligations around the service. Foundations represent the structural necessities that allow the rest of the system to stand, including contracts, security, lifecycle, data protection and operational responsibilities.

A foundation is not valuable because it is impressive or large. It is valuable because the parts above it can rely on it. A feature that works only because each caller remembers an unwritten rule is standing on uncertain ground.

### Contracts and formwork

A contract says what a part of the system provides, what it needs, what it means and how it behaves when something goes wrong. It gives different parts a shared agreement before they are connected.

In the building picture, contracts are part of the structural frame and also act like formwork. Formwork holds wet concrete in the intended shape while it sets. In the same way, a contract gives implementation a stable shape while the details are being built and refined. It helps the team discover disagreement before that disagreement has spread through callers, storage and user experiences.

Concrete pouring can feel frustrating because the builders may construct a temporary wall only to remove it again. That is not wasted work. The formwork is formal work that must exist before the concrete and the supporting services can be developed safely around it. It fixes the shape, position and boundaries while the concrete becomes strong enough to carry its load. If everyone focuses only on the concrete because it is the visible material, the building can still be poorly shaped.

Software teams can make the same mistake when everyone focuses on objects. Objects are visible in code and feel like tangible progress, but they are not the whole structure. The delayed work of designing contracts gives later objects a clearer shape, responsibility and place. That delay can feel less satisfying than creating a class or record immediately, but it allows the resulting system to become stronger without each object quietly inventing its own rules.

This matters especially in a high-rise or shared service. A weak boundary is not confined to one room; it can be repeated across many floors, capabilities or consuming systems. Time spent making the formwork sound can therefore prevent much more expensive changes after the structure has spread.

Whether that preparation is creating agility or merely delaying useful work is a sequence and scope decision. [Speed is not the same as agility](../orientation/design-before-build-and-wgf.md) explains how to make that decision.

Formwork is not the finished building. A contract should not contain every private implementation detail, and it should not pretend that undiscovered business detail is already known. It should be clear enough to protect the boundary and open enough to allow the responsible implementation to change behind it.

### Objects: blocks and pours

Objects are the parts that give the contracts a concrete form. They may represent configuration, settings, policies, definitions, mappings, business concepts or other named responsibilities.

Some objects are like concrete masonry units: prepared pieces with a clear shape that can be placed where they belong. Other objects are like pours: material shaped in place because it must connect several structural needs at a particular boundary. Both are useful, but neither should be mistaken for the formwork, the building or the responsible design that gives them a place.

A block or pour should have a clear responsibility, a known responsible boundary and a reason for existing. Reusing one object everywhere may look efficient while placing several unrelated responsibilities in the same piece. Separating every small idea into its own object may produce a pile of pieces with no useful structure. The question is whether the object has a coherent job at the boundary where it is used.

### Services: building systems

Services are the systems that use objects and contracts to provide an operating capability. They may coordinate a use case, apply policy, read or change state, call an external system or make a capability available to another boundary.

A building needs more than walls. It needs systems such as access, water, power, communications, ventilation and maintenance. Software services play a similar role: they make the structural parts useful to the people and systems that rely on them.

A service should not quietly take responsibility for every concern it touches. Its responsibility, dependencies, security decisions, failure behaviour and lifecycle should be visible. Otherwise the service becomes a room containing an unrecorded collection of utilities, and later changes become difficult to make safely.

### Shafts and vertical slices

A vertical slice carries one owned capability through the relevant layers of the building. It may begin at an external boundary, pass through application rules and objects, and reach persistence or an external effect.

The shaft image helps show why a capability should remain coherent as it travels through those layers. The code may be organised into layers, but responsibility for the capability should not disappear between them. A vertical slice is the unit that can be delivered, tested and operated as a meaningful whole.

### Slabs and shared boundaries

Slabs separate floors and provide a stable surface for the spaces above them. In software, shared boundaries and platform services play a similar role. Examples include identity, access control, configuration, startup, diagnostics, persistence conventions and messaging boundaries.

A shared slab must have an understood responsibility and a way to change without surprising every tenant above it. Shared does not mean without responsibility. The team responsible for a shared boundary must know its consumers, compatibility expectations, lifecycle and failure behaviour.

### Flows and tenant spaces

Horizontal flows move through the building rather than belonging to one vertical shaft. In software, a flow coordinates several capabilities into a journey such as preparing and submitting a request, assessing and deciding, or publishing and maintaining an item.

Tenant spaces represent experiences adapted for particular users or organisations. The tenant experience may change the rooms, signs and routes that a person sees without changing who owns the underlying capability. A tenant-specific experience should not quietly duplicate the rules that belong to the shared capability.

## Buildings have different sizes

The smallest building in this picture is a **temporary shelter**, like a short-lived script or one-off integration. Its materials can be simple because its life and consequences are limited. A **single dwelling** is like a small internal application used by one team. A **multi-unit building** is like a shared service used by several teams or groups, where common spaces and services need care. A **high-rise or commercial building** is like a service used by external people, organisations and systems, where failure can affect people beyond the team that built it.

A small internal application may tolerate lighter construction when its failures can be handled within the team and its life is limited. That does not make disorganisation good; it makes the consequences more contained.

When external consumers rely on a service, the organisation's reputation, obligations and relationships are also exposed. At that point, clear contracts, boundaries, security, diagnostics, recovery and compatibility are not monumental extras. They are the minimum structure needed to operate responsibly.

The guidance is mainly concerned with shared services and public-facing or enterprise systems. These systems are sometimes treated as internal applications even when other people and organisations depend on them. A service should not be treated as small merely because it began as an internal tool.

Different buildings also need different kinds of builders. [Different Types of Builders](./builders-metaphor.md) explains how platform, integration, maintenance, test and system developers contribute different strengths and risk perspectives to the same building.

[Systems Within Systems](../orientation/systems-within-systems.md) explains how a service participates in wider physical, logical, enterprise, regulatory and legal systems.

## How to use the picture

Use the building picture to show where a responsibility belongs and what it depends on. Do not use it as decoration or as a substitute for the concrete software decision.

Questions about what should be designed first, what should be built now and what can be deferred belong to [The Structure Before the Feature](../orientation/the-structure-before-the-feature.md). This page supplies the building-to-software relationships that help make those decisions visible; it does not replace the sequence and scope guidance.

The practical question is not, "Are we building enterprise software?" It is, "Who relies on this service, for how long, and what happens if its assumptions are wrong?" Those answers should determine how much design, evidence and operational structure the service needs.

Return to concrete software terms once the relationship is clear. The [Human Documentation Writing Style](./writing-style.md) explains how to introduce and use the metaphor in other human-facing documents.
