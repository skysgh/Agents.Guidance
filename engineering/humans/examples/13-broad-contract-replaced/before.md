# A broad contract spreads the change

A service exposes one shared `RequestService` contract. It started with a read operation, then gained submission, approval, notification, export, retry and workflow methods because each new consumer already depended on the same interface.

The interface looks convenient, but its consumers do not share one responsibility. A browser needs a status query and submit result. An approval worker needs a state transition. A notification process needs an event or message. An export process needs a governed read model. The contract now carries different authorities, data classifications, failure meanings and lifecycles.

A change to approval rules requires every consumer to rebuild. A notification dependency outage changes the error behaviour of a submission call. The export team adds fields that should not be visible to the browser. Tests require unrelated infrastructure because the contract's implementation composes persistence, workflow, messaging and external providers.

The team has one interface, but no dependable boundary. Rework spreads because every consumer is coupled to responsibilities it does not own.

## Evidence

- One contract contains reads, state changes, notifications, export and workflow.
- Consumers depend on methods and failure meanings unrelated to their capabilities.
- A provider outage changes the behaviour of an unrelated consumer.
- Tests need unrelated infrastructure and data to exercise one operation.
- No single Domain or LDM owns the complete contract meaning and lifecycle.
