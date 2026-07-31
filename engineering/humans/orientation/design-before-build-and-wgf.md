# YAGNI versus WGF

## Purpose

This paper explains how to decide what to build first without allowing the first feature to decide the whole architecture. It is for anyone involved in deciding scope, design, implementation, testing or delivery.

## The short version

YAGNI helps prevent unnecessary construction. WGF helps prevent necessary structure from being omitted. Use them together: understand the intended shape, then decide which part is most valuable or safest to build first.

YAGNI is useful advice with a narrow purpose: do not build speculative features or unjustified infrastructure merely because they might be useful one day.

WGF asks a different question:

> What goes first, and what are the consequences of including, deferring or omitting each part of the intended design?

YAGNI protects construction priority. WGF protects the ability to continue construction later without guessing.

## The difference

YAGNI asks:

> Do we need to build this now?

WGF asks:

> What must be understood and placed now so that later construction will fit, and which part should we build first?

A capability may therefore be designed now and built later. A contract, boundary, lifecycle, security posture, persistence intention and relationship to other capabilities may be needed even when the implementation is deferred.

## A simple example

Suppose a service will eventually support several kinds of external participant. The first release needs only one kind.

YAGNI may correctly say: do not build every participant implementation now.

WGF adds: define the participant contract, identify the boundary that stewards it, record the lifecycle and security assumptions, and decide which implementation goes first. Otherwise the first implementation silently becomes the architecture and later participants must conform to accidental details.

## Inclusion and omission both have consequences

Including something now may bring:

- earlier evidence;
- reduced future rework;
- an important dependency being made explicit;
- security or operational safety; or
- cost, complexity and support burden.

Omitting or deferring something may bring:

- reduced immediate construction cost;
- delayed learning;
- a missing extension point;
- duplicated future work;
- migration or compatibility risk; or
- a hidden assumption that another team must later uncover.

WGF does not tell us always to include the larger option. It makes the consequences visible so that a smaller first construction is deliberate rather than accidental.

## The instinct to develop

When the team hears "not yet," the next question is:

> What structure must still be defined so that "not yet" does not become "someone else must invent it later"?

When the team hears "we already do that," the next question is:

> Show one real capability where the contract, stewardship, implementation, security, lifecycle, mapping, persistence, startup and evidence are assembled together.

This is not a compliance exercise. It is a way to tell the difference between a shared design and a collection of familiar practices.

## The practical rule

Use YAGNI to decide what not to build yet. Use WGF to decide what must be designed now and what should be built first.

The result is staged construction without structural amnesia.
