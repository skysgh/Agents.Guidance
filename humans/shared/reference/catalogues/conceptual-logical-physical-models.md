# Conceptual, Logical and Physical Models

Imagine developing a building for a restaurant business. The business may be the only customer today, but it will not remain unchanged. It may move from fine dining to fast service, add catering, change its menu, reorganise its kitchen or introduce a new way for customers to order. The building should support those changes without requiring the whole structure to be rebuilt.

The organisation around the restaurant may also change more slowly. Departments may merge, split, exchange responsibilities or adopt a different operating model. Those changes should not force a new system simply because the people, teams or reporting lines have moved. The durable structure should carry the business through both kinds of change: the business unit adapting its work, and the wider organisation restructuring around it.

Only after those changes should we ask whether the building could be adapted for another restaurant business. That is not the main reason to design it well, and it does not mean the team is secretly building a different system for a different tenant. It is a useful resilience test: if another tenant ever became an option, would the existing structure make that change possible without ruinous reconstruction?

Software needs the same kind of adaptability. The architect abstracts the durable responsibilities from the current arrangement. The technical lead recognises that abstraction, checks whether it is achievable with the available team, technology, dependencies and constraints, and plots the path to implementation. The developer implements the prepared structure and raises a design problem when the construction path does not fit it.

The words **conceptual**, **logical** and **physical** name three different questions about the same subject. They are not, by themselves, three floors in a software stack. A second vocabulary describes implementation position: consumer-facing interface, application coordination, domain objects, persistence, infrastructure and deployment. Those positions are physical implementations. They may express, translate or support different kinds of model.

Keeping these questions separate prevents a common mistake: calling the top of the stack conceptual, the middle logical and the bottom physical as though each implementation position has only one meaning.

## The three model types

### Conceptual model

A conceptual model describes how people or connected systems understand, name and recognise the subject. It carries the language, distinctions, relationships, outcomes and expectations that make sense to those consumers and stakeholders.

Conceptual language is valuable because it connects the service to the people who need it. It may also be local, incomplete, informal, ambiguous or shaped by today's organisation. Two groups may use the same word differently, or describe the same underlying responsibility through different words. The model should preserve those differences until the team has enough evidence to decide whether they are genuinely the same or need separate treatment.

A conceptual model is not a user-interface mock-up. A screen is one physical representation of a consumer's conceptual view. The conceptual model includes the meaning behind the screen: what the person believes they are doing, what result they expect, what distinctions matter and what consequences follow.

### Logical model

A logical model is the team's considered decomposition of the subject into the things, identities, relationships, states, rules, policies, capabilities and responsibilities that the system must understand and preserve.

This is ontological modelling in practical terms. The team asks what kinds of things exist in the problem space, what makes one thing the same thing over time, what can happen to it, which relationships matter, which states and decisions must be distinguished and which responsibilities belong together. The result is an abstraction from stakeholder evidence, not a transcription of one customer's current process, screen, team structure, vendor or database.

Logical modelling does not mean inventing generic objects until the customer language disappears. The model must preserve meaningful customer differences and provide mappings back to the concepts people recognise. It abstracts what is durable while leaving genuinely local or peculiar concerns at the boundary where they belong.

A logical model is not automatically a DDD model, a class diagram, a database schema or an API contract. Those may represent parts of it. The logical model is the meaning and responsibility that those physical representations must carry.

### Physical model

A physical model describes how a model or responsibility is represented and executed by actual technology, people, processes and infrastructure. It includes screens, API messages, application objects, domain objects, mappings, database records, files, queues, indexes, provider resources, configuration, deployment and runtime behaviour.

Physical does not mean inferior or merely technical. The physical model is where the service becomes usable and dependable. It may need to shape information for accessibility, security, bandwidth, protocol compatibility, performance, storage or operational reasons. Those are real design decisions, but they should remain recognisable as representations and implementations rather than silently becoming the only statement of meaning.

A physical representation can be close to the conceptual model or close to the logical model depending on its responsibility. A user-facing label may intentionally use the consumer's language. An application or domain object may implement an ontological distinction that has a different name from the customer's phrase. A persistence record may contain storage-only keys and indexes that have no business meaning.

## Enduring and Transient concepts

