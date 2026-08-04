# Selecting a Language and Framework

The architect lays out the logical shape of the building: its responsibilities, boundaries, capabilities, dependencies and qualities. The tech lead then chooses the construction methods and tools that can realise that shape. Language and framework selection is part of that technical-lead work. It is an architecture decision, not a personal preference or a late implementation detail.

A language is not good or bad in isolation. A framework is not a guarantee of quality. The decision depends on what the software does, where it runs, how often it runs, how much work it performs, who must support it and what evidence the organisation needs over its life.

Do not turn the decision into a slogan such as "this language can never serve a national system". Large systems can use more than one language. The important questions are whether the chosen runtime can meet the workload, security, availability, recovery, accessibility, maintainability and operating obligations, and whether the organisation can support it. A language that is suitable for a browser, a build tool or a bounded integration may be unsuitable for a continuously operated, CPU-intensive service path without further evidence.

## The execution boundary

First identify what is being built and where it runs:

- a browser application used by people;
- a continuously operated service that handles requests;
- a scheduled job or worker;
- a build, deployment or infrastructure tool;
- a one-off migration, analysis or test utility; or
- an integration adapter that calls or receives information from another system.

The same language may be reasonable in one boundary and poor in another. A browser language is not automatically a service language. A script that runs for a few minutes is not automatically comparable with a service that runs continuously under sustained load. An integration adapter may be mostly network-waiting, but a high-volume, security-critical or continuously operated integration still needs production-service evidence.

## Gather the decision evidence

Before selecting a language or framework, record:

- the representative workload, including CPU work, I/O, data size, concurrency, throughput, latency and memory;
- the execution frequency, uptime, availability target and recovery requirement;
- the security, privacy, data protection, accessibility and audit obligations;
- the libraries and frameworks needed for the actual capability, not only a demonstration;
- the team's implementation, testing, operations, security and recovery capability;
- the language and framework support lifecycle, update process, vulnerability response and licensing;
- the deployment environment, observability, scaling model, startup behaviour and resource cost; and
- the replacement, migration and exit conditions if the choice becomes unsuitable.

The decision must consider the whole service path. A fast language does not compensate for an inefficient query, an unsuitable provider or an unmeasured deployment. A productive framework does not remove the need for secure boundaries, tests, diagnostics and recovery.

## Count the whole cost, not only the first result

An unfamiliar or less structured choice can appear faster because a developer can produce a script or first endpoint immediately. That is one cost measurement, and sometimes it is the right measurement for a bounded tool. It is not the complete cost of a continuously operated service.

The longer-lived costs include:

- CPU and memory allocation for production instances;
- capacity headroom, horizontal scaling and redundancy;
- staging, test, performance-test and disaster-recovery environments;
- cloud, hosting, power and network consumption;
- monitoring, diagnostics, profiling and incident response;
- dependency, runtime and security maintenance;
- specialist support, training and recruitment; and
- migration or replacement when the original choice no longer fits.

These costs recur for as long as the service is operated. They also multiply when the service has several environments, regions, tenants, replicas or recovery copies. A choice that saves time at the beginning can therefore impose a larger infrastructure and operating commitment over the service's life. That commitment must be weighed alongside the immediate delivery benefit.

The available measurements show why this matters without becoming universal language laws. In one named CPU-bound `binary-trees` workload, a reported result took approximately 33 seconds in CPython 3.13 and 1.6 seconds in the compiled baseline, an approximately 21x difference. Other named comparisons reported approximately 29x and 32x differences between CPython and .NET for `nsieve` and `nbody`. Separate CPU-bound cases in the same reported study showed approximately 145x, 177x and 875x differences against compiled native baselines. These are workload measurements, not promises about every Python, .NET or JavaScript program.

The practical infrastructure implication is still material: if a representative implementation needs approximately 21x the CPU capacity to achieve equivalent throughput, the service may need roughly 21x the CPU allocation, subject to concurrency, I/O waits, memory pressure, startup behaviour, scaling design and platform pricing. That can affect not only the live service, but also non-production environments, capacity reserves, failover regions, performance testing and recovery exercises.

### An illustrative ten-year cost

Suppose one production server environment costs between $1,000 and $2,000 per month. Over ten years, that is approximately $120,000 to $240,000 for that environment before counting wider support and service costs.

If a measured workload required 21 equivalent environments to deliver the same capacity, the arithmetic would become approximately:

| Capacity assumption | Monthly infrastructure | Ten-year infrastructure |
| --- | ---: | ---: |
| 1 equivalent environment | $1,000-$2,000 | $120,000-$240,000 |
| 21 equivalent environments | $21,000-$42,000 | $2,520,000-$5,040,000 |

That does not mean a service will literally need 21 physical servers. Horizontal scaling, I/O behaviour, caching, workload shape and provider pricing may reduce or change the multiplier. Even a partial result can still be large: seven equivalent environments at the same rate would be approximately $840,000-$1,680,000 over ten years.

These figures are deliberately illustrative, not a cloud-provider quotation. They exclude storage, data transfer, observability, backups, support, security response, failover regions, non-production environments and the people needed to operate the service. Those omissions make the example a lower-bound warning, not an inflated total. The point is that a language decision can create a long-term infrastructure commitment measured in millions, even when the first script appeared to save a few days or weeks.

