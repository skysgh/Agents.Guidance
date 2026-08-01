# What Architects Need to Know

Architecture is the responsibility of understanding the whole system that a service must support. That whole is larger than the business capability and larger than the code repository. It includes the people and systems that enter through the service, the platform capabilities that allow it to operate, and the downstream systems that depend on what it produces.

The wider context is described in [Systems Within Systems](./systems-within-systems.md). That paper is the shared foundation for understanding digital systems as parts of enterprise, policy, regulatory, legal and international systems. [Legal and Regulatory Context](./legal-context.md) explains how to map both where a service is offered and where it is delivered, including the wider implications of remote access, processing, hosting and suppliers. This paper applies that foundation to interfaces and dependencies.

An architect does not need to prescribe every class or framework choice. They do need to make the boundaries, obligations, dependencies and consequences visible before local implementation decisions make them difficult to change.

## Start with the system landscape

Every service should have two related maps:

- an **interface map**, showing which groups and systems use the service and what each interface is for; and
- a **dependency map**, showing which capabilities and external systems the service needs, what data crosses each boundary and what happens when the dependency is unavailable.

These maps are architecture work. They should not be reconstructed later from routes, login screens, storage tables, monitoring dashboards or integration code.

## Interfaces are distinct boundaries

An interface is a way for a defined audience or system to use a capability. It has a purpose, contract, data shape, lifecycle, security context, operational expectations and failure behaviour.

The service commonly grows several interfaces as its responsibilities become clearer:

1. **Public anonymous experience**: an unauthenticated site or experience for public information, discovery, registration or other deliberately open actions.
2. **Service consumer interface**: an interface for customers, partners or other external consumers who use the service's capabilities.
3. **Service provider interface**: an interface for the internal business unit or operational team that provides, manages or decides the business content and outcomes.
4. **Support interface**: an interface for support staff to investigate, assist, correct or safely replay work within their authority.
5. **Monitoring and maintenance interface**: an interface for operators, system monitors and maintainers to inspect health, readiness, diagnostics, queues, dependencies, configuration and recovery actions.

These interfaces may be separate sites, applications, APIs, command surfaces or carefully bounded areas of one application. The decision is about audience, purpose, trust boundary and operational consequence, not about how many web projects happen to exist.

Do not collapse these audiences into one generic interface and expect roles to make the distinction disappear. A customer-facing experience, an internal provider workspace, a support console and an operator surface have different information needs, language, safe actions, audit obligations and failure concerns.

## Interfaces are not RBAC

Role-based access control answers a different question from interface design.

- The **interface boundary** says who the surface is for, what purpose it serves, which contract it exposes and what kind of interaction is appropriate.
- **Authentication** establishes who or what is acting.
- **Authorisation**, often implemented with RBAC, decides whether that actor may perform a particular action on a particular resource in a particular context.

RBAC must control access within an interface, but RBAC is not a substitute for designing the interfaces. Giving a customer an internal support role does not make a support console a customer interface. Giving a support user a permission does not remove the need for safe support workflows, restricted projections, stronger audit and deliberate correction behaviour.

The same person may use more than one interface in different contexts. The same role may exist in more than one interface with different actions. Keep the interface contract and the authorisation policy explicit rather than inferring one from the other.

For each interface, document:

- its audience and purpose;
- whether it is anonymous, user-authenticated or service-authenticated;
- the capabilities and contracts it exposes;
- the data it may display, accept, export or change;
- the mapping and projection rules at its boundary;
- the permissions and protected actions it requires;
- the audit and support expectations;
- its availability, rate, timeout and failure behaviour; and
- how it is monitored, retired and kept compatible.

## Map dependencies as obligations

A dependency is not just a package, URL or connection string. It is an external or platform capability with an owner, contract, data classification, lifecycle, availability expectation and recovery policy.

The following is the default dependency landscape for a serious service. The exact adoption and order depend on the service, but an omission must be deliberate rather than accidental.

### Secure key-value storage

The service needs a protected place for secrets, credentials, tokens, certificates, keys and other sensitive values. Secure key-value storage is not ordinary configuration and should not be replaced by committed settings files or environment variables without an explicit security decision.

Define access identity, secret scope, rotation, expiry, redaction, startup failure and recovery behaviour. The service should be able to start safely without exposing the values it needs to use.

### Relational storage

Relational storage usually holds the service's durable transactional state: records, relationships, state transitions, constraints and audit references.

Define ownership, schema contribution, migrations, transaction boundaries, retention, backup, restore, readiness, failure and recovery. Keep the relational model physical and mapped; it must not silently become the definition of the domain meaning.

### Media storage

Media storage is distinct from relational storage because large files, images, documents and other binary content have different access, lifecycle, transport and retention concerns.

Provide both:

- a **secure container** for protected media that requires authorised access; and
- an **open container** for media intentionally available through an open or broadly accessible path.

Open does not mean that every file is automatically public or that classification can be ignored. The service must decide which media belongs in which container, prevent accidental cross-container publication, control content type and size, scan or validate content as required, and define deletion, retention, caching and link-expiry behaviour.

### Identity provider

