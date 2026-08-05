[Up](./readme.md)

# Security at Rest Checklist


Use this checklist when information, secrets, credentials, keys, certificates, logs, media or derived copies are stored. Read [Data Protection](../../../../agents/conventions/foundations/data-protection.md), [External Dependencies](../catalogues/external-dependencies.md) and [Detailed Data Deletion Considerations](../../../development/detailed-data-deletion-considerations.md) first. The checklist is a design prompt, not a universal legal declaration.

## Understand what is stored

- [ ] Does each stored information category have an owner, classification and purpose?
- [ ] Is the authoritative record distinguished from caches, indexes, queues, reports, exports, replicas, archives, logs and backups?
- [ ] Are production integration credentials, tokens, encryption keys and certificates stored only in Key Vault, never in ordinary system configuration, source control, generated artifacts, URLs or logs?
- [ ] Are uploaded files and media given controlled identity, content-type and size rules, integrity checks and a decision about scanning or validation?
- [ ] Are data minimisation, retention, legal hold and deletion or anonymisation decisions recorded for each copy?

## Control access and protection

- [ ] Is access to every store authenticated through an identified workload, service, operator or recovery identity?
- [ ] Are permissions scoped to the smallest store, operation and data classification that the role requires?
- [ ] Is sensitive information encrypted at rest using an approved platform or cryptographic control, with the scope and exceptions recorded?
- [ ] Are keys protected separately from the data they protect, with ownership, purpose, rotation, expiry, revocation and recovery defined?
- [ ] Are provider-managed encryption, customer-managed keys, access logs and backup encryption responsibilities understood rather than assumed?
- [ ] Are exports, caches, search indexes, replicas, logs, temporary files and provider copies protected to the same standard as the source where their classification requires it?
- [ ] Are all media containers private, with protected and public content never mixed? If publication is required, is it served from a separately named and deliberately approved public container?
- [ ] Do protected media and downloads use an authorised access path and SAS or pre-signed links that expire in 30 seconds or less, rather than permanent bearer URLs?

## Keep secret values out of human hands

Use a portable **local development secret store** for developer-only values. In .NET, the repository binding for that store is commonly [User Secrets](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets) backed by a local `secrets.json` file outside the project directory. It must not be committed or treated as a production store.

- [ ] Does the delivery pipeline use its identity to provision, configure or retrieve secret values only when the release operation requires them?
- [ ] Does the executing production application use a workload identity to retrieve only the values it needs, and cache them only for the required lifetime?
- [ ] Are humans prevented from retrieving or copying production secret values? Human administrators may manage permissions, rotation, expiry and metadata without reading the values.
- [ ] Are local development secrets kept in the approved local development secret store and excluded from source control, build output, logs and support bundles?

## Make lifecycle and recovery real

- [ ] Can the service identify every copy that must be retained, deleted, anonymised, restricted or placed beyond use?
- [ ] Does deletion or anonymisation cover linkage keys, free text, media, indexes, caches, exports, events, replicas, archives and backups where applicable?
- [ ] Where immediate removal from a backup is not possible, are expiry, access restriction, restore handling and proof of non-return to active use defined?
- [ ] Are backups encrypted, access-controlled, monitored, retained for a defined period and tested through restoration?
- [ ] Are backups taken on a regular schedule, with incremental capture between full or baseline backups where the recovery objectives require it?
- [ ] Are restore procedures tested with the required permissions, keys, schema versions, media and reconciliation steps?
- [ ] Is the failure behaviour defined when storage, key access, media scanning, backup or restore is unavailable?
- [ ] Does the service fail closed, become read-only, queue work or degrade only where the resulting risk and operator action are explicit?

## History and self-service restoration

History tables are not encryption, backups or a substitute for disaster recovery. They are application-level version history or audit records. They become a security and resilience feature when authorised end users can inspect or restore an earlier state without maintainer intervention.

- [ ] Is the history record append-only or otherwise protected against unauthorised alteration?
- [ ] Does each entry record the relevant actor, time, reason, affected record, version and outcome without exposing unnecessary personal information?
- [ ] Are history records classified, retained and deleted or anonymised according to their own lifecycle?
- [ ] Is viewing history authorised separately from changing or restoring the current record?
- [ ] Does restoration validate the actor, current version, business rules, conflicts, relationships, media and downstream effects before applying the change?
- [ ] Is a restore itself auditable, reversible where appropriate and visible to the affected people and operators?
- [ ] Does the design still have independent backups and a maintainer-led recovery path for corruption, compromise, accidental deletion or unavailable application history?

## Prove and maintain the controls

- [ ] Are access, key use, security-relevant changes, deletion, restore and provider actions recorded without logging secrets or unnecessary personal information?
- [ ] Are retention, deletion, backup, restore, key rotation and access-review tests part of the delivery evidence?
- [ ] Are storage providers, regions, subprocessors, quotas, support arrangements and exit or migration conditions recorded?
- [ ] Is there a named owner for each store, copy, key and recovery procedure?
- [ ] Are expiry, rotation, revocation, restore failure, dependency outage and accidental exposure exercised before the service is treated as ready?

Related guidance: [Security in Transit Checklist](./security-in-transit.md), [External Dependency Checklist](./external-dependencies.md), [Regulatory and Obligation Checklist](./regulatory-obligations.md) and [Operations](../../../../agents/conventions/development/operations.md).
