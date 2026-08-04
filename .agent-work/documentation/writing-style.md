# Human Documentation Writing Style

This is the writing contract for human-facing delivery guidance.

## Purpose

Human-facing guidance should help people understand a system and contribute to its design. It should be readable by non-specialists, junior developers, testers learning automation, business analysts, operations staff and people reading in a second language.

## Concept before technical term

Begin with the practical idea and its consequence. Introduce the technical term after the idea is understandable.

Use this pattern:

> Each layer has a clear job. This allows one part to change without forcing every other part to change at the same time. In technical language, this separation is often called brokering.

The technical word adds precision. It is not a test of whether the reader understood the idea.

## Conceptual pacing and transitions

Human readers need time to form a mental picture. Do not move abruptly from one concept to the next, even when the connection seems obvious to the writer. Explain the first idea and its consequence, allow it to settle, then use a short bridge to show why the related idea is being introduced.

A bridge might say that a familiar comparison will make the difference visible, that the next idea depends on the one just explained, or that a practical example will make the principle concrete. The reader should understand why the direction is changing before the change happens.

Prefer a gentle progression over compressed routing. A person reading for understanding cannot be expected to pivot conceptually as quickly as an agent following explicit instructions. Human guidance should therefore feel like a connected explanation, with enough space between ideas for the reader to carry the earlier one forward.

## Introduce before asking

An introductory human page is not an instruction sheet. Its first responsibility is to help the reader recognise a problem, understand why it matters and see how the proposed way of thinking could make their work clearer or less burdensome. Links, examples, related concepts and practical tools give the reader ways to continue when curiosity or need takes them there; they do not create a reading assignment.

Do not ask the reader to act merely because they reached an introduction. Avoid turning the opening into a gate with phrases such as "Start here", "Read this before continuing" or "Do not begin until". Explain why a destination may be useful and leave the reader free to follow it. A later decision, development or checklist page can ask for a specific action once the reader understands the reason for it.

This gives the guidance a gentle progression: introduction creates understanding and desire; links provide routes to deeper meaning; examples make the benefit tangible; catalogues and checklists provide tools; and the responsible role or decision record asks for action when the situation calls for it. The reader is being brought along, not tested at the door.

## System design is an engineering discipline

Do not describe system design as an equal mixture of science and art when that suggests that every design is a unique act of personal creativity. After decades of enterprise software, many of the structural problems are recurring: boundaries, contracts, identity, data protection, persistence, lifecycle, failure, recovery, observation and operation. The programming languages, vendors and materials change, but the engineering relationships return.

The custom part is real, but it is usually concentrated in the organisation's meaning, decisions, constraints, workflows and human experience. Those choices deserve careful thought. They do not justify reinventing the supporting structure or treating improvisation as architecture. A building may have distinctive rooms, finishes and furnishings, but most of its strength comes from the repeated engineering of foundations, frames, connections, services and safety margins.

Use the building comparison to keep the proportions visible. Objects, screens and visible features are the paint, curtains and rooms people notice. Contracts, boundaries, data handling, security, recovery and operating evidence are closer to the steel, concrete, pipes and cables that make the building usable. A workaround may be necessary for a time, but duct tape is not a design philosophy and improvisation is not the same as engineering judgement.

This does not mean that system design is mechanical or that every problem has one correct answer. It means that teams should first recognise the established engineering problem, use the known patterns that fit it and make the genuinely new decisions explicit. Guidance should give people confidence to reuse sound structure rather than making novelty a status test.

## Patterns before bespoke solutions

Do not treat patterns as vocabulary that developers use to get hired and then leave behind when real work begins. Patterns are working tools. They record solutions to problems that have already appeared repeatedly, along with the forces, trade-offs and consequences that made those solutions useful.

A bespoke solution may be justified when the domain, constraints or evidence genuinely do not fit an established pattern. It should not be the default simply because the team can make a local version that works. Before inventing a new shape, ask which known patterns apply, what they would protect, where they would need adaptation and what evidence would justify departing from them.

