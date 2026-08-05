[Up](../readme.md)

# LDM Directory Structure


A directory tree can make an LDM easier to navigate, but it must not be mistaken for the LDM itself. The LDM is a logical package of responsibilities, contracts, dependencies, data and lifecycle. Projects and folders are physical representations of that package.

This example shows one possible service with a System LDM and a business LDM. It is deliberately detailed so a developer can see the relationship between projects, layers, Domains, purpose categories, contracts and implementations in one place.

The example uses the `App.Modules.{LDM-Key}.{Layer}` project convention and the `Tests.Module.{LDM-Identifier}.{Static-or-Dynamic}` test convention. These names are a repository binding, not a universal architecture. A real project may use different names while preserving clear responsibility and dependency direction.

## Read the tree

The tree is read from the outside of the package toward its internal responsibilities:

1. The project identifies the LDM and architectural layer.
2. The `Domains` directory separates coherent business or technical meanings within a project.
3. Purpose directories identify what a type does.
4. Contracts appear before their implementations when both are present.
5. Tests are organised by Domain and behaviour, while their project name identifies the execution requirement.

A directory does not grant authority. A class placed in `Domain` does not become a domain rule unless its responsibility, contract and meaning support that placement.

## Example repository tree

```text
src/
  App.Host/                                             # Composition root and process host.
    Program.cs                                          # Starts the selected service host.
    Composition/
      ServiceRegistration.cs                            # Composes application-owned contracts and implementations.
      EndpointRegistration.cs                           # Registers transport endpoints at the boundary.

  App.Modules.Sys.Shared/                               # System LDM vocabulary and narrow shared contracts.
    Constants/
      SystemLdmConstants.cs                             # Stable system-LDM key and shared technical names.
    Contracts/
      IClock.cs                                         # Application-owned time boundary.
      ICorrelationContext.cs                            # Correlation identity available to the current operation.
    Models/
      CorrelationId.cs                                  # Small logical value used across system boundaries.

  App.Modules.Sys.Domain/                               # System LDM domain meaning and ports.
    Domains/
      Identity/
        Constants/
          IdentityClaimConstants.cs                     # Names owned by the Identity Domain.
        Models/
          Entities/
            Actor.cs                                    # Enduring identity concept and lifecycle.
          ValueObjects/
            ActorId.cs                                  # Identity value with domain meaning.
        Repositories/
          IActorRepository.cs                           # Domain-facing persistence contract.
        Services/
          IActorAccessService.cs                        # Domain-facing access decision contract.
      Authorisation/
        Constants/
          PermissionConstants.cs                       # Stable permission meanings for this Domain.
        Models/
          Entities/
            Permission.cs                               # Permission definition and lifecycle.
          ValueObjects/
            PermissionKey.cs                            # Stable permission identity.
        Repositories/
          IPermissionRepository.cs                      # Domain-facing permission lookup contract.
        Services/
          IAuthorisationPolicy.cs                       # Contract for evaluating an authorisation rule.
      Audit/
        Models/
          Entities/
            AuditRecord.cs                               # Evidence of a significant system action.
        Repositories/
          IAuditRecordRepository.cs                     # Contract for storing audit evidence.

  App.Modules.Sys.Application/                           # System LDM use-case coordination and application contracts.
    Domains/
      Identity/
        Commands/
          RegisterActorCommand.cs                        # Application input for an identity use case.
        Handlers/
          RegisterActorHandler.cs                        # Coordinates the use case through domain contracts.
        Queries/
          GetActorQuery.cs                               # Application query contract.
        Results/
          ActorResult.cs                                 # Application result, not a persistence entity.
        Validators/
          RegisterActorValidator.cs                      # Validates application input and boundary conditions.
      Authorisation/
        Services/
          AuthorisationService.cs                       # Composes permission and policy contracts.
        Queries/
          EvaluateAccessQuery.cs                        # Application request for an access decision.
        Results/
          AccessDecisionResult.cs                        # Result shaped for the consuming application boundary.
      Audit/
        Commands/
          RecordAuditEventCommand.cs                    # Application request to record evidence.
        Handlers/
          RecordAuditEventHandler.cs                    # Coordinates audit recording.

  App.Modules.Sys.Infrastructure/                        # System LDM adapters for providers and technical mechanisms.
    Domains/
      Identity/
        Brokers/
          IdentityProviderBroker.cs                     # Encapsulates an external identity provider.
        Services/
          ClockService.cs                               # Technical implementation of the clock contract.
      Authorisation/
        Brokers/
          PolicyProviderBroker.cs                       # Encapsulates a provider policy mechanism.
      Audit/
        Services/
          AuditWriter.cs                                # Technical writer for the selected audit sink.
    Configuration/
      IdentityOptions.cs                                # Typed non-secret provider configuration.
    Startup/
      InfrastructureRegistration.cs                    # Registers adapters and provider integrations.

  App.Modules.Sys.Infrastructure.Persistence.EF/         # System LDM physical persistence and mappings.
    Domains/
      Identity/
        Models/
          Entities/
            ActorRecord.cs                              # Persistence representation, not the domain entity.
        Maps/
          ActorRecordMap.cs                             # Database mapping and storage constraints.
        Repositories/
          ActorRepository.cs                            # Implements IActorRepository.
      Authorisation/
        Models/
          Entities/
            PermissionRecord.cs                         # Persistence representation of permission data.
        Maps/
          PermissionRecordMap.cs                        # Database mapping and indexes.
        Repositories/
          PermissionRepository.cs                       # Implements IPermissionRepository.
      Audit/
        Models/
          Entities/
            AuditRecordRecord.cs                        # Physical audit storage representation.
        Maps/
          AuditRecordMap.cs                             # Retention and storage mapping decisions.
        Repositories/
          AuditRecordRepository.cs                      # Implements IAuditRecordRepository.
    Migrations/
      InitialSystemSchema.cs                            # Versioned physical schema change.
    DbContexts/
      SystemDbContext.cs                                # Persistence provider boundary.

  App.Modules.Sys.AppInterfaces/                         # System LDM transport and presentation boundaries.
    Domains/
      Identity/
        Controllers/
          ActorsController.cs                            # Thin HTTP adapter for application contracts.
        Models/
          Requests/
            RegisterActorRequest.cs                      # Transport input model.
          Responses/
            ActorResponse.cs                             # Transport output model.
      Authorisation/
        Controllers/
          AuthorisationController.cs                     # Adapts access requests to application contracts.
      Audit/
        Controllers/
          AuditController.cs                             # Exposes only the intended audit boundary.
    Maps/
      ApiModelMap.cs                                    # Maps transport models to application models.

  App.Modules.Enrolment.Shared/                         # Business LDM vocabulary and narrow contracts.
    Constants/
      EnrolmentConstants.cs                             # Business LDM key and stable business names.
    Contracts/
      IEnrolmentReader.cs                               # Contract shared by the intended consumers.
    Models/
      EnrolmentId.cs                                    # Business identifier with explicit meaning.

  App.Modules.Enrolment.Domain/                         # Business meaning, rules and domain-facing ports.
    Domains/
      Enrolment/
        Constants/
          EnrolmentStatusConstants.cs                   # Stable status meanings for the Enrolment Domain.
        Models/
          Entities/
            Enrolment.cs                                # Aggregate or entity with enrolment lifecycle.
          ValueObjects/
            EnrolmentPeriod.cs                          # Effective dates and temporal meaning.
        Repositories/
          IEnrolmentRepository.cs                       # Domain-facing persistence contract.
        Services/
          IEnrolmentEligibilityService.cs               # Domain-facing eligibility rule contract.
        Validators/
          EnrolmentRules.cs                             # Rules that protect valid domain state.
      Student/
        Models/
          Entities/
            Student.cs                                  # Identity and lifecycle owned by this Domain if applicable.
          Repositories/
            IStudentRepository.cs                       # Contract for student lookup.

  App.Modules.Enrolment.Application/                    # Business use-case coordination.
    Domains/
      Enrolment/
        Commands/
          SubmitEnrolmentCommand.cs                     # Application command for submission.
        Handlers/
          SubmitEnrolmentHandler.cs                     # Orchestrates validation, rules and persistence ports.
        Queries/
          GetEnrolmentQuery.cs                          # Application query contract.
        Results/
          EnrolmentResult.cs                            # Result model for a use case.
        Validators/
          SubmitEnrolmentValidator.cs                   # Boundary and application validation.
      Student/
        Queries/
          GetStudentQuery.cs                            # Query composed from the Student contract.
        Results/
          StudentResult.cs                              # Consumer-facing application result.

  App.Modules.Enrolment.Infrastructure/                 # Business LDM technical adapters.
    Domains/
      Enrolment/
        Brokers/
          FundingProviderBroker.cs                      # External funding or partner boundary.
        Services/
          EnrolmentNumberService.cs                     # Technical support for number generation.
    Startup/
      EnrolmentRegistration.cs                          # Registers business adapters.

  App.Modules.Enrolment.Infrastructure.Persistence.EF/  # Business LDM persistence.
    Domains/
      Enrolment/
        Models/
          Entities/
            EnrolmentRecord.cs                           # Physical persistence representation.
        Maps/
          EnrolmentRecordMap.cs                         # Mapping, indexes and concurrency configuration.
        Repositories/
          EnrolmentRepository.cs                        # Implements IEnrolmentRepository.
      Student/
        Models/
          Entities/
            StudentRecord.cs                             # Physical student representation where owned here.
        Maps/
          StudentRecordMap.cs                           # Storage mapping for the Student Domain.
        Repositories/
          StudentRepository.cs                          # Implements IStudentRepository.
    Migrations/
      InitialEnrolmentSchema.cs                         # Versioned schema change for this LDM.

  App.Modules.Enrolment.AppInterfaces/                  # Business API or user-facing boundary.
    Domains/
      Enrolment/
        Controllers/
          EnrolmentsController.cs                       # Thin adapter for enrolment application contracts.
        Models/
          Requests/
            SubmitEnrolmentRequest.cs                   # Transport representation of submitted data.
          Responses/
            EnrolmentResponse.cs                        # Transport representation of result data.
      Student/
        Controllers/
          StudentsController.cs                         # Boundary for the intended student capability.
    Maps/
      EnrolmentApiMap.cs                                # Explicit transport-to-application mapping.

Tests/
  Tests.Module.Sys.Static/                             # Tests executable inside the test process.
    Identity/
      ActorTests.cs                                    # Domain behaviour tests.
      ActorAccessServiceTests.cs                       # Application or contract tests without a host.
    Authorisation/
      PermissionTests.cs                               # Permission and rule tests.
    Audit/
      AuditRecordTests.cs                              # Audit meaning and validation tests.

  Tests.Module.Sys.Dynamic/                            # Tests requiring a host, provider or infrastructure.
    Identity/
      ActorEndpointTests.cs                            # HTTP boundary and authentication tests.
      ActorPersistenceTests.cs                         # Persistence and query-policy tests.
    Audit/
      AuditRecoveryTests.cs                            # Runtime failure and recovery evidence.

  Tests.Module.Enrolment.Static/                       # Business LDM tests without running infrastructure.
    Enrolment/
      SubmitEnrolmentTests.cs                           # Application and domain behaviour.
      EnrolmentEligibilityTests.cs                      # Rule and boundary tests.
    Student/
      StudentTests.cs                                  # Student behaviour where owned by this LDM.

  Tests.Module.Enrolment.Dynamic/                      # Business LDM tests requiring a host or provider.
    Enrolment/
      EnrolmentEndpointTests.cs                        # Externally reachable behaviour.
      EnrolmentPersistenceTests.cs                     # Persistence, mapping and recovery behaviour.
```

