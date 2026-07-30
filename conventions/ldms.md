# Develop LDMs

Read this document only when creating, restructuring or managing a Logical Deployment Module or its project boundaries.

Systems are developed as a stack of discrete Logical Deployment Modules (LDMs), per stakeholder.

### Sys

The bottommost LDM is referred to as the System LDM. It's purpose is to wrap dependencies on external libraries with app-specific services to protect the rest of the code from code rot/dll hell.


## LDM components

Each LDM is composed of 5 or more projects:

```
App.Modules.{key}.AppInterface.REST				# REST, OData endpoints
App.Modules.{key}.Application					# Coordinator of Infra & Domain
App.Modules.{key}.Infrastructure				# App specific service wrappers of external dependencies
App.Modules.{key}.Infrastructure.Persistence.EF	# Domain specific
App.Modules.{key}.Shared						# Shared constants and contracts
App.Modules.{key}.Domain						# non-tech entitities and repository contracts
```


## Project Traits

Shared:
- defines LDM-specific constants, including the unique key of the LDM, used to compose controller routes, permission names, storage locations and diagnostic categories;
- consumes lower-level platform constants but does not redefine them;
- provides the LDM vocabulary to Domain, Infrastructure, Application and AppInterface projects;
- define LDM specific contracts
Domain:
- references Shared for access to LDM specific constants and contracts.
- defines the LOGICAL & PHYSICAL Entities (not CONCEPTUAL Entities)
- defines a repository Contract that is instantiated within `App.Modules.{key}.Infrasrtucture.Persistence.EF`
Infrastructure:
- references Shared for access to LDM specific constants and contracts.
- define app specific services that wrap external framework or 3rd party dependencies
  - ConfigurationService
  - DiagnosticsService
  - KeyVaultStorageService
  - MediaStorageService
Infrastructure.Persistence.EF:
- references Shared for access to LDM specific constants and contracts.
- implementation of the Repository defined in the Domain project.
Application:
- references Shared for access to LDM specific constants and contracts.
- The coordinator of Infrastructure and Domain, so that Business and Infratructure Domains are kept apart. 
- develops the Conceptual Models that the Logical models are mapped to for use by Controllers
AppInterface:
- references Shared for access to LDM specific constants and contracts.

## Constant dependency direction

Constants should form a dependency tree, not a collection of unrelated string bags:

```text
platform constants
  -> LDM constants
      -> domain or capability constants
          -> composed route, permission, storage and diagnostic values
```

Platform constants define genuinely shared building blocks. Each LDM's Shared project defines its own key and vocabulary. A domain or capability adds only values within its boundary. Controllers, policies, storage configuration and tests consume the composed constants rather than repeating literals.

This direction makes the LDM boundary visible and prevents higher layers from creating a second spelling for an existing value. Constants remain for immutable shared meaning. Runtime configuration, settings, secrets, persisted reference data and environment-specific locations belong in their appropriate typed contracts or data models.


## Code Organisation Conventions

- Infrastructure code is determined as one of the following:
- Services - Stateless singletons 
- Registries - Stateful singletons
- Repositories


## Maintenance

- If you come across projects that are still called App.Modules.{Key}.Interfaces[.*REST] rename to be `App.Modules.{Key}.AppInterfaces[.REST]`
- If you come across projects whose project names are correct, but the project folder name is not the same, update the folder name.





