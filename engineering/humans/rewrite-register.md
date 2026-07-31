# Human Documentation Rewrite Register

This register tracks the human and agent documentation rewrite in bounded batches. It prevents the work from becoming a sequence of unconnected edits.

## Status values

- `planned`: identified but not started;
- `analysis`: content and audience review in progress;
- `rewrite`: editing in progress;
- `technical-review`: technical meaning being checked;
- `validation`: links, terminology and formatting being checked;
- `human-complete`: human-facing rewrite is complete, but agent alignment or independent technical review remains;
- `complete`: reviewed and validated; and
- `deferred`: deliberately postponed with a reason and next action.

## Batch register

| Batch | Documents or subject | Human layer | Agent layer | Examples | Technical review | Links | Translation review | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Human and agent gateways; writing contract | complete | complete | not applicable | complete | complete | complete | complete | Separate `HUMAN/` and `AGENTS/` gateways created. |
| 2 | Current state, stakeholder outcomes, DBB and WGF | complete | aligned | available | complete | complete | complete | complete | Human and agent layers align; technical review found no blocking contradiction in the rewritten scope. |
| 3 | Foundations: contracts, configuration, settings, startup, security, schema, mapping and caching | complete | aligned | available | complete | complete | complete | complete | Human and agent layers align; technical review found no blocking contradiction in the rewritten scope. |
| 4 | Slices, flows, stewardship, deferred design, queryability and API lifecycle | complete | aligned | expanded | complete | complete | complete | complete | Human palette, flow catalogue, examples and precise routing align; technical review fixed lifecycle-responsibility and event wording. |
| 5 | Code, testing, operations, dependencies, accessibility and completion | complete | aligned | available | complete | complete | complete | complete | Human introductions and precise conventions align; technical review found no blocking contradiction in the rewritten scope. |
| 6 | MB and repository bindings | complete | aligned | repository evidence | complete | complete | complete | complete | MB and BASE instructions route to the human concept layer before precise contract and implementation bindings. Existing human rationale remains in the documentation repository. |

## Document inventory

The subject batches are the primary work units. Add a row here when a document has a material audience, terminology or technical review decision that cannot be represented by the batch row.

| Path | Audience | Subject | Human rewrite | Agent rewrite | Example | Technical review | Link review | Translation review | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [HUMAN/README.md](./README.md) | human | entry point | complete | n/a | n/a | complete | complete | complete | complete | Concept-first route. |
| [HUMAN/WRITING-STYLE.md](./writing-style.md) | human and agent authors | writing contract | complete | n/a | n/a | complete | complete | complete | complete | Governs future rewrites. |
| [AGENTS/README.md](../AGENTS/README.md) | agents and human maintainers | agent route | n/a | complete | n/a | complete | complete | complete | complete | Points to human explanation. |
| [conventions/documentation.md](../agents/conventions/documentation.md) | human and agents | documentation maintenance | complete | aligned | n/a | complete | complete | complete | complete | Routes to the human writing contract and preserves precise link-maintenance rules. |
| [conventions/principles.md](../agents/conventions/principles.md) | human and agents | durable principles | complete | aligned | available | complete | complete | complete | complete | High-rise, shared-design and stewardship language reviewed. |
| [conventions/startup.md](../agents/conventions/startup.md) | human and agents | startup and discovery | complete | aligned | available | complete | complete | complete | complete | Concept-first introduction and precise lifecycle rules reviewed. |
| [conventions/iqueryable.md](../agents/conventions/iqueryable.md) | human and agents | governed queryability | complete | aligned | available | complete | complete | complete | complete | Consumer benefit explained before `.NET` term; safety boundary retained. |
| [conventions/data-protection.md](../agents/conventions/data-protection.md) | human and agents | security and data protection | complete | aligned | available | complete | complete | complete | complete | Protection and trust explained before authorisation vocabulary. |
| [HUMAN/CONFIGURATION-AND-SETTINGS.md](./CONFIGURATION-AND-SETTINGS.md) | human | configuration and settings | complete | n/a | n/a | complete | complete | complete | complete | Explains construction values versus managed product choices. |
| [examples/05-ef-schema-development/](./examples/05-ef-schema-development/before.md) | human | schema development | complete | n/a | complete | complete | complete | complete | complete | Paired example explains repetition, bundles and contract-backed schema. |
| [examples/06-object-mapping/](./examples/06-object-mapping/before.md) | human | object mapping | complete | n/a | complete | complete | complete | complete | complete | Paired example explains reusable contract map parts and query projection. |
| [examples/07-caching-at-the-wrong-boundary/](./examples/07-caching-at-the-wrong-boundary/before.md) | human | caching | complete | n/a | complete | complete | complete | complete | complete | Paired example explains optional in-memory/shared provider choice. |
| [HUMAN/FLOWS.md](./flows.md) | human | common flow catalogue | complete | n/a | available | complete | complete | complete | complete | Leads with recognition, BREAD/ST and three reuse levels. |
| [examples/10-request-bread-flow/](./examples/10-request-bread-flow/before.md) | human | Request, Evidence and Comments flow | complete | n/a | complete | complete | complete | complete | complete | Parent and nested BREAD/ST flow with reuse ladder. |
| [examples/11-request-offer-approval/](./examples/11-request-offer-approval/before.md) | human | offer request, assessment, approval and payment | complete | n/a | complete | complete | complete | complete | complete | BREAST preparation, separate assessment/approval and FMIS hand-off. |
| [HUMAN/STEWARDSHIP-AND-DEFERRED-DESIGN.md](./responsible-boundaries-and-deferred-design.md) | human | stewardship and deferred design | complete | n/a | available | complete | complete | complete | complete | Design responsibility without waiting for a named person. |
| [HUMAN/API-LIFECYCLE.md](./api-lifecycle.md) | human | published contract lifecycle | complete | n/a | available | complete | complete | complete | complete | Consumer contract, change, compatibility and retirement. |
| [HUMAN/PALETTE-FIRST-LOOK.md](./palette/first-look.md) | human | palette first look | complete | n/a | available | complete | complete | complete | complete | Simple concept-first entry before detailed terms. |
| [HUMAN/PALETTE-ELEMENTS.md](./palette/elements.md) | human | palette element jobs | complete | n/a | available | complete | complete | complete | complete | Individual element responsibilities before relationships. |
| [HUMAN/PALETTE-RELATIONSHIPS.md](./palette/relationships.md) | human | palette relationships | complete | n/a | available | complete | complete | complete | complete | Composition and optional relationships. |
| [HUMAN/PALETTE-TECHNICAL-TERMS.md](./palette/technical-terms.md) | human | palette technical terms | complete | n/a | available | complete | complete | complete | complete | Optional frontend vocabulary and BASE correspondence. |
| [HUMAN/GLOSSARY.md](./glossary.md) | human | recurring guidance vocabulary | complete | n/a | available | complete | complete | complete | complete | Plain meaning first, technical label second. |
