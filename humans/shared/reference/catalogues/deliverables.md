[Up](./readme.md)

# Deliverables


A deliverable is something that must exist, be configured, be registered, be migrated, be published or be maintained for the intended outcome to be available. A deliverable may be executable, data, content, infrastructure, evidence or an external registration.

Deliverables are wider than software packages. A service can compile successfully and still be undeliverable because its domain is not registered, its DNS is missing, its certificate is expired, its reference data is absent, its public discovery is broken or its corporate sites do not link to it.

A release can also fail before the service is reached. The pipeline may run, while the environment-definition code is missing, the runner has the wrong permission, the test code is not the version that was qualified or the resulting environment differs from the one that was reviewed. The delivery therefore includes the codebases, the execution system, the resulting environments and the evidence that connects them.

The deliverable list is outcome-specific. It is not a demand to create every category for every service. The team should record which categories apply, who owns them, what evidence proves them ready and when they can be retired. A project-produced [Deliverables Registry](./registries.md#project-produced-registries) can provide that record, while enterprise-referred registries provide shared constraints such as approved technologies, systems, obligations and suppliers.

## Relationship to deliverable systems

[Deliverable Systems](./deliverable-systems.md) describes the distinct delivery, service, consumer, testing and cross-system test-context systems that produce, use or qualify these deliverables. It also distinguishes Pipeline Definition, Pipeline Execution and Environment Definition Systems within delivery. The [Deliverables Checklist](../checklists/deliverables.md) checks the relationship in practice. Use the systems catalogue to find boundaries and the deliverables catalogue to find everything that must cross, support or prove those boundaries.

## Deliverable systems

The primary deliverable systems are described separately in [Deliverable Systems](./deliverable-systems.md):

1. The compilation, qualification, packaging and deployment delivery system.
2. The service system.
3. The service consumer system, such as a browser SPA, running in a distinct client execution environment.
4. The testing system used by the delivery system to qualify the service and consumer systems.

The same team may deliver all four. That is a relationship of shared responsibility and coordination, not proof that they are one system. The service consumer is not the service runtime, and neither is the System LDM.

The delivery system also contains the Pipeline Definition, Pipeline Execution and Environment Definition Systems described in [Deliverable Systems](./deliverable-systems.md#delivery-system-constituents). These constituents may share a repository, but their deliverables are different: a flow definition describes what should run, a runner executes it, an environment definition describes what should exist and the resulting environment provides the execution context.

## Codebase and definition deliverables

The code that makes the outcome possible is itself part of the delivery. Depending on the service, this may include:

- **Service codebase:** application and domain code, interfaces, persistence mappings, integrations and service tests.
- **Client codebase:** SPA or other consumer code, assets, components, client-side flows and client tests.
- **Pipeline definition codebase:** delivery flows, gates, approvals, runner selection, evidence handling and release orchestration.
- **Environment definition codebase:** desired environments, infrastructure, networking, identities, policies, configuration scaffolding and deployment targets.
- **Test codebase and test context:** automated tests, Test Suites, exploratory test support, synthetic data generation, portable scenario context and system-specific translators.
- **Deployment definitions:** manifests, release configuration, migration instructions or other code that belongs to a distinct delivery boundary when its responsible team and lifecycle differ from the environment definition codebase.

These codebases may be stored together or separately. A shared repository does not make them one system. Their source history, dependencies, permissions, build path, generated outputs, review authority, release relationship, rollback and recovery conditions should remain understandable.

### Environment and execution-context deliverables

The code that defines an environment and the environment that results from applying it are related but different deliverables:

- **Environment definition:** the versioned desired state for networks, compute, storage, identity, policy, DNS, certificates, monitoring, queues, databases and other resources in a named environment.
- **Environment parameters and bindings:** the approved values, references, scopes, regions, subscriptions, accounts, tenants, variable sets and secret-store bindings that allow one definition to produce a particular environment without exposing secret values.
- **Environment instance:** the actual development, integration, test, business-test, qualification, production or recovery context, including its resource identities, versions, configuration, access, dependencies, health and drift state.
- **Environment baseline and evidence:** the version, plan or preview, approvals, applied result, resource inventory, health/readiness evidence, exceptions and recovery point that show what the environment actually contains.
- **Runner and execution support:** the runner image, installed tools, worker identity, network access, permissions, caches, logs, retention and recovery arrangement needed to execute the pipeline safely.

An environment definition is not proof that an environment exists. A successful pipeline run is not proof that the resulting environment matches the definition. The baseline and evidence connect the two.

## Data deliverables

- **Test data:** controlled data used to exercise behaviour, quality and failure paths. Define provenance, classification, isolation, reset, generation, retention and proof that production data is not exposed unnecessarily.
- **Cross-system test context:** a shared, neutral information system containing portable scenario context that multiple projects can translate into their own test inputs. It may describe people, organisations, students, universities, relationships, states and events without adopting one system's schema as the universal truth. Define stable scenario identifiers, responsible authority, versioning, contribution rules, translators, generated representations, reset, retention and expected outcomes. This is a deliverable to which many projects may contribute, not private seed data belonging to one service.
- **Reference data:** governed values used to interpret or constrain behaviour, such as codes, categories, translations, geographical values or policy tables. Define authority, version, effective dates, stewardship, change approval and compatibility.
- **Migrated data:** data transformed or transferred from an existing source into the delivered service. Define source authority, mapping, transformation, validation, reconciliation, rejected records, provenance, rollback or recovery and post-migration retention.
- **Derived and operational data:** indexes, projections, caches, queues, search documents, reports, audit records, backups and other copies required for operation or obligations. Define rebuild, retention, deletion, reconciliation and recovery behaviour.

## Content and presentation deliverables

- **Branding and service identity:** service names, logos, marks, colour and visual identity, tone, legal attribution, publication rules and the assets that help people recognise the responsible service. Define the responsible authority, licensing, accessibility and retirement treatment.
- **Textual templates:** emails, notifications, documents, page content, system messages, legal notices, help content and other governed text. Define the responsible person or team, version, review, escaping, localisation, accessibility and publication lifecycle.
- **Media:** imagery, video, audio, icons, documents, fonts and other binary content. Define the responsible authority, licensing, classification, formats, accessibility alternatives, scanning, transformation, retention, publication status and delivery path.
- **Translations and language resources:** translated content, locale rules, fallback behaviour, terminology and review evidence. A translated string is a deliverable with meaning and quality consequences, not merely a resource-file entry.
- **Search and discovery content:** page titles, descriptions, structured metadata, sitemaps, robots directives, canonical links and other material needed for search engines or other discovery agents to understand the service.

## Addressing, trust and reachability deliverables

- **Domain name:** the registered name and its responsible authority, renewal, recovery and transfer arrangements.
- **DNS records:** the records, delegation, validation and change controls that make the service reachable and support certificates, mail, verification or failover.
- **Certificates and trust configuration:** certificates, private-key protection, renewal, trust chain, hostname coverage, revocation and monitoring.
- **Discovery and SEO:** the deliberate public signals that let people and agents find, identify and correctly interpret the service. Include indexing policy, structured information, search previews, accessibility of public content and the path from discovery to the intended site or service.
- **Corporate sites and organisational surfaces:** internal portals, public corporate sites, intranets, service directories, application launchers, support sites and other organisational surfaces that link to or describe the service.

Corporate sites are often integration dependencies as well as deliverables. They may be maintained by another team, but without their links, directory entries, navigation, authentication handoff or content updates the service may be technically live and practically undiscoverable. Record the responsible teams, interfaces, publication process, update timing, failure behaviour and retirement obligations.

## Delivery and operational deliverables

- **Solution Architecture Document (SAD):** a controlled, pre-market description of the problem space, intended outcome, desired solution shape, boundaries, constraints, responsibilities, quality expectations and response conditions. It may form the basis of a procurement, proposal, statement of work or contract, so released versions must remain stable and identifiable. It is not a living document; material changes require an explicit version, amendment or replacement with their effect on responses and commitments made visible.
- **Solution Design Document (SDD):** a respondent's or solution provider's proposed design for satisfying the SAD. It records the proposed solution structure, interfaces, data, delivery approach, quality characteristics, assumptions, dependencies, exclusions, risks and responsibilities. An SDD is a proposal until evaluated and accepted; acceptance and contractual commitment must be recorded separately. Different respondents may produce different SDDs for the same SAD.
- **Technical Design Document (TDD):** an implementation-level design for an accepted solution or a specific change. It records the technical choices and consequences at the relevant boundary, such as components, interfaces, schemas, mappings, configuration, security, observability, migration, rollout, rollback, recovery and compatibility. TDDs are developed as work becomes sufficiently understood and referenced from the work items, decisions, contracts, tests and evidence they support. TDD means Technical Design Document here, not Test-Driven Development.
- Source, configuration templates, pipeline definitions and environment definitions.
- Compiled packages, container images, client bundles and signed or versioned artifacts.
- Deployment configuration, environment parameters, migrations and release notes.
- Runner images, tool manifests, execution identities, pipeline logs and retained delivery evidence where the runner is a distinct delivery dependency.
- Environment instances, resource inventories, readiness evidence, applied plans, drift findings and recovery baselines.
- Test plans, automated tests, test data, test context, test results, quality evidence and acceptance records.
- Interface definitions and boundary contracts, including compatibility and deprecation information.
- Event and message definitions, delivery, acknowledgement, retry, replay, reconciliation and evidence where the service uses asynchronous or cross-system communication.
- Monitoring, dashboards, alerts, health and readiness definitions, runbooks and support procedures.
- **Support manuals and information:** the information support staff need to diagnose, explain and resolve expected user and service problems, including known symptoms, supported responses, escalation routes, responsible boundaries and links to authoritative evidence.
- **Operational manuals and information:** the information operators need to run the service safely, including readiness, deployment, configuration, monitoring, alert response, access procedures, routine operation, dependency failure and recovery responsibilities.
- **Maintenance manuals and information:** the information maintainers need to change, repair, upgrade, migrate, deprecate and retire the service, including architecture decisions, contracts, dependency lifecycle, compatibility, rollback, data protection and replacement or decommissioning procedures.
- Backup, restore, recovery, rollback, incident and decommissioning procedures.
- Access policies, identities, certificates, secret-store bindings and configuration responsibility. Secret values are not ordinary deliverables to copy between environments.

## A useful omission test

Ask: "What must exist outside the code repository for a real person, browser, connected system, operator or recovery process to use, trust, find, support, repair or retire this service?"

The answer commonly exposes missing deliverables such as:

- hosting, environments and network routes;
- identity-provider registration and redirect configuration;
- domain, DNS and certificate responsibility;
- public and internal navigation or directory entries;
- accessibility, legal, privacy and support content;
- seed, reference, test and migrated data;
- shared cross-system test context and its system-specific translators;
- monitoring, backup and recovery evidence; and
- supplier, licence, retention and exit arrangements.

These items are part of a delivered outcome, not a second definition of the service. [Deliverables](../../../deliverables/readme.md) provides the wider explanation of how software, material, responsibility and evidence meet the people who depend on them. From this catalogue, [Deliverable Systems](./deliverable-systems.md) shows which distinct systems produce and use the items, [External Dependencies](./external-dependencies.md) shows the boundaries on which they rely and the [Deliverables Checklist](../checklists/deliverables.md) provides review prompts.
