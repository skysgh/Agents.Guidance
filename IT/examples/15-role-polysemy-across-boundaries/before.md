[Up](../readme.md)

# One Role name hides four meanings

A team is asked to add an `Approver` role. The business means a person authorised to approve a particular request for an organisation. The access model means the context in which a user is acting for that organisation and request. The system means a configured permission grouping that allows an approval command. A developer also names a coordinator class `Approver` because it performs the application step.

The same word is used in requirements, route checks, database values, UI labels and code. A user who has the configured `Approver` permission can approve every request, even when they are not the authorised approver for the relevant organisation. Support cannot explain whether removing a user's role removes their business appointment, their access context or only a system permission. The class name is mistaken for evidence that the user has authority.

The team has reused one word, but the meanings have different owners, lifecycles and security consequences. A system role is not automatically a real-world authority, and a software component's role is not a person-held permission.

## Evidence

- `Approver` is used for business authority, access context, system permission and implementation behaviour.
- No contract states which resource, organisation and decision context an approval concerns.
- Permission assignment is treated as proof of appointment.
- Support cannot explain the effect of removing or changing a role.
- Tests cover an allowed permission but not the wrong organisation, request or authority context.
