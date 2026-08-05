[Up](./readme.md)

# Constants and Shared Vocabulary

A constant is a named piece of immutable meaning. It is useful when several parts of a system must refer to the same stable value, such as an LDM key, route segment, permission name or infrastructure category.

Constants are small, but they shape the vocabulary of the system. A second spelling of a route or permission is not merely a typo. It is a second architectural decision that can make boundaries, policies and tests disagree.

## The dependency tree

Constants should form a dependency tree rather than a collection of global bags:

```text
platform constants
  -> LDM constants
      -> domain or capability constants
          -> composed route, permission, storage and diagnostic values
```

Platform constants define genuinely shared building blocks. An LDM adds its key and vocabulary. A domain or capability adds values that belong only to its responsibility. Higher layers compose those values rather than inventing another spelling.

This keeps the LDM boundary visible. A route, policy or diagnostic category can be followed back to the vocabulary that owns it.

## Constants as building vocabulary

In the building metaphor, constants are labelled dimensions, identifiers and shared signs. They let different builders refer to the same doorway, service route or safety category without writing a new description each time.

They are not the building's policy by themselves. A permission constant names a permission; the owning boundary still decides when that permission is granted. A route constant names a route segment; the interface still maps that route to an application contract. A storage constant names a stable location category; configuration and deployment still decide the actual environment-specific location.

## What belongs in constants

Use constants for values that are:

- immutable for the life of the compiled design;
- shared by more than one consumer;
- meaningful enough to deserve a name; and
- owned by a clear platform, LDM, domain or capability boundary.

Typical examples include LDM keys, route segments, permission verbs, stable diagnostic categories, separator rules and well-known infrastructure paths.

Do not create a constant merely because a value appears once. The name should clarify meaning or protect a relationship that consumers genuinely share.

## What does not belong in constants

Do not use constants as substitutes for values that have their own lifecycle. Use the appropriate typed contract or data model for:

- deployment or runtime configuration;
- secrets and credentials;
- user- or administrator-managed settings;
- persisted reference data;
- environment-specific locations;
- values that must be changed without recompilation; or
- values whose authority, retention or audit needs their own model.

A constant is not safer merely because it is compiled. Hard-coding a value can make a change less visible, less configurable or harder to govern.

## A worked direction

```csharp
public static class PlatformApiConstants
{
    public const string RestRoot = "api/rest";
    public const string VersionPrefix = "v";
}

public static class RequestsConstants
{
    public const string LdmKey = "requests";
    public const string Resource = "requests";
}

public static class RequestPermissionConstants
{
    public const string Read = "Requests.Request.Read";
    public const string Submit = "Requests.Request.Submit";
}
```

The exact code arrangement depends on the language and repository. The dependency direction does not:

- platform constants do not depend on an LDM;
- an LDM's constants may depend on platform constants;
- a capability may depend on its LDM vocabulary;
- application, interface, policy and test code consume the vocabulary; and
- no higher layer creates a second spelling for existing meaning.

## The human and agent views

This paper explains why constants protect shared vocabulary and where their limits are. The [agent code convention](../../agents/conventions/development/code-csharp.md) gives the precise rules for magic values, dependency direction and language-specific implementation.

## Related guidance

- [Human Development Guidance](./readme.md)
- [LDM Layers and Contents](./layers.md)
- [Contracts](./contracts.md)
- [Cohesive Constants by Platform and LDM](../examples/09-magic-strings/after.md)
- [Code Conventions](../../agents/conventions/development/code-csharp.md)
- [Logical Deployment Modules](../../agents/conventions/development/ldms.md)
