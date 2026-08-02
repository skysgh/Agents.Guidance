# Logical Deployment Modules

A Logical Deployment Module, or LDM, is a logical package. Its components are delivered together as one package. It gives a coherent part of the system a place where its contracts, data, dependencies, security and responsibility for change can remain understandable across time.

An LDM is not a service. It is not a project, a layer, a database or a single domain. It is the logical package that contains and organises those things. An LDM may be deployed at the same time as other LDMs, including in a whole-system deployment. It does not promise that it can be deployed independently, and it does not need to be independently deployable to be useful.

A service may begin as one deployment and still carry identity, permissions, requests, evidence, payments and diagnostics with different responsible boundaries and lifecycles. When those responsibilities are placed together only because they share a process or database, the first change can make later separation expensive. An LDM gives a coherent responsibility a place before the project structure hardens around the first implementation.

## Why an LDM exists

A simple application may begin as one deployed service and one LDM. That does not make all of its concerns one domain. The logical package should be visible from the beginning so that the service can grow without forcing unrelated responsibilities into one undifferentiated project.

The risk of having only one LDM is not the number one. The risk is using that number as permission to place unrelated domains together. Once data responsibility, contracts, permissions and workflows are mixed, later separation becomes expensive. The first LDM should therefore be small enough to operate and structured enough to preserve future choices.

For most enterprise applications, a useful minimum is:

```text
application
  -> System LDM
       -> shared technical and system domains
  -> Business LDM
       -> the commissioned department's business domains
```

The System LDM is commonly developed first because business capabilities need somewhere dependable to obtain configuration, identity context, storage, diagnostics, access policy and other shared foundations. The business LDM is then responsible for the business concepts, decisions and workflows that give the application its purpose.

An application commissioned by one department may stop at those two LDMs. A more sophisticated system serving several departments may add further LDMs where different departments or business areas need distinct responsibility, contracts, data, deployment cadence or operational responsibility.

## When to add another LDM

Create or consider another LDM when a part of the system has a genuinely different combination of:

- business or technical purpose;
- data responsibility or classification;
- deployment or release needs;
- security or authorisation responsibility;
- operational team or lifecycle;
- dependency and failure behaviour; or
- consumer and compatibility expectations.

Do not split merely because a folder is large, and do not merge merely because two domains currently share a database or user interface. Related domains may live in one LDM when their purpose, responsibility and lifecycle remain coherent. A separate LDM becomes useful when keeping them together would hide a meaningful difference or constrain future change.

## The System LDM and business LDMs

The System LDM contains shared system capabilities and technical domains. It may include identity, users, roles, permissions, settings, configuration, diagnostics, storage, startup, mapping, auditing and other services described in [System LDM Services](./services.md).

The System LDM can provide the ability to authenticate an actor or evaluate permission. It does not define what a business approval means. A business LDM is responsible for its concepts, states, decisions and workflow, while using System LDM contracts where appropriate.

Person and Group may begin in the System LDM when they are shared identity concepts. They may later deserve another LDM when their relationships, administration, reuse or lifecycle become substantial. The boundary follows responsibility and evidence, not the apparent familiarity of a word.

## An LDM contains logical layers

An LDM is not a bag of services. Between the LDM and its components are implementation responsibilities. The consumer-facing interface physically represents how people or connected systems recognise the interaction. Application and domain code physically implements the logical model's ontological categories, identities, relationships, states and rules. Persistence and external-effect code represents information and behaviour through databases, files, caches, indexes, queues and other technical media.

These responsibilities are architectural rather than necessarily separate projects or deployments. They keep the conceptual meaning, logical model and physical representation from being confused. The [Logical Layers](../../reference/catalogues/logical-layers.md) catalogue explains the implementation areas, while [Conceptual, Logical and Physical Models](../../reference/catalogues/conceptual-logical-physical-models.md) explains the model types. The areas contain contracts, constants, models, services, registries, repositories, interfaces and implementations as appropriate.

When a new type needs a home, [Logical Deployment Modules](../../reference/catalogues/ldms.md), [Logical Layers](../../reference/catalogues/logical-layers.md) and [Logical Building Blocks](../../reference/catalogues/logical-building-blocks.md) explain the structures that make that decision clearer. They are reference points to return to when the responsibility is uncertain, not a reading gate before useful work can begin.

## A portable naming example

A repository may use a structure such as:

```text
App.Modules.{LDM-Key}.AppInterfaces
App.Modules.{LDM-Key}.Application
App.Modules.{LDM-Key}.Domains
App.Modules.{LDM-Key}.Infrastructure
App.Modules.{LDM-Key}.Shared
```

The names are a binding example, not a universal requirement. `App` keeps the application prefix deliberately portable. `Modules` keeps the modular structure visible. The LDM key identifies the specific responsibility or entry point. Another repository may use different names while preserving the same boundary and dependency direction.

## The human and agent views

This paper explains why LDMs exist and how to decide whether a boundary is meaningful. The [agent LDM convention](../../../agents/conventions/development/ldms.md) gives the precise project, dependency and maintenance rules for a repository that adopts the binding.

## Related guidance

- [Service System Guidance](./readme.md)
- [LDM Layers and Contents](./layers.md)
- [System LDM Services](./services.md)
- [Logical Deployment Modules](../../reference/catalogues/ldms.md)
- [Logical Building Blocks](../../reference/catalogues/logical-building-blocks.md)
- [Guidance for Developers](../../orientation/guidance-for-developers.md)
- [Systems Within Systems](../../orientation/systems-within-systems.md)
- [The Structure Before the Feature](../../orientation/the-structure-before-the-feature.md)
- [Logical Deployment Modules](../../../agents/conventions/development/ldms.md)
- [Project Naming](../../../agents/conventions/development/projects.md)
