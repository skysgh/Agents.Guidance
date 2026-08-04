# Testing Conventions

Apply these conventions whenever tests are created, changed, moved, reviewed or used to validate a change.

For the accessible explanation of testing as shared evidence, read [What the Guidance Gives Each Stakeholder](../../../humans/orientation/what-this-guidance-gives.md), [Deliverable Systems](../../../humans/reference/catalogues/deliverable-systems.md), [Deliverables](../../../humans/reference/catalogues/deliverables.md) and the [Deliverables Checklist](../../../humans/reference/checklists/deliverables.md).

## Purpose

Testing gives the team evidence that the building behaves as designed. It is not only a final search for defects. Tests help developers check contracts, help testers challenge boundaries, help business roles confirm meaning and help operations understand failure and recovery.

## The short version

Choose the smallest test that can prove the behaviour, then add broader tests where the boundary itself needs proving. A passing screen is not enough. The team should know what happens when information is invalid, access is denied, a state change is wrong, storage fails or an external dependency is unavailable.

In technical language, tests may be static or dynamic. The practical difference is whether the test can run inside the test process or needs a running host, deployed component or external service.

## Projects

Create two test projects for each Logical Deployment Module (LDM):

```text
Tests.Module.{LDM-Identifier}.Static
Tests.Module.{LDM-Identifier}.Dynamic
```

Place tests according to the dependencies required to execute them.

`Static` tests execute within the test process. They may use mocks, substitutes, fakes or in-memory implementations, but must not require a running application host or external infrastructure.

`Dynamic` tests require a running host, deployed component or infrastructure dependency. They may use `WebApplicationFactory`, HTTP endpoints, SQL Server, Azurite, containers or other running services.

Do not describe the projects as `Unit` and `Integration`. Those terms describe the scope of a test, whereas `Static` and `Dynamic` describe its execution requirements.

## Cross-system test context

When a scenario crosses service, consumer or provider boundaries, use a shared cross-system test context rather than unrelated service-local fixtures. The context is a neutral information system with stable scenario identifiers, relationships, lifecycle states, expected outcomes and provenance. Each participating system translates it into its own seeds, requests, messages, files or provider setup.

The shared context is a deliverable to which multiple projects may contribute. Keep its meaning independent from any one database schema, API, ORM model or vendor representation. Review contributions for compatibility, ownership, classification, reset, retention and deprecation, and preserve evidence of which context version produced each test result.

Production data must not leave production environments. Generate synthetic context by default. If an exceptional need requires a transformed dataset, it must be formally approved as a new non-production dataset with explicit authority, minimisation, de-identification, access control, retention, deletion and audit evidence; it must not be treated as a casual copy of production.

## Files

Do not accumulate unrelated tests in a single large file.

Organise tests by domain and then by the subject or behaviour under test.

Keep each test class focused on one coherent subject. Split a test class when it becomes difficult to identify its purpose, navigate its cases or determine which behaviour has failed.

Name test files after the subject or behaviour being tested:

```text
Identity/
  PersonIdentityTests.cs
  IdentityResolutionTests.cs

Commerce/
  CatalogueTests.cs
  CatalogueEndpointTests.cs
```

## Test Scope

Test behaviour at the narrowest level that proves it reliably:

- Test domain rules through domain tests.
- Test orchestration, mapping, permissions and state transitions through application service tests.
- Test query policies, shares, classifications, history and persistence through repository or integration tests.
- Test externally reachable behaviour, including authentication and authorisation failures, through endpoint tests.
- Test determinism where reflected models or other discovered metadata generate seed data, registrations or projections that could drift between executions.

Cover the following outcomes where applicable:

- successful execution;
- validation failure;
- unauthenticated access;
- forbidden access;
- missing records;
- invalid state transitions; and
- persistence failure and recovery.

Do not duplicate the same assertion unnecessarily at every testing level. Use broader dynamic tests only where narrower static tests cannot prove the behaviour.

Do not add meaningless tests solely to increase coverage of unreachable or behaviour-free code.

## Traits

Apply traits consistently so that tests can be selected independently by purpose, execution requirements, domain and quality concern.

Use constants for trait names and values where practical. Do not repeatedly introduce equivalent string values with different spelling or structure.

### Category

Use `Category` to identify the primary purpose of the test:

```text
Functional
Quality
```

A `Functional` test proves that a capability behaves as required.

A `Quality` test proves a measurable quality characteristic, such as security, reliability, performance or maintainability.

### Type

Use `Type` to identify the execution requirements:

```text
Static
Dynamic
```

`Static` tests execute in-process and require no running host or real infrastructure.

