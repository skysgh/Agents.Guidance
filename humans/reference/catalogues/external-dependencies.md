# External Dependencies

An external dependency is a system, provider or technical capability that a service needs but does not contain within the responsibility currently being designed. The dependency may be operated by another team, supplied by a platform, provided by a vendor or represented by infrastructure outside the application process. External does not necessarily mean outside the organisation. It means that the current capability relies on a separate boundary and must deal with that boundary deliberately.

A database, cache, identity provider, identity and access management service, search service, queue, email provider, key vault, file store, payment provider, mapping provider, corporate site and partner API can all be external dependencies. A downstream warehouse, reporting service or archive can also be an external dependency when the service sends it information or relies on it for an obligation. A domain registry, DNS service, certificate authority and discovery service may likewise be separate dependencies even when their outputs are treated as deliverables.

The dependency is not just a package, URL or connection string. It has a purpose, a contract, a data classification, a responsible boundary, a lifecycle, an availability expectation and a failure policy. The service needs to know what it is allowed to send, what it may rely on in return, how it proves the interaction and what it does when the dependency is slow, unavailable, inconsistent or changed.

These dependencies often belong to different [Deliverable Systems](./deliverable-systems.md), and their outputs may be separate [Deliverables](./deliverables.md). Map both the dependency boundary and the thing it helps produce, such as a deployed artifact, reachable domain, trusted certificate, test context or operational record. Use [Registries](./registries.md) to distinguish enterprise-referred system, technology, supplier and obligation records from the project's own component, expiry and dependency records.

## Dependency categories

Durable storage keeps authoritative or operational records. The service must distinguish the logical meaning of the information from the physical representation held by the provider. Schema changes, transactions, backups, restoration, retention, deletion and recovery all belong in the dependency design.

Transient storage and caching can reduce repeated work or share derived values across instances. A cache is not an authority for business truth. Its keys, expiry, invalidation, classification and failure behaviour must prevent stale or protected information from bypassing current policy.

Identity and access providers establish identity or supply claims and credentials. They do not automatically decide what an actor may do within the service. The service maps that information to its own context, permissions and protected actions.

Search and analytics systems provide derived views for discovery or analysis. They are not automatically the authoritative record. Indexing, refresh, reconciliation, minimisation, deletion and outage behaviour must be explicit.

Queues and messaging systems provide durable deferred communication or work. They introduce identity, correlation, ordering, duplication, retry, expiry, poison-message and reconciliation concerns. A message being accepted is not the same as the business operation being completed.

Email, notification and document providers carry information beyond the immediate process. Their templates, recipients, attachments, links, tokens, retention and failure behaviour are part of the data and security design. A link is not authorisation; a recipient who holds an old link must not retain access merely because the link still resolves.

Key Vault holds production secrets, certificates, keys and other sensitive values. Production integration credentials belong only in Key Vault, never in ordinary system configuration, source control, generated artifacts, URLs or logs. The delivery pipeline may use its identity to provision or retrieve a value only when required for delivery; the executing application uses a workload identity to retrieve only what it needs at runtime. Humans must not retrieve or copy production secret values, although they may manage access, rotation, expiry and metadata without seeing the values.

Partner systems are external dependencies when the service exchanges information or invokes capabilities across an organisational or product boundary. A stable, understood interface lets the partner build its own experience or integrate its process. This is interoperability. It is not permission to depend on private tables, internal classes or undocumented provider behaviour.

Corporate sites and organisational surfaces are also integration dependencies when they link to, describe, launch or authenticate into the service. An internal portal, public corporate site, service directory or support site may be owned elsewhere, but its content and links can determine whether people find and reach the service. Record the responsible team, publication or integration contract, update timing, failure behaviour and retirement path. See [Deliverables](./deliverables.md) for the wider deliverable view.

## Delivery and deployment dependencies

The service that people use is not the only system that must be understood. A separate delivery system usually turns source, configuration and infrastructure definitions into a tested and deployable release. It may not receive a user's request at runtime, but the service depends on it to receive security fixes, recover from defects, change certificates or DNS, rebuild compatible environments and restore a known version.

