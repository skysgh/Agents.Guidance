[Up](../readme.md)

# After: Enums as Developer Shorthand for Reference Data

The team separates the compiled shorthand from the persisted reference-data record.

The database stores a reference-data entity with a stable identifier, key, display information, lifecycle, classification and any required administration or translation metadata. The entity has a contract such as `IReferenceData` or the platform's equivalent. APIs and integrations use the stable reference-data contract rather than exposing language-specific enum member names or numeric values.

The developer may still use an enum as a convenient declaration of the platform's built-in defaults:

```csharp
public enum BuiltInProviderStatus
{
    Draft,
    Active,
    Retired
}
```

A deterministic identifier function maps each built-in member to a stable reference-data identifier. Startup or idempotent seeding then ensures that the corresponding reference-data records exist with their keys, labels, descriptions, translations and lifecycle metadata. The enum is a seed declaration and developer shorthand. It is not the database source of truth.

This permits a useful division:

- platform-defined defaults can be seeded deterministically;
- reference-data records have real identity and referential integrity;
- descriptions and translations can be managed as data;
- effective dates, retirement and classification can be represented explicitly;
- end-user or administrator extensions can be added where the contract allows;
- other languages and systems can use stable keys or identifiers; and
- code can still refer conveniently to well-known built-in values.

The deterministic mapping must be designed carefully. It should be stable across deployments, independent of enum ordering, resistant to accidental collisions and covered by tests. Renaming an enum member must not silently create a new reference-data identity. The seed definition should carry the stable key explicitly or use a governed naming rule whose compatibility is tested.

The database must not store the enum's underlying integer as the meaning of the reference-data row. **No enums in databases.** The database stores the reference-data identity and record. The enum, if retained, describes the built-in seed set used by developers and startup.

This is the same pattern used elsewhere in the guidance: keep a convenient language-level shorthand where it helps, but place the authoritative contract at the boundary that must support lifecycle, administration, internationalisation, referential integrity and future extension.
