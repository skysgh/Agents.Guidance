# Data Protection Conventions

Apply these conventions wherever software collects, stores, transmits, displays, logs or deletes data.

## Data handling

- Classify data before choosing storage, access, retention and transmission controls.
- Collect the minimum data needed for a stated purpose.
- Keep personal, confidential and security-sensitive data out of URLs, logs, telemetry and notification text unless explicitly required.
- Redact or pseudonymise data in diagnostics and test fixtures.
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
- Verify that error responses and telemetry do not disclose protected data.
- Document the classification, owner and lifecycle for new sensitive data.
