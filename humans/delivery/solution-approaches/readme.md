# Solution Approaches

A service outcome can be produced in different ways. A team may write custom software, configure a managed platform, compose workflows and data models through low-code tools, extend a vendor platform with code, or combine several approaches. The approach changes the physical implementation. It does not remove the need to understand the meaning, responsibility, quality, security, evidence and lifecycle of the outcome.

This page uses **platform-composed solution** as a vendor-neutral term for a solution whose behaviour, data, workflow or interface is substantially created through configuration, declarative definitions, managed services, visual composition or platform extension. It includes what organisations may call no-code, low-code, configuration-first, SaaS extension, workflow automation or citizen development. These labels describe a way of producing software; they do not prove that the result is simple, safe or suitable.

## Why the distinction matters

A configured solution can be delivered quickly and still create serious long-term obligations. Its behaviour may be spread across visual flows, rules, permissions, data configuration, vendor defaults, integration settings and release controls. A team may be unable to explain which boundary owns a decision, how a change is tested, what happens when a platform limit is reached or how the solution would be recovered or replaced.

Treating a platform configuration as "not implementation" creates the same risks as treating custom code as self-explanatory. Someone still has to define the model, make the decisions, test the behaviour, protect the data, operate the result, preserve evidence and manage the platform relationship.

The useful question is not whether a solution contains code. The useful questions are:

- what responsibility does it perform;
- what meaning and data does it own or represent;
- where does it execute;
- who can change it;
- what contracts and dependencies does it have;
- how is it tested and observed; and
- what happens when the platform, supplier, configuration or organisation changes?

## Keep three decisions separate

Do not use one label to answer three different questions.

### Responsibility

Identify the responsibility before selecting the construction approach. It may be a service capability, consumer experience, integration flow, delivery process, testing capability or supporting record system. The [Deliverable Systems](../../reference/catalogues/deliverable-systems.md) catalogue helps identify the boundary and its evidence.

### Implementation approach

Choose how the responsibility will be produced:

- **Custom-built:** behaviour is primarily implemented in software the team controls.
- **Configured:** behaviour is primarily selected and shaped through platform settings, data definitions, rules, permissions or workflow configuration.
- **Low-code or declarative composition:** behaviour is assembled from visual flows, expressions, reusable components, forms, rules and managed connectors.
- **Platform-extended:** a managed platform supplies the runtime and foundation while the team adds custom code, components, data structures or extensions.
- **Hybrid:** responsibility is deliberately divided between custom services, clients, integrations and one or more configured platforms.

These are implementation approaches, not quality levels. A configured solution may be well engineered. A custom solution may be poorly designed.

### Execution environment

Record where the result runs and who controls that environment. It may run in a custom service runtime, browser, integration runtime, managed SaaS tenant, workflow engine, data platform or several connected environments. The environment's limits, release model, identity boundary, data location, availability, support route and failure behaviour are part of the design.

A platform can be an external dependency and also host a delivered solution. Those are different relationships. The organisation may depend on the supplier while still being responsible for the configured capability, its data, its decisions and its users.

## Model before configuring

Platform objects, fields, screens, flows and rules are physical representations. They should not silently become the logical model just because the platform presents them first.

Use the existing [Conceptual, Logical and Physical Models](../../reference/catalogues/conceptual-logical-physical-models.md) guidance:

```text
Conceptual:
  What do people, organisations and connected systems recognise and need?

Logical:
  What identities, relationships, states, rules, capabilities and authorities
  must remain meaningful and dependable?

Physical:
  How are those meanings represented and executed through platform objects,
  configuration, workflows, custom code, interfaces, storage and infrastructure?
```

For a platform-composed solution, make the mappings visible. For each important platform representation, be able to explain which logical responsibility it carries, which rules it enforces, which system is authoritative and what happens if the platform representation changes.

A platform's standard object or workflow may be useful. It is not automatically the right domain concept. A vendor's organisational structure, record lifecycle or terminology may fit the problem, may need translation at the boundary or may be unsuitable for the responsibility being designed.

## Develop the solution responsibly

Use a sequence that keeps the platform decision subordinate to the outcome:

1. Define the outcome, affected people, obligations, qualities and failure consequences.
2. Identify the responsibility and system boundary, including what the platform will and will not own.
3. Establish the conceptual and logical models before creating platform objects or workflows.
4. Compare custom, configured, platform-extended and hybrid approaches against the real workload and lifecycle.
5. Record the platform constraints that affect data, security, performance, accessibility, integration, testing, recovery and change.
6. Build a thin representative slice that proves the difficult boundaries, not only the easiest screen or flow.
7. Put configuration, declarative definitions, custom extensions and environment bindings under controlled change wherever the platform permits.
8. Test normal behaviour, permissions, invalid states, duplicate actions, retries, limits, vendor failures, upgrades and recovery.
9. Make operational ownership, support routes, monitoring, audit evidence, data deletion and migration explicit.
10. Record portability, replacement and exit conditions before the organisation becomes dependent on the platform.

The fastest first configuration is not necessarily the fastest path to a dependable service. The evidence from the representative slice should decide whether the approach remains suitable.

## Questions to consider

Use the relevant catalogue and checklist after understanding the responsibility. [Deliverables](../../reference/catalogues/deliverables.md) identifies the wider outcome beyond the configured solution. [External Dependencies](../../reference/catalogues/external-dependencies.md) helps describe supplier and platform boundaries. [Registries](../../reference/catalogues/registries.md) helps record platform, component, dependency, expiry, release and evidence facts. The [Deliverables Checklist](../../reference/checklists/deliverables.md) and subject checklists turn those concerns into review prompts.

Ask:

- Which logical concepts are represented by platform records, rules or workflows?
- Which system is authoritative for each important fact?
- Which decisions are enforced by configuration, custom code, a connected service or a person?
- Can the team inspect, version, review, test and roll back the actual behaviour?
- What platform limits affect scale, transaction volume, storage, automation, API use or recovery?
- How are identity, access, segregation of duties, privacy, retention and deletion handled?
- What evidence proves that the configured behaviour meets the functional and quality requirements?
- How are vendor releases, default changes, outages and deprecations detected and managed?
- Can data, rules, mappings and contracts be migrated if the platform becomes unsuitable?
- Who maintains the solution when the original configurator, supplier or delivery team is no longer available?

## Examples without making them architecture

Salesforce, MuleSoft, Informatica, workflow products, CRM platforms, case-management products, data platforms and other managed services may all be examples of platform-composed implementation. They are not recommendations and they do not define the category.

A Salesforce configuration may implement a service capability, a consumer experience, an integration flow or several connected responsibilities. MuleSoft or Informatica may implement a dedicated Integration System, or a small connector may remain part of another system. The classification follows responsibility, execution boundary, lifecycle and evidence rather than the product name.

## Related guidance

- [Delivery Guidance](../readme.md)
- [Conceptual, Logical and Physical Models](../../reference/catalogues/conceptual-logical-physical-models.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [External Dependencies](../../reference/catalogues/external-dependencies.md)
- [Registries](../../reference/catalogues/registries.md)
- [Deliverables Checklist](../../reference/checklists/deliverables.md)
- [Vendor Material and Engineering Competence](../../orientation/vendor-material-and-engineering-competence.md)
- [Selecting a Language and Framework](../../orientation/language-and-framework-selection.md)
