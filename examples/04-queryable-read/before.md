# Before: Queryable Read Rejected or Exposed Directly

A team needs a list that will eventually serve screens, exports and integrations. They reject `IQueryable` because exposing database entities would be unsafe, then add a fixed endpoint returning a collection.

A later consumer needs different filtering, projection or paging. Another endpoint is added. The number of shapes grows, and each one repeats some access or mapping decision.

The opposite mistake is also common: expose the entity query directly and call the result flexible. Internal fields, relationships and persistence assumptions now form an accidental public contract.

Both choices confuse a safe boundary with the query capability itself.
