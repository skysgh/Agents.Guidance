# Dependency and Supply-Chain Conventions

Apply these conventions when adding, updating or distributing third-party dependencies, tools or build actions.

For the accessible explanation of dependencies as organisational commitments, read [The Current State](../../../humans/foundations/current-state.md), [Vendor Material and Engineering Competence](../../../humans/foundations/vendor-material-and-engineering-competence.md), [External Dependencies](../../../humans/shared/reference/catalogues/external-dependencies.md), [Deliverable Systems](../../../humans/shared/reference/catalogues/deliverable-systems.md), [Deliverables](../../../humans/shared/reference/catalogues/deliverables.md) and [Security in Transit Checklist](../../../humans/shared/reference/checklists/security-in-transit.md).

## Purpose

A dependency is part of the building, even when it arrives as a package or platform service. It brings behaviour, assumptions, updates, vulnerabilities, licensing obligations and operational work.

## The short version

Before adding a dependency, know what problem it solves, which boundary stewards it and what commitment the organisation is making by adopting it. Keep the dependency behind the boundary where its behaviour belongs, and check what changes when its version or provider changes.

In technical language, this is dependency and supply-chain management. The practical idea is that an import is also a maintenance and risk decision.

- Prefer platform or organisation-approved dependencies over novel packages.
- Dependency choices MUST be based on maintainability, extensibility, security, lifecycle, operating environment, organisational capability and service need; personal developer preference is not an architecture rationale.
- Use technologies from the organisation's approved, supported and non-sunset technology registry where one exists. An approved entry is an organisational capability decision, not proof that the technology fits every feature.
- Treat an unapproved dependency as a documented exception. Record the alternatives considered, reason, owner, support and skills plan, security and supply-chain review, operational consequences, exit conditions and review date.
- Record why each direct dependency exists and which boundary owns it.
- Pin or otherwise constrain versions so restores and builds are reproducible.
- Review transitive dependencies, native components, permissions, maintenance activity and licence obligations.
- Use trusted package sources and verify package provenance where the ecosystem supports it.
- Scan dependencies and build actions for known vulnerabilities and record the treatment of findings.
- Generate an SBOM for releasable products where the delivery platform supports it.
- Do not copy third-party code into the repository without recording origin, licence and update responsibility.
- Remove unused dependencies and avoid adding a package for trivial functionality already provided by the platform.
- Test dependency upgrades for security, compatibility, performance, startup and resource changes.
- Keep dependency credentials and registry tokens outside source control and build logs.

Do not allow a vendor, procurement preference or sales-led architecture exercise to define the technology registry without independent engineering review. A product may be approved only after its capability fit, total lifecycle cost, operational ownership, extensibility, portability, data consequences and replacement or exit path have been considered. No-code or low-code products are not exempt from these questions, and they must not displace an appropriate code capability merely because they are easier to demonstrate.

An unfamiliar persistence model or framework requires capability evidence before adoption. For example, replacing an established relational and Entity Framework capability with Marten and event sourcing is a material organisational commitment. The decision must account for event design and versioning, replay and projections, correction, reporting, retention, migration, operations, training, incident response and long-term support. A shorter first implementation is not enough justification.

See [Technology Registries](./registries.md) and the human explanation in [Vendor Material and Engineering Competence](../../../humans/foundations/vendor-material-and-engineering-competence.md).

A dependency is an operational commitment, not only an import statement.
