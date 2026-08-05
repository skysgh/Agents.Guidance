[Up](../readme.md)

# Integration System


The service has a useful interop API, but a dependent organisation may have no API, no reachable gateway, or no permission to expose one. A business process may still depend on a scheduled export, a managed file transfer, a partner-hosted folder or an SFTP exchange. The absence of a modern interface at one boundary does not make the exchange disappear; it changes the system that must carry it safely.

The Integration System is the system that moves, translates, schedules, observes and reconciles information or work between the delivered service and external systems. It is a separate deliverable system when it has its own execution environment, identity, dependencies, lifecycle, failure behaviour and evidence, even when it is used only once for migration or runs every few minutes as an operational process.

It may be implemented with a cloud provider's integration service, a cloud-neutral product, a managed transfer service, service-owned workers or a combination. Azure Data Factory or Data Fabric, AWS integration services, Informatica, MuleSoft and similar products are implementation options, not architectural authorities. The choice should account for enterprise strategy, existing skills, data location, network topology, egress cost, security controls, portability, supplier dependence and the consequences of being unable to change provider later.

## Boundary and responsibilities

The Integration System may include:

- API, event, message, database, file and SFTP connectors;
- schedules, triggers, orchestration, batching, throttling and dependency coordination;
- schema mapping, validation, transformation, enrichment and filtering;
- credentials, certificates, network routes, private endpoints and managed identities;
- staging, quarantine, dead-letter, retry, replay, backfill and idempotency controls;
- transfer receipts, correlation, lineage, reconciliation and operational evidence; and
- monitoring, alerting, runbooks, support procedures, recovery and controlled retirement.

It does not become the authority for business meaning merely because it transforms data. The sending or receiving system remains authoritative for the facts it owns. The Integration System must preserve provenance and make each mapping, transformation, acceptance and failure visible enough for the responsible authority to investigate.

An Integration System may support the Service System, the Delivery System, a migration activity or several external systems. A one-time migration still requires a controlled boundary, repeatable execution where practical, validation, reconciliation, rollback or recovery treatment and retained evidence. A recurring integration also requires freshness, duplicate, outage, replay, late-arriving data and decommissioning decisions.

## Choosing cloud-specific and cloud-neutral capability

There is no universal ratio of provider-specific to cloud-neutral integration. Record the decision rather than treating portability as automatically more valuable or provider integration as automatically simpler.

A provider-native capability may reduce network distance, egress, operational effort and identity complexity when the participating data and runtime already live in that provider's boundary. A cloud-neutral or independently operated capability may reduce lock-in, support several providers, preserve an enterprise integration operating model or remain available when no single cloud can host every boundary. Cross-cloud movement can introduce egress cost, additional trust boundaries, duplicated monitoring and more complicated incident response.

For each material flow, record the selected capability, the alternatives considered, the data location, network path, cost assumptions, security boundary, exit or migration condition, responsible operator and evidence that the choice remains appropriate.

## Flow lifecycle

A dependable integration flow makes its lifecycle visible:

```text
source and authority
    -> extract or receive
        -> validate and classify
            -> map and transform
                -> deliver or apply
                    -> acknowledge and record
                        -> reconcile, retry, quarantine or recover
```

A successful connection or file transfer is not proof that the receiving system accepted the intended meaning. Evidence should distinguish sent, received, parsed, validated, accepted, applied, rejected, quarantined, retried, replayed and reconciled states. A duplicate, partial batch, timeout, changed schema, unavailable endpoint or expired certificate needs a defined response and an owner.

## Data protection and security

Treat API payloads, files, extracts, staging areas, logs, transfer receipts and rejected records according to their classification. SFTP is a transport, not a complete security or retention design. Define key or certificate ownership, host verification, credential rotation, least privilege, network restriction, encryption, malware or content checks where relevant, temporary-file handling, log redaction, retention, deletion and recovery.

Do not copy production data into development or test integration environments for convenience. Use synthetic data or an explicitly governed non-production transformation. Test the integration boundary with representative schemas, failure paths and reconciliation evidence without making the test fixture the authority for business truth.

## Required delivery evidence

For each Integration System or material flow, deliver and maintain:

- the purpose, participating systems, data authority and intended freshness;
- the topology, connectors, network routes, hosting boundary and provider choice;
- interface, file, message or schema contracts with version and compatibility rules;
- mappings, transformations, validation rules, filters and provenance requirements;
- schedules, triggers, batching, ordering, idempotency and throughput assumptions;
- identities, credentials, certificates, secret-store bindings and access decisions;
- retry, timeout, duplicate, quarantine, replay, backfill, outage and recovery behaviour;
- monitoring, correlation, alerting, transfer receipts and reconciliation evidence;
- support, operational and maintenance information with named ownership; and
- migration, deprecation, exit and deletion conditions, including any one-time flow.

The [Deliverables Checklist](../../../shared/reference/checklists/deliverables.md) provides the review prompts. The [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md#5-integration-system) catalogue defines the system boundary, while [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md) describes the separate boundaries on which a flow may rely.

## Current entry points

The [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md#5-integration-system) catalogue gives the Integration System its place among the systems delivered around a service. [Deliverables](../../../shared/reference/catalogues/deliverables.md) lists its code, configuration, mappings, evidence and operational material. The [Testing System](../tests/readme.md) describes integration and data-ingress/egress test areas; the Integration System remains responsible for operating the flow and preserving its runtime evidence.

A fuller project route belongs here when the actual topology, participating systems, vendor or platform choice, contracts, data classifications, schedules, recovery exercises and retained evidence are known.
