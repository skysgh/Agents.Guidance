# After: Caching as a Registered Object Capability

The platform defines an `ICachingObject<TValue>` contract for a cacheable capability. A caching object describes and owns the policy for its value:

- a stable cache key;
- the value type;
- expiry and refresh policy;
- the operation that obtains a fresh value;
- cancellation and timeout behaviour;
- retry and fallback policy; and
- classification and access requirements.

The object should know how to obtain its own value through a narrow injected provider or loader. It should not become a general application service, controller, database gateway or mapper for unrelated work. Its responsibility is the cacheable capability and its freshness policy.

At startup, contract-based discovery finds the caching objects and registers them in a cache registry. The registry owns the single shared entry for each key. A caching service resolves an object by contract or key and handles the common mechanics:

```text
consumer -> caching service -> cache registry -> caching object
                                      |
                                      -> current value or controlled refresh
```

The consumer does not know whether the value came from memory, a shared provider, a database, an API or a mapped projection. It asks for the cacheable capability. The registry and `CacheObjectService` provide one place for expiry, refresh coordination, cancellation, retries, observability and concurrency control.

The cache object can state whether it is suitable for:

- **in-memory caching**, where each process has a local, rebuildable copy; or
- **shared caching**, where multiple processes or instances need coordinated reuse.

The object expresses the requirement; the provider selection remains behind `CacheObjectService`. A downstream controller does not need to know whether the active provider is local memory, a distributed cache or a later provider. Shared caching is not automatically better: it adds network, availability, consistency, security and operational cost, so the object and startup policy must justify it.

The first invocation is now designed rather than improvised. A miss can use single-flight refresh so concurrent callers share one load. Refresh failure can follow an explicit fallback policy. A cache key can include the required context and classification. Startup diagnostics can show which cache objects were registered and which provider is active.

This is object-oriented design used properly: the object represents one cacheable capability; the registry manages the collection and shared lookup; the service coordinates access; the consumer remains independent of storage and loading details. The value is not that every object manages the whole world. The value is that each object manages the policy and refresh behaviour for the capability it represents.

Caching is still not automatic infrastructure. Introduce it when latency, load, availability, provider cost or a deliberate resilience boundary justifies it. When it is introduced, define invalidation, stale-value tolerance, stampede protection, security context and observability rather than treating a cache hit as the whole design.
