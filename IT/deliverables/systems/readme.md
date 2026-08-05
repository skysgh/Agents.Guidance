[Up](../readme.md)

# System Perspectives


The browser page says that a request was submitted. The service is still processing it. The delivery team knows which version was released, but the operator cannot tell whether the dependency is slow or broken. A tester has a passing browser result, while the person waiting for the outcome has no useful explanation or way to recover.

Nothing in that situation is necessarily a careless local decision. The visible experience, the service, the release path and the test environment are different systems with different conditions. A dependable outcome appears when their responsibilities join clearly.

The browser or client presents a consumer experience. The service runtime owns capabilities and durable decisions. The delivery or pipeline system builds and releases the result. The testing system qualifies the systems and preserves evidence. Shared contracts, flows, quality conditions and lifecycle decisions connect them.

These routes make those differences visible without requiring a separate repository, deployment or team for every folder. The [Deliverable Systems](../../shared/reference/catalogues/deliverable-systems.md) catalogue remains the canonical description of the systems, their boundaries and their relationships.

## Choose a system perspective

- [Client System](./client/readme.md): browser or client execution, SPA assets, views, components, consumer-side flows, accessibility, usability and browser security.
- [Organisational Site Systems](./sites/readme.md): intranet and extranet service surfaces, their content and media, publication handoffs, reachability, lifecycle and maintenance responsibilities.
- [Service System](./service/readme.md): server-side capabilities, domains, LDMs, persistence, integrations, diagnostics, authorisation, operation and recovery.
- [Integration System](./integration/readme.md): API, event, message, database, file and SFTP exchanges, mappings, orchestration, reconciliation and transfer evidence.
- [Pipeline System](./pipeline/readme.md): source, build, qualification, packaging, promotion, deployment, release controls and artifact evidence. The foundation route exists; project-specific evidence remains open.
- [Testing System](./tests/readme.md): test execution, browser and device qualification, test data, cross-system evidence and result retention. The foundation route exists; project-specific evidence remains open.
- [Shared System Concerns](./shared/readme.md): contracts, flows, models, quality, lifecycle and evidence that cross or connect the system boundaries.

The same person may contribute to several systems. Their contribution still changes with the boundary: a front-end developer sees browser state and task completion, a service developer sees durable authority, a pipeline developer sees provenance and promotion, and a tester sees claims and evidence. Naming those differences gives each person a place to contribute without asking them to carry the whole delivery in their head.

## Related guidance

- [Systems Boundary Migration Plan](../../../.agent-work/plans/SYSTEMS-BOUNDARY-MIGRATION-PLAN.md)
- [Deliverable Systems](../../shared/reference/catalogues/deliverable-systems.md)
- [Deliverables](../../readme.md)
- [Finding a Useful Starting Point](../../foundations/ways-into-guidance.md)
- [Engineering for People](../../../readme.md)
