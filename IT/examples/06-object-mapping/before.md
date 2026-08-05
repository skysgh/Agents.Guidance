[Up](../readme.md)

# Before: Object Mapping by Repetition or Guesswork

A system has many entities and DTOs with recurring parts: identity, title, description, image, reference-data labels, audit information and state metadata.

The team writes one map per object and repeats the same member configuration. Small differences creep in. One map forgets an image URL. Another maps an internal reference-data key as a display label. A third includes a field that should not cross the boundary.

The repetition becomes tiring, so the team asks AutoMapper, Mapster or another mapper to infer everything by convention. The first version is shorter. Later, a projection returns an unexpected property, a nested object is materialised unexpectedly, a query stops translating efficiently or a sensitive value appears in a response. The team blames the mapper and considers removing the mapping abstraction entirely.

Two different failures have been combined:

- explicit mapping was repeated without reusable contract parts; and
- implicit mapping was trusted without a deliberate boundary contract.
