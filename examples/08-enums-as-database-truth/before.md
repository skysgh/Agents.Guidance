# Before: Enums Become Database Truth

A developer needs a status, category or type field. An enum is familiar, concise and supported by the language and ORM, so it becomes the source of truth:

```csharp
public enum ProviderStatus
{
    Draft,
    Active,
    Retired
}
```

The database stores the enum as an integer or string. The first version is easy to read, and the code appears strongly typed.

The hidden costs accumulate:

- the numeric value has no useful meaning outside the compiled language;
- renaming a member may change labels or break clients while the database retains old values;
- inserting or reordering members can change numeric meaning;
- upper and lower bounds are fixed by the compiled deployment;
- administrators and end users cannot add a valid value without a code release;
- another language or external system must understand a private code vocabulary;
- labels, descriptions, translations, effective dates and classification have nowhere natural to live;
- values cannot have their own identity, lifecycle, permissions or audit history; and
- the ORM may make the mapping look more deliberate than it really is.

The enum has quietly become a database schema, an API contract, an administrative catalogue and a cross-language integration vocabulary all at once. It is good at none of those jobs.

The problem is not that enums are always bad. The problem is allowing a developer shorthand to become the authoritative representation of managed data.