These dependencies are often operated by different teams or providers and have their own identities, permissions, availability, audit, retention, recovery and exit concerns:

- **Code repository:** stores the versioned source, configuration templates, infrastructure definitions, documentation and change history from which a release is built. Define ownership, branch and review rules, protected history, access recovery, retention and the response to compromise.
- **Build and deployment pipeline:** checks, builds, tests, scans, packages, approves and promotes a release into an environment. Define triggers, identities, permissions, environment separation, approval points, secret handling, provenance, rollback, logs and what happens when the pipeline is unavailable.
- **Artifact, package and container registries:** hold the outputs and third-party inputs used by a build or deployment. Define trusted sources, immutability or replacement rules, provenance, vulnerability scanning, retention, access, restore and the treatment of a withdrawn or compromised artifact.
- **Infrastructure automation and state:** creates or changes networks, identities, storage, DNS, certificates, hosting and other resources. Define state ownership, locking, review, drift detection, secret handling, recovery and how a previous known-good infrastructure state is restored.
- **Domain Registry:** controls domain ownership, registration, delegation and renewal. Protect its accounts, named owners, recovery contacts, change approvals and expiry monitoring. Losing registration authority can make an otherwise healthy service unreachable or allow a domain to be misused.
- **DNS service:** publishes the records that direct users and connected systems to the service and may support validation, failover and certificate issuance. Define zone authority, delegation, record ownership, change control, propagation expectations, monitoring and recovery.
- **Certificate authority and renewal service:** issues or validates certificates and may support automated renewal. Define issuance permissions, trust chain, private-key protection, renewal ownership, expiry alerts, revocation and the behaviour when issuance or validation fails. Do not treat a provider's certificate automation as proof that the service has a complete transport-security design.
- **Cloud hosting and control plane:** provides the runtime, network, identity, storage and operational resources on which the service is hosted. Define the boundary between application ownership and provider responsibility, control-plane access, quotas, region or location, outage behaviour, backup, recovery and exit conditions.

For each delivery dependency, record whether it is required for a release, required for runtime operation, required for security maintenance, required for repair or required for recovery. This prevents the pipeline from being mistaken for a request-time dependency while still making its operational importance visible. The [Security in Transit Checklist](../checklists/security-in-transit.md) and [Security at Rest Checklist](../checklists/security-at-rest.md) provide related prompts for protecting the connections, credentials, artifacts and stored copies involved.

## Platform and service dependencies

The platform is the technical ground on which a service runs. Its capabilities may be supplied by a shared platform, a hosting environment, a managed provider or the service's own System LDM. The platform is not a site and it is not a substitute for the logical responsibilities of the business LDMs.

The following dependencies are common architectural considerations. They are not a mandatory shopping list. The service should adopt each one only when its capability, contract, data and failure consequences are understood.

### Protected key-value storage

Protected key-value storage holds secrets, credentials, tokens, certificates, keys and other sensitive values. It is not ordinary configuration. Define access identity, scope, rotation, expiry, redaction, startup failure and recovery. The service should start safely without exposing the values it needs to use.

### Relational storage

Relational storage commonly holds durable transactional state, relationships, state transitions, constraints and audit references. Define schema contribution, migrations, transaction boundaries, retention, backup, restore, readiness, failure and recovery. Keep the relational representation physical and mapped; it must not silently become the definition of domain meaning.

### Media and object storage

Media storage is distinct from relational storage because large files, images, documents and other binary content have different access, lifecycle, transport and retention concerns. Define protected and intentionally open containers separately, control content type and size, scan or validate content as required, and specify deletion, retention, caching and link-expiry behaviour. Open access is a publication decision, not a default for every object.

Read [Storage Types](./storage-types.md) for the shared vocabulary of key-value, relational, document, media and derived storage.

### Identity providers

