# Storage Types Catalogue

Storage is a physical way to retain, retrieve or exchange information. A storage type is not automatically a domain model, and a product name is not automatically a design. The service first decides what information it must represent, what lifecycle it has, what relationships and queries are needed, and what consequences follow from loss, duplication, delay or exposure. It then chooses storage that can support those requirements.

Storage types are often external dependencies of an LDM. The LDM keeps the logical contracts, mappings, classification and lifecycle decisions. The storage provider supplies a physical representation and operational mechanism. Several storage types may be used together for one capability, but each copy and representation needs a deliberate relationship to the logical information.

## Key-value storage

Key-value storage retrieves a value by a key. It is useful when the service already knows the key and does not need rich relationships, joins or flexible queries. Common uses include protected configuration references, settings, session data, feature values, idempotency records and cache entries.

The key is part of the design. Its scope, classification, format, expiry, invalidation and collision behaviour must be clear. A key-value store is not automatically suitable for authoritative transactional records merely because it is quick to read or easy to configure. When a value affects a decision, the service must know whether the store is authoritative, derived or temporary and what happens when it is unavailable or stale.

Secure key-value storage for secrets is a specialised use. Secrets, credentials, certificates and keys need access control, rotation, expiry and redaction. They must not become ordinary application settings simply because both are retrieved by a key.

## Relational storage

Relational storage represents information through related records, constraints and transactions. It is useful when the service needs durable state, relationships, controlled state transitions, consistency across related records, governed queries or reporting over well-defined structures.

Relational storage can enforce valuable physical constraints, but tables and ORM entities remain physical representations. They must not silently become the logical domain model. The service should map between the logical concepts and relational records when their responsibilities differ. Schema contribution, migrations, transaction boundaries, indexes, backup, restore, retention, deletion and recovery are part of the storage design.

A relational database can support several domains or LDMs, but sharing a database does not make those responsibilities one domain. Conversely, separate databases do not create meaningful boundaries if the logical responsibilities remain tangled.

## Document storage

Document storage keeps a structured document as a physical unit. It is useful when information is naturally retrieved together, when the structure varies in controlled ways, when an aggregate or document has a clear consistency boundary, or when the access pattern is primarily document-oriented.

A document boundary can reduce joins and make a particular read or write efficient. It can also duplicate information, make cross-document consistency harder and encourage a physical document to become an accidental domain model. Decide which values are authoritative, which are derived, how references are maintained and how document versions, migrations, retention and deletion behave.

Document storage is not the same as media storage. A JSON or similar structured document contains data that needs to be interpreted. A media object contains bytes such as an image, audio recording or uploaded file and usually needs separate metadata, classification and access handling.

## Media and object storage

Media or object storage holds large binary content such as images, documents, audio, video, generated files and archives. It is useful when content has different size, transport, caching, scanning, access or retention needs from transactional records.

Keep metadata and business relationships in a suitable logical and transactional structure. The media object should have a controlled identity, classification, content type, size limit, integrity check, retention policy and deletion or anonymisation path. Protected media needs an authorised access path. Open media needs an intentional publication decision; an open container is not permission to publish every object placed in it.

Generated documents, attachments, URLs, access tokens and deep links are part of the media and notification design. A link is not authorisation. An old link must not continue to expose protected content after the relevant person association or permission changes.

## Related storage and derived copies

A cache stores rebuildable or reusable values and is not a second source of truth. A search index stores a derived projection for discovery and must have refresh, reconciliation and deletion behaviour. A queue stores deferred work and requires identity, correlation, retry, idempotency and recovery rules. An event store or append-only log preserves facts or history with its own query, retention and privacy obligations. A warehouse supports cross-source analysis, while an archive preserves records for long-term access or legal and historical purposes. A backup supports recovery and is not automatically an archive or an operational record.

These forms may contain copies of personal, confidential or regulated information. A lifecycle decision must consider each relevant copy, including indexes, caches, exports, reports, replicas, messages, archives and backups. Read [Data Deletion Guidance](../../development/data-deletion-guidance.md) and [Detailed Data Deletion Considerations](../../development/detailed-data-deletion-considerations.md) when the representation or copy must change.

## Choosing and combining storage

Choose storage from the logical information and its required capabilities, not from fashion or the shortest first implementation. A request may use relational storage for authoritative state, document storage for a bounded aggregate representation, media storage for attachments, key-value storage for settings and a search index for discovery. That combination is coherent when the contracts, mappings, authority, consistency, failure, recovery, classification and lifecycle of each representation are explicit.

The [External Dependencies](./external-dependencies.md) catalogue explains how storage crosses a service boundary. [Guidance for System Design Architects](../../orientation/guidance-for-system-design-architects.md) explains how storage appears in the system dependency map. The [External Dependency Checklist](../checklists/external-dependencies.md) provides the review prompts.
