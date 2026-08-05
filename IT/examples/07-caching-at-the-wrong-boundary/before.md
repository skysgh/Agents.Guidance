[Up](../readme.md)

# Before: Caching at the Wrong Boundary

A team introduces an application-specific caching service around a library. That is a useful first boundary, but the cache is still controlled from the controller or application service.

The caller knows:

- the cache key;
- which cache library or wrapper method to call;
- how to decide whether the value is present or expired;
- how to load the value from a database or API;
- how to map the result for consumers; and
- what to do when the first invocation has no cached value.

The first invocation is where the mini-tornado appears. Several requests may discover the miss together. Each may call the source. One path may use a different key or timeout. Another may cache a presentation shape rather than a reusable value. A controller now contains transport handling, cache policy, loading, mapping and failure behaviour.

The cache library is not necessarily at fault. The application has placed a shared capability at a boundary that must know too much about it.
