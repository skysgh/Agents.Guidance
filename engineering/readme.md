# Engineering Guidance

Engineering is the work of making a service dependable enough for other people and systems to rely on it.

The visible feature is only one part of that work. A service also needs clear responsibilities, boundaries, security, persistence, recovery and evidence that it behaves as intended. These needs become more important when other people and systems depend on the result.

Not every service needs the same amount of structure. A short-lived script, a tool used by one team, a shared service and a public-facing system have different audiences and different consequences when something goes wrong. The construction effort should match those consequences.

Across all of these situations, the same questions matter. Who depends on the service? What does it promise? Which responsibilities and boundaries keep it dependable? What happens when information, access or a supporting service fails? How can people operate and change it after the first team has moved on?

You do not need to know whether a question belongs to application code, a database, infrastructure, testing or operations before you can raise it. Start with the people and systems that rely on the result, then follow the responsibility to the boundary where it can be understood and maintained.

These questions provide the shared engineering context. The guidance then takes two forms because understanding a design and applying a precise convention are different activities.

The [human guidance](./humans/readme.md) takes time to explain the ideas, consequences and examples in a connected story. It uses familiar comparisons when they help people see relationships that are difficult to hold in a screen, ticket or code file.

The [agent guidance](./agents/readme.md) keeps the same engineering intent while stating the precise conventions, invariants and validation requirements used when changing a system. It is designed to be consulted selectively, at the point where a specific change needs a specific rule.

Both forms ask the same underlying question: what must be true for this service to remain useful and trustworthy as people, dependencies, priorities and teams change? The human pages explain why the answer matters; the agent pages make the answer actionable.
