# Deliverables Checklist

Use this checklist with [Deliverables](../catalogues/deliverables.md) and [Deliverable Systems](../catalogues/deliverable-systems.md). It helps identify everything required for the intended outcome, not only the code that implements it.

## Scope and responsibility

- [ ] Is the intended outcome and its real consumer or audience clear?
- [ ] Have the applicable deliverable systems and delivery constituents been identified: delivery, Pipeline Definition, Pipeline Execution, Environment Definition, service, consumer and testing?
- [ ] Is each deliverable assigned a responsible person, team, operator or external authority?
- [ ] Is each deliverable's execution environment, publication boundary or physical location recorded?
- [ ] Are dependencies between deliverables, systems and external organisations explicit?
- [ ] Are the pipeline definition codebase, environment definition codebase, service codebase, client codebase, test codebase and test context distinguished, even when they share a repository?
- [ ] Are Test Suites distinguished from the Test System that runs them, the Test Data they use, the Test Plan that scopes them and the evidence produced by execution?

## Service systems

- [ ] Are the service runtime and the service consumer treated as distinct systems with distinct execution environments?
- [ ] Are the delivery system and testing system described separately from the service runtime?
- [ ] Does the testing system qualify both the service and consumer systems, including their integration contract?
- [ ] Are versioning, compatibility, deployment order, rollback and recovery relationships defined?
- [ ] Are the systems' identities, permissions, data classifications, diagnostics and failure behaviour defined?
- [ ] Is the Pipeline Execution System distinguished from the Pipeline Definition System that it runs?
- [ ] Is the Environment Definition System distinguished from the environment instance it creates or changes?

## Data and content

- [ ] Are test data, reference data, migrated data and derived operational copies distinguished?
- [ ] Is there a neutral cross-system test context for scenarios that cross service, consumer and provider boundaries?
- [ ] Does the shared context have stable scenario identifiers, responsible authority, versioning, contribution rules, translators, generated representations and expected outcomes?
- [ ] Can each participating system translate the neutral context into its own inputs without making one system's schema the shared authority?
- [ ] Are development, integration, testing, qualification and recovery environments prevented from receiving production data, with synthetic cross-system context used instead?
- [ ] If an exceptional transformed dataset is proposed, is it formally approved as a new non-production dataset with authority, minimisation, de-identification, access, retention, deletion and audit evidence rather than treated as a copy of production?
- [ ] Are data authority, provenance, version, effective dates, validation, reconciliation, retention and deletion defined?
- [ ] Are textual templates, legal or policy content, help content and notifications owned, reviewed, versioned and localised where needed?
- [ ] Are branding and service-identity assets, including names, logos, marks, visual identity, attribution and publication rules, accounted for with a responsible authority, licensing, accessibility and retirement treatment?
- [ ] Are imagery, documents, audio, video, fonts, translations and accessibility alternatives accounted for, including licensing and classification?
- [ ] Are search and discovery content such as metadata, sitemaps, robots directives and canonical links included where relevant?

## Reachability and discovery

- [ ] Is the domain name registered to the correct responsible authority with renewal and recovery controls?
- [ ] Are DNS records, delegation, verification, certificates, trust chains and renewal responsibilities defined?
- [ ] Can intended people and discovery agents find and correctly identify the service?
- [ ] Are internal and external corporate sites, portals, directories, launchers and support surfaces identified as deliverables or integration dependencies?
- [ ] Are the responsible teams, contracts, publication process, update timing and failure behaviour of those corporate surfaces known?

## Delivery and operations

- [ ] Are source, pipeline definitions, environment definitions, packages, images, bundles, deployment configuration and migrations versioned and traceable?
- [ ] Are environment parameters, scopes, regions, accounts, subscriptions, identities, secret-store bindings and tool or runner versions controlled without copying secret values?
- [ ] Does each environment have a recorded baseline showing the definition revision, plan or preview, approvals, applied result, resource inventory, readiness evidence, drift and recovery point?
- [ ] Is the runner or execution support sufficient and recoverable, including its image, tools, identity, permissions, network access, logs, retention and failure behaviour?
- [ ] Are qualification results, acceptance evidence, release notes and compatibility decisions retained?
- [ ] Are monitoring, alerts, health and readiness definitions, runbooks, backup, restore, rollback and incident procedures delivered?
- [ ] Do incident procedures distinguish immediate recovery from learning, name decision authority and link corrective work to verification evidence?
- [ ] Are Support Manuals or Information, Operational Manuals or Information and Maintenance Manuals or Information delivered, owned, current and reachable by the people who need them?
- [ ] Are access policies, identity registrations, secret-store bindings and certificate responsibility delivered without copying secret values into ordinary configuration?
- [ ] Is the maintenance, update, deprecation and decommissioning path defined for every deliverable?
- [ ] Is there evidence that the delivered set is complete enough for a person, system, operator and recovery process to use the intended outcome?