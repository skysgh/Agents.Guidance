# Common Flows

## Purpose

This document helps people recognise the journeys that appear repeatedly in enterprise applications. It is for business analysts, developers, testers, operations staff, delivery roles and architects.

When a word such as Request, Approval, Evidence or Service appears, check its Domain before assuming its meaning. See the [Guidance Glossary](./glossary.md) for polysemy, Domain, Capability and Function.

## The short version

A flow is a repeated shape for moving from one useful result to another. The business content changes, but the shape often does not. Using a known shape reduces missed steps, surprises and repeated design work.

A vertical slice carries one capability through the building. A flow connects several capabilities across the floors. The flow gives the journey a known route; the slices provide the rooms and services.

## The everyday baseline: BREAD/ST

Many managed items can begin with **BREAD/ST**:

- **Browse**: find available items or requests;
- **Read**: inspect one item or a useful projection;
- **Edit**: change permitted information;
- **Add**: create a new item;
- **Delete**: remove, withdraw or retire it according to its rules; and
- **State Transition**: move it through meaningful states such as draft, submitted, approved, published, suspended or closed.

The last part is important. Submitting, approving, publishing, suspending and closing often require decisions that are different from changing a field.

BREAD/ST is a useful starting shape. It is not a command to force every business action into generic CRUD.

## The assembly palette

Before describing a screen, describe the small set of things being assembled. A screen may look like one postcard or painting, but it is usually made from recurring elements:

- **Presenters** show collections or structures such as lists, trees, summaries and detail areas.
- **Players or renderers** show one record or one focused capability.
- **Actions** ask the system to do something, such as add, edit, submit, approve, return or cancel.
- **Action zones** group actions that belong together, such as actions for one record, one step or one permission context.
- **Flows or sequences** describe the order in which capabilities are visited or actions are taken.
- **Events** announce that something happened. Consumers may respond, retry their own handling or explicitly propagate a new event.
- **States** describe where a capability is in its lifecycle.
- **State changes and saves** record a deliberate move or persistence of information.
- **Brokers** connect these elements to application or external services without making the presenter or player know the underlying calls.

This palette helps a team look through a visible experience and find the reusable parts underneath it. The visual arrangement may be unique to a tenant or product. The elements that make it work are often familiar.

## How the elements relate

The elements have different jobs. Keeping those jobs separate prevents a visible page from becoming one large special case.

```text
View
  -> Coordinator
	  -> Presenter
		  -> Player or Renderer
			  -> Inputs and Questions
			  -> Actions and Action Zones
			  -> States and State Changes
			  -> Feedback and Evidence
	  -> Broker
		  -> Application capability or external service
```

This is a relationship map, not a requirement that every screen contain every element.

### View

A **View** is the experience a person recognises: a page, panel, workspace, form, list, tree or sequence. It is the starting point for discussion, not necessarily the boundary that owns all of the behaviour.

### Coordinator

A **Coordinator** manages movement between surfaces. It decides which Presenter or Player is active, sequences steps, applies transition conditions and handles transition events. It should not become responsible for every business rule; those rules remain with the capability that has lifecycle responsibility for them.

In the frontend code, this is the role represented by the Coordinator contracts and generic Coordinator components. Earlier design material may call this an Orchestrator. The current term is Coordinator.

### Presenter

A **Presenter** frames and coordinates a collection, page, tree or ordered group. It commonly manages collection behaviour such as selection, ordering, paging, filtering and action zones. It decides how child surfaces are arranged, but it should not know the details of every application or external call.

### Player

A **Player** presents and operates one capability or one focused record. It may load, validate, track changes, submit or cancel. Different Players can frame the same children with different interaction rules. A read Player and a write Player are siblings with different responsibilities, not simply two names for the same component.

### Renderer

A **Renderer** turns a definition, model or state into visible UI. It should concentrate on representation. A Renderer may emit events, but it should not quietly become the Coordinator, application service or persistence boundary.

### Inputs and Questions

Inputs and Questions are the information needed to perform an action safely. They include form fields, requirements, evidence requests and answers. They belong to the capability and flow that needs the information, not only to the first screen that displays it.

### Actions and Action Zones

An **Action** asks the system to do something, such as add, edit, submit, approve, return, cancel or retry. An **Action Zone** groups actions that belong together because of their record, step, state or permission context. Grouping actions makes the available choices understandable and reduces accidental mixing of applicant, assessor, approver and operator actions.

### States and State Changes

A **State** describes where a capability is in its lifecycle. A **State Change** is a deliberate move between states, such as draft to submitted or recommended to approved. A save may change data without changing lifecycle state; approval, submission and closure normally require explicit transition rules.

### Feedback and Evidence

Feedback tells a person or system what happened: validation results, progress, warnings, errors and completion messages. Evidence records what the system must later prove, such as a submitted version, decision reason, audit event or payment acknowledgement. A successful screen is not enough if the outcome cannot be explained later.

### Event

An **Event** announces that something happened. The producer owns the fact. A consumer may respond, retry or cancel its own work, but an event should not silently become an unowned command. Event handling must define delivery, duplication and failure behaviour.

### Broker

A **Broker** connects a Presenter, Player or Coordinator to an application capability or external service. It knows how to cross the boundary so the visible surface does not need to know about HTTP, databases, mapping libraries, storage providers or finance systems. The Broker connects calls; it does not absorb the business rules owned by the capability it reaches.

## The shared design contribution

No single role sees this whole palette alone:

