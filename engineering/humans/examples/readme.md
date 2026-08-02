# Example Gallery

These examples are for recognition. They show ordinary situations in which a local decision appears reasonable but creates a wider structural problem. Each case has two files:

- `before.md` describes the common starting point and its consequences;
- `after.md` shows how the same work can move through shared design, responsible boundaries and staged construction.

No role is presented as the sole cause of the problem. Each example shows how business meaning, implementation, testing, operations and architecture contribute different evidence to the improvement. The examples are places to see the ideas in motion, not tests of whether the reader already knows the vocabulary.

The examples are illustrative patterns, not universal architecture or legal advice. The durable point is the decision they make visible: authority, boundary, lifecycle, evidence or cost of omission. Adapt the arrangement to the responsible Domain, obligations, systems and people in the real work.

Choose a case that feels familiar, then follow its improvement to see how the decision changes when the wider structure is made visible:

## Find an example by role or problem

**I am responsible for:**

- **Product, scope or delivery pressure:** [Request, assessment, approval and payment](./11-request-offer-approval/after.md), [Product Owner foundation under pressure](./12-product-owner-foundation-under-pressure/after.md), [Ambiguity in status states](./14-ambiguity-in-status-states-before-authority-emerges/after.md), [Request submission full lifecycle](./17-request-submission-full-lifecycle/after.md)
- **Capability design or architecture:** [Screen request becomes storage design](./01-screen-to-capability/after.md), [Concrete model before contract](./02-model-before-contract/after.md), [Broad contract replaced](./13-broad-contract-replaced/after.md), [Ambiguity in status states](./14-ambiguity-in-status-states-before-authority-emerges/after.md), [Enduring entities and bounded membership](./16-enduring-entities-and-membership/after.md), [Request submission full lifecycle](./17-request-submission-full-lifecycle/after.md)
- **Implementation or contracts:** [Concrete model before contract](./02-model-before-contract/after.md), [Queryable read](./04-queryable-read/after.md), [EF schema development](./05-ef-schema-development/after.md), [Object mapping](./06-object-mapping/after.md), [Caching](./07-caching-at-the-wrong-boundary/after.md), [Enums as database truth](./08-enums-as-database-truth/after.md), [Magic strings](./09-magic-strings/after.md), [Request BREAD/ST flow](./10-request-bread-flow/after.md)
- **Analysis, meaning or stakeholder language:** [Screen request becomes storage design](./01-screen-to-capability/after.md), [Request BREAD/ST flow](./10-request-bread-flow/after.md), [Ambiguity in status states](./14-ambiguity-in-status-states-before-authority-emerges/after.md), [Role polysemy across boundaries](./15-role-polysemy-across-boundaries/after.md), [Enduring entities and bounded membership](./16-enduring-entities-and-membership/after.md)
- **Testing, Operations or Support handoff:** [Screen request becomes storage design](./01-screen-to-capability/after.md), [Request, assessment, approval and payment](./11-request-offer-approval/after.md), [Product Owner foundation under pressure](./12-product-owner-foundation-under-pressure/after.md), [Request submission full lifecycle](./17-request-submission-full-lifecycle/after.md)
- **Client system, SPA or accessibility boundary:** [SPA consumer system](./18-spa-consumer-system/after.md), [Screen request becomes storage design](./01-screen-to-capability/after.md), [Request, assessment, approval and payment](./11-request-offer-approval/after.md)

**I am facing:**

- **A screen-driven design or unclear capability boundary:** [Screen request becomes storage design](./01-screen-to-capability/after.md), [Request BREAD/ST flow](./10-request-bread-flow/after.md), [Request, assessment, approval and payment](./11-request-offer-approval/after.md)
- **Conflicting state or role meanings:** [Ambiguity in status states](./14-ambiguity-in-status-states-before-authority-emerges/after.md), [Role polysemy across boundaries](./15-role-polysemy-across-boundaries/after.md)
- **Coupled authority or an over-broad contract:** [Broad contract replaced](./13-broad-contract-replaced/after.md), [Role polysemy across boundaries](./15-role-polysemy-across-boundaries/after.md)
- **Entity lifecycle or membership ownership:** [Enduring entities and bounded membership](./16-enduring-entities-and-membership/after.md), [Request submission full lifecycle](./17-request-submission-full-lifecycle/after.md)
- **Data representation or schema drift:** [EF schema development](./05-ef-schema-development/after.md), [Enums as database truth](./08-enums-as-database-truth/after.md), [Magic strings](./09-magic-strings/after.md)
- **A browser client that is carrying service authority:** [SPA consumer system](./18-spa-consumer-system/after.md)

- [Screen request becomes storage design](./01-screen-to-capability/before.md) -> [improvement](./01-screen-to-capability/after.md)
- [Concrete model before contract](./02-model-before-contract/before.md) -> [improvement](./02-model-before-contract/after.md)
- [Startup wiring by accumulation](./03-startup-wiring/before.md) -> [improvement](./03-startup-wiring/after.md)
- [Queryable read rejected or exposed directly](./04-queryable-read/before.md) -> [improvement](./04-queryable-read/after.md)
- [EF schema development by repetition](./05-ef-schema-development/before.md) -> [improvement](./05-ef-schema-development/after.md)
- [Object mapping by repetition or guesswork](./06-object-mapping/before.md) -> [improvement](./06-object-mapping/after.md)
- [Caching at the wrong boundary](./07-caching-at-the-wrong-boundary/before.md) -> [improvement](./07-caching-at-the-wrong-boundary/after.md)
- [Enums as database truth](./08-enums-as-database-truth/before.md) -> [improvement](./08-enums-as-database-truth/after.md)
- [Magic strings for routes and permissions](./09-magic-strings/before.md) -> [improvement](./09-magic-strings/after.md)
- [Request BREAD/ST flow](./10-request-bread-flow/before.md) -> [improvement](./10-request-bread-flow/after.md)
- [Request, assessment, approval and payment](./11-request-offer-approval/before.md) -> [improvement](./11-request-offer-approval/after.md)
- [Product Owner foundation under delivery pressure](./12-product-owner-foundation-under-pressure/before.md) -> [improvement](./12-product-owner-foundation-under-pressure/after.md)
- [Broad contract replaced by responsible boundaries](./13-broad-contract-replaced/before.md) -> [improvement](./13-broad-contract-replaced/after.md)
- [Ambiguity in status states before authority emerges](./14-ambiguity-in-status-states-before-authority-emerges/before.md) -> [improvement](./14-ambiguity-in-status-states-before-authority-emerges/after.md)
- [Role polysemy across boundaries](./15-role-polysemy-across-boundaries/before.md) -> [improvement](./15-role-polysemy-across-boundaries/after.md)
- [Enduring entities and bounded membership](./16-enduring-entities-and-membership/before.md) -> [improvement](./16-enduring-entities-and-membership/after.md)
- [Request submission capability through its full lifecycle](./17-request-submission-full-lifecycle/before.md) -> [improvement](./17-request-submission-full-lifecycle/after.md)
- [SPA consumer system treated as presentation furniture](./18-spa-consumer-system/before.md) -> [improvement](./18-spa-consumer-system/after.md)

The [YAGNI versus WGF](../orientation/design-before-build-and-wgf.md) paper explains the planning instinct behind the examples.
