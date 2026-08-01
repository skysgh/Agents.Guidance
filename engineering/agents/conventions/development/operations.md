# Operations Conventions

Apply these conventions to deployable services, workers, scheduled jobs and infrastructure integrations.

For the accessible explanation of operations as the part of the building that keeps it safe after people move in, read [Human Guidance](../../../humans/readme.md).

## Purpose

Operations is the part of the building that keeps it safe after people move in. It covers readiness, health, shutdown, dependency failure, diagnostics, recovery and the information needed by the people supporting the service.

## The short version

A service is not complete when its happy path works once. It is complete when the team can explain how it starts, how it reports readiness, what happens when a dependency is slow or unavailable, how work is retried or stopped, and how an operator restores service.

Developers define safe behaviour. Testers exercise failure and recovery. Operations checks whether the signals and runbooks are useful. Security checks that diagnostics do not expose protected information.

## Service behaviour

- Define startup, readiness, liveness, graceful shutdown and dependency-failure behaviour.
- Propagate cancellation and enforce timeouts at every external boundary.
- Use retries only for transient failures. Apply bounded exponential backoff and jitter.
- Make retried commands idempotent or attach an idempotency key.
- Do not retry validation, authentication, authorisation or permanent data errors.
- Bound queues, request bodies, concurrency, memory and untrusted input.
- Define overload behaviour. Reject or defer work deliberately rather than allowing unbounded growth.
- Treat poison messages as an explicit recovery path with visibility, quarantine and replay rules.

## Diagnostics

- Emit structured logs with correlation, operation, actor, resource and outcome fields where appropriate.
- Never log credentials, tokens, secrets or unnecessary personal information.
- Provide metrics for throughput, latency, failures, saturation, dependency health and resource use.
- Trace cross-service operations without copying sensitive payloads into spans.
- Make failure messages useful to operators without exposing internal or private data to callers.

## Recovery

- Document the expected failure mode for each required external dependency.
- Define whether the service fails closed, fails open, degrades, queues or becomes read-only.
- Test dependency outage, timeout, retry exhaustion, restart and recovery behaviour.
- Provide an operator-visible runbook for incidents that can reasonably recur.

A service is not operationally complete merely because its happy path works.
