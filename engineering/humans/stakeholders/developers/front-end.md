# Front-end Developer Guidance

A service can have a correct API and still fail the person who needs to use it. The page may combine too many actions, hide the current state, lose work when a request is slow or fail when someone uses a keyboard, zoom or assistive technology. A front-end developer works where the service becomes a usable experience, so those failures are part of the system rather than decoration around it.

The front-end developer builds the service consumer system: for a browser-based service, commonly a single-page application (SPA), its assets, browser execution, client-side state, views, interaction flows and calls to the service interfaces. The consumer system is distinct from the server-side service system. They may be delivered by the same team and released together, but they have different execution environments, trust boundaries, failure modes and evidence.

## A useful way into the responsibility

Imagine a request journey that works in a developer demonstration. A person can enter information, click through the screens and receive a response. In real use, the person loses connection between steps, cannot tell whether the submission succeeded, cannot reach the control with a keyboard and sees a generic error that does not explain what to do next. The server may be functioning correctly. The delivered service is still failing its consumer.

The front-end developer turns the consumer side of the journey into something people can find, understand, complete and recover from. They work from prepared capabilities and contracts, but they also provide evidence when the service contract, flow or wording cannot support a credible user experience.

This route focuses on the client side of the boundary. It does not make the SPA the authority for business meaning, authorisation or durable state. The server must enforce those responsibilities even when the SPA provides the visible interaction.

## What the front-end developer owns

The exact assignment depends on the team, but this responsibility normally includes:

- the consumer system's views, client-side state, navigation and interaction behaviour;
- the browser-side part of horizontal flows, including movement between capabilities and handling of waiting, failure, retry and return conditions;
- the mapping between service contracts and the information a person can understand and act on;
- component boundaries, composition, rendering, input handling and feedback;
- keyboard, assistive-technology, zoom, reflow, language and reduced-motion behaviour;
- protection of browser-side data, credentials, links, messages, dependencies and generated assets;
- evidence that the consumer system meets functional, accessibility, usability, security and quality-in-use expectations; and
- the consumer system's delivery, compatibility, diagnostics and maintenance needs.

This does not make the front-end developer the Product Owner, business analyst, accessibility authority, security authority or service-side domain owner. Those perspectives still contribute meaning and authority. The front-end developer makes the client-side responsibility real, testable and maintainable.

## The consumer system is a real system

The SPA is not merely a set of screens attached to the service. It has its own:

- execution environment: browser, device, network and runtime capabilities;
- state: transient input, navigation, loading, error, retry and view state;
- contracts: service calls, client-side component contracts and user-facing interaction expectations;
- dependencies: browser APIs, frameworks, packages, fonts, scripts, media and external origins;
- lifecycle: build, publish, cache, update, compatibility, rollback and retirement;
- security boundary: untrusted browser code and content must not become an authority for protected data or decisions; and
- evidence: functional, integration, accessibility, usability, performance, security and recovery behaviour must be checked.