## Why the tree is shaped this way

### Project first

The project name identifies the LDM and the layer. This lets a reader distinguish application coordination from domain meaning, persistence, infrastructure adapters and transport without relying only on a folder name.

### Domain before purpose

The `Domains` directory keeps related meaning together. `Enrolment/Repositories` and `Student/Repositories` are easier to reason about than one repository folder containing every contract in the LDM. The folder does not decide ownership by itself; it makes the intended ownership visible enough to challenge.

### Purpose before type detail

`Repositories`, `Brokers`, `Handlers`, `Maps`, `Validators` and `Models` describe why a type exists. This is more useful than a single folder containing classes that happen to share a technical base class.

These model categories are examples, not requirements for every directory:

- `Entities`: things with identity and lifecycle;
- `ValueObjects`: complete values without independent identity;
- `ReferenceData`: governed values with authority and lifecycle;
- `Commands` and `Queries`: application requests;
- `Results`, `Responses` and `Requests`: representations at a defined boundary;
- `Events` and `Messages`: communication contracts with explicit delivery meaning; and
- `Projections` and `Snapshots`: derived or historical representations with defined rebuild and retention rules.

### Contracts before implementations

A Domain project may own `IEnrolmentRepository`, while the persistence project implements it. The interface is not automatically a public API; it is a contract at the boundary that owns the responsibility. The implementation belongs with the provider or physical mechanism.

