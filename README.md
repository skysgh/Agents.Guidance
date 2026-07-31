# Engineering Guidance

This repository contains guidance intended to travel between products and teams. It separates durable engineering ideas from repository-specific implementation choices.

## Start here

- Human guidance: [HUMAN/README.md](./HUMAN/README.md)
- Agent guidance: [AGENTS/README.md](./AGENTS/README.md)
- Human introduction: [HUMAN-START-HERE.md](./HUMAN-START-HERE.md)
- Current state and recurring problems: [HUMAN-CURRENT-STATE.md](./HUMAN-CURRENT-STATE.md)
- Stakeholder outcomes: [HUMAN-WHAT-GUIDANCE-GIVES.md](./HUMAN-WHAT-GUIDANCE-GIVES.md)
- YAGNI and WGF: [HUMAN-YAGNI-VERSUS-WGF.md](./HUMAN-YAGNI-VERSUS-WGF.md)
- Example gallery: [examples/README.md](./examples/README.md)
- Agents: [AGENTS.md](./AGENTS.md)
- Human work instructions: [conventions/.md](./conventions/.md)
- Principles and rationale: [conventions/principles.md](./conventions/principles.md)
- Normative constraints: [conventions/constraints.md](./conventions/constraints.md)
- Developer orientation: [conventions/developers-need-to-know.md](./conventions/developers-need-to-know.md)
- Development standards: [conventions/design-standards.md](./conventions/design-standards.md)
- Code organisation: [conventions/code.md](./conventions/code.md)
- C# conventions: [conventions/code-csharp.md](./conventions/code-csharp.md)
- TypeScript conventions: [conventions/code-typescript.md](./conventions/code-typescript.md)
- Python conventions: [conventions/code-python.md](./conventions/code-python.md)
- Operations: [conventions/operations.md](./conventions/operations.md)
- Startup and discovery: [conventions/startup.md](./conventions/startup.md)
- IQueryable and governed queryability: [conventions/iqueryable.md](./conventions/iqueryable.md)
- Data protection: [conventions/data-protection.md](./conventions/data-protection.md)
- API lifecycle: [conventions/api-lifecycle.md](./conventions/api-lifecycle.md)
- Performance: [conventions/performance.md](./conventions/performance.md)
- Dependencies: [conventions/dependencies.md](./conventions/dependencies.md)
- Accessibility: [conventions/accessibility.md](./conventions/accessibility.md)
- Frontend security: [conventions/frontend-security.md](./conventions/frontend-security.md)
- Agent workflow: [conventions/agent-workflow.md](./conventions/agent-workflow.md)
- Vertical slices: [conventions/slices.md](./conventions/slices.md)
- Horizontal flows: [conventions/flows.md](./conventions/flows.md)
- Repository bindings: [conventions/bindings.md](./conventions/bindings.md)

## Two audiences

The [HUMAN](./HUMAN/README.md) folder is the accessible human route. The [AGENTS](./AGENTS/README.md) folder explains the compact agent route, whose loading contract remains [AGENTS.md](./AGENTS.md). Keep the two consistent, but do not copy the whole human reference into the agent entry point.

## Portable language

A portable document may describe a capability, boundary, invariant, state transition or responsibility. It should not name a product's base class, namespace, assembly, ORM or UI framework. Those details belong in a repository binding document.

## How to add a pattern

Start with a short concept document. Record the problem, forces, invariant, participating slices, failure cases, security implications and evidence that the pattern is useful. Mark unsettled ideas as candidates. Promote a candidate only after a real implementation or design review demonstrates that it generalises.
