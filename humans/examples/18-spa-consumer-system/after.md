# After: A Client System with a Service Boundary

The team recognises two systems that participate in one experience:

- the **client system** owns browser execution, views, component assemblies, client-side state, consumer-side flow, feedback and the mapping of service results into understandable interaction; and
- the **service system** owns business capabilities, authorisation, durable state, authoritative transitions, audit and external effects.

The [Deliverable Systems](../../shared/reference/catalogues/deliverable-systems.md) catalogue gives the wider system relationship. The [Client System Guidance](../../delivery/systems/client/readme.md) follows the client boundary, while the [Service System Guidance](../../delivery/systems/service/readme.md) follows the server-side responsibility.

## The client flow

The client coordinates the human journey without becoming the authority for the business decision:

1. The Presenter shows the offer and the current request summary.
2. Input components collect answers and identify presentation-level errors.
3. Output components show requirements, evidence status and service feedback.
4. Collections arrange questions, Evidence and Comments without absorbing their ownership.
5. The Coordinator moves between preparation, review and submission surfaces.
6. The Broker calls the request, evidence and decision capabilities through contracts.
7. The client shows a pending state while the outcome is uncertain and gives the person a safe retry or return path.
8. The service confirms the authoritative result before the client presents the request as submitted.

The [Client UX Palette](../../delivery/systems/client/ux-palette.md) describes these assemblies. The [Common Flows](../../orientation/flows.md) describes the shared prepare-and-submit shape. The client can make the journey feel complete, but it cannot approve, authorise or invent a durable state transition.

## Component responsibility

The page is composed from focused responsibilities:

- input-only components collect a value or answer and report intent;
- output-only components present requirements, state, evidence or feedback;
- collections of inputs or outputs arrange repeated content;
- collections of collections organise a page or step without taking ownership of every child rule; and
- a focused assembly may combine input and output when the person needs context to complete one action.

Each component has a contract, an accessible name and a primary responsibility. Business invariants, authorisation and persistence remain behind the service capability. Similar visual shapes are not enough reason to share a component when their permissions, states, error conditions or lifecycle differ.

## Accessibility and usability evidence

The client identifies the applicable WCAG target and records exceptions. The team checks semantic structure, headings, labels, focus order, keyboard operation, error association, status announcements, contrast, zoom, reflow, reduced motion and representative assistive-technology tasks.

The task evidence also asks whether a person understands what to do, knows whether the request succeeded, can recover from interruption and can complete one focused action without mixing unrelated decisions. Passing an automated accessibility scan is useful evidence, but it does not by itself prove quality in use.

## Browser security evidence

OIDC establishes and validates identity where it is used, but browser-to-service interaction uses the protected cookie session. Authentication and authorisation tokens are not placed in `localStorage`, `sessionStorage`, IndexedDB, the Cache API, URLs or client logs.

Cookies use `Secure`, `HttpOnly` and an appropriate `SameSite` policy. `Secure` makes the browser send the cookie only over HTTPS; `HttpOnly` prevents client JavaScript from reading it; `SameSite` limits cross-site cookie sending. State-changing cookie-authenticated requests also have CSRF protection. The service enforces authorisation even when the SPA hides an action from the user.

The team tests authentication expiry, logout, CSRF, XSS, unsafe redirects, `postMessage` targets, third-party scripts, stale assets and sensitive-data leakage. It records Content Security Policy, dependency, source-map and telemetry decisions.

## Client and service evidence

The testing system preserves a scenario identity and correlation identity across the browser, service and any provider boundary. Evidence shows:

- what the client displayed and requested;
- what the service received, accepted or rejected;
- which system owned each state and decision;
- what happened during timeout, duplicate submission, retry or stale data;
- whether accessibility and security conditions held; and
- how the published client assets were versioned, invalidated, rolled back or recovered.

A green browser test and a successful API response are not the same claim. The client, service, testing system and delivery pipeline each provide evidence for their own boundary and for the contract between them.

## What changed

The first version treated the SPA as presentation furniture and allowed the browser to carry hidden authority. The improved version gives the client its own system boundary, component vocabulary, human-quality responsibilities, security controls and evidence path while preserving the service as the authority for business meaning and durable outcomes.