The same distinction applies to brokers, application services and transport adapters. Controllers should adapt requests and responses, not become the place where domain rules, persistence queries or substantial orchestration accumulate.

### Test project and test folder

`Static` and `Dynamic` describe how the test executes, not the business meaning of the test. Within each project, tests are still organised by Domain and behaviour. A dynamic test may test an endpoint, persistence, an external integration or recovery because its claim requires a running boundary.

## What this example does not prescribe

This tree does not require:

- one project for every folder;
- one Domain per LDM;
- independent deployment of every project;
- Entity Framework or another particular persistence provider;
- controllers for every capability;
- generic CRUD folders;
- a fixed number of LDMs; or
- copying the example names into a real service without checking responsibility.

The durable questions are: which responsibility owns this type, which Domain gives it meaning, which layer implements it, which contract protects the relationship, and what evidence proves it behaves correctly?

## Related guidance

- [LDM Layers and Contents](../../deliverables/systems/service/layers.md)
- [Logical Deployment Modules](../../deliverables/systems/service/ldms.md)
- [Logical Deployment Modules Catalogue](../../shared/reference/catalogues/ldms.md)
- [Logical Building Blocks](../../shared/reference/catalogues/logical-building-blocks.md)
- [Guidance for Developers](../../foundations/guidance-for-developers.md)
- [Develop LDMs agent convention](../../../agents/conventions/development/ldms.md)
- [C# code organization agent convention](../../../agents/conventions/development/code-csharp.md)
- [Testing Conventions](../../../agents/conventions/development/testing.md)
