# Phases, Roles and Stakeholders

## Purpose

Imagine a building whose architect, funder, construction team, occupants, operators and maintenance staff are all asked who is responsible for a leaking service. They may give different answers because they are talking about different responsibilities. One person designed the route, another installed it, someone else operates the building and a tenant depends on the water arriving. The disagreement is not solved by finding a single permanent owner. It is solved by understanding when the responsibility applies, what kind of work it involves and who is affected by the result.

A dependable service has the same shape. Work happens at different times, people contribute different knowledge and other people may depend on the result without building or operating it themselves. **Phases** describe when responsibility changes. **Roles** describe the kinds of work and knowledge contributed. **Stakeholders** describe who depends on the result, funds it, governs it, uses it or is affected by it.

One person or team may contribute in more than one category. The categories still matter because they help the team ask who is responsible for a decision, when that responsibility applies and who needs evidence about it.

## Phases

Phases are a sequence of responsibility, not sealed boxes. Design decisions continue into development, development can begin before every design question is closed, and operation may begin while later capabilities are still being developed.

### Design and financing

Owners, funders, architects, engineers and specialist advisers shape what the service is for, what it must support and what can responsibly be afforded. They identify constraints, intended outcomes, major dependencies, risks and the structure that later work must fit.

An architect may rely on a builder as a consultant because builders understand materials, construction methods, sequencing and practical constraints. That consulting builder is not necessarily the builder who later performs the construction work.

In software, this phase includes understanding the service's purpose, consequences, boundaries, obligations, lifecycle and intended capabilities. It does not require every implementation detail to be complete before learning begins.

### Development and delivery

Construction and delivery specialists turn the design into a working system of structure, services, connections and evidence. They make the foundations, install the routes, connect the utilities, test the boundaries and resolve details that allow the building or service to function.

In software, development creates the complex system that supports the business or service. It is not only the creation of the visible experience that customers were promised. The work also includes contracts, security, persistence, mappings, startup, testing, diagnostics and recovery where the service requires them.

### Operations

During operations, the service is offered from the completed or partially completed structure. Operators, tenants, customer-facing staff and support teams use the structure and its services to provide the intended experience.

Their responsibilities differ from those of the people who designed or constructed the service. They may identify failures, operational constraints or needed changes that return to design or development.

### Maintenance and change

Maintenance continues while the building or service is occupied. Maintenance personnel clean, repair, inspect, renew and preserve the building. Software maintenance means understanding what people already rely on, making controlled changes, preserving compatibility and keeping the service trustworthy.

Maintenance is not evidence that the original design failed. It is a normal lifecycle responsibility. The risk comes when maintenance has no usable evidence of the decisions, boundaries and assumptions that shaped the existing service.

## Role families

Role names vary between organisations. The useful question is not whether someone has a particular job title, but what responsibility they carry in the current phase. Design and advisory roles shape purpose, constraints, structure, affordability and specialist requirements. Build and delivery roles assemble the structure, services, connections, implementation and evidence. Operating and support roles provide the service, respond to users, observe behaviour and manage operational conditions. Maintenance and change roles preserve compatibility, repair faults, renew dependencies and extend the service without losing its existing responsibilities.

The same person may work in several families. A developer may contribute to design, implementation and maintenance. An operations specialist may advise during design and later operate the result. Naming the responsibility for the current work is more useful than treating the role name as permanent.

## Stakeholders

Stakeholders are separate from phases and roles. They are the people and organisations who use the service, depend on its results, own or fund it, regulate it or carry responsibility for what happens through it.

A customer may describe the experience they need without building the structure that makes it possible. A funder may define an outcome without operating the service. A regulator may require evidence without implementing the feature. An operator may depend on a safe workflow without owning the contracts or persistence behind it.

The categories can overlap, but they should not be collapsed. Keeping them distinct makes it possible to ask who is affected if something fails, who owns the decision or boundary, which role has the knowledge to carry the work and during which phase the responsibility must be exercised and evidenced.

## Handoffs and overlap

A handoff is not a transfer of all understanding. The next phase needs enough design, evidence and operational knowledge to continue safely. The previous phase remains relevant when its decisions constrain later changes.

Before a capability moves between phases, the people involved need to understand what is complete and what is deliberately deferred, which boundary owns each unresolved decision, what users, operators and maintainers need to know, which tests and operational checks provide evidence, and how later changes return to design without bypassing the responsible boundary.

This is why phases should be separate from sequence. Phases describe when responsibility changes. Sequence describes the order in which a particular structure or capability is designed and built within those phases.

## Questions to carry forward

When a service or capability is changing, pause long enough to ask which phase the work serves, which role family has the knowledge and responsibility to do it, which stakeholders depend on the result, what must be handed to the next phase and what evidence will let a different person operate, maintain or change it later.

These questions keep lifecycle responsibility visible without pretending that every organisation uses the same job titles or phase names.

## Related guidance

- [The Structure Before the Feature](./the-structure-before-the-feature.md)
- [What This Guidance Gives](./what-this-guidance-gives.md)
- [Systems Within Systems](./systems-within-systems.md)
- [What Architects Need to Know](./architects-need-to-know.md)
- [What Tech Leads Need to Know](./tech-leads-need-to-know.md)
