# Dependency and Supply-Chain Conventions

Apply these conventions when adding, updating or distributing third-party dependencies, tools or build actions.

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
