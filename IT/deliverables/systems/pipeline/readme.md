[Up](../readme.md)

# Pipeline System


The pipeline system turns reviewed source, dependencies and configuration into qualified, identifiable and deployable deliverables. It may include source control, build agents, static analysis, security scanning, test execution, artifact and package registries, infrastructure automation, approvals and deployment promotion.

The service is working in one environment, but nobody can say which source revision produced it. A security scan ran against one artifact and deployment used another. The release may still appear successful to its users, yet the organisation cannot give a trustworthy account of what is running or how to recover it.

This route is now the reader foundation for a system that the repository has not yet developed with one project's concrete evidence. The absence of a project-specific pipeline does not make the pipeline optional: source provenance, artifact integrity, environment separation, secret handling, approvals, rollback, recovery and release evidence remain delivery responsibilities.

## The pipeline runs more than service code

A delivery flow may retrieve a service codebase, a client codebase, test code and test context, pipeline definitions and environment definitions. The Pipeline Execution System runs or applies those codebases and produces artifacts, test evidence and changed environments. The environment definition code is not the environment, and the pipeline definition is not the runner that executes it.

The [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md#delivery-system-constituents) catalogue gives these delivery constituents names. The [Deliverables](../../../shared/reference/catalogues/deliverables.md#codebase-and-definition-deliverables) catalogue describes the codebases as deliverables. Keeping the code, runner, resulting environment and hosted systems distinct gives each one a responsible boundary for change, security and recovery evidence.

The Pipeline Execution System also protects the change paths of those codebases. Branch protection, review requirements, required quality checks, signed or identifiable artifacts and controlled promotion keep an unqualified change from silently becoming a released Service or Client system. The pipeline enforces the agreed delivery conditions; it does not decide the business meaning or acceptance authority itself.

## The pipeline lifecycle

[Pipeline Development and Infrastructure as Code](./development-language.md) gives the reader entry into the languages and tools that express this lifecycle: declarative resource definitions, typed infrastructure frameworks and PowerShell or Bash orchestration.

The pipeline turns an intended change into an identifiable change that can be introduced, examined and recovered:

```text
source and dependency selection
	-> build and static qualification
		-> security and supply-chain checks
			-> test execution and evidence collection
				-> artifact packaging and provenance
					-> environment promotion and approval
						-> deployment and readiness verification
							-> release observation, rollback or recovery
```

The pipeline does not own the business meaning of the change. Product, architecture, service, client, testing, security, operations and change authorities supply the conditions that the pipeline preserves and makes visible.

## What the pipeline must make visible

A useful account of a material release identifies the source revision, dependency set, build inputs and configuration used. It connects the release to the person, service identity or approved process that initiated and approved promotion, and to the artifact identity, integrity, provenance and destination environment. The tests, scans, reviews, exceptions and evidence associated with the artifact remain visible, as do the secrets, credentials, permissions and environment boundaries used without exposing their values. Readiness, migration, compatibility, communication and rollback conditions belong in the same account. So does the behaviour expected when the pipeline, provider, artifact store, deployment target or release dependency is unavailable, together with the way an operator can determine which version is running and recover to a known safe version.

The pipeline evidence is not the same as service evidence. A pipeline can prove which artifact was deployed; the service and client must still prove that the delivered behaviour and qualities are appropriate in their own environments.

## Pipeline boundary and security

The pipeline is a privileged system. Its source control, build agents, artifact stores, package feeds, infrastructure automation, environment credentials and approval controls must be treated as protected assets. A successful build does not prove that the source, dependency or artifact path was trustworthy.

Production secrets belong outside source, logs, artifacts, test output and ordinary configuration. Development, qualification and production identities and environments remain distinct. Dependency changes are reviewable. Publishing, promotion, approval, deployment, rollback and pipeline-definition changes have bounded authority. Exceptions have a named responsible person or team, a consequence and a review condition.

## Handoffs

Product and Sponsor roles provide the commitment, scope, risk and release decision context. Architecture and technical leadership provide boundaries, dependencies, compatibility and readiness conditions. Client and service developers provide buildable changes, migrations, configuration needs and diagnostics. The Testing System provides qualification results and retained evidence. Security, privacy, records, operations and change authorities provide their controls and acceptance conditions. The pipeline assembles, protects, promotes and records the resulting delivery; it does not silently decide that an unmet condition is acceptable.

## Project-specific evidence still needed

This route gives the system a durable responsibility model. A real service still needs its own pipeline evidence: supported environments, deployment topology, identity model, approval authority, artifact registry, dependency policy, migration path, rollback procedure, monitoring and recovery exercise. Those project-specific decisions and records are what turn the general route into credible evidence for a particular service.

## Current entry points

[Pipeline Development and Infrastructure as Code](./development-language.md) explains the languages and tools used to declare resources and coordinate delivery. [Deliverables](../../readme.md) explains how delivery joins software with data, configuration, infrastructure, dependencies, supporting material, evidence and responsibility. The [Delivery System](../../../shared/reference/catalogues/deliverable-systems.md#1-delivery-system) describes the system boundary, while [Deliverables](../../../shared/reference/catalogues/deliverables.md) describes the wider material that accompanies a delivered outcome. [Operations and delivery conventions](../../../../agents/conventions/development/operations.md) provide task-time rules where the pipeline or deployment path is involved.

A fuller project route belongs here when there is concrete material to explain the actual source-to-release path, environments, supply-chain controls, deployment recovery and responsible boundaries without pretending that a generic pipeline is the organisation's actual one.
