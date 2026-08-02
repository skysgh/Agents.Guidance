# Guidance for Dependable Services

Software becomes harder to trust when its meaning, boundaries and responsibilities are left to emerge from the first screen, class or database table. This repository is a place to think about those things before they become expensive to change, and to keep the reasoning visible after the first release and the first team.

The guidance is written for people who design, build, test, operate, support and maintain services. It treats a service as a living system: something with users, records, decisions, dependencies, evidence, failure modes and a future.

## Find your route

The [human guidance](./engineering/humans/readme.md) is the welcoming route into the ideas, examples and practical questions. It explains why the structures matter and connects them to the people who depend on the result.

The [agent guidance](./engineering/agents/readme.md) is the precise route for applying repository conventions while changing a system. It states the invariants, boundaries and validation expectations that protect the design in implementation.

Both routes describe the same engineering concerns at different moments: understanding the system, then working within it.

## Keep the evidence close

The [audit evidence](./audit/HUMAN-GUIDANCE-AUDIT-FINDINGS.md) records how the human guidance was reviewed. The [implementation plan](./IMPLEMENTATION-PLAN.md) records the current improvement cycle and keeps larger capability gaps visible without pretending that a navigation improvement solves them.

The repository is an invitation to make serious systems more understandable, dependable and able to change. Choose the page that matches the question in front of you, and follow the connections that make the answer clearer.