An Identity Provider (IdP) establishes user identity for authenticated interfaces. It is distinct from authorisation: the IdP says who the actor is, while the service decides what that actor may do in its own resource and business context.

Define issuer, audience, claims, key rotation, clock tolerance, logout, provisioning, deprovisioning, outage and account recovery behaviour. Do not allow an IdP claim or group name to become the complete authorisation model without an explicit mapping and ownership decision.

### Distributed cache service

A distributed cache shares values across service instances and can preserve reusable values beyond one process restart. It is optional infrastructure, not a second source of truth.

Define keys, classification, expiry, invalidation, consistency, stampede protection, network failure, provider cost and fallback. A cache must never bypass authorisation or allow stale protected data to escape its owning boundary.

### Optional full-text search service

Full-text search is an optional read and discovery dependency. It should be introduced when relational queries cannot provide the required language-aware search, scale or relevance behaviour.

Define the indexed projection, permitted fields, classification, refresh and reconciliation process, deletion and retention behaviour, query limits and outage fallback. The search index is a derived copy, not the authoritative domain or relational record.

### Optional geolocation service

Geolocation may be needed to enforce geographic restrictions, determine applicable policy or support a location-aware experience. It is not automatically trustworthy merely because it returns coordinates or a country code.

Define source, accuracy, freshness, spoofing assumptions, user notice, privacy classification, fallback and the policy boundary that makes the decision. A location signal may inform authorisation or policy; it should not silently become the sole evidence for a high-consequence decision without an appropriate control.

## Downstream obligations are different systems

The service may need to support several downstream consumers. Do not call all of them “reporting” or treat one export as an adequate substitute for the others.

### Reporting

Reporting serves defined operational or business questions, often with known measures, filters and periods. It needs stable meaning, access control, reproducible results and a clear freshness expectation.

### Analytics

Analytics supports exploration, analysis and decision-making across broader questions. It may need event history, derived measures, experimentation data or different retention and privacy controls from operational reporting.

### Warehouse

A warehouse is a managed analytical store that integrates data from one or more systems for governed cross-source analysis. It has ingestion, transformation, ownership, lineage, quality and reconciliation obligations. It is not simply a reporting screen or a copy of the relational database.

### Archiving

Archiving preserves records for long-term retention, legal, historical or regulatory reasons, usually with different access, immutability, retrieval and lifecycle requirements. It is not the same as a warehouse, a backup or a soft-delete flag.

For each downstream system, define:

- the facts or projections it receives;
- whether delivery is synchronous, event-driven, queued or batch;
- freshness, ordering, duplication and reconciliation expectations;
- data classification, minimisation, retention and deletion rules;
- the contract owner and consumer owner;
- failure, replay and backfill behaviour; and
- how the source service proves what was sent and what was accepted.

Deletion and anonymisation decisions cross these dependency boundaries. A personal-data representation may remain in a search index, cache, event store, warehouse, report, archive, export, replica or backup after the source record changes. The architecture must identify who owns each copy, how the lifecycle decision reaches it and what happens when immediate technical removal is unavailable. [Digital Data Lifecycle](../development/digital-data-lifecycle.md) sets out the preferred digital outcome and the evidence needed to defend it.

## The architecture review questions

Before approving a new capability or a major platform change, ask:

1. Which interfaces will use it, and which audience does each interface serve?
2. Is the anonymous public experience separate from authenticated consumer, provider, support and monitoring concerns where their obligations differ?
3. Which permissions are enforced within each interface, and where does the owning boundary make the decision?
4. Which dependencies are required, optional, authoritative or derived?
5. What data crosses each dependency boundary, and how is it classified and protected?
6. What is the failure mode when each dependency is unavailable: fail closed, degrade, queue, read-only or stop ready?
7. Which downstream obligations exist for reporting, analytics, warehouse and archiving, and why are they not interchangeable?
8. Which contracts, diagnostics, tests, reconciliation and recovery evidence prove the design?

The architect makes the whole obligation visible. The technical lead uses that map to keep implementation coherent, and developers use the resulting contracts and boundaries to build slices without inventing private substitutes.

## Related guidance

- [What Tech Leads Need to Know](./tech-leads-need-to-know.md)
- [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md)
- [Logical Deployment Modules](../development/ldms.md)
- [LDM Layers and Contents](../development/layers.md)
- [Vertical Slices: Common Shafts](../development/vertical-slices.md)
- [Cross-Cutting Services](../development/cross-cutting-services.md)
- [System LDM Services](../development/services.md)
- [Contracts](../development/contracts.md)
- [System LDM Service Readiness Reference](../reference/platform-services.md)
- [What Developers Need to Know](./developers-need-to-know.md)
- [API Lifecycle](./api-lifecycle.md)
- [Data Protection](../../agents/conventions/foundations/data-protection.md)
- [Startup and discovery](../../agents/conventions/foundations/startup.md)
- [Operations](../../agents/conventions/development/operations.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Data Deletion Guidance](../development/digital-data-lifecycle-overview.md)
- [Detailed Data Deletion Considerations](../development/digital-data-lifecycle.md)