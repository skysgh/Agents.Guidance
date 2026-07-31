# Before: Startup Wiring by Accumulation

A host starts with a few explicit registrations. As modules grow, configuration objects, mappings, schema participants, cache providers and initialisers are added wherever a developer finds a convenient place.

The system may work for a long time. Its lifecycle is held in memory by people who know the history.

Later, a participant is registered twice, runs before its dependency, is forgotten in a new host, or fails without appearing in startup diagnostics. A developer proposes reflection and another developer objects that reflection is magic.

Both are discussing wiring before discussing organisation. The real problem is that the participants do not share clear contracts, lifecycle rules, scope, ordering or diagnostic identity.