"It works" is necessary but incomplete evidence. A locally successful solution may still leave unclear responsibility, hidden coupling, weak recovery, poor auditability or a difficult path for the next team. A pattern gives the team a shared starting point and language for reviewing those risks. If the team chooses a bespoke design, record why, what risk it accepts and how it will remain understandable to people who did not invent it.

## Taking responsibility for entrusted systems

When people or organisations entrust a system with their records, money, access or essential services, the system carries a responsibility that is larger than its visible feature set. The people who build and maintain it must protect what has been entrusted to them, keep it available to the people who are allowed to use it, preserve its accuracy and make it understandable and usable. Good engineering should help the service improve people's lives, not merely make a process run.

That responsibility does not mean quietly turning every existing policy or process into permanent software behaviour. A process may have grown from a temporary limitation, an old assumption or a well-intentioned response to an earlier problem. Even when its original reason was good, embedding it invisibly in code can make it difficult to question, explain or change.

Human-facing guidance should therefore make these decisions visible. It should distinguish the responsibility the system must uphold from the policy or process currently used to uphold it. Where a policy belongs in the software, explain its purpose, authority and expected change points. Where a process is only one way of meeting the responsibility, keep that choice replaceable and do not present it as an unchangeable truth.

## Responsibility before hierarchy

Describe people as contributors who can notice, question, improve and take responsibility for the work in front of them. Do not make collaboration sound like a chain of permission by repeatedly saying that one role “has authority” while others merely wait for approval. A role may step up to contribute outside its usual focus, especially in a small team, while the team still keeps the relevant decision boundary and specialist contribution visible.

Use authority language when it carries useful meaning: for example, when a decision has a legal duty, an explicit approval boundary, a formal delegation or a clear accountable decision-maker. Otherwise, prefer language such as “takes responsibility for”, “contributes to”, “raises”, “helps decide”, “recommends” or “is responsible for bringing the relevant evidence”. This keeps the emphasis on participation and dependable decisions rather than status.

When several people perform different roles, describe the responsibility being exercised rather than assuming that each role belongs to a different person. The question is not only who may decide. It is also who can contribute, who needs to be involved, what evidence is needed and how the decision remains understandable to the people who depend on it.

## Building and operating are different responsibilities

People cannot spend unlimited time on one construction effort. A service also has to remain dependable after the people who built it have moved to other work. This gives us two related responsibilities: building the service so that its structure, boundaries and behaviour can be understood, and operating it so that it remains secure, available, accurate and useful over time.

Building responsibility includes making sound decisions, joining the parts carefully, recording what future people need to know and leaving the unfinished parts structurally safe. Operating responsibility includes watching what is happening, responding when the service or its dependencies change, protecting the records and access entrusted to the service, and helping people recover when something goes wrong.

These responsibilities meet at the point where the building is handed over and then maintained. A service that can only be operated by the people who originally built it is not complete, however elegant its code may be. Guidance should therefore describe both what the builders must establish and what the operators must be able to understand, observe and change without depending on an absent expert.

## Plain and translation-friendly language

Human-facing documents should:

- avoid terseness;
- avoid technical terms until the concept is understandable;
- use familiar words;
- do not rely on short sentences so heavily that the prose becomes terse or uninviting;
- do not use one long sentence to carry several unrelated ideas at once;
- keep to one main idea in each paragraph;
- define a technical term when it first appears;
- use the same word for the same idea throughout a document;
- prefer active voice where it makes the actor clearer;
- avoid lists when flowing paragraphs would be more natural; after the ideas have been introduced, lists can summarise sequences, responsibilities and choices;
- explain acronyms the first time they appear, then also point to the glossary;
- use metaphors to introduce when examples are difficult; 
- use examples before abstract generalisations where the subject is difficult;
- explain the consequence of including, omitting or deferring a design choice;
- say what each role contributes to the shared design; and
- finish a section with the practical meaning or next step.

Write for people who may understand the business problem but not the implementation vocabulary. 

Do NOT make terminology a gate to participation.

### Weave links into the explanation

