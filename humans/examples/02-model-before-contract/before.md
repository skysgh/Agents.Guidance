[Up](../readme.md)

# Before: Concrete Model Before Contract

A developer creates a model with useful methods and properties. Services call the concrete model directly because it is available and easy to understand.

Over time, different services add methods for their own needs. Controllers, persistence code, tests and integrations begin depending on the model's accidental shape.

The consequences arrive gradually:

- a model carries responsibilities from several boundaries;
- persistence concerns leak into application behaviour;
- mappings become inconsistent;
- schema changes affect unrelated consumers;
- tests need concrete infrastructure; and
- replacement or discovery has no stable capability to identify.

Everyone may truthfully say that contracts exist somewhere. The current model still has no contract that describes the capability all these consumers are using.
