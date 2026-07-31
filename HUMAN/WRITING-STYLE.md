# Human Documentation Writing Style

This is the writing contract for human-facing engineering guidance.

## Purpose

Human-facing guidance should help people understand a system and contribute to its design. It should be readable by non-specialists, junior developers, testers learning automation, business analysts, operations staff and people reading in a second language.

## Concept before technical term

Begin with the practical idea and its consequence. Introduce the technical term after the idea is understandable.

Use this pattern:

> Each layer has a clear job. This allows one part to change without forcing every other part to change at the same time. In technical language, this separation is often called brokering.

The technical word adds precision. It is not a test of whether the reader understood the idea.

## Plain and translation-friendly language

Human-facing documents should:

- use short sentences and familiar words;
- state one main idea in each paragraph;
- define a technical term when it first appears;
- use the same word for the same idea throughout a document;
- prefer active voice where it makes the actor clearer;
- use lists for sequences, responsibilities and choices;
- explain acronyms the first time they appear;
- use examples before abstract generalisations where the subject is difficult;
- explain the consequence of including, omitting or deferring a design choice;
- say what each role contributes to the shared design; and
- finish a section with the practical meaning or next step.

Write for people who may understand the business problem but not the implementation vocabulary. Do not make terminology a gate to participation.

## High-rise teaching metaphor

The high-rise metaphor may be used consistently:

- bedrock represents dependable evidence and foundations;
- foundations represent contracts, security, lifecycle and other structural necessities;
- vertical shafts represent capabilities carried through layers;
- slabs represent shared boundaries and platform services;
- horizontal flows represent journeys between capabilities; and
- tenant spaces represent experiences adapted for particular users or organisations.

Use the metaphor to explain relationships, not to decorate a document. Return to concrete terms after the picture is understood.

The building picture explains relationships and dependencies. It does not mean that every future business detail can be predicted, or that software must be delivered through one rigid construction process. Buildings have different sizes, and software has different levels of consequence.

The metaphor must also allow for different building sizes. Not every piece of software needs the same construction method:

- a **temporary shelter** may be a short-lived script or one-off integration, built quickly from simple materials because its life and consequences are limited;
- a **single dwelling** may be an internal application used by one team, with lighter construction and fewer shared services;
- a **multi-unit building** may support several teams or groups and therefore need shared entrances, utilities, maintenance and rules for different residents; and
- a **high-rise or commercial building** may support many external users, integrations and obligations, requiring deliberate foundations, boundaries, safety checks, services and operating evidence.

The guidance is aimed primarily at the later cases: services that matter beyond the immediate development team. The larger the audience, the longer the service life, the greater the external reliance and the greater the reputational or legal consequence of failure, the more organised the foundations must be. Scale the construction method to the consequences, but do not use a small-looking building as an excuse to ignore a known boundary when the outside world depends on it.

## Inclusive voice

Write as if the reader is a capable person who has not yet been shown this way of seeing the problem. Avoid blame, sarcasm, status contests and language that suggests only architects can understand the design.

Say:

> A ticket gives the team an important business starting point. It does not contain every logical and technical decision needed to build the service safely.

Avoid language that assigns fault to the person who wrote the ticket or the person who implemented the first version.

## Words and habits to avoid

Avoid unexplained or culturally specific expressions such as "magic", "hell on wheels", "blank cheque", "punch out a brick" and "read between the lines". When a technical document needs to discuss hidden framework behaviour, say that the behaviour is implicit, difficult to inspect or controlled by a default.

Avoid relying on these words without explanation:

- abstraction;
- aggregate;
- brokering;
- contract;
- domain;
- lifecycle;
- projection;
- registry;
- schema; and
- stewardship.

For wide human audiences, prefer **responsible boundary** or **lifecycle responsibility** on first use. Explain that this means the part of the system or team that keeps a capability coherent as it is created, changed, operated and eventually retired. Introduce **stewardship** later as the technical term if it helps precision. Do not assume that Owner or Steward is clear without explaining what responsibility the word represents.

These terms are valid. Explain them in the context where they matter.

## Human document structure

Where the subject is substantial, use this order:

1. purpose;
2. who should read it;
3. the short version;
4. the current problem;
5. why the problem matters;
6. the proposed approach;
7. how different roles contribute;
8. what is designed, built and deferred;
9. a before-and-after example;
10. common questions or concerns; and
11. the next step and related links.

Not every document needs every heading. The order is a guide for helping readers build understanding.

## Relationship to agent guidance

Human documents explain why and show examples. Agent documents state precise actions, constraints and routing. Keep the technical meaning consistent, but do not copy a long human explanation into a compact agent instruction.

When a human document introduces a technical rule, link to the precise agent or implementation guidance. When agent guidance uses a term that a human may not know, link to the human explanation.

Use the [Guidance Glossary](./GLOSSARY.md) for recurring terms. Add a term when it has a specific meaning in this guidance and readers may reasonably interpret it in more than one way.
