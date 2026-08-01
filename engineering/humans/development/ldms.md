# Logical Deployment Modules

A Logical Deployment Module, or LDM, is a boundary for deployment, ownership and change. It gives a coherent part of the system a place where its contracts, data, dependencies, security and operational responsibility can remain understandable across time.

An LDM is not a service. It is not a project, a layer, a database or a single domain. It is the boundary that contains and organises those things.

## Why an LDM exists

A simple application may begin as one deployed service and one LDM. That does not make all of its concerns one domain. The modular boundary should be visible from the beginning so that the service can grow without forcing unrelated responsibilities into one undifferentiated project.

The risk of having only one LDM is not the number one. The risk is using that number as permission to place unrelated domains together. Once data ownership, contracts, permissions and workflows are mixed, later separation becomes expensive. The first LDM should therefore be small enough to operate and structured enough to preserve future choices.

For most enterprise applications, a useful minimum is:

```text
application
  -> System LDM
       -> shared technical and system domains
  -> Business LDM
       -> the commissioned department's business domains
```

The System LDM is commonly developed first because business capabilities need somewhere dependable to obtain configuration, identity context, storage, diagnostics, access policy and other shared foundations. The business LDM then owns the business concepts, decisions and workflows that give the application its purpose.

An application commissioned by one department may stop at those two LDMs. A more sophisticated system serving several departments may add further LDMs where different departments or business areas need distinct ownership, contracts, data, deployment cadence or operational responsibility.

## When to add another LDM

Create or consider another LDM when a part of the system has a genuinely different combination of:

- business or technical purpose;
- data ownership or classification;
- deployment or release needs;
- security or authorisation responsibility;
- operational team or lifecycle;
- dependency and failure behaviour; or
- consumer and compatibility expectations.

Do not split merely because a folder is large, and do not merge merely because two domains currently share a database or user interface. Related domains may live in one LDM when their purpose, ownership and lifecycle remain coherent. A separate LDM becomes useful when keeping them together would hide a meaningful difference or constrain future change.

## The System LDM and business LDMs

The System LDM contains shared system capabilities and technical domains. It may include identity, users, roles, permissions, settings, configuration, diagnostics, storage, startup, mapping, auditing and other services described in [System LDM Services](./services.md).

The System LDM can provide the ability to authenticate an actor or evaluate permission. It does not own what a business approval means. A business LDM owns its concepts, states, decisions and workflow, while using System LDM contracts where appropriate.

Person and Group may begin in the System LDM when they are shared identity concepts. They may later deserve another LDM when their relationships, administration, reuse or lifecycle become substantial. The boundary follows responsibility and evidence, not the apparent familiarity of a word.

## An LDM contains layers

An LDM is not a bag of services. It contains layers that keep different responsibilities separate while allowing a capability to travel through them. Those layers contain contracts, constants, models, services, registries, repositories, interfaces and implementations as appropriate.

Read [LDM Layers and Contents](./layers.md) before deciding where a new type belongs.

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

This paper explains why LDMs exist and how to decide whether a boundary is meaningful. The [agent LDM convention](../../agents/conventions/development/ldms.md) gives the precise project, dependency and maintenance rules for a repository that adopts the binding.

## Related guidance

- [Human Development Guidance](./readme.md)
- [LDM Layers and Contents](./layers.md)
- [System LDM Services](./services.md)
- [What Developers Need to Know](../orientation/developers-need-to-know.md)
- [Systems Within Systems](../orientation/systems-within-systems.md)
- [The Structure Before the Feature](../orientation/the-structure-before-the-feature.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
- [Project Naming](../../agents/conventions/development/projects.md)
