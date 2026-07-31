# Palette Relationships

This document follows [Palette Elements](./elements.md). It explains how the parts fit together after their individual jobs are familiar.

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
          -> Application capability or external service
```

This is a common relationship, not a mandatory component list. A background job may have a Coordinator and Broker but no visible View. A simple Renderer may have no Coordinator. A one-record form may use a Player without a collection Presenter.

## How the pieces cooperate

The View is the experience people recognise. The Coordinator moves between surfaces within that experience. A Presenter frames a collection, page, tree or sequence. A Player operates one capability or record. A Renderer provides visible representation.

Questions and Inputs give the capability the information it needs. Actions ask the system to do something. Action Zones group those actions by context. States show where the capability is in its lifecycle. State Changes move it deliberately. Feedback explains the result. Evidence records what must later be proved. Events announce facts that other participants may respond to. A Broker crosses the boundary to the application or external capability.

The separation means that a page does not need to know how a database, mapper, storage provider, finance system or external API works. The Presenter and Player can coordinate the experience while the Broker and application capability handle the boundary work.

## A request example

For a Request, the relationship may look like this:

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

The Request Coordinator sequences preparation, submission, assessment and approval. The Request Presenter frames the request and its child capabilities. Evidence and Comments retain their own rules. The Broker connects the experience to application and external boundaries.

## Optional and missing pieces

The palette is a way to notice responsibility, not a form to complete. A team can choose the pieces that match the experience:

- use a Coordinator when the experience has movement between surfaces or steps;
- use a Presenter when a collection, page, tree or ordered group needs framing;
- use a Player when one capability or record needs interaction;
- use a Renderer when representation is the main responsibility;
- use a Broker when a boundary call should be hidden from the surface; and
- use Events, States, Evidence and Feedback when the capability needs them.

The palette helps the team recognise responsibility. It does not prescribe a component hierarchy for every kind of work.

## The shared design contribution

No single role sees the whole relationship map alone:

- business analysis contributes meaning, questions, actions and expected states;
- developers test whether the relationships can be implemented cleanly;
- testers verify actions, transitions, events and failure behaviour;
- operations checks readiness, external dependencies and recovery;
- security checks which paths and data are permitted; and
- architecture preserves coherence across the View, Coordinator, Presenter, Player, Renderer and Broker boundaries.

## Continue when ready

- [Palette Technical Terms](./technical-terms.md)
- [Common Flows](../flows.md)
- [Request, assessment, approval and payment example](../examples/11-request-offer-approval/after.md)
