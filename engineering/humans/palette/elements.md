# Palette compatibility route

The element catalogue now lives in the [Client UX Palette](../systems/client/ux-palette.md). This page remains temporarily so older links reach the canonical client-system catalogue.

## View

A **View** is the experience a person recognises: a page, panel, workspace, form, list, tree, report or sequence. It starts the conversation. It does not automatically own all of the behaviour visible within it.

## Coordinator

A **Coordinator** manages movement between surfaces. It sequences steps, applies transition conditions and responds to transition events. It coordinates the journey without absorbing every business rule.

## Presenter

A **Presenter** frames a collection, page, tree or ordered group. It may manage selection, ordering, paging, filtering and action zones. It should not need to know how every record is loaded or saved.

## Player

A **Player** operates one capability or focused record. It may load, validate, track changes, submit or cancel. Read and write Players may share visual children while retaining different responsibilities.

## Renderer

A **Renderer** turns a model, definition or state into visible UI. It concentrates on representation. It may report user interaction, but it should not quietly become an application service or persistence boundary.

## Questions and Inputs

Questions and Inputs are the information needed to make a decision or perform an action. They include fields, requirements, answers and Evidence. They belong to the capability and flow that need them, not only to the first form that displays them.

## Actions and Action Zones

An **Action** asks the system to do something. An **Action Zone** groups actions by record, step, state or permission context. This makes it clear which actions belong to an applicant, assessor, approver, operator or another role.

## States and State Changes

A **State** describes where a capability is in its lifecycle. A **State Change** moves it deliberately, such as draft to submitted, submitted to under assessment or recommended to approved. A save may change information without changing lifecycle state.

## Feedback and Evidence

Feedback tells people or systems what happened. Evidence records what must later be proved, such as a submitted version, decision reason, audit entry, validation result or payment acknowledgement.

## Events

An **Event** announces that something happened. The producer owns the fact. A consumer may respond, retry or cancel its own work, but an Event should not silently become an unowned command.

## Brokers

A **Broker** knows how to reach another capability or external system. It hides transport, persistence, mapping, storage and provider details from the View, Presenter and Player. It connects calls; it does not take responsibility for the business decision made by the capability it reaches.

## The main lesson

Name the elements that are present. Do not create elements only to satisfy the vocabulary. The value comes from separating responsibilities that are already different, then reusing the parts that genuinely recur.

When these element jobs are familiar, continue to [Palette Relationships](./relationships.md).