The decision should therefore ask two separate questions:

1. How quickly can the team produce the first useful evidence?
2. What infrastructure, operational and maintenance commitment will the organisation carry for every subsequent day of the service's life?

Immediacy is valuable. It must not silently consume the forethought needed to control the larger recurring cost.

## Repository defaults and their reasons

This repository uses the following defaults because they fit its current platform and service design. They are defaults, not permission to ignore evidence.

### C# and .NET for production service-side code

Use C# and .NET for the supported production service-side implementation unless an approved exception demonstrates that another runtime is materially more suitable. This default provides a supported typed platform for long-running services, modular application code, data access, diagnostics, testing and resource-efficient execution within the repository's existing conventions.

The choice still needs workload evidence. A .NET service can be poorly designed, over-sized or operationally unsafe. The language does not decide the domain model, boundary, security policy or storage design.

### TypeScript and Angular for browser applications

Use TypeScript rather than untyped JavaScript for browser application code, with Angular as the supported front-end framework unless a repository binding authorises another choice. TypeScript is compiled to JavaScript because browsers execute JavaScript; it is still valuable because its type checking catches many contract errors before runtime.

This browser default must not be confused with a default for production service-side code. A Node.js or other JavaScript service may be appropriate for a bounded workload or an approved exception, but its runtime, resource use, security, support and recovery evidence must be assessed as a service decision.

### Python for bounded and specialist work

Python is appropriate for development tooling, one-off migration or analysis scripts, test utilities, local automation and other bounded work that is not a continuously operated production service. It may also be the right choice for a specialist production workload when a mature Python library is materially safer or more capable than the supported alternatives.

A production Python exception must compare representative workload and concurrency with the supported .NET alternative. Measure CPU, memory, startup, throughput, latency, failure behaviour, dependency maintenance, isolation, scaling and observability. Record the owner, operating boundary, exit or review condition and the evidence supporting the decision.

### Pipeline and infrastructure development

Pipeline development has a different execution boundary from the service request path. Azure infrastructure may be expressed in ARM templates or Bicep. AWS infrastructure may be expressed in CloudFormation templates or authored through AWS CDK using TypeScript, JavaScript, Python, Java, C# or Go. PowerShell and Bash commonly coordinate provider tools, environments, approvals and evidence around those definitions.

TypeScript is prominent in AWS CDK because it was the first supported CDK language and the CDK itself is developed in TypeScript. That is not a general AWS requirement or a reason to make TypeScript the only pipeline language. The decision should fit the provider model, team capability, support lifecycle, security boundary, testing, rollback and recovery evidence. [Pipeline Development and Infrastructure as Code](../delivery/systems/pipeline/development-language.md) explains the distinction between declarative infrastructure, typed infrastructure programming and imperative orchestration.

## Recognise DevOps and integration engineering

DevOps, environment and pipeline engineers work on software that is executed by build systems, deployment systems, infrastructure automation and operators. Integration engineers work on software that crosses system boundaries, often through provider SDKs, queues, scheduled transfers or network protocols. Their work is still production engineering when it is trusted with release authority, credentials, regulated information or a critical operational path.

A bounded build script, migration tool or analysis utility can use a language that would not be suitable for the main request path. An integration adapter can use a language that fits its provider ecosystem and mostly I/O-bound workload. The decision must still account for retries, timeouts, idempotency, secrets, audit, supply chain, failure, recovery and the people who will maintain it.

Use the workload and lifecycle to distinguish these cases, not a claim that one group of engineers writes less important software or that a machine uses a tool only occasionally.

## Framework selection

Select a framework only after the language and execution boundary are understood. Check that it:

- supports the required interfaces, data access, identity, security and accessibility behaviour;
- has a credible maintenance and security-update path;
- works with the organisation's testing, diagnostics, deployment and recovery practices;
- has enough ecosystem and staff capability for the full service life;
- does not force provider or framework concepts into the logical domain model;
- has acceptable resource, startup and operational characteristics; and
- has a replacement, migration or exit path if its support or suitability changes.

A framework can provide mechanisms. It does not decide the service's responsibilities, data classification, lifecycle, external dependencies or quality evidence.

## Record the decision

The tech lead should record the selected language and framework, the execution boundary, the alternatives considered, the workload evidence, the operational owner, the support and security lifecycle, the deployment and recovery consequences, and any exception or review condition. Revisit the decision when the workload, boundary, platform, organisation, support capability or obligation changes.

The architect checks that the choice can realise the logical design. The tech lead checks that it is achievable and plots the implementation path. Developers implement within the chosen boundary and raise evidence when the choice no longer fits.

Related guidance: [Guidance for System Design Architects](./guidance-for-system-design-architects.md), [Guidance for Tech Leads](./guidance-for-tech-leads.md), [Guidance for Developers](./guidance-for-developers.md), [Quality Perspectives](../shared/reference/catalogues/qualities.md), [External Dependencies](../shared/reference/catalogues/external-dependencies.md), [Performance](../../agents/conventions/development/performance.md), [C# Conventions](../../agents/conventions/development/code-csharp.md), [TypeScript Conventions](../../agents/conventions/development/code-typescript.md) and [Python Conventions](../../agents/conventions/development/code-python.md).