Enduring versus Transient is one of the key questions in the logical decomposition of a conceptual model. An Enduring concept retains identity and responsibility across changing transactions, roles, memberships, providers and physical representations. A Transient concept records a bounded relationship, participation, appointment, assignment, decision or interaction involving enduring concepts.

For example, the conceptual phrase "a student at a school" may translate into a logical **Person**, an enduring **School** or **Group**, a distinct **Location** where location has its own authority and lifecycle, and a transient **StudentAt** relationship with effective dates, status, authority and history. A consumer may still see "Student" because that is meaningful language. The logical model must not let a current membership become the person's identity or the school's complete meaning.

This classification does not replace DDD. It gives DDD and architecture evidence for deciding which entities, aggregates, relationship shafts, events, bounded contexts and mappings are responsible. See [Entity Lifecycle Patterns](./entity-lifecycle-patterns.md) for the modelling questions, temporal rules and role consequences.

## Two separate questions

The model type answers **what kind of meaning is being described**. The implementation position answers **where and how that meaning is represented or executed**. These are two separate questions, not a required stack shape.

| Model type | Main question | Typical evidence |
| --- | --- | --- |
| Conceptual | What do the people or connected systems recognise, need, expect or mean? | stakeholder language, outcomes, user journeys, policies, familiar distinctions and business terms |
| Logical | What must the system distinguish, relate, remember, decide and protect for that meaning to remain dependable? | ontological concepts, identities, relationships, states, rules, capabilities, contracts and responsibilities |
| Physical | How are those meanings and responsibilities represented, executed, stored, transported, secured and operated? | interface models, application and domain code, mappings, schemas, records, queues, providers, infrastructure and runtime behaviour |

The implementation stack may then contain physical representations of more than one model type:

```text
consumer-facing physical representation
  -> application coordination and boundary contracts
  -> domain and application physical objects that implement logical meaning
  -> mappings and persistence physical representation
  -> infrastructure, providers and runtime physical representation
```

This is a relationship map, not a rule that every service must use these exact projects or layers. The important point is that all of these are physical implementations, while the conceptual and logical models are meanings that those implementations carry and translate.

## A restaurant example

Imagine a customer describing an Italian restaurant. Their immediate conceptual world may contain pasta, pesto, wine, a table, a waiter and a meal. Those words matter because they are how that customer recognises the experience and explains what they want.

The service should not assume that the customer's first vocabulary is already the full logical model. A broader logical model of food service may need to distinguish offerings, recipes, ingredients, stock, dry storage, cold storage, preparation, cooking, orders, reservations, tables, service, payment, cleaning, safety and supplier replenishment. These responsibilities recur across many kinds of restaurant, even though the menu, terminology, cuisine and local practices differ.

The Italian restaurant still has real peculiarities. Pesto may be a menu item, a recipe, an ingredient, a prepared batch or an allergen-bearing information item depending on the capability being designed. Pasta may describe a dish to a diner, a recipe family to a kitchen, a stock item to procurement or a line item in an order. The logical model should not flatten those differences into one universal `Pasta` object merely because the word appears in every conversation. It should identify the responsibility and then map each consumer's meaning to the appropriate logical concept.

A customer-facing menu may continue to say **Pesto Pasta** because that is the language the diner recognises. The application may coordinate an order line, the domain may protect the lifecycle and pricing rules of an offered item, the kitchen system may represent preparation work and the storage system may hold inventory movements. Those physical representations can use different names without losing the customer's meaning, provided the mappings and contracts are deliberate.

The same reasoning applies beyond food. A customer's visible request is often a local expression of a more durable responsibility. The design challenge is to discover the durable responsibility without erasing what is unique about the customer.

## Why abstract for one customer?

The argument for abstraction does not depend on having several customers today. Imagine that this Italian restaurant is the only customer the team expects to serve. Designing directly around its current menu, kitchen process and vocabulary may feel efficient, but it quietly turns today's tenant into the structure that every later change must work around. The restaurant may move from fine dining to fast pizza, add catering, change its ordering model, introduce new dietary requirements or adopt a different way of organising preparation. Businesses change, even when they change slowly.