`Dynamic` tests exercise a running host, deployed component or infrastructure dependency.

The `Type` trait must agree with the project containing the test.

### Quality

Use `Quality` to identify the ISO/IEC 25010 quality characteristic being tested:

```text
FunctionalSuitability.Completeness
FunctionalSuitability.Correctness

Security.Confidentiality
Security.Integrity
Security.Authenticity
Security.Accountability
Security.NonRepudiation

Reliability.Maturity
Reliability.FaultTolerance
Reliability.Recoverability

Maintainability.Modularity
Maintainability.Reusability
Maintainability.Analysability
Maintainability.Modifiability
Maintainability.Testability

PerformanceEfficiency.TimeBehaviour
PerformanceEfficiency.ResourceUtilisation

Portability.Adaptability
Portability.Installability
```

Add further ISO/IEC 25010 characteristics only when tests exist for them. Do not create trait values merely to reproduce the complete standard.

### Domain

Use `Domain` to identify the business or system domain principally exercised by the test:

```text
Identity
Commerce
Resources
ReferenceData
Authorization
```

Use the recognised domain name from the implementation. Do not invent a broader or alternative name solely for testing.

### OWASP

Use `OWASP` to identify a security concern mapped to an OWASP category:

```text
A01.BrokenAccessControl
A02.SecurityMisconfiguration
```

Use the OWASP category applicable to the adopted edition of the standard. Do not mix category identifiers from different editions without recording the edition.

An OWASP-mapped test is also a `Quality` test and must carry an appropriate `Quality` trait.

### Scenario

Use scenario traits when tests are intended to prove behaviour across reusable scenarios, professions, use cases or capabilities.

Examples include:

```text
Scenario.Profession
Scenario.UseCase
Scenario.Capability
```

Use scenario traits in addition to, rather than instead of, `Category`, `Type` and `Domain`.

## Examples

### Static Functional Test

```csharp
[Trait("Category", "Functional")]
[Trait("Type", "Static")]
[Trait("Domain", "Identity")]
public sealed class PersonIdentityTests
{
}
```

### Dynamic Functional Test

```csharp
[Trait("Category", "Functional")]
[Trait("Type", "Dynamic")]
[Trait("Domain", "Commerce")]
public sealed class CatalogueEndpointTests
{
}
```

### Static Quality Test

```csharp
[Trait("Category", "Quality")]
[Trait("Type", "Static")]
[Trait("Quality", "FunctionalSuitability.Correctness")]
[Trait("Domain", "ReferenceData")]
public sealed class ReferenceDataCorrectnessTests
{
}
```

### Dynamic Reliability Test

```csharp
[Trait("Category", "Quality")]
[Trait("Type", "Dynamic")]
[Trait("Quality", "Reliability.Maturity")]
[Trait("Domain", "Hosting")]
public sealed class ModuleStartupMaturityTests
{
}
```

### Dynamic Security Test

```csharp
[Trait("Category", "Quality")]
[Trait("Type", "Dynamic")]
[Trait("Quality", "Security.Confidentiality")]
[Trait("OWASP", "A01.BrokenAccessControl")]
[Trait("Domain", "Authorization")]
public sealed class AccessControlSecurityTests
{
}
```

### Scenario Test

```csharp
[Trait("Category", "Functional")]
[Trait("Type", "Static")]
[Trait("Domain", "Capacity")]
[Trait("Scenario.Profession", "Hospitals")]
[Trait("Scenario.UseCase", "CapacityRespect")]
[Trait("Scenario.Capability", "LinearCapacity")]
public sealed class HospitalCapacityTests
{
}
```

## Filtering

Filter tests using their trait names and values:

```shell
dotnet test --filter "Category=Functional"
dotnet test --filter "Category=Quality"
dotnet test --filter "Type=Static"
dotnet test --filter "Type=Dynamic"
dotnet test --filter "Quality=Reliability.Maturity"
dotnet test --filter "Domain=Identity"
dotnet test --filter "OWASP=A01.BrokenAccessControl"
```

Combine filters when a more specific selection is required:

```shell
dotnet test --filter "Category=Quality&Type=Dynamic"
dotnet test --filter "Domain=Authorization&OWASP=A01.BrokenAccessControl"
```

## Maintenance

When encountering tests that do not follow these conventions:

1. add the applicable traits;
2. correct inconsistent trait names or values;
3. move each test into the correct `Static` or `Dynamic` project;
4. move tests into the appropriate domain folder;
5. split files or classes containing unrelated tests; and
6. update filtering scripts affected by renamed traits.

Do not change the behaviour or purpose of an existing test merely while reorganising it.
