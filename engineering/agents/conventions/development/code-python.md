# Python Code Conventions

## Scope

Do not use Python for code intended to run as part of a production service or production request path unless there is no adequate alternative. An exception requires an explicit decision that records the reason, the operational boundary, the resource impact, the support owner and the exit or review condition.

Python remains appropriate for development tooling, one-off migration or analysis scripts, test utilities, local automation and other code that is not a continuously operated production service. Production use may also be justified for a specialist workload when a mature Python library is materially safer or more capable than the available alternatives, but that is an exception to the default and must be measured.

## Resource rationale

The policy is based on resource efficiency, not dislike of Python. CPython executes Python bytecode through an interpreter, while .NET languages are compiled to Intermediate Language and the CLR Just-In-Time compiles that code to machine code. For CPU-bound application logic, this can create a substantial throughput and memory cost difference.

Do not present a fixed multiplier as a language law. However, the "21 times" figure is supported as a measured result in a named workload: Cemrehan Cavdar's 2026 [Optimization Ladder](https://cemrehancavdar.com/2026/03/10/optimization-ladder/) reports approximately 33 seconds for CPython 3.13 versus 1.6 seconds for the compiled baseline on the Computer Language Benchmarks Game `binary-trees` case. The same report gives approximately 177x for `n-body`, 875x for `spectral-norm` and 145x for `fannkuch-redux` in its reproduced CPU-bound cases. Those comparisons are against compiled native implementations, not a universal Python-versus-.NET law.

Independent data also shows that the difference can remain material in a .NET comparison. The [Programming Language Benchmarks](https://programming-language-benchmarks.vercel.app/csharp-vs-python) comparison, generated on a four-core AMD EPYC host, reports CPython 3.13.5 at 2,989 ms versus .NET 9 at 94 ms for one `nbody` input, approximately 32x, and 2,819 ms versus 98 ms for one `nsieve` input, approximately 29x. The same page reports much smaller differences for HTTP and JSON workloads. This is why the policy is workload-specific but still strict for production service code.

The correct response to "other organisations use Python" is that many workloads are I/O-bound or delegate their hot path to native libraries, and therefore do not show the CPU-bound ratios above. That may make Python the right choice for a particular workload. It does not establish that Python has an acceptable resource cost for this framework's service workload. The exception must be demonstrated with a representative service benchmark.

The operational implication is still important: if one implementation requires approximately 21 times the CPU capacity of another for the same measured workload, the service may need roughly 21 times the CPU allocation to achieve equivalent throughput, subject to concurrency, I/O waits, memory pressure, startup behaviour and platform pricing. Resource multiplication must be measured, not assumed.

## Production exception checklist

Before approving Python in a production path:

- identify why the supported .NET implementation is inadequate;
- benchmark representative workload and concurrency against the proposed alternative;
- measure CPU time, memory, startup time, throughput, latency and failure behaviour;
- include dependency, interpreter and native-library maintenance in the operational plan;
- define isolation, scaling and observability boundaries; and
- record the decision and a review date.

## Sources

- [Python FAQ, What is Python?](https://docs.python.org/3/faq/general.html): the Python documentation describes Python as an interpreted language.
- [Microsoft, What is managed code?](https://learn.microsoft.com/en-us/dotnet/standard/managed-code): Microsoft explains that the CLR compiles .NET Intermediate Language to machine code using Just-In-Time compilation.
- [Computer Language Benchmarks Game](https://benchmarksgame-team.pages.debian.net/benchmarksgame/): a comparative benchmark source. Its [measurement method](https://benchmarksgame-team.pages.debian.net/benchmarksgame/how-programs-are-measured.html) explicitly warns that source code, implementation choices, hardware and measurement conditions matter.
- [AWS Well-Architected Cost Optimization](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html): resource consumption and cost are architectural concerns.
- [Azure Well-Architected Cost Optimization](https://learn.microsoft.com/en-us/azure/well-architected/cost-optimization/): cost and resource efficiency should be considered throughout the workload lifecycle.
