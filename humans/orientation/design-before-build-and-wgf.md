# YAGNI versus WGF

## Purpose

This paper explains how to decide what to build first without allowing the first feature to decide the whole architecture. It is for anyone involved in deciding scope, design, implementation, testing or delivery.

## The short version

YAGNI helps prevent unnecessary construction. WGF helps prevent necessary structure from being omitted. Together they support a useful sequence: the intended shape becomes understandable before the team decides which part is most valuable or safest to build first.

YAGNI is useful advice with a narrow purpose: do not build speculative features or unjustified infrastructure merely because they might be useful one day.

WGF asks a different question:

> What goes first, and what are the consequences of including, deferring or omitting each part of the intended design?

YAGNI protects construction priority. WGF protects the ability to continue construction later without guessing.

## The familiar disagreement

Imagine a team discussing a service that will eventually support several kinds of external participant. The first release needs only one kind. Someone says that designing for the others is waste because they are not being built yet. Someone else says that the first implementation must leave room for the later participants. Both are responding to a real risk.

The first person is protecting the team from speculative construction. The second is protecting it from accidental architecture. If the team builds the first participant directly into every boundary, the later participants will not merely require more implementations. They will have to fit decisions that were made before their differences were understood.

The useful answer is not to build every future participant. It is to understand the participant contract, identify the responsible boundary, record the lifecycle and security assumptions and then choose which implementation gives the most valuable or safest evidence first.

## YAGNI and WGF ask different questions

YAGNI asks:

> Do we need to build this now?

WGF asks:

> What must be understood and placed now so that later construction will fit, and which part should we build first?

A capability may therefore be designed now and built later. A contract, boundary, lifecycle, security posture, persistence intention and relationship to other capabilities may be needed even when the implementation is deferred.

## Inclusion and omission both have consequences

Including something now may provide earlier evidence, reduce future rework, make an important dependency explicit or provide security and operational safety. It may also add cost, complexity and support burden. Omitting or deferring it may reduce immediate construction cost, but it may delay learning, remove an extension point, duplicate future work, create migration or compatibility risk or leave a hidden assumption for another team to uncover.

WGF does not tell us always to include the larger option. It makes the consequences visible so that a smaller first construction is deliberate rather than accidental.

## The instinct to develop

When the team hears "not yet," it needs to ask what structure must still be defined so that "not yet" does not become "someone else must invent it later." A capability can be designed now and built later. Its contract, boundary, lifecycle and security posture may need to be understood even when its implementation is deferred.

When the team hears "we already do that," it should be able to show one real capability where the contract, responsible boundary, implementation, security, lifecycle, mapping, persistence, startup and evidence are assembled together. That is how a familiar practice becomes a shared design rather than a claim that everyone has interpreted differently.

This is not a compliance exercise. It is a way to tell the difference between a shared design and a collection of familiar practices.

## Speed is not the same as agility

Frustration is understandable when contracts, boundaries, tests and other preparation produce no visible feature. It can be a useful signal that the team is blocked, waiting for evidence or carrying work that has not been explained well. It is not, by itself, evidence that the preparation should be skipped.

Impatience often treats the absence of a visible object as the absence of progress. That can lead a team to create classes, records or screens before the structure that gives them a responsible place is clear. The result may look fast at first while making later change slower and more expensive.

Agility is the ability to learn, change and continue safely. Sometimes the most agile step is a small visible construction. Sometimes it is the less visible work of clarifying a contract, boundary, dependency or test. The team can ask what evidence can be gained now, what must be designed before construction spreads assumptions and which small step remains reversible. That is how frustration becomes information rather than a command to rush.

## The practical rule

YAGNI helps decide what need not be built yet, while WGF helps decide what must be designed now and what should be built first.

The result is staged construction without structural amnesia.

## Related guidance

[The Structure Before the Feature](./the-structure-before-the-feature.md) explains why the shape of the system matters before visible features. [The Current State](./current-state.md) describes how to understand an existing arrangement, while [What This Guidance Gives](./what-this-guidance-gives.md) describes the support available through the wider route. [Development Principles](../../agents/conventions/foundations/principles.md) and [Development Constraints](../../agents/conventions/foundations/constraints.md) provide the corresponding engineering rules.
