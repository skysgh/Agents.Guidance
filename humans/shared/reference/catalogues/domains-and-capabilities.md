# Domains and Capabilities

A domain is an area of meaning in which concepts, relationships, rules and decisions belong together. A capability is a useful ability provided within that meaning, such as preparing a request, submitting evidence, assessing an application, approving a decision or producing a report.

The domain gives a capability its language and purpose. The capability gives the domain a way to act. Neither term is merely a project name, database area or class namespace. A technical domain can describe configuration, identity, storage, diagnostics or messaging just as a business domain can describe applications, people, decisions or payments.

## From meaning to implementation

The people and systems around a service usually describe a problem in conceptual terms. They recognise a request, a student, a teacher, an assessment, a payment or a decision. Those words may be imprecise, locally understood or used differently by different groups. That conceptual language is still valuable because it is how the participants recognise the service.

Engineering then performs the harder logical work. It identifies the things, identities, relationships, states and rules that must be distinguished for the system to behave consistently. A logical model may separate concepts that people casually combine, or recognise that one familiar word has several meanings in different domains. This is why a screen, a conversation or a vendor model should not be copied directly into the domain model.

A capability should have a responsible domain, a contract, a lifecycle and a clear relationship to the information and effects it controls. It may be reached from several sites and flows. Those consumers can have different views and input or output shapes while using the same capability rules.

## Separation and cohesion

Separation of concerns keeps different kinds of responsibility from becoming one tangled decision. High cohesion keeps the responsibilities that belong together close enough to understand and change together. Low coupling keeps the relationships between separate responsibilities small, explicit and replaceable.

These principles apply before code. They help decide whether a site should be combined with another site, whether a flow belongs to one capability or coordinates several, whether a domain is being asked to understand a provider detail and whether a logical package is carrying unrelated change. They also apply inside components and classes.

A service is one possible implementation shape for a capability or a coordinator. It is not the starting point for discovering the capability. A repository, broker, presenter, coordinator, registry, renderer, constant or contract is also an implementation shape that may be appropriate when its responsibility is real and coherent.

For implementation guidance, read [Logical Deployment Modules](./ldms.md), [Logical Layers](./logical-layers.md), [Logical Building Blocks](./logical-building-blocks.md), [LDM Layers and Contents](../../../development/layers.md) and [Contracts](../../../development/contracts.md). For design prompts, use the [domain and capability checklist](../checklists/domains-and-capabilities.md).
