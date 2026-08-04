# Client System Guidance

Someone fills in a request while the connection is unreliable. The page shows a spinner, the person is unsure whether the action worked and a second click creates a duplicate. Another person reaches the same page with a keyboard and cannot find the error message. The service may be enforcing its rules correctly, but the consumer is still carrying the cost of an unclear client experience.

The client system is where a person or connected consumer reaches the service. In a browser-based service it commonly includes the SPA assets, browser execution, client-side state, views, components, interaction flows and calls to service interfaces.

A client can look like a set of screens attached to a server. It is a system with its own execution environment, dependencies, lifecycle, security boundary, failure behaviour and evidence. A network can disappear, an asset can become stale, a browser can be inspected and a person can need to complete a task with a keyboard, zoom or assistive technology. Those are client-system conditions, not decoration around server code.

The service system remains authoritative for business meaning, authorisation, durable state, audit and consequential decisions. The client system makes the journey understandable and operable for its consumer, then relies on service contracts for the capabilities and decisions it does not own. This gives front-end developers, service developers, testers and accessibility specialists a shared place to examine the same journey from their different responsibilities.

## Client responsibilities and related concepts

[First Look at the Client Experience](./first-look.md) explains how to recognise the parts beneath a visible page before technical terms take over. The [Client UX Palette](./ux-palette.md) then gives those recurring parts a shared catalogue. [Client Implementation Vocabulary](./implementation-vocabulary.md) records the more precise terms and current implementation correspondence without making code names the general system vocabulary.

The [Front-end Developer Guidance](../../stakeholders/developers/front-end.md) follows the developer responsibility through client-side horizontal flows, component assemblies, accessibility, usability and browser security. [Deliverable Systems](../../reference/catalogues/deliverable-systems.md#3-service-consumer-system) explains the boundary between this consumer system and the service system.

## Client and service together

The person may experience one journey, but the journey crosses systems. The client coordinates views, focused actions, navigation, loading, feedback, retry, unsaved work and return conditions. The service provides authoritative capabilities, validates permissions, owns durable state and records consequential outcomes. The contract connects the two without allowing either side to impersonate the other's responsibility.

The [Common Flows](../../orientation/flows.md) guide gives the shared journey language. The [Service System Guidance](../service/readme.md) gives the current server-side route. The [Shared System Concerns](../shared/readme.md) explains the material that both sides need to understand.

## Related guidance

- [Stakeholder Guidance](../../stakeholders/readme.md)
- [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md)
- [Quality Perspectives](../../reference/catalogues/qualities.md)
- [Accessibility Conventions](../../../agents/conventions/development/accessibility.md)
- [Frontend Security Conventions](../../../agents/conventions/development/frontend-security.md)
- [Service Consumer System](../../reference/catalogues/deliverable-systems.md#3-service-consumer-system)