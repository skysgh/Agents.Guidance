# Dependency and Supply-Chain Conventions

Apply these conventions when adding, updating or distributing third-party dependencies, tools or build actions.

For the accessible explanation of dependencies as organisational commitments, read [The Current State](../../../humans/orientation/current-state.md).

## Purpose

A dependency is part of the building, even when it arrives as a package or platform service. It brings behaviour, assumptions, updates, vulnerabilities, licensing obligations and operational work.

## The short version

Before adding a dependency, know what problem it solves, which boundary stewards it and what commitment the organisation is making by adopting it. Keep the dependency behind the boundary where its behaviour belongs, and check what changes when its version or provider changes.

In technical language, this is dependency and supply-chain management. The practical idea is that an import is also a maintenance and risk decision.

- Prefer platform or organisation-approved dependencies over novel packages.
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

A dependency is an operational commitment, not only an import statement.
