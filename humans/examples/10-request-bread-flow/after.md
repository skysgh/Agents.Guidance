[Up](../readme.md)

# After: Request Decomposed Through BREAD/ST

The team first recognises the journey as a managed Request capability with a BREAD/ST baseline.

## Parent Request flow

- **Browse** requests that the caller may see;
- **Read** one request through a permitted projection;
- **Edit** request information while it is editable;
- **Add** a new request;
- **Delete** or withdraw it according to its lifecycle; and
- **State Transition** from draft to submitted, then through review, approval, rejection, cancellation or closure.

Submit and approve are explicit state transitions. They are not hidden inside a general update method.

## Nested Evidence flow

Evidence is a separate capability connected to the Request:

- browse the evidence attached to a request;
- read the evidence metadata or a permitted content reference;
- add evidence;
- edit its description while permitted;
- withdraw or replace it; and
- move it through review or acceptance states.

The Evidence flow has its own access, classification, storage, retention and audit rules. The Request flow provides context but does not absorb those rules.

## Nested Comments flow

Comments are another connected capability:

- browse comments in the permitted conversation;
- read a comment;
- add a comment;
- edit or withdraw it under the comment policy; and
- record any moderation or visibility transition.

Comments are not simply extra Request fields. Their history, visibility and notification behaviour may require separate rules.

## What each role contributes

- business analysis explains what a Request, Evidence item and Comment mean;
- developers test whether the contracts and nested boundaries are implementable;
- testers check each flow, denied action, transition and failure path;
- operations checks upload, storage, notification and readiness behaviour; and
- architecture keeps the parent and nested flow shapes coherent.

## Reuse levels

At the first level, the team uses BREAD/ST to design this Request without inventing the journey from nothing.

At the second level, repeated behaviour such as loading, mapping, permissions, validation, state transitions and error handling can move into a reusable coordinator. The Request-specific calls remain visible in a small adapter.

At the advanced level, a Presenter can coordinate a read Player and a write Player, while a Broker manages the calls to the Request, Evidence and Comment capabilities. Common buttons, loading, errors and permission display can then be solved once for many BREAD/ST capabilities.

That advanced arrangement is not required before the first Request is built. It is a possible destination made visible by recognising the repeated structure early.

The result is a Request that can be built now, nested capabilities that have a clear place, and later reuse that does not require another team to guess what the original screen was trying to do.
