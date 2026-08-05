# Agent Conventions

This is the agent-facing entrance to the delivery guidance domain.

The compact repository entry point is [agents.md](../agents.md). Agents should load the mandatory baseline conventions first, then load only the additional conventions relevant to the task.

## Human explanation

For the accessible explanation, read [Human Guidance](../humans/readme.md). Use the [Guidance Glossary](../humans/shared/reference/glossary.md) when a term is unfamiliar.

## Convention groups

- [Foundation conventions](./conventions/foundations/readme.md)
- [Capability conventions](./conventions/capabilities/readme.md)
- [Development conventions](./conventions/development/readme.md)
- [Documentation and workflow conventions](./conventions/documentation/readme.md)

The agent layer defines intent, responsibilities, invariants, decision rules and validation requirements. Human documents explain why and show examples; these conventions state the precise rules.