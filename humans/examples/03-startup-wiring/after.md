[Up](../readme.md)

# After: Startup Wiring by Accumulation

The team first defines the participant contracts and lifecycle:

- what capability each participant provides;
- which module or boundary carries responsibility for it;
- when it may run;
- what it depends on;
- how duplicates and exclusions work;
- whether it is idempotent; and
- how discovery, activation, success and failure appear in startup diagnostics.

At that point, explicit registration or contract-based reflection can be chosen on evidence. Reflection is useful because the system is organised enough to discover contract-bearing participants, not because reflection itself creates the organisation.

The first implementation may still be hard-wired while the contract is proven. The design is not postponed. Later discovery can reduce repetitive host knowledge without hiding the lifecycle.
