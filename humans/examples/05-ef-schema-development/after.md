[Up](../readme.md)

# After: EF Schema Development by Contracts and Bundles

The team identifies recurring schema capabilities and gives them structural contracts. Examples might include:

- an entity identity contract;
- a title and description contract;
- an image or media reference contract;
- a reference-data contract;
- an audit or timestamp contract; and
- a lifecycle or state contract.

Reusable extension methods bundle the fluent configuration for each stable capability. A title-and-description bundle can apply requiredness, lengths, Unicode policy, comments and indexes in one tested place. A navigation bundle can apply the foreign key, relationship cardinality, delete behaviour, index and documentation consistently.

The important step is not merely writing extension methods. It is allowing schema configuration methods to accept contract-bearing abstractions or constrained generic types. The configuration can then say, in effect:

```csharp
builder.ApplyTitleAndDescription<TEntity>();
builder.ApplyReferenceData<TEntity>();
builder.ApplyAuditFields<TEntity>();
builder.ApplyNavigation<TEntity, TRelated>();
```

The exact method names depend on the platform. The design value comes from the contract: any entity that implements the required capability receives the same reviewed schema policy, while genuinely different cases remain explicit exceptions.

This improves more than typing effort:

- omissions become less likely because the bundle is the unit of review;
- indexes and relationships have a predictable home;
- migrations show deliberate policy rather than scattered repetition;
- schema conventions can be tested against every participating contract;
- provider-specific behaviour remains inside the persistence boundary; and
- a developer can still see and override a deliberate exception.

The ORM is still used. Convention-based inference is still useful where it is safe. The improvement is that important structure is expressed by contracts and tested bundles rather than left to either repetitive code or unexamined framework defaults.