- business analysis contributes the meaning of the View, Questions, Actions and States;
- developers test whether the Coordinator, Presenter, Player, Renderer and Broker boundaries can be implemented;
- testers check that actions, state changes, events and feedback behave correctly;
- operations checks readiness, retries, external dependencies and recovery evidence;
- security checks which Inputs, Actions, States, Events and Brokers may expose protected information; and
- architecture keeps the relationships coherent across Views, slices and flows.

The palette teaches the team how to look at a visible experience and find the design underneath it. The correct technical term is useful, but recognising the relationship is the primary goal.

## Flows that appear repeatedly

### Discover and select

Find, compare, qualify and choose one or more available items.

### Prepare and submit

Gather information, check that it is complete and commit a formal submission.

### Assess and decide

Review information or evidence, ask for clarification, recommend, escalate, approve, reject or defer.

### Publish and maintain

Prepare an item, make it available to others, change it safely, replace it or withdraw it.

### Onboard and establish participation

Identify a person or organisation, collect what is needed, establish participation and provide the correct access.

### Provision and fulfil

Turn an approved request into an allocated resource, service, entitlement or delivered result.

### Change, renew and close

Manage a live relationship or case through change, renewal, suspension, expiry and closure.

### Import, synchronise and reconcile

Receive or send information, check it, apply accepted changes, find differences and bring the systems back into agreement.

### Report and export

Prepare an authorised view or extract for a person, organisation, regulator, operator or another system.

### Notify and respond

Notice an event, choose recipients, send a message, receive a response and update the relevant capability.

### Detect, contain and recover

Find a problem, limit its effects, investigate, restore service or data and record what was learned.

Most enterprise applications use several of these shapes. Start by choosing the closest one. Do not ask a team to invent a new flow language when an existing shape already makes the journey understandable.

## Nested flows

A flow can contain another flow.

For example, a Request may use BREAD/ST. The Request may contain Evidence attachments and Comments. Evidence may have its own smaller BREAD/ST flow: browse evidence, read an attachment, add a new item, edit its description, withdraw it and move it through review states.

The parent Request flow does not need to contain every detail of the Evidence flow. It provides the connection and the context. Each smaller flow keeps its own rules visible.

## Requests and approvals

A request for something on offer is usually two connected flows.

### Part A: Prepare and submit a request

This flow helps a person or organisation turn an intention into a request that another party can assess. They browse or select the offered item or service, read its requirements and questions, add or edit the request details, attach the required Evidence and review what is complete and who may see it. They then submit the request, which records the submitted state and notifies the next participant.

This is a BREAD/ST extension. Browse, Read, Edit and Add remain useful. The important ending is **Submit**, which freezes or versions the submitted information and moves the request into assessment. It is not simply another Edit.

For request preparation, teams may remember this as **BREAST**: Browse, Read, Edit, Add, Submit and Transition. Delete or withdrawal remains a controlled lifecycle transition rather than an invitation to remove records without considering history.

### Part B: Assess and decide a request

The service or decision side receives the submitted request and checks its completeness, eligibility and Evidence. If something is missing or unclear, it returns the request for more information. Otherwise it assesses the request and records its findings, recommends, rejects, defers or sends it for approval, and then approves or declines it under the required authority. The decision is published and an approved request is handed to fulfilment or payment.

Approval is therefore a separate flow from preparation and submission. The same request record connects them, but the actors, permissions, evidence, state changes and audit requirements differ.

### Part C: Fulfil and pay when required

Payment is usually not part of approval itself. Once approved, the request may enter a fulfilment and payment flow. The system creates the approved fulfilment instruction, sends the required contract to a finance or payment system, records acknowledgement or rejection, reconciles uncertain or failed delivery and records the payment or fulfilment outcome against the request.

This shape also appears in commercial service requests. A commercial request may use different terminology, pricing, service-level rules and payment providers, but the recurring structure can still be similar: select an offer, prepare a request, submit, assess, approve or reject, then fulfil and settle. Reuse the shape only where the contracts and decision rules genuinely match.

This works at two levels:

- the pattern helps a team design a single Request capability; and
- the repeated pattern can later support reusable software that presents and coordinates many similar capabilities.

## Three levels of reuse

### Level 1: Recognised pattern

The team uses the flow name and shape to organise one capability. The code remains specific to that capability, but the design is no longer invented from nothing.

### Level 2: Reusable coordinator

When several capabilities use the same shape, shared services can handle common work such as loading, saving, validation, state changes, permissions, mapping and error presentation. The capability-specific calls remain in a small, visible part of the implementation.

### Level 3: Presenter and players

A mature platform may separate:

- a **Presenter**, which coordinates the experience and common actions;
- a **read Player**, which supplies the read capability;
- a **write Player**, which performs commands and state changes; and
- a **Broker**, which owns the calls across the relevant boundary.

This can make buttons, loading, errors, permissions and common flow behaviour reusable across many capabilities. It is an advanced destination, not the starting requirement. The first job is to recognise the flow and keep its boundaries clear.

## How to use this

When you meet an existing screen, request or journey, begin by finding the catalogue shape that feels closest. Notice whether a BREAD/ST baseline is present, whether some parts are nested capabilities and what the smallest useful complete flow would be. As similar work appears, notice which behaviour is repeating and may later move into a reusable coordinator. The purpose is to give the team a route that is already known. The business content remains specific, but the journey shape does not need to be reinvented each time.

## Related guidance

- [Portable horizontal flow rules](../agents/conventions/flows.md)
- [Vertical slices](../agents/conventions/slices.md)
- [Request flow example](./examples/10-request-bread-flow/before.md)
- [Human Documentation Writing Style](./writing-style.md)
