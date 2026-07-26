
# Code Conventions

Apply these conventions when creating, reviewing, restructuring or refactoring code in a domain-driven modular monolith.

## Purpose

Organise code consistently so that its structure, responsibilities and patterns are recognisable and predictable.

A developer should be able to infer:

- where code belongs;
- where related code will be found;
- what responsibility a type has; and
- how an unfamiliar part of the system is likely to work.

Consistency reduces the time and risk involved in understanding, navigating, reviewing and maintaining the system.

## Methodologies and Conventions

Code adheres to:

- object-oriented programming;
- domain-driven design;
- SOLID principles, principally the Single Responsibility Principle and Liskov Substitution Principle;
- inversion of control;
- dependency injection;
- separation of contracts from implementations;
- composition over inheritance;
- no magic strings or numbers - use constants for semantically shared values.
- DRY.
- governed `IQueryable` query surfaces where the application contract is queryable.

Services are stateless. Objects are stateful.

## Anti-Patterns and Design Judgment

Do not use YAGNI as a reason to ignore foreseeable requirements, planned extensions or known directions of change. Its misuse is commonly based on ignorance of the plan rather than an informed architectural decision.

Prefer the simplest design that accommodates both the current requirement and known directions of change.

## Code Organisation

Organise code in the following order:

1. architectural layer;
2. domain;
3. code purpose;
4. contract; and
5. implementation.

The project or assembly identifies the architectural layer.

Within the layer, organise code by domain. Within each domain, organise code by its primary purpose. Within each code category, present contracts before implementations.

## Project Naming 

Use the intentionally generic prefix `App.` for project filenames and their base namespaces.

The remainder of the project name identifies the Logical Deployment Module (LDM) and architectural layer:

```
App.Modules.{LDM Identifier}.{Layer} 
```

Note: Apply the detailed project naming and configuration rules defined by `conventions-projects`.

## Namespaces

Match namespaces to the folder structure in all cases except for extension methods.

Place extension methods in the root namespace `App`, regardless of their folder location, to maximise their discoverability throughout the application.

```text
App.Modules.{LDM identifier}.{Layer}
therefore implies that the project's namespace root for all Files
bar extension methods, is:
App.Modules.Foo.Infrastructure
```

## Domains

A Logical Deployment Module (LDM) Layer project may contain (often does!) several domains.

So in the project develop a `Domains` folder.

Under that develop domain specific folders.


```text
Domains/
  Authorisation/  <- domain #1
  Authentication/ <- domain #2
  Auditing/       <- domain #3
  Caching/        <- etc.
```



## Code Purpose Categories

Within a specific Domain namespace, classify each class according to its purpose category:

- `Constants` do everything you can to not develop magic strings/values. 
- `Extensions` add cohesive behaviour to an existing type.
- `Services` provide stateless behaviour or orchestration.
- `Registries` statefully manage and provide access to registered objects.
- `Repositories` abstract persistence and retrieval in domain terms.
- `Brokers` encapsulate communication with external systems or infrastructure mechanisms.
- `Controllers` receive boundary requests and return responses.
- `Factories` construct and initialise valid objects.
- `Maps` declaratively configure mappings between representations.
- `Mappers` perform procedural or contextual translation between representations.
- `Validators` evaluate data against defined rules.
- `Handlers` process one defined command, query, event, message or request.
- `Constants` contain named, immutable values that are genuinely shared.
and
- `Models` represent data, state, contracts or domain concepts.

Give each type one primary responsibility.

Do not give a type several architectural responsibilities merely because those responsibilities are related.

The differences between these purpose categories can be summarised as follows:

### Enumerations and Reference Data

Do not use C# enumerations as the source of truth for database values.

Enumerations belong to compiled code and do not provide the identity, lifecycle, administration or referential integrity required of persisted data.

Use stable reference-data identifiers for values that are persisted, administered, shared between systems or expected to change independently of a deployment.

### Constants

Never use magic strings or unexplained magic values.

Replace repeated values or values with shared semantic meaning with clearly named constants, configuration or reference data, as appropriate.

Do not create a constant for a value used once where its meaning is already explicit from its immediate context.


### Extensions

- Keep extension methods cohesive with the type or concept they extend.
- Do not use extension methods to conceal unrelated services, persistence, external communication or substantial application orchestration.
- As discussed elsewhere, regardless of their folder location, extension methods use the root namespace `App`.

