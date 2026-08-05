[Up](../readme.md)

# After: Cohesive Constants by Platform and LDM

The team replaces shared literals with named constants that describe their meaning. Constants are organised as a dependency tree rather than as unrelated bags of strings.

A typical direction is:

```text
platform constants
  -> LDM constants
      -> domain or capability constants
          -> composed route, permission, storage and diagnostic values
```

The platform layer defines stable building blocks such as route prefixes, API version segments, shared permission verbs, separator rules or well-known infrastructure paths. Each LDM's Shared project defines its LDM key and LDM-specific vocabulary. A domain or capability adds only the values that belong to that boundary. Higher layers compose those values; they do not redefine the lower-level meaning.

For example:

```csharp
public static class PlatformApiConstants
{
    public const string RestRoot = "api/rest";
    public const string VersionPrefix = "v";
}

public static class SocialConstants
{
    public const string LdmKey = "social";
    public const string PersonaResource = "personas";
}

public static class SocialPersonaPermissionConstants
{
    public const string Read = "Social.Persona.Read";
    public const string Update = "Social.Persona.Update";
}
```

A route or policy then composes the vocabulary instead of repeating its literal parts. The exact C# arrangement depends on the platform, but the dependency direction matters:

- shared platform constants do not depend on an LDM;
- an LDM's constants may depend on platform constants;
- a capability may depend on its LDM vocabulary;
- application, controller, policy and test code consume the constants; and
- no higher layer creates a second spelling for an existing value.

This provides more than find-and-replace convenience:

- one named source makes changes reviewable;
- the compiler catches many spelling and renaming errors;
- route and permission composition becomes visible;
- tests can assert the same vocabulary that startup and transport use;
- LDM boundaries become clearer;
- an LDM can be moved or shared without scattering unrelated literals; and
- tooling can navigate from a composed value to its platform and LDM building blocks.

Constants are not a universal answer. Values that are runtime configuration, user-manageable settings, persisted reference data, secrets or environment-specific locations belong in the appropriate typed contract or data model. Constants are for genuinely shared immutable meaning.

The result is a cohesive tree of values. The code does not merely avoid magic strings in individual files; it makes the vocabulary and its dependency direction part of the architecture.
