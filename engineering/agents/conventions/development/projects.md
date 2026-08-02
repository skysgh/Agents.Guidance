# Project Naming

Read this document when creating, renaming, restructuring or configuring projects and their namespaces.

For the accessible explanation of how project and deployment boundaries relate to responsibility, read [Logical Deployment Modules](../../../humans/reference/catalogues/ldms.md), [LDM Layers and Contents](../../../humans/development/layers.md), [Deliverable Systems](../../../humans/reference/catalogues/deliverable-systems.md), [Deliverables](../../../humans/reference/catalogues/deliverables.md) and [Guidance for Developers](../../../humans/orientation/guidance-for-developers.md).

Name each project so that its filename and default namespace identify its place within the system.

Use the intentionally generic `App.` prefix.

Follow the prefix with the Logical Deployment Module (LDM) key and architectural layer:

```text
App.Host
...
App.Modules.{LDM-Key}.AppInterfaces
App.Modules.{LDM-Key}.Application
App.Modules.{LDM-Key}.Domains
App.Modules.{LDM-Key}.Infrastructure
App.Modules.{LDM-Key}.Infrastructure.{Dependency}
App.Modules.{LDM-Key}.Infrastructure.Persistence.EF
App.Modules.{LDM-Key}.Shared
```

Use `AppInterfaces`, rather than the more usual `Interfaces`, for interfaces exposed to users (GUI) and applications (API).
The name intentionally places `AppInterfaces` alphabetically before `Application`.

## Project Configuration

Configure every .NET project to:

- generate XML documentation;
- enable nullable-reference-type analysis;
- disable implicit global using directives;
- enable all currently available .NET analyser rules;
- treat warnings as errors; 
- use warning level 9999
- enable all compiler warning waves available to the installed SDK.

Apply the following configuration:

``` XML
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <Nullable>enable</Nullable>
  <ImplicitUsings>disable</ImplicitUsings>
  <AnalysisLevel>latest-all</AnalysisLevel>
  <WarningLevel>9999</WarningLevel>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
</PropertyGroup>
```

## namespaces

Keep namespace roots as the project filename.


## Explicit Types

Enforce Prefer explicit local variable types over var because the visible type improves comprehension.

Enforce this through `.editorconfig`:

``` INI
csharp_style_var_for_built_in_types = false:error
csharp_style_var_when_type_is_apparent = false:error
csharp_style_var_elsewhere = false:error
```

This is a code-style rule. It discourages `var`; it does not remove the keyword from the C# language.

## Warning Resolution

Suppress a warning only when:

- its cause has been understood;
- the relevant behaviour is intentional;
- correcting it would make the implementation less accurate or maintainable;
- the suppression has the narrowest practical scope; and
- the reason is recorded beside the suppression.

Prefer a source-level suppression with a justification over a project-wide <NoWarn> entry.

Do **NOT** ever suppress warnings merely to obtain a successful build.

## Warning Policy

Consider avoiding suppressing:

- `CS1591` — A publicly visible type or member lacks XML documentation.
- `IDE0047` — Parentheses are unnecessary according to the configured style.
- `NU5104` — A stable NuGet package depends on a prerelease package. Use a stable dependency or publish the containing package as prerelease.
- `CA1816` — GC.SuppressFinalize is missing or used incorrectly. Correct the disposal implementation.
- `CA1869` — A JsonSerializerOptions instance is repeatedly created. Cache and reuse the instance unless its configuration genuinely varies.
- `NU1510` — A direct package reference is unnecessary because the target framework already provides it. Remove the redundant PackageReference.
- `CA1805` — A member is explicitly initialised to its default value. Remove the redundant initialiser.

Generally Ok to suppress:

- `CA1848` — Logging uses ordinary ILogger extension methods instead of source-generated LoggerMessage methods. Prefer source-generated logging, particularly in shared or frequently executed code.
- `CA1873` — A logging argument performs potentially unnecessary work when its log level is disabled. Pass uncomputed values, use source-generated logging, or guard the operation with IsEnabled. Suppress only when the argument is known to be inexpensive and readability would otherwise suffer.
- `CA1852` — An internal type can be sealed. Seal it unless inheritance is intentionally supported, required by a framework, or likely within the designed extension model.


## Maintenance

If you encounter projects that do not adhere to the above, implement the above recommended strictness.