### Services 
- Services provide cohesive stateless behaviour or application orchestration that does not naturally belong to a stateful domain object.
- Services do not retain mutable business or request state between operations. - They may retain injected dependencies and immutable configuration.

### Registries 
- Registries own the registration, indexing, lookup and, where applicable, lifecycle of their registered objects.
- Do not use Registry as another name for a repository or general-purpose collection.

### Repositories
- hide database, ORM and persistence details from their consumers.
- Express repository operations in domain terms.
- Expose repository query surfaces as `IQueryable` where the application-service contract is queryable. The repository remains responsible for the source query, security policy, permitted data, provider boundary and execution constraints; consumers must not bypass it through `DbContext` or an unrelated provider query.

### Brokers
- isolate communication with external systems, transports or infrastructure mechanisms. 
- Brokers do not contain domain rules or application orchestration.

### Controllers
-  They receive and validate boundary input, invoke the appropriate application operation and produce the boundary response.
- Keep controllers thin! 
- Controllers do not contain domain rules, persistence logic or substantial application orchestration.

### Factories
- construct objects whose creation requires rules, dependencies or several coordinated steps. 
- Factories ensure that created objects begin in a valid state. - Do not create a factory where a straightforward constructor or static creation method is sufficient.

### Maps
- they declaratively configure translation between representations, such as Mapster or AutoMapper configuration. Maps contain mapping declarations only. Maps do not perform persistence, external communication or application orchestration.


### Mappers
 perform procedural mapping that cannot be expressed clearly as declarative map configuration. Use a mapper where translation requires context, conditional construction or coordinated conversion. Mappers do not perform persistence, external communication or application orchestration.

### Validators
 evaluate input or state against defined rules and return validation outcomes. Validators do not replace the enforcement of domain invariants by aggregates, entities or value objects.

### Handlers 
Give each handler one defined command, query, event, message or request responsibility.

Place shared behaviour in the appropriate service or domain model rather than duplicating it across handlers.


### Models

Models are another type of code purpose category - however maybe deserve their own section as they are subdivided themselves. 

Models represent data, state, contracts or domain concepts.

Models implement the applicable structural contracts so that schemas, mappers, validators, persistence mechanisms, serialisers and other generic infrastructure can process them consistently. These interfaces make capability and intent explicit, allow generic infrastructure to use reliable constraints, and reduce repeated per-type configuration. They do not exist merely to create an interface beside every class.

These contracts are usually defined in the appropriate Substrate assembly. This allows modules to implement shared conventions without the Substrate depending upon module implementations.

Further classify models according to their semantic role:


- `Aggregates` define transactional consistency boundaries around aggregate roots.
- `Entities` represent stateful domain concepts with identity and lifecycle.
- `ValueObjects` represent identity-free concepts defined by their values.
- `ReferenceData` represents controlled and relatively stable classifications or permitted values.
- `DTOs` transfer data where no more specific transfer role applies.
- `ViewModels` provide shapes designed specifically for presentation.
- `Requests` define inputs accepted at a boundary.
- `Responses` define outputs returned across a boundary.
- `Commands` instruct the application to change state.
- `Queries` request information without changing state.
- `Results` represent the outcomes of operations.
- `Events` represent facts that have occurred.
- `Messages` define integration or transport contracts that are not necessarily domain events.
- `Options` provide strongly typed configuration.
- `Projections` provide read-optimised representations assembled from other state.
- `Records` represent physical persistence structures where these intentionally differ from logical entities.
- `Snapshots` represent state captured at a particular point in time.

Consider using DTOs sparingly if a more specific category applies. Requests, responses, commands, queries, messages and view models may technically be data-transfer objects, but their specific responsibilities are more informative.

While most Models do not define a local contract first, they *use* system-wide model contracts (IHasId, IHasEnabled, IHasTitleAndDescription, IHasImage, etc.) which
in turn allows data schema development and object mapping by convention, rather than be custom specific instances as that increases work while decreasing certainty of no error.

Where a model implements a contract from the Substrate assembly, the local category may contain only the Implementations folder.

Note: whether to keep an Implementations folder or not to align with all other circumstances is a metter of preference - but it reminds one that the models should all be implementing interfaces. Profusely. 