Links in human guidance should help the reader understand the idea being explained. They should not make the reader stop and follow an instruction before the explanation has finished. This is especially important for catalogue and reference links, which should answer the reader's likely next question in the words around the link.

Use inline links to let readers take a simpler or more detailed explanation when they need it. A long guidance set asks readers to absorb many connected ideas. A well-placed link gives them permission to follow the question that matters most to them, then return to the main path when they are ready. The link should support understanding, not test whether the reader is willing to leave the page.

When the destination contains several subjects, link to the exact heading or passage that answers the immediate question. Prefer an exact anchor over a link to the top of a long document. Use the surrounding sentence to say what the reader will find there, so the destination is predictable before they leave the current explanation.

For example:

> A role can describe business responsibility, access context or system authorisation. The [Polysemy guidance for Role](../../humans/shared/reference/glossary.md#role-is-polysemous) separates these meanings before the example applies them.

An inline link is not a substitute for the local explanation. State enough here for the reader to understand the current point, then offer the link for readers who need a gentler introduction, a deeper explanation or the canonical definition. Keep the link close to the term or question it supports, and do not make readers hunt through a navigation list to recover the missing context.

Prefer:

> The [Logical Deployment Modules](../../humans/shared/reference/catalogues/ldms.md) catalogue explains the boundary, while the [Logical Deployment Modules development guidance](../../humans/development/ldms.md) explains what that boundary means for delivery.

Avoid:

> [Logical Deployment Modules](../../humans/shared/reference/catalogues/ldms.md) is required reading before you may continue.

The first version keeps the link inside the story and tells the reader why it is relevant. The second version sounds like a route for an automated agent and interrupts the explanation with an instruction. Navigation lists at the end of a document may still use direct links because their purpose is to help readers find related material.

### Give the reader a way out

Deep guidance should not leave a reader dependent on the browser Back button or on remembering the path that led there. Use a consistent upward link at the end of each page:

- a non-index page links to the `readme.md` in its immediate folder;
- a folder `readme.md` links to the parent folder's `readme.md`; and
- the repository root `readme.md` has no upward link.

Use a useful label such as `[Up: Stakeholder Guidance](../../humans/shared/reference/readme.md)` or `[Up: Human Guidance](../../humans/readme.md)`. The link is navigation, not an instruction to read the parent first. Keep the page's local explanation complete and place the upward link after the related links or next-step material.

## Building and High-rise teaching metaphor

People have some experience of buildings, so the building picture can help explain software relationships and dependencies. The fuller explanation belongs in [The Building Metaphor](../../humans/shared/reference/building-metaphor.md). Use that explanation before introducing the metaphor in another human-facing document.

Use the metaphor to explain relationships, not to decorate a document. Introduce the practical software idea first, use the building picture to make the relationship easier to see, and return to concrete software terms once the picture is understood.

Keep the scale of the metaphor proportional to the consequences of the service. A temporary shelter, single dwelling, multi-unit building and high-rise do not need the same construction method. The audience, service life, external reliance and legal, financial or reputational consequences should determine how much structure and evidence the guidance asks for. Do not use a small-looking building as an excuse to ignore a boundary on which other people depend.

Keep the shared vocabulary consistent when it is useful: bedrock and foundations for dependable evidence and structural necessities; vertical shafts for capabilities carried through layers; slabs for shared boundaries and platform services; horizontal flows for journeys between capabilities; and tenant spaces for experiences adapted for particular users or organisations.

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

Prefer **responsible person**, **responsible team**, **responsible boundary** or **responsible authority** to the generic word **owner** when describing human accountability. “Owner” can sound like a job title, imply total authority or hide the difference between business, technical, operational and legal responsibility. Keep formal titles such as Product Owner, and retain technical field or provider terminology when the exact term is the subject, but explain the responsibility in plain language.

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

Use the [Guidance Glossary](../../humans/shared/reference/glossary.md) for recurring terms. Add a term when it has a specific meaning in this guidance and readers may reasonably interpret it in more than one way.

[Up: Documentation Guidance](../../humans/shared/reference/readme.md)
