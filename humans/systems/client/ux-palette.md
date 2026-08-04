# Client UX Palette

This catalogue names recurring parts of a client experience and the relationships among them. It is a client-system catalogue, not a business-domain model and not a required component hierarchy.

A person may see one form, one table or one workspace. The team may later discover that it combines questions, outputs, state, feedback, actions and several service capabilities. The palette gives those parts names after the experience is understood, so the names help the conversation rather than becoming a test at the door.

The broader [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md) catalogue explains how sites, flows, views and components relate to responsibilities and capabilities. This palette gives the client developer a more focused vocabulary for the visible experience.

## View

A **View** is the experience a person recognises: a page, panel, workspace, form, list, tree, report or sequence. It starts the conversation. It does not automatically own all of the behaviour visible within it.

## Coordinator

A **Coordinator** manages movement between client surfaces. It sequences steps, applies transition conditions and responds to transition events. It coordinates the journey without absorbing every business rule.

## Presenter

A **Presenter** frames a collection, page, tree or ordered group. It may manage selection, ordering, paging, filtering and action zones. It should not need to know how every record is loaded or saved.

## Player

A **Player** operates one capability or focused record through the client experience. It may load, validate presentation-level input, track changes, submit or cancel. Read and write Players may share visual children while retaining different responsibilities.

## Renderer

A **Renderer** turns a model, definition or state into visible UI. It concentrates on representation. It may report user interaction, but it should not quietly become an application service, business authority or persistence boundary.

## Questions and Inputs

Questions and Inputs are the information needed to make a decision or perform an action. They include fields, requirements, answers and Evidence. They belong to the capability and flow that need them, not only to the first form that displays them.

## Actions and Action Zones

An **Action** asks the system to do something. An **Action Zone** groups actions by record, step, state or permission context. This makes it clear which actions belong to an applicant, assessor, approver, operator or another role.

## States and State Changes

A **State** describes where a capability is in its lifecycle. A **State Change** moves it deliberately, such as draft to submitted, submitted to under assessment or recommended to approved. A client may display and request a transition, but the service validates and owns the authoritative state change.

## Feedback and Evidence

Feedback tells people or systems what happened. Evidence records what must later be proved, such as a submitted version, decision reason, audit entry, validation result or payment acknowledgement. Client feedback must not claim a durable outcome before the service has supplied the relevant result.

## Events

An **Event** announces that something happened. The producer owns the fact. A client may respond to an event or refresh its view, but an Event should not silently become an unowned command.

## Brokers

A **Broker** knows how to reach a service capability or external system. It hides transport, mapping and provider details from the View, Presenter and Player. It connects calls; it does not take responsibility for the business decision made by the capability it reaches.

## The relationship map

```text
View
  -> Coordinator
      -> Presenter
          -> Player or Renderer
              -> Questions and Inputs
              -> Actions and Action Zones
              -> States and State Changes
              -> Feedback and Evidence
      -> Broker
          -> service capability or external system
```

This is a common relationship, not a mandatory component list. A background client process may have a Coordinator and Broker but no visible View. A simple Renderer may have no Coordinator. A one-record form may use a Player without a collection Presenter.

## A request example

```text
Request View
  -> Request Coordinator
      -> Request Presenter
          -> Request Read Player
          -> Request Edit Player
          -> Evidence Presenter
              -> Evidence Player
          -> Comments Presenter
              -> Comment Player
      -> Request Broker
          -> Request capability
          -> Evidence capability
          -> Decision capability
          -> Finance integration
```

The Request Coordinator sequences the consumer experience. The service capabilities retain their own rules, permissions, state, evidence and external effects. Evidence and Comments remain separate capabilities when their responsible boundaries and lifecycles require it.

## Optional and missing pieces

The palette is a way to notice responsibility, not a form to complete. A Coordinator becomes useful when the experience has movement between surfaces or steps; a Presenter when a collection or page needs framing; a Player when one capability or record needs interaction; a Renderer when representation is the main responsibility; a Broker when a boundary call should be hidden from the surface; and Events, States, Evidence and Feedback when the capability needs them.

The vocabulary is most helpful when it follows a real difference. A component created only to satisfy a name, or made generic because two screens look similar, can hide different meanings, permissions, states and failure conditions. Recognition comes before reuse.

## Shared design contribution

Business analysis contributes meaning, questions, actions and expected states. Front-end developers test whether client relationships can be implemented accessibly and maintainably. Service developers preserve authoritative capabilities and contracts. Testers verify actions, transitions, events and failure behaviour. Operations checks readiness, external dependencies and recovery. Security checks which paths and data are permitted. Architecture preserves coherence across client, service and shared boundaries.

## Related guidance

- [First Look at the Client Experience](./first-look.md)
- [Client Implementation Vocabulary](./implementation-vocabulary.md)
- [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md)
- [Common Flows](../../orientation/flows.md)
- [Front-end Developer Guidance](../../stakeholders/developers/front-end.md)
- [Request, assessment, approval and payment example](../../examples/11-request-offer-approval/after.md)
