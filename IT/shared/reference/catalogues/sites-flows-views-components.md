[Up](./readme.md)

# Sites, Flows, Views and Components


This explanation gives a deeper description of the internal shape of a site. The site catalogue remains understandable without it; the additional detail becomes useful when a conversation turns to interface structure.

A site is not a bag of pages. It is a curated way for a group to use system-managed information and capabilities in support of a responsibility. The site becomes understandable when its journeys, views and interface components remain connected to that responsibility.

## A site is a collection of flows

A flow is a recognisable journey through one or more capabilities. It may describe preparing and submitting a request, reviewing evidence, approving a decision, responding to a notification, correcting a record or recovering from an interrupted operation. A flow gives the journey a name and a shape, but it does not take responsibility for all the rules of the capabilities it coordinates.

The site collects the flows that the group needs. A consumer site may collect registration, application, submission and status flows. A provider site may collect assessment, decision and fulfilment flows. A support site may collect investigation, assistance and controlled correction flows. Some flows may be shared by several sites when the responsibility and information presented to each site remain appropriate.

A flow should not become a disguised site-wide coordinator that knows every rule. It should guide the journey and call the capabilities that own the relevant meaning. The flow can manage sequence, waiting, hand-off, retry and outcome presentation while the underlying capabilities keep their own rules, state and evidence.

## A flow is a collection of views

A view is the presentation of one meaningful point in a flow. It may show a collection of records, collect information, present a result, display a decision or help a person choose the next action. An API view may be a request or response contract rather than a visual screen. The same flow can have different views for different sites because each site has a different audience and information need.

A view should be understandable without requiring the reader to reconstruct the whole flow from unrelated controls. It should expose the information and actions needed at that point, while leaving the authoritative rules and state changes to the responsible capability.

Views are not domain models. They are conceptual representations for a consumer. They may combine information from several capabilities, omit information the audience does not need or use language that makes sense to the group. Mapping between the view and the logical model protects both meanings.

## A view is a collection of components

A component is a coherent part of a view with one primary presentation responsibility. Components are classified as collection, input or output components. The classifications are kept distinct within the component. A component that displays a collection should not also quietly become responsible for input validation and state transition rules. An input component should collect and communicate input without becoming the domain model. An output component should present a result without becoming the authority for how that result was produced.

A collection component organises a set of related items for inspection, comparison or selection. It may be a list, table, group, tree or another repeated representation. It should make the identity, status and relevant actions of the items understandable without assuming that the collection itself owns their business rules.

An input component collects a value, choice, document, instruction or other request from the consumer. It may help the consumer provide a valid value, but validation that protects a business invariant belongs to the responsible application or domain boundary. Input is not permission, and a well-designed control cannot make an unsafe request safe by itself.

An output component presents information produced by a capability. It may be a summary, status, decision, message, document, result or explanation. It should respect the classification and visibility policy of the source capability and should not expose internal state merely because that state is available to the implementation.

The view may use several component types together. The important separation is that each component has one primary kind and does not mix collection, input and output responsibility into an inseparable unit. This keeps changes easier to isolate and makes the meaning of each part easier to test.

## The relationship to capabilities

Sites, flows, views and components are interface structures. They are not replacements for domains, capabilities or logical layers. A component calls or receives a contract. A view uses the results needed at one point in a flow. A flow coordinates capabilities. The capability remains responsible for the rules, state and effects that give the interaction its meaning.

When a component begins to decide business state, write directly to storage, call several providers without an application boundary or enforce a rule that other consumers also need, the responsibility has escaped its interface role. Move that responsibility to the appropriate capability and expose the result through a contract.

This separation is the practical expression of separation of concerns, high cohesion and low coupling at the interface level. Interface parts stay close to the information and interaction they present. Domain and application responsibilities stay with the capabilities that own them. The boundaries between them remain explicit enough that a site, flow or view can change without silently changing the meaning of the system.

For design and review prompts, use the [site and interface checklist](../checklists/sites-and-interfaces.md).
