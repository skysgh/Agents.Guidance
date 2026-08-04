# External Dependencies Checklist

Use this checklist with [External Dependencies](../catalogues/external-dependencies.md).

- [ ] The dependencyÔÇÖs purpose and boundary are described in plain language.
- [ ] The responsible team, provider or organisational boundary is known, without making uncertain ownership a reason to stop the design.
- [ ] The contract, data classification, authority and lifecycle are recorded.
- [ ] Required, optional, authoritative and derived dependencies are distinguished.
- [ ] Startup, readiness, timeout, retry, degradation and recovery behaviour are defined.
- [ ] Authentication, authorisation, secret handling and credential rotation are defined.
- [ ] Integration credentials are stored only in a managed protected secret store, never in ordinary system configuration, source control, generated artifacts, URLs or logs.
- [ ] Pipeline and workload identities retrieve secret values only when required, while humans are prevented from retrieving or copying production secret values.
- [ ] Copies in caches, indexes, queues, reports, archives, exports and backups are included where relevant.
- [ ] Reconciliation, replay, duplicate handling and backfill are defined for deferred or derived interactions.
- [ ] The dependency can change or fail without leaking provider-specific meaning into the logical model.
- [ ] The service does not depend on private tables, classes or undocumented behaviour.
