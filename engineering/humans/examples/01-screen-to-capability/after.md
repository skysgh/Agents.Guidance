# After: Screen Request Becomes Storage Design

The team treats the page request as evidence about a capability, not as the complete model.

Business analysis contributes the meaning of a provider, relevant decisions and the states users recognise. Developers and architecture identify the boundary contract, logical model, mappings and persistence intention. Security identifies visibility and approval rules. Testers identify the behaviours and denied paths that must be proved. Operations identifies readiness, diagnostics and recovery needs.

The design records:

- the provider capability and stewarding boundary;
- the external read projection and explicit commands;
- valid states and transitions;
- access and classification rules;
- mapping between boundary, application and persistence models;
- governed query operations;
- intended relationships, including those deferred from construction;
- schema and startup participation; and
- tests and WGF consequences for what goes first.

The first screen can still be built. It is now one consumer of a capability rather than the accidental author of the whole system. Later construction has a place to fit.
