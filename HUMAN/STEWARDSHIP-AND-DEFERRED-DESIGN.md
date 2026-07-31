# Responsible Boundaries and Deferred Design

## Purpose

This document explains how a team can design a capability even when the eventual business contact, operator or named responsible person is not yet available.

## The short version

Do not wait for a person before defining the structure. Define which boundary has lifecycle responsibility for the capability, what contract it provides, what it depends on, what security rules apply and what safe default exists.

A named person may later approve a policy, operate a service or make a business decision. The technical design should remain understandable and deliverable before that person is known.

## Lifecycle responsibility is a design responsibility

Lifecycle responsibility means that a boundary or team is responsible for keeping a capability coherent:

- its contract remains understandable;
- its state and data rules remain consistent;
- its security and classification rules remain visible;
- its dependencies remain known;
- its tests and diagnostics remain useful; and
- its changes remain compatible with consumers.

This does not mean one person must answer every question. It means the design has a place where the question belongs.

In technical language, this may be called stewardship or ownership. The more useful question is not "Which person owns this?" but "Which boundary has responsibility for this capability across its lifecycle, and how does a person or team later engage with it?"

## Deferred does not mean undefined

A capability may not be built in the current release. It should still have:

- a place in the intended structure;
- a responsible boundary;
- a contract or intended contract;
- dependencies;
- lifecycle and security expectations;
- persistence or external-system intention;
- related slices and flows; and
- a condition that would cause the work to begin.

This is design completeness without build completeness. It protects later construction from becoming a new invention.

## What can be decided from design evidence

A team can usually define the technical structure from the problem, existing patterns and platform constraints:

- which capabilities are distinct;
- which information crosses each boundary;
- which states and actions are required;
- which data needs protection;
- which parts are reusable;
- which dependencies are optional or required; and
- which later construction must fit the existing structure.

A business decision may still be open. Record it as an open decision with a safe default or a deliberate block. Do not leave the technical boundary undefined because the business decision is waiting.

## How to use this with WGF

For each capability or design choice, ask:

- What becomes safer, clearer or more reusable if we include this now?
- What cost or complexity does inclusion add?
- What becomes harder, riskier or more expensive if we omit or defer it?
- What structure must remain defined even if construction is deferred?
- Which boundary carries lifecycle responsibility while the final organisational assignment is unresolved?

WGF makes omission visible. It does not require every capability to be built immediately.

## Related guidance

- [The Palette: First Look](./PALETTE-FIRST-LOOK.md)
- [Common Flows](./FLOWS.md)
- [Design Before Build and What Goes First](../HUMAN-YAGNI-VERSUS-WGF.md)
- [Developers Need to Know](../conventions/developers-need-to-know.md)
