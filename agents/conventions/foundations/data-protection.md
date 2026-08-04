# Data Protection Conventions

Apply these conventions wherever software collects, stores, transmits, displays, logs or deletes data.

For the accessible explanation of protection, trust and stewardship, read [Human Guidance](../../../humans/readme.md), [Deliverable Systems](../../../humans/shared/reference/catalogues/deliverable-systems.md), [Deliverables](../../../humans/shared/reference/catalogues/deliverables.md), [Deliverables Checklist](../../../humans/shared/reference/checklists/deliverables.md), [Legal and Regulatory Context](../../../humans/orientation/legal-context.md), [Security at Rest Checklist](../../../humans/shared/reference/checklists/security-at-rest.md), [Security in Transit Checklist](../../../humans/shared/reference/checklists/security-in-transit.md) and [Regulatory and Obligation Domains](../../../humans/shared/reference/catalogues/regulatory-obligations.md).

## Purpose

These rules help protect people, organisations and the trust placed in a service. They apply to business data as well as information that identifies a person or could harm someone if it were exposed, changed or retained for too long.

## The short version

Treat information as something entrusted to the system. First understand what it is, why it is needed, who may use it, how long it should remain and what must be recorded. Then choose storage, access, sharing and deletion behaviour that matches that understanding.

Security is not a final coat of paint. It shapes the foundations, rooms, doors, lifts and service routes of the building. Developers, testers, business analysts, operations and security roles each contribute evidence about what must be protected and how that protection can be checked.

In technical language, access decisions are often called authorisation and the description of how sensitive information must be handled is called classification. The concepts come first: protect the information and make the reason for access visible.

## Data handling

- Classify data before choosing storage, access, retention and transmission controls.
- Collect the minimum data needed for a stated purpose.
- Keep personal, confidential and security-sensitive data out of URLs, logs, telemetry and notification text unless explicitly required.
- Redact or pseudonymise data in diagnostics and test fixtures.
- Use synthetic or separately governed non-production data in development, integration, testing, qualification and recovery environments. Do not copy production data into those environments as a convenience.
- Encrypt sensitive data in transit and at rest using platform-managed controls where available.
- Keep secrets, credentials, tokens and encryption keys out of source code, configuration committed to Git and generated artefacts.
- Define retention, archival, export, correction, deletion or depersonalisation behaviour for each persisted personal-data category.
- Preserve required audit history without retaining unnecessary identifying data.

## Access and sharing

- Authorise every read and write at the owning boundary.
- Treat exports, caches, search indexes, backups and replicated stores as copies requiring the same protection as the source.
- Do not infer permission from possession of an identifier or link.
- Use short-lived, scoped access for temporary media or download links.
- Record access to sensitive data where accountability is required.

## Verification

- Test redaction, authorisation, retention and erasure behaviour.
- Test the cross-system test context translations and verify that non-production environments cannot receive unapproved production data.
- Verify that error responses and telemetry do not disclose protected data.
- Document the classification, stewarding boundary and lifecycle for new sensitive data.
