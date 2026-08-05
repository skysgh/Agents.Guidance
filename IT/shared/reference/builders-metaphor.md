[Up](./readme.md)

# Different Types of Builders


Different buildings need different builders. A person who is excellent at pouring the structure of a new high-rise is not automatically the right person to maintain every occupied room. A person who can keep an occupied building safe and comfortable is not automatically the right person to design its foundations. Both kinds of skill matter, and a serious building needs more than one kind of builder.

Software development is similar. "Developer" is a useful broad word, but it does not describe one uniform set of strengths. Being able to write code is only a starting capability. People who work with infrastructure, integrations, testing, maintenance and system creation all contribute to the building, but they do different work and see different risks.

These are role families, not sealed job titles. One person may work in more than one family, and a team may use different names. The point is to make the differences visible so that a team can ask the right person the right question.

## Builder roles

### DevOps and platform developers

DevOps and platform developers create infrastructure through code and configuration. They shape the environment in which services are built, deployed, observed, scaled, secured and recovered.

Their work includes pipelines, hosting, networking, identity integration, secrets handling, environments, telemetry and operational automation. They are concerned with whether the building can be assembled repeatedly, whether its utilities are available and whether the service can be operated after the original construction team has moved on.

### Integration developers

Integration developers connect systems that were created at different times or by different organisations. They work with integration configuration, transport, authentication, schedules, message handling, compatibility and data transformation.

Their work is not only wiring. Data often has to be translated between meanings, formats, identifiers, lifecycles and failure rules. An integration can be technically connected and still be wrong if it changes the meaning of a value or loses the history needed by the receiving system.

### Maintenance developers

Maintenance developers keep existing products useful, safe and understandable. They may work on products they did not create, use technologies they would not have chosen and investigate behaviour whose original reasoning is no longer recorded.

This requires a particular kind of skill and patience. A maintenance developer must read the building as it exists, identify which tenants and shared services depend on it, make a precise change and leave enough evidence for the next person. Their work protects continuity, compatibility, recovery and trust.

Maintenance is not lesser creation. It is creation under the constraint that people already rely on the result.

### Test developers

Test developers turn acceptance criteria, contracts, risks and failure expectations into automated evidence. They create tests that check whether the building behaves as promised, including when access is denied, information is invalid, a state transition is wrong, storage fails or an external dependency is unavailable.

They do more than check the happy path after development. They help make the expected behaviour precise, expose weak boundaries and preserve evidence when the system changes. A test developer may find that a building looks complete while one of its fire doors, tenant boundaries or recovery paths is not actually safe.

### System developers

System developers create systems and capabilities. They shape the overall structure, establish contracts, build objects and services, connect the parts into vertical slices and create the first working form of a new product or major capability.

Their work requires a broad view. They must make enough of the whole system real to discover which assumptions are valid, while keeping the foundations and boundaries clear enough for other builders to extend, operate and maintain it.

## Different strengths, shared responsibility

Each builder family can become highly skilled within its own work. That strength can create a blind spot when a person assumes that the risks of their work are the risks of the whole building.

A platform developer may see a service as a repeatable deployment unit. An integration developer may see it as one participant in a chain of systems. A test developer may see the claims that need evidence. A maintenance developer may see the tenants who cannot tolerate an avoidable interruption. A system developer may see the whole capability that still needs to become real.

None of these views is complete by itself. The design becomes stronger when the views meet at shared contracts, boundaries, evidence and lifecycle decisions. A role should not be asked to supply evidence that belongs to another role, and no role should be treated as the sole owner of the whole system merely because its work is the most visible at that moment.

## The builder's risk posture

Different work also creates different kinds of risk. A new system may be built before tenants move in. During that stage, the builders can sometimes stop and start whole services, replace large sections and test assumptions that would be unacceptable in an occupied building. The work is still hazardous, but the immediate impact of failure may be contained because no one depends on the unfinished service yet.

This is like builders pouring concrete while working on open platforms before the windows, services and tenant spaces are complete. They work in a higher physical and design hazard space, but they have more freedom to change the structure because occupancy has not begun.

Maintenance work happens in a different risk environment. The building is occupied. Tenants may rely on access, data, schedules, integrations and shared utilities every day. A maintenance developer therefore prefers controlled changes, narrow failure domains, compatibility, rollback and evidence before interruption. That caution is not a lack of imagination. It is respect for the people and systems already depending on the building.

Creation and maintenance both involve risk, but the risk is different. Creators can make larger structural changes while the service is unoccupied, but they must establish foundations that future occupants can trust. Maintainers make smaller, more carefully bounded changes while the service is occupied, but they must understand consequences that may be invisible in the original design. Platform, integration and test developers provide the surrounding construction, connections and evidence that allow both kinds of work to succeed.

The useful distinction is not "bold developers" versus "careful developers." It is whether the service is occupied, what can be changed safely, who relies on it and what evidence supports the decision.

## Building together

A system needs creators who can establish a coherent whole, maintainers who can preserve and improve it under real reliance, platform developers who can make its environment repeatable, integration developers who can connect it without losing meaning, and test developers who can provide evidence that its promises hold.

The practical question is not which developer type is the best. It is which kind of knowledge is needed for the decision in front of the team. Before changing an occupied service, ask a maintenance-minded person to identify existing consumers, compatibility obligations, recovery options and the smallest safe change. Before creating a new capability, involve people who can see the whole structure, its platform needs, its integrations and the evidence required to trust it.

These roles are all builders. Their strengths become most valuable when they are connected by a shared design rather than allowed to mistake one part of the building for the whole.

## Related guidance

- [The Building Metaphor](./building-metaphor.md)
- [The Structure Before the Feature](../../foundations/the-structure-before-the-feature.md)
- [What This Guidance Gives Each Stakeholder](../../foundations/what-this-guidance-gives.md)
- [Developer Architecture Route](../../../agents/conventions/development/guidance-for-developers.md)
