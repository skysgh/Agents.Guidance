[Up](./readme.md)

# Client Implementation Vocabulary


This page gives more precise client terms after the [First Look at the Client Experience](./first-look.md) and [Client UX Palette](./ux-palette.md) have made the responsibilities familiar. These terms help developers discuss code, but code names are not automatically the system's business vocabulary.

## View and Surface

A **View** is the user-recognisable experience. A **Surface** is a bounded part of that experience that can be hosted, replaced or composed with other surfaces.

## Coordinator

The client **Coordinator** manages movement between Presenters and Players. Its core behaviour is transition, sequence and gating. A Coordinator is not a Navigator. A Navigator owns a routing scope or URL boundary; a Coordinator owns movement within an experience whether or not the URL changes.

## Presenter

A **Presenter** provides collection or surface framing. Its common verbs include filtering, sorting, paging, selecting and reordering. It frames children and may choose which Player or Renderer presents them.

## Player

A **Player** provides single-capability or single-record interaction. Its common verbs include loading, presentation-level validation, dirty-state tracking, submitting and cancelling. A read Player and write Player may share visual children while retaining different responsibilities.

## Renderer

A **Renderer** translates a model, definition or state into visible output. It should be replaceable without moving business orchestration into the visual component.

## Broker

A **Broker** is an application or integration boundary connector. It may call a service capability, storage provider, message endpoint or external system. It hides the mechanics of crossing that boundary while the capability on the other side retains its rules.

## Action, State and Event

An **Action** is an intentional request for the system to do something. A **State** is the current lifecycle position. A **State Change** is a deliberate transition. An **Event** is a fact that a change or outcome occurred.

These are different:

- an Action asks;
- a State describes;
- a State Change moves; and
- an Event announces.

Keeping them distinct prevents a button click, client state update, service command and business transition from becoming one ambiguous operation.

## Correspondence with the current frontend implementation

The current frontend implementation contains examples of these distinctions:

- `ISurfaceCoordinator` and `SurfaceCoordinatorBase` represent the Coordinator role;
- `SurfacePresenterBase` represents shared Presenter behaviour;
- `SurfacePlayerBase` represents shared Player behaviour;
- `FormRendererComponent` represents a Renderer that wraps a form engine; and
- `GenericCoordinatorComponent` hosts Presenter and Player surfaces while using a Broker for capability calls.

These names are implementation bindings, not universal architecture. The durable idea is the separation of movement, framing, single-capability interaction, representation and boundary calls.

## Related guidance

- [Client UX Palette](./ux-palette.md)
- [First Look at the Client Experience](./first-look.md)
- [Common Flows](../../../foundations/flows.md)
- [Guidance Glossary](../../../shared/reference/glossary.md)
- [Portable horizontal flow rules](../../../../agents/conventions/capabilities/flows.md)