```
Models/
  Entities/
    Implementations/
      PersonEntity.cs
  DTOs/
    Implementations/
      PersonDto.cs
```

The absence of a locally defined interface does not remove the distinction between the contract and its implementation.

Every contract must define a behavioural or structural convention used by consumers, schemas, mappers, infrastructure or generic constraints.

### DTOs

Use a Universal Data Item based DTO to return Browse items. 
Use separate Read, Create, and Update DTOs when their responsibilities differ.
Define DTOs in the Application Layer - **NOT** Controllers (that's an anti pattern).

## Contracts and Implementations

Define the contract before its implementation.

Contracts may define:

behavioural capabilities for services, repositories, brokers and similar components; or
structural conventions for entities, DTOs and other models processed by schemas, mappers or generic infrastructure.

Contracts are commonly defined in an appropriate Substrate assembly so that they can be consumed without depending upon a module’s implementation assembly.

Within a code category, place locally defined contracts directly in the category folder. Place concrete implementations within a nested Implementations folder:

Services/
  IFooService.cs
  Implementations/
    FooService.cs

This structure makes the contract more prominent than its implementations and encourages consumers to depend upon the abstraction.

Consumers depend upon contracts rather than concrete implementations.

Only dependency-injection composition, construction, persistence, serialisation, framework integration and relevant tests should ordinarily reference concrete implementations directly.

Do not create meaningless interfaces merely to mirror concrete types. Every contract must support substitution, structural conventions, schemas, mapping, infrastructure processing or generic constraints.

## Files

Use one primary interface, class, structure, record or enumeration per file.

Name the file after its primary type.

Keep a private nested type in the same file only when it exists solely to support the primary type.


## Typical Structure

A project may have the following structure:

```text
Domains/
  Authorisation/
    Constants/
    Extensions/
    Models/
      Aggregates/
        Implementations/
      Entities/
        Implementations/
          AuthorisationEntity.cs
      ValueObjects/
        Implementations/
      ReferenceData/
        Implementations/
      DTOs/
        Implementations/
          AuthorisationDto.cs
      ViewModels/
        Implementations/
      Requests/
        Implementations/
      Responses/
        Implementations/
      Commands/
        Implementations/
      Queries/
        Implementations/
      Results/
        Implementations/
      Events/
        Implementations/
      Messages/
        Implementations/
      Options/
        Implementations/
      Projections/
        Implementations/
      Records/
        Implementations/
      Snapshots/
        Implementations/

    Maps/

    Mappers/
      IAuthorisationMapper.cs
      Implementations/
        AuthorisationMapper.cs

    Services/
      IAuthorisationService.cs
      Implementations/
        AuthorisationService.cs

    Registries/
      IAuthorisationRegistry.cs
      Implementations/
        AuthorisationRegistry.cs

    Repositories/
      IAuthorisationRepository.cs
      Implementations/
        AuthorisationRepository.cs

    Brokers/
      IAuthorisationBroker.cs
      Implementations/
        AuthorisationBroker.cs

    Controllers/
      Implementations/
        AuthorisationController.cs

    Factories/
      IAuthorisationFactory.cs
      Implementations/
        AuthorisationFactory.cs

    Validators/
      IAuthorisationValidator.cs
      Implementations/
        AuthorisationValidator.cs

    Handlers/
      Implementations/
        AuthorisationCommandHandler.cs

  Authentication/
    ...

  Caching/
    ...
```

The structure is illustrative rather than exhaustive or prescriptive.

Create only the domain and code-category folders required by the code present. Within an existing category, retain the contract-first and implementation-second structure consistently.


# Maintenance

When code does not follow these conventions:

determine its actual domain and primary responsibility;
identify the appropriate category, folder and namespace;
move the file;
correct its namespace;
correct affected references and using directives; and
verify that the solution builds and its tests pass.


When a code file is not within an appropriate category folder, identify and apply the category that best describes its primary responsibility.

When no suitable category exists, propose a clear category name based upon the type’s primary responsibility and then apply it consistently.

Correct non-conforming namespaces when encountered.

Do not preserve misplaced code merely to avoid updating its references.
Services are stateless. Objects are stateful.

Do not use YAGNI as a reason to ignore foreseeable requirements, planned
extensions or known directions of change. Its application is often based on
ignorance of the plan rather than an informed architectural decision.

Prefer the simplest design that accommodates both the current requirement and
known directions of change.



