# Before: EF Schema Development by Repetition

An entity has a title, description, image reference, status, timestamps and one or more navigations. The schema configuration is written as a long sequence of fluent calls:

- configure the key;
- set string lengths and requiredness;
- choose Unicode and column types;
- add comments;
- configure indexes;
- configure relationships and delete behaviour;
- configure foreign keys;
- configure concurrency or audit fields; and
- repeat similar calls for the next entity.

The code is legal and often works in the first migration. It is also tedious enough that omissions become normal. An index is forgotten. A relationship uses the wrong delete behaviour. One property has a different length from all of its peers. A comment or classification is missing. A developer eventually asks the ORM to infer the model by convention because the explicit work feels like ceremony.

The resulting schema is then difficult to explain. When a query is slow or a migration behaves unexpectedly, it is not clear whether the cause is a deliberate policy, a missed fluent call or a framework convention that silently filled the gap.

The problem is not fluent configuration itself. The problem is repeating known structural decisions without bundling them behind the contracts that make them reusable.