The building analogy makes the value easier to see. An architect can develop a restaurant space with durable structural and service capabilities: suitable access, ventilation, drainage, utilities, storage, preparation areas, customer areas and adaptable circulation. The tenant can then fit out that space for its current cuisine and service without making every wall, pipe or doorway a permanent statement about one menu. The space is not abstract because it is vague. It is abstract because it preserves the capabilities that outlast the current tenant while still allowing the tenant's recognisable experience to be real.

Software needs the same separation. The conceptual model preserves what this customer recognises, such as pesto pasta, tables, orders and service. The logical model identifies the durable responsibilities beneath those words, such as offerings, recipes, ingredients, stock, preparation, ordering, pricing and lifecycle. The physical implementation then provides the interfaces, application and domain behaviour, persistence and infrastructure that realise today's service. This investment is what lets the same system adapt when the business changes without forcing it to watch its peers move ahead while it remains locked to an earlier era.

## Abstraction without losing recognition

There are two opposite failures.

The first is **direct physicalisation of the conceptual model**. The team takes today's customer words, screen fields or current process and turns them directly into tables, classes and endpoints. There is no deliberate abstraction between what this customer says and what the system must preserve. The result may be easy to recognise at first, but a later customer, process or integration has to fit yesterday's local arrangement. Maintenance becomes difficult because the physical design has become the logical design by accident.

The second is **unsupported abstraction**. The team invents broad universal objects without enough evidence from real stakeholders, so the model no longer explains the customer's decisions, language or consequences. The result may look elegant while being difficult to use and impossible to validate.

The enduring design sits between them:

1. Elicit the conceptual language, desires, needs, obligations, outcomes and consequences from representative stakeholders and SMEs.
2. Identify which differences are local expression and which represent a real difference in responsibility, authority, lifecycle, state or rule.
3. Decompose the subject into logical concepts that can remain useful when the current customer, screen, process, vendor or storage technology changes.
4. Keep mappings and contracts that let each consumer recognise the result in its own language.
5. Physicalise the design in interfaces, application and domain code, persistence and infrastructure without allowing any one representation to redefine the meaning silently.
6. Use evidence from development, testing, operations and maintenance to refine the model when an assumption does not hold.

The goal is not to make every customer speak in universal technical language. The goal is to build a system whose enduring responsibilities are clear while each consumer can still recognise the service in the language and context that matter to them.

## How this relates to layers

Logical layers are implementation responsibilities that help keep representations apart. They are not the same thing as the three model types, and every layer is physicalized in the delivered system.

The consumer-facing interface position contains physical DTO and view-model code shaped close to the concepts and language that consumers or the business recognise. Application and domain positions contain physical code and entities shaped closer to the ontological and logical distinctions that carry durable meaning. Persistence positions contain physical persistence-model code that carries those distinctions into records while adding storage-system requirements such as primary keys, foreign keys, indexes, concurrency rules and provider constraints. These are different semantic proximities and responsibilities, not a claim that one layer is conceptual, another is logical and another is physical. A single physical type may legitimately serve more than one model when the meanings and lifecycles genuinely match, but resemblance is not proof that the distinction has disappeared.

The practical test is whether the team can explain:

- what the stakeholder or consumer means;
- what durable logical distinction or responsibility carries that meaning;
- where the physical representation lives;
- how the representations are mapped;
- which representation owns each rule, policy and lifecycle decision; and
- what evidence would show that a change preserves both recognition and enduring meaning.

The [Logical Layers](./logical-layers.md) catalogue describes implementation responsibilities. [Logical and Physical Models in ORM](../../../development/logical-and-physical-models.md) explains the special case where persistence classes and records resemble logical objects. [Ontological Decomposition](../../../orientation/ontological-decomposition.md) explains how to choose the useful level of decomposition and why every LDM layer remains physicalized. The [Stakeholder Roles](./stakeholder-roles.md) catalogue explains who supplies the evidence from which the conceptual model is elicited.

## Related guidance

The [Glossary](../glossary.md) provides short definitions of Conceptual, Logical and Physical. [Guidance for System Design Architects](../../../orientation/guidance-for-system-design-architects.md) uses the distinction when moving from stakeholders and system responsibilities to components and delivery boundaries. [Guidance for Developers](../../../orientation/guidance-for-developers.md) explains how physical code should preserve logical responsibility and map consumer representations. [Domains and Capabilities](./domains-and-capabilities.md) explains how coherent responsibilities are named before implementation shapes are chosen.
