# Engineering Agent Guidance

This is the agent-facing entrance to the portable engineering guidance.

The compact repository entry point is [agents.md](../../agents.md). This domain route is intentionally short because an agent should load only the rules relevant to the task.

## Human explanation

For the accessible explanation of why these rules exist, read [Human Guidance](../humans/readme.md). The human layer explains the high-rise picture, the current problems, the examples and the contribution each role makes. Use the [Guidance Glossary](../humans/glossary.md) when a term is unfamiliar.

## Agent route

Before changing an adopting repository:

1. read the [portable agent entry point](../../agents.md);
2. read [Development Principles](./conventions/principles.md);
3. read [Development Constraints](./conventions/constraints.md);
4. select applicable documents through [Work Instructions](./conventions/.md); and
5. read the adopting repository's binding document when one exists.

The agent layer defines intent, responsibilities, invariants, decision rules and validation requirements. It should remain precise and readable. It should not require a particular product, assembly, class name or vendor library unless the document is a repository binding.

## Progressive disclosure

- [Human Guidance](../humans/readme.md) explains the problem and teaches the concepts.
- [Portable conventions](./conventions/.md) select the rules for a task.
- [Repository bindings](./conventions/bindings.md) connect portable ideas to concrete implementations.

The human route is not a substitute for the precise rules. The agent route is not a substitute for understanding when a design decision is difficult.
