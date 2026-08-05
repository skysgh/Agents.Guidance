[Up](../readme.md)

# Before: Screen Request Becomes Storage Design

A ticket asks for a page to manage providers. It names fields visible on the page and a few buttons.

The team builds a controller shaped around the page, a service shaped around the controller action and a database entity shaped around the form. The first version works.

The hidden decisions are not discussed:

- whether a provider is a reusable reference, a managed relationship or an external participant;
- who may see, change, approve or retire it;
- which states matter beyond the first screen;
- which fields are presentation convenience rather than durable meaning;
- which future queries and integrations need a stable projection; and
- which relationships should exist but are not in the first release.

The screen has become the conceptual model and the conceptual model has become the storage schema. A later consumer now needs a second endpoint, a migration or a workaround around the first screen's assumptions.

The issue is not that anyone failed to work hard. The ticket supplied a useful business starting point, but the system needed a design step between business request and storage shape.
