[Up](../readme.md)

# Engineering Checklists


The reader guidance explains the reasoning behind the structures used in a dependable service. Checklists provide practical prompts for applying that reasoning to a design, review or delivery decision.

Checklists are kept apart from the development folder because they are used across engineering phases and stakeholder groups. An architect, tech lead, developer, operator or reviewer may use the same subject checklist at a different level of detail. The checklist belongs to the subject being checked, not to the job title of the person using it.

There is one shared checklist folder rather than a separate copy for each stakeholder group. Separate role-based copies would repeat the same prompts and would eventually disagree. When a subject needs different prompts for architecture, development or operations, give those prompts clearly named sections or separate subject files and link them from the shared index. Create another top-level checklist folder only when a genuinely different audience needs a different kind of checklist collection, not merely because the reader has a different role.

The checklists are not a substitute for understanding the subject. They are deliberately separate so that the explanatory documents can flow as teaching rather than becoming a sequence of questions. Use the checklist after reading the relevant catalogue or guidance page and record the answers with the design evidence for the service.

Use [Regulatory and Obligation](./regulatory-obligations.md) when identifying the actual legal, regulatory, contractual, policy and standards sources, duties and evidence for a service. Use [Sites and Interfaces](./sites-and-interfaces.md) when defining the groups, sites, flows and views a service will provide. Use [External Dependencies](./external-dependencies.md) when a capability crosses into another provider or technical system. Use [Deliverables](./deliverables.md) when checking that the outcome includes its systems, data, content, addressing, discovery, corporate surfaces and operational evidence, not only its code. Use [Deliverable Systems](../catalogues/deliverable-systems.md) to check that the delivery, service, consumer, testing and cross-system test-context systems remain distinct. Use [Deliverables Checklist](./deliverables.md) for the combined review. Use [Domains and Capabilities](./domains-and-capabilities.md) when placing meaning and behaviour. The [LDM and Logical Layers](./ldms-and-logical-layers.md) checklist supports a review across both subjects, while the separate [Logical Deployment Modules](../catalogues/ldms.md) and [Logical Layers](../catalogues/logical-layers.md) catalogues explain their distinct concepts.

Use [Security at Rest](./security-at-rest.md) when information, secrets, media, copies or backups are stored. Use [Security in Transit](./security-in-transit.md) when information, credentials, media or operational traffic crosses a device, network, process, provider or organisational boundary. Use both when reviewing a complete capability.

The checklists should grow when repeated omissions reveal a missing prompt. They should not become a second implementation standard or require an answer that is irrelevant to the consequences of the service.