The [Deliverable Systems](../../reference/catalogues/deliverable-systems.md) catalogue calls this the service consumer system. Its separation from the [service system](../../reference/catalogues/deliverable-systems.md#2-service-system) matters because a browser can lose memory, lose connectivity, run stale assets, be inspected by its user or execute an injected script in ways a server process cannot.

## Two sides of a horizontal flow

The user may experience one journey, but the journey crosses two systems.

The consumer-side flow is where the experience becomes complete for a person. It coordinates views, focused actions, navigation, client-side validation, loading, progress, errors, retry, cancellation, unsaved work and the return to a meaningful state. The SPA is often the clearest place to discuss how several capabilities are assembled into one human journey.

The service-side system supplies capabilities, enforces rules and owns durable state. It may also coordinate a business flow when several capabilities, actors or durable steps must be managed together. The SPA must not become the authority for approval, access, business state, audit or a consequential transition merely because it displays the button.

The two sides therefore have a partnership:

- the SPA makes the journey understandable and operable for its consumer;
- the service provides authoritative capabilities, decisions and durable effects;
- the contract states what can be requested, what comes back and how failure is represented; and
- the testing system checks both systems separately and checks the relationship between them.

A successful HTTP response does not prove that the person received the intended outcome. A visually complete page does not prove that the service accepted the intended meaning. Both sides need evidence.

## Components are assemblies, not authorities

A component is a physical assembly for a focused part of the consumer experience. It should have a clear responsibility and a contract with the components or capability around it. It is not automatically a business object, a domain boundary or an owner of persistence.

Useful component shapes include:

- **Input-only components:** collect a value, choice or answer and communicate the user's intent or validation result. They should not decide authoritative permissions, state transitions or business meaning on their own.
- **Output-only components:** present information, status, evidence or a result without changing it. They should make important states and feedback understandable without requiring a hidden interaction.
- **Collections of inputs or outputs:** arrange repeated fields, choices, records, messages or summaries while keeping the child responsibilities visible.
- **Collections of collections:** organise a larger experience such as a page, workspace, table with grouped rows or multi-step flow. The parent coordinates composition; it should not absorb every rule belonging to its children or the service capabilities it calls.
- **Assemblies containing both input and output:** combine a focused question with the information needed to answer it, such as a form with guidance, validation and a submitted result. The assembly still needs a clear primary action and a visible owner for each rule.

These are responsibility descriptions, not a mandatory class hierarchy. A component may be reused when its meaning and contract remain sound. It should not be made generic merely because two screens look similar. Reuse that hides different permissions, states, error conditions or accessibility needs creates a harder system rather than a simpler one.

The [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md) catalogue gives the shared vocabulary. The [Common Flows](../../orientation/flows.md) guide explains how a visible journey can reveal presenters, players, actions, states, feedback and brokers beneath it.

## Accessibility and usability are part of the contract

The front-end developer gives the service its practical access to people. Accessibility is not a visual polish step after implementation. It is part of the experience contract and acceptance evidence.

The applicable [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/TR/WCAG22/) conformance target, jurisdictional requirement and any exception must be identified for the service. The front-end developer then helps make that expectation real through:

- semantic structure, meaningful headings, landmarks, accessible names and labels;
- complete keyboard operation and a visible, logical focus order;
- validation errors that identify the affected field and explain how to correct it;
- status, progress, success and failure messages that assistive technology can perceive;
- sufficient colour contrast without using colour as the only signal;
- zoom, text resizing, reflow, high contrast and reduced-motion support;
- usable controls, tables, dialogs, menus and touch targets;
- clear language, predictable movement and one meaningful primary action where a focused step is appropriate; and
- evidence from automated checks, keyboard use, representative screen-reader workflows, zoom and real task exploration.

Usability is broader than conformance. A page can pass a technical accessibility check and still make a person unsure what to do, combine unrelated decisions, lose entered information or provide feedback too late. The front-end developer works with users, analysts, product, design, testers and support to expose those failures before release and after change.

Mobile consideration belongs here for the underlying reason, not as an automatic device mandate. Designing a focused action for a small screen can improve data entry, attention and error recovery for everyone. A mobile application is only one possible physical response.

## Browser security is boundary security

The browser is a hostile or inspectable execution environment. A person can inspect their own browser state, and injected or compromised code may run with the page's privileges. The SPA must therefore never be treated as the place where the organisation's final authorisation decision lives. The service enforces access, data protection, state transitions and audit at its own boundary.

For browser applications:

- do not put access tokens, ID tokens, refresh tokens, secrets or equivalent credentials in `localStorage`, `sessionStorage`, IndexedDB, the Cache API, URLs or client logs;
- local browser storage may hold non-security preferences such as theme or UI choices, but it must not become an authentication or authorisation authority;
- where cookies carry the authenticated session, use `Secure`, `HttpOnly` and an appropriate `SameSite` policy, and protect state-changing requests against cross-site request forgery;
- `Secure` means the browser sends the cookie only over HTTPS. It does not itself encrypt the cookie; HTTPS provides transport encryption and server identity protection;
- `HttpOnly` means client-side JavaScript cannot read the cookie. This reduces the value of token theft through script injection, but it does not make cross-site scripting harmless and it does not remove the need for CSRF protection;
- `SameSite` controls when the browser sends the cookie with cross-site requests. It is useful protection, but its setting must fit the actual sign-in and integration flow;
- encode untrusted text for its output context and avoid unsafe HTML, script, URL and style injection;
- use a restrictive Content Security Policy and Trusted Types where supported and appropriate;
- validate redirect, download, `postMessage` and external-link targets;
- for a browser SPA using OIDC, let OIDC establish and validate identity while the SPA-to-service interaction uses the protected cookie session only; do not persist access or ID tokens in browser storage or URLs;
- make third-party scripts, frames, fonts, analytics, source maps and client telemetry explicit trust and privacy decisions; and
- test authentication expiry, logout, CSRF, XSS, clickjacking, unsafe redirects, stale assets and sensitive-data leakage.

The [Frontend Security Conventions](../../../agents/conventions/development/frontend-security.md) and [Security in Transit Checklist](../../reference/checklists/security-in-transit.md) provide the detailed prompts. They support this explanation; they do not replace the service's own security authority or server-side enforcement.

## Evidence and handoffs

The front-end developer receives:

- the user and affected-person meaning from analysis and product;
- capability and contract definitions from the responsible Domain and service system;
- quality, accessibility, privacy and security conditions from the relevant authorities;
- flow and boundary structure from architecture and technical leadership; and
- release, support, operational and maintenance conditions from the wider delivery team.

The front-end developer returns:

- a consumer system that implements the intended interaction and client-side flow;
- explicit mappings between service responses and user-visible states;
- component contracts and the boundaries that keep them focused;
- accessibility, usability, security, integration, performance and failure evidence;
- diagnostics and support information for problems a consumer can see; and
- known limitations, compatibility conditions and deliberate deferrals.

When a requirement cannot be made accessible, usable, secure or understandable in the current contract, raise it to the responsible authority. Do not hide the problem in a component, local browser state or a generic error message.

## Related guidance

- [Developer Guidance](./readme.md)
- [Stakeholder Guidance](../readme.md)
- [Guidance for Developers](../../orientation/guidance-for-developers.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md)
- [Common Flows](../../orientation/flows.md)
- [Quality Perspectives](../../reference/catalogues/qualities.md)
- [Accessibility Conventions](../../../agents/conventions/development/accessibility.md)
- [Frontend Security Conventions](../../../agents/conventions/development/frontend-security.md)
- [Security in Transit Checklist](../../reference/checklists/security-in-transit.md)