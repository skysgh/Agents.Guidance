# Agent Guidance

This repository contains portable engineering guidance. Before changing code in a repository that adopts it:

For a human explanation of these instructions, read the [Human Guidance](./HUMAN/README.md). It explains the concepts, examples and high-rise model in accessible language. This file remains the compact loading contract for agents.

1. Read this file.
2. Read [Development Principles](./conventions/principles.md).
3. Read [Development Constraints](./conventions/constraints.md).
4. For code work, read [Code](./conventions/code.md).
5. Read the conventions listed in [Work Instructions](./conventions/.md) that match the task.
6. Read that repository's binding document, if one exists. The binding document maps portable concepts to local projects, contracts, base classes and infrastructure.

## Guidance layers

Portable guidance defines intent, responsibilities, invariants and decision rules. It must not require a particular framework, assembly, class name or vendor library.

Repository bindings define the local implementation: project names, namespaces, contracts, base classes, persistence mechanisms, endpoint conventions and known exceptions. A binding may be stricter than the portable guidance, but must not silently weaken it. Resolve conflicts in this order: non-negotiable security and safety constraints; more-specific applicable portable conventions; repository bindings; established local patterns; then the user request.

Do not treat candidate slices or flows as settled architecture. Each candidate must be validated against a real use case, its state transitions, security boundary, data ownership and test strategy before implementation.

## Pattern vocabulary

- A [vertical slice](./conventions/slices.md) is an end-to-end capability with a coherent contract and test boundary.
- A [horizontal flow](./conventions/flows.md) coordinates one or more slices to achieve a user or organisational outcome.
- A [binding](./conventions/bindings.md) connects portable guidance to a concrete repository.

Keep portable documents human-readable. Keep this entry point short enough to load before work begins.
