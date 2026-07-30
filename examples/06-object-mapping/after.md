# After: Object Mapping by Contracts and Reusable Parts

The team keeps an application-owned object-mapping service around the selected mapping library. The wrapper is not there to hide every mapping detail. It provides a stable place for mapping policy, projection support, diagnostics and library replacement.

The mapping design uses structural contracts for recurring capabilities. Reusable map parts can describe:

- identity;
- title and description;
- image or media references;
- reference-data labels and keys;
- audit display fields; and
- state metadata.

A map for a concrete object composes the parts required by the contracts it implements:

```csharp
CreateMapPartsFor<IHasTitleAndDescription>();
CreateMapPartsFor<IHasTitleAndDescriptionAndImage>();
CreateMapPartsFor<IHasReferenceData>();
```

The exact API will vary. The important rule is that a contract map is explicit about what crosses the boundary. Once tested, the same map part can be reused for every participating object without copying member-by-member configuration.

The application service still chooses the destination DTO and use-case projection. Security and classification rules still decide what may cross the boundary. The mapping service must support provider-translatable projection where queryability is required; it must not force every query to materialise full entities first.

This gives the team both reuse and control:

- recurring contract members are configured once and tested once;
- concrete maps remain visible where the boundary differs;
- unexpected fields do not appear merely because names happen to match;
- projections can remain composable and provider-translatable;
- the mapping library remains an implementation dependency rather than the application architecture; and
- developers can diagnose a wrong result through an explicit contract part instead of searching through framework magic.

The goal is not to choose between manual mapping and magical mapping. It is to make mapping a governed contract-based capability that is reusable, inspectable and compatible with safe `IQueryable` reads.
