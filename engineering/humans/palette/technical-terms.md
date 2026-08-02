# Palette compatibility route

The client implementation vocabulary now lives in [Client Implementation Vocabulary](../systems/client/implementation-vocabulary.md). This page remains temporarily so older links reach the canonical client-system route.

## View and surface

A View is the user-recognisable experience. A Surface is a bounded part of that experience that can be hosted, replaced or composed with other surfaces.

## Coordinator

The frontend Coordinator manages movement between Presenters and Players. Its core behaviour is transition, sequence and gating. It is the current term for the broader role that earlier design material may have called an Orchestrator.

A Coordinator is not a Navigator. A Navigator owns a routing scope or URL boundary. A Coordinator owns movement within an experience, whether or not the movement changes the URL.

## Presenter

A Presenter provides collection or surface chrome. Its common verbs include filtering, sorting, paging, selecting and reordering. It frames children and may choose which Player or Renderer presents them.

## Player

A Player provides single-capability or single-record interaction. Its common verbs include loading, validation, dirty-state tracking, submitting and cancelling. A read Player and write Player may share visual children while retaining different responsibilities.

## Renderer

A Renderer translates a model, definition or state into visible output. It should be replaceable without moving business orchestration into the visual component.

## Broker

A Broker is an application or integration boundary connector. It may call an application service, repository-backed capability, storage provider, message endpoint or external system. It hides the mechanics of crossing that boundary, while the capability on the other side retains its rules.

## Action, state and event

An Action is an intentional request for the system to do something. A State is the current lifecycle position. A State Change is a deliberate transition. An Event is a fact that a change or outcome occurred.

These are different:

- an Action asks;
- a State describes;
- a State Change moves; and
- an Event announces.

Keeping them distinct prevents a button click, database update and business transition from becoming one ambiguous operation.

## Correspondence with the frontend

The BASE frontend already contains these distinctions in code:

- `ISurfaceCoordinator` and `SurfaceCoordinatorBase` represent the Coordinator role;
- `SurfacePresenterBase` represents shared Presenter behaviour;
- `SurfacePlayerBase` represents shared Player behaviour;
- `FormRendererComponent` represents a Renderer that wraps a form engine; and
- `GenericCoordinatorComponent` hosts Presenter and Player surfaces while using a Broker for capability calls.

The precise names are implementation bindings. The durable idea is the separation of movement, framing, single-capability interaction, representation and boundary calls.

## Related guidance

- [The Palette: First Look](./first-look.md)
- [Palette Relationships](./relationships.md)
- [Common Flows](../orientation/flows.md)
- [Portable horizontal flow rules](../../agents/conventions/capabilities/flows.md)
