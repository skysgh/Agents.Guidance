[Up](./readme.md)

# Security in Transit Checklist


Use this checklist when information, credentials, tokens, media, configuration or operational traffic crosses a device, network, process, provider or organisational boundary. Read [Design Standards](../../../../agents/conventions/development/design-standards.md), [Frontend Security](../../../../agents/conventions/development/frontend-security.md) and [External Dependencies](../catalogues/external-dependencies.md) first. The checklist is a design prompt, not a universal legal declaration.

## Media storage has two protection boundaries

Media or object storage commonly exposes separate controls for stored bytes and transferred bytes. Server-side or customer-managed encryption protects the object at rest. A secure-transfer or HTTPS-only requirement protects uploads and downloads while they cross the network. Both controls may need to be enabled explicitly at the provider boundary. A SAS or pre-signed URL controls scoped access; it does not replace HTTPS encryption.

- [ ] Is encryption at rest enabled for the media store, with the key and ownership policy recorded?
- [ ] Is secure transfer or HTTPS-only access enabled for the media store and its clients?
- [ ] Are uploads, downloads, provider callbacks and management operations prevented from falling back to unencrypted transport?
- [ ] Are SAS or pre-signed media links authorised, scoped to the smallest required operation and expired in 30 seconds or less? Any exception has an explicit owner, reason, compensating control and review date.
- [ ] Are protected and public media kept in separate containers, with public access enabled only for a deliberately approved publication container?

## Protect every connection

- [ ] Is every incoming, outgoing and internal connection identified, including browser traffic, service-to-service calls, administration, media transfer, queues, backups, DNS and delivery automation?
- [ ] Is TLS 1.3 the baseline for supported connections, with any TLS 1.2 use limited to a recorded legacy compatibility decision?
- [ ] Are endpoint identity, certificate trust, hostname validation and protocol or cipher configuration controlled rather than left to accidental provider defaults?
- [ ] Are certificates issued, stored, renewed, rotated, revoked and monitored by an identified owner and automated process where practical, using a short-lived certificate policy where the organisation or provider supports it?
- [ ] Are expiry alerts early enough for investigation and renewal, and is the failure behaviour tested when renewal or certificate validation fails?
- [ ] Is HSTS enabled for suitable web domains, with its scope and rollout consequences understood?
- [ ] Are outbound connections protected as carefully as inbound connections, including provider, partner, identity, storage and telemetry traffic?

## Protect browser and user interactions

- [ ] Are authentication cookies Secure, HttpOnly and appropriately SameSite? Secure means the browser sends the cookie only over HTTPS; HttpOnly prevents client-side JavaScript from reading it, reducing token theft through script injection; SameSite limits cross-site cookie sending.
- [ ] Is CSRF protection applied to every state-changing request authenticated by a cookie? SameSite reduces cross-site exposure but does not replace CSRF protection.
- [ ] For a browser SPA using OIDC, does OIDC establish and validate identity while the SPA-to-service interaction uses the protected cookie session only? Are access and ID tokens kept out of browser storage and URLs?
- [ ] Are bearer tokens kept out of URLs, localStorage, sessionStorage, IndexedDB, the Cache API, other browser-controlled or isolated storage, client logs and other places where an injected script or recipient could read them? Non-security preferences may use local storage where appropriate.
- [ ] Are trusted origins, CORS rules, redirects, framing, postMessage targets and external links explicit and restrictive?
- [ ] Are Content Security Policy, output encoding, Trusted Types where suitable, Subresource Integrity and third-party script decisions part of the security design?
- [ ] Are download, upload, media and notification links authorised, scoped and short-lived where the content is protected, with SAS or pre-signed links expiring in 30 seconds or less?
- [ ] Are request size, upload type, redirect target and external destination restrictions enforced at the responsible boundary?

## Protect identities and exchanged information

- [ ] Does every connection use an identified workload, user, device or provider identity with only the permissions needed for that exchange?
- [ ] Are credentials, tokens, signing keys and certificates prevented from appearing in source code, URLs, logs, telemetry, error messages or build output?
- [ ] Are message, media and API payloads classified, minimised and validated at both sides of the boundary?
- [ ] Are replay, duplication, ordering, correlation, freshness and expiry handled for messages or links that can be delivered more than once?
- [ ] Are partner and provider trust assumptions, authentication, authorisation, rate limits and failure policies recorded?
- [ ] Is sensitive information protected when it crosses queues, proxies, gateways, monitoring systems, support tools and delivery services?

## Protect domains and delivery paths

- [ ] Is domain registration protected by named ownership, strong authentication, change control, renewal monitoring and recovery contacts?
- [ ] Are DNS zones, records, delegation, signing and change access controlled and monitored?
- [ ] Are certificate authority accounts and issuance permissions separated from ordinary application access where appropriate?
- [ ] Are code repository, build pipeline, artifact or package registry, infrastructure automation and deployment credentials protected against unauthorised changes?
- [ ] Are build and deployment actions authenticated, reviewable, reproducible and traceable to the source and approval that produced the release?
- [ ] Is the path from source to deployed service protected against tampering, dependency substitution, secret leakage and unapproved release?

## Prove failure and change behaviour

- [ ] Are certificate renewal, DNS change, TLS negotiation, provider outage, identity expiry, token theft, revoked credentials and rollback scenarios tested?
- [ ] Are failures observable without exposing protected payloads, tokens, keys or unnecessary personal information?
- [ ] Is there a documented response when a certificate, domain, DNS record, credential, signing key or delivery account is compromised?
- [ ] Are transport configuration, cookie policy, origin policy, dependency changes and delivery permissions reviewed as part of change control?
- [ ] Are the owner, evidence, monitoring, recovery path and review date recorded for each important connection and trust boundary?

Related guidance: [Security at Rest Checklist](./security-at-rest.md), [External Dependency Checklist](./external-dependencies.md), [Design Standards](../../../../agents/conventions/development/design-standards.md) and [Frontend Security](../../../../agents/conventions/development/frontend-security.md).
