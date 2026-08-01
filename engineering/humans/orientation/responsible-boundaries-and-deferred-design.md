# Responsible Boundaries and Deferred Design

## Purpose

This document explains how a team can design a capability even when the eventual business contact, operator or named responsible person is not yet available.

## The short version

Do not wait for a person before defining the structure. Define which boundary has lifecycle responsibility for the capability, what contract it provides, what it depends on, what security rules apply and what safe default exists.

A named person may later approve a policy, operate a service or make a business decision. The technical design should remain understandable and deliverable before that person is known.

Imagine a service team asked to prepare a capability for a programme that has not yet appointed its permanent operator. The team could wait until the person arrives, but that would leave the boundary, data and failure responsibilities implicit while other work grows around them. It could also guess the future person's decisions and hard-code them too early. A better approach is to define the technical place where the capability belongs, record the decisions that are still open and give the service a safe default while the organisational assignment is resolved.

## Lifecycle responsibility is a design responsibility

Lifecycle responsibility means that a boundary or team keeps a capability coherent as it changes. Its contract must remain understandable, its state and data rules consistent, its security and classification rules visible, its dependencies known, its tests and diagnostics useful and its changes compatible with consumers.

This does not mean one person must answer every question. It means the design has a place where the question belongs.

In technical language, this may be called stewardship or ownership. The more useful question is not "Which person owns this?" but "Which boundary has responsibility for this capability across its lifecycle, and how does a person or team later engage with it?"

## Deferred does not mean undefined

A capability may not be built in the current release. It should still have a place in the intended structure and a responsible boundary. The team should understand its intended contract, dependencies, lifecycle, security expectations, persistence or external-system relationship, related slices and flows and the condition that would cause construction to begin.

This is design completeness without build completeness. It protects later construction from becoming a new invention.

## What can be decided from design evidence

A team can usually define much of the technical structure from the problem, existing patterns and platform constraints. It can distinguish capabilities, describe the information that crosses each boundary, identify required states and actions, recognise protected data, decide which parts are reusable, separate optional from required dependencies and show which later construction must fit the existing structure.

A business decision may still be open. Record it as an open decision with a safe default or a deliberate block. Do not leave the technical boundary undefined because the business decision is waiting.

## How to use this with WGF

When the team decides what to include now, it can compare what becomes safer, clearer or more reusable with the cost and complexity of including it. It can also compare what becomes harder, riskier or more expensive if the work is omitted or deferred. The important question is which structure must remain defined even while construction waits, and which boundary carries lifecycle responsibility while the final organisational assignment is unresolved.

WGF makes omission visible. It does not require every capability to be built immediately.

## Related guidance

- [The Palette: First Look](../palette/first-look.md)
- [Common Flows](./flows.md)
- [Design Before Build and What Goes First](./design-before-build-and-wgf.md)
- [Developers Need to Know](../../agents/conventions/development/developers-need-to-know.md)