An identity provider establishes who or what is acting. It does not automatically decide what that actor may do within the service. Define issuer, audience, claims, key rotation, clock tolerance, logout, provisioning, deprovisioning, outage and account recovery behaviour. Map external identity information to the service's own permissions and protected actions.

### Distributed caching

A distributed cache shares reusable values across service instances. It is optional infrastructure, not a second source of truth. Define keys, classification, expiry, invalidation, consistency, stampede protection, network failure, provider cost and fallback. A cache must not bypass authorisation or let stale protected data escape its responsible boundary.

### Search and geolocation

Full-text search is a derived discovery dependency. Define its indexed projection, permitted fields, classification, refresh and reconciliation process, deletion and retention behaviour, query limits and outage fallback. A search index is not the authoritative domain or relational record.

Geolocation may support geographic restrictions or location-aware behaviour. Define its source, accuracy, freshness, spoofing assumptions, user notice, privacy classification, fallback and policy boundary. A location signal should not silently become the sole evidence for a high-consequence decision without an appropriate control.

## Downstream obligations

Reporting, analytics, warehouses and archives are different downstream systems. They should not be collapsed into a generic reporting feed because they have different meanings, freshness, access, retention, reconciliation and recovery requirements.

Reporting serves defined operational or business questions and needs stable meaning, access control, reproducible results and a clear freshness expectation. Analytics supports broader exploration and decision-making and may require event history, derived measures, experimentation data or different privacy controls. A warehouse integrates data from one or more systems for governed cross-source analysis and needs ingestion, transformation, lineage, quality and reconciliation. An archive preserves records for long-term, legal, historical or regulatory reasons and has its own access, immutability, retrieval and lifecycle requirements.

For each downstream system, define the facts or projections it receives, the delivery mode, freshness, ordering, duplication and reconciliation expectations, classification, minimisation, retention and deletion rules, responsible contract boundary, failure, replay and backfill behaviour, and evidence of what was sent and accepted.

Deletion and anonymisation decisions cross these dependency boundaries. Personal information may remain in a search index, cache, event store, warehouse, report, archive, export, replica or backup after the source record changes. Identify each copy, how the lifecycle decision reaches it and what happens when immediate technical removal is unavailable. Read [Detailed Data Deletion Considerations](../../development/detailed-data-deletion-considerations.md) for the preferred digital outcome and the evidence needed to defend it.

## Dependency boundaries and responsibility

A service may use a dependency through an internal component such as a repository, broker, adapter or provider-specific service. That component protects the rest of the system from transport and vendor detail, but it does not erase the dependencyÔÇÖs consequences. The contract, classification, failure mode and recovery evidence remain part of the service design.

Several sites may use the same backend service and therefore the same external dependencies. A public site, consumer site and provider site may all rely on one relational store while receiving different projections and invoking different capabilities. The shared backend must enforce the policy for each request; the sites must not rely on being separate applications as their security control.

An external dependency may be required for readiness, optional for enhanced behaviour, authoritative for a particular fact or merely a derived copy. Those distinctions affect startup, degradation, retry, recovery and reconciliation. The [External Dependency Checklist](../checklists/external-dependencies.md) provides the prompts for reviewing them without interrupting the explanation here.

## Dependencies and logical structure

External dependencies sit outside the logical package that uses them, even when they are deployed alongside it. An LDM can contain the internal contracts and components that use a dependency, but the database, provider or remote service remains a separate boundary. The LDM is delivered as a whole; the dependency may have its own delivery and availability lifecycle.

The boundary between an external dependency and an internal component should remain visible. Internal components express the serviceÔÇÖs responsibility. External dependencies provide or receive capabilities across a contract. Confusing the two leads to vendor concepts leaking into the domain, private copies of shared behaviour and recovery plans that exist only in someoneÔÇÖs memory.

For a wider map of the system landscape, read [Guidance for System Design Architects](../../orientation/guidance-for-system-design-architects.md). For implementation placement, read [Logical Deployment Modules](./ldms.md), [Logical Layers](./logical-layers.md) and [Logical Building Blocks](./logical-building-blocks.md).
