# Performance Conventions

Apply these conventions to production services, workers, data access, browser applications and resource-sensitive tooling.

For the accessible explanation of performance as a system quality and delivery concern, read [Quality Perspectives](../../../IT/shared/reference/catalogues/qualities.md) and [Guidance for Tech Leads](../../../IT/foundations/guidance-for-tech-leads.md).

## Define the target

Before optimising, record the representative workload, data size, concurrency, throughput target, latency target and resource budget. Use percentile latency, including p95 and p99, rather than averages alone.

## Measure

- Measure CPU, memory, allocation, I/O, startup, throughput, latency and saturation.
- Use production-like data shape and realistic dependency behaviour.
- Compare alternatives on the same hardware, runtime versions, configuration and workload.
- Repeat measurements and record variance, environment and implementation details.
- Benchmark the complete service path when making capacity claims; a language microbenchmark is not a deployment plan.
- Establish regression thresholds for important workloads.

## Resource discipline

- Fix algorithmic, query and allocation problems before adding infrastructure.
- Bound work and input size at trust boundaries.
- Do not add caching, parallelism, batching or replicas without measuring their cost and benefit.
- Treat memory pressure, garbage collection, connection pools and queue growth as performance behaviour.
- Re-measure after changing runtime, libraries, persistence, deployment or concurrency settings.

Report both the improvement and the remaining bottleneck.
