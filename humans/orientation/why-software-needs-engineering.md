# Why Software Needs Engineering

## Purpose

Software can look unlike a building. It is made from information, instructions and services rather than concrete, steel and glass. It can also be changed after people begin using it, often without anyone seeing the change happen. Those differences are real, but they can hide a similar responsibility: a service must be designed, built, operated and changed in ways that protect the people and organisations that depend on it.

This paper explores why software practice does not always provide the same preparation, incentives and independent assurance that building work does. It is not an argument that every service needs the process used for a high-rise. It is an argument that the engineering effort should match the service's life, reliance and consequences.

## How a reasonable team gets into trouble

Imagine a team asked to add a new screen to a service. The request is clear enough: show a person's information, let someone change it and make the result available to another part of the organisation. The team opens the framework documentation, follows the local example and produces a working screen. The result is visible, testable and easy to demonstrate.

The screen has also made several decisions that nobody set out to make. It has chosen the shape of the stored data, the boundary that owns the information, the rules for access, the meaning of a change, the way another system will read it and the evidence that will remain after the original team has moved on. Each choice may look harmless when viewed from the screen. Together they become the structure of the service.

The next request exposes the problem. A different user needs a different view. An operator needs to correct an earlier decision. A report needs historical information. A security review asks who may see a field. A service restart loses an assumption that existed only in startup code. The team can still make each change, but every change now has to negotiate with decisions that were made accidentally in the first screen.

No one needed to be careless for this to happen. The team was asked for visible progress, the product material showed how to use the tools and the whole service was larger than any one person's view. This is why software needs engineering beyond programming: the service needs someone to make the relationships and responsibilities deliberate before local solutions become the building everyone else must extend.

## How people learn

Many people enter software through programming, a local team or a product area. They learn how to solve the problems that are close to them, using the tools and habits that their colleagues already use. That experience can be valuable and practical, but it may expose someone to only one part of the system.

A computer science education can provide useful foundations, but it does not automatically provide experience of designing, operating and changing a large entrusted service. Programming is one part of software work. Whole-system design also requires attention to boundaries, contracts, data protection, security, failure, recovery, dependencies, evidence and the people who rely on the result.

This is not a criticism of people who learned on the job. It is a reminder that local experience is not the same as whole-system experience. A person may be excellent at building one room, service or feature and still need support to understand how that work affects the rest of the building.

## What vendor material teaches

Much of the material available to developers comes from vendors. Documentation teaches people how to configure a platform, use a framework, call an API or operate a product. That material is necessary construction material. It helps people become effective users of a product.

Vendor documentation is not usually intended to teach the larger responsibilities of the service being built. It may not explain where a capability should belong, which boundary should own a decision, how a failure affects other services, what must be recorded for later evidence or how the service should be changed after the original team has gone.

A team can therefore become very good at using products while still lacking a shared way to design the whole service. Product knowledge is useful, but it is not a substitute for system design, operational responsibility or independent challenge.

See [Vendor Material and Engineering Competence](./vendor-material-and-engineering-competence.md) for the commercial incentives behind product documentation, the difference between product fluency and system competence, and why out-of-the-box behaviour is only a baseline.

## Patterns are working tools

Software teams often know the names of patterns because patterns appear in interviews, courses and technical discussions. The names are less useful if they disappear when delivery begins. A pattern is not a decoration or a badge of sophistication. It is a record of a problem that has appeared before, the shape that helped solve it and the trade-offs that came with that choice.

Many bespoke solutions are not genuinely novel. They are local versions of familiar problems, created because no one stopped to search the pattern vocabulary or because visible delivery pressure made invention feel quicker. Such a solution may work for its first use while leaving ownership, coupling, failure behaviour, recovery and future change unexplained. The first team experiences a successful feature; later teams inherit a building with no account of why its rooms and routes were shaped that way.

Bespoke design still has a place. A domain may have unusual rules, constraints or evidence that an established pattern does not fit. The responsible sequence is to recognise the recurring problem, examine the patterns that might apply, adapt one when appropriate and make the reason for a departure explicit. A working result is necessary evidence, but it is not enough to show that the system is well designed.

## Patterns worth carrying

The team in the example does not need a catalogue of fashionable names. It needs a few dependable shapes that make the next decisions easier. Startup and discovery give the service a place to assemble its known participants, check its dependencies and make readiness or failure visible before it accepts responsibility for work. That is not incidental framework wiring; it is the construction and inspection of the building's shared services. See [Startup and Discovery](../../agents/conventions/foundations/startup.md).

A vertical slice gives one owned capability a complete route through the relevant boundaries, from its external entry to its application rules, data and effects. It lets the team build, test and operate a meaningful unit instead of scattering one capability across unfinished layers. A horizontal flow then gives a longer journey a known shape when several capabilities need to work together, such as preparing, submitting, assessing, approving, fulfilling and closing. The flow coordinates the journey without taking ownership of every rule inside each capability. See [Vertical Slices](../../agents/conventions/capabilities/slices.md), [Common Flows](./flows.md) and [Horizontal Flows](../../agents/conventions/capabilities/flows.md).

These patterns are useful because they give recurring problems somewhere to live. A team may adapt them to its domain, but it should be able to explain what the pattern protects, where responsibility sits and why a different shape is necessary.

## What speed and cost incentives change

Buildings, bridges and high-rises are designed with explicit safety margins because structural failure can cause immediate and severe harm. Software is often treated as cheaper and easier to change. Commercial pressure can therefore favour visible speed, with an assumption that the structure will be improved later if a problem appears.

That trade can be reasonable for a small, temporary or contained service. It becomes dangerous when the service is shared, public-facing or entrusted with records, money, access or essential decisions. By the time the weakness is visible, other capabilities and organisations may already depend on it. The later repair can then cost more, interrupt more people and require changes that are no longer reversible.

The issue is not that software should move slowly. Good engineering helps a team move quickly without making every later change more expensive. The issue is whether the pressure for an immediate visible result has removed the work needed to make future change safe.

## What assurance is missing

Software has no single universal equivalent of building codes, inspections and independent structural approval. Some areas have strong standards, regulated environments and formal assurance. Many commercial services rely more heavily on peer review, automated tests, security assessment, operational checks and the judgement of the people closest to the work.

Those practices can provide valuable evidence, but they are unevenly applied. A review may check style without checking system responsibility. A test may prove that a screen works without proving that access, recovery or data history is safe. A security check may find a configuration problem without asking whether the capability is owned by the right boundary. A team may approve its own assumptions because no independent view was available.

This is why evidence needs to be designed into the service. Contracts, boundaries, tests, security decisions, operational readiness, recovery plans and records of deliberate deferrals make more of the structure visible to people who were not present when it was created.

## The obligations are catching up

Legislation, regulation and accreditation are changing as software becomes responsible for more of people's records, money, access and essential services. The exact obligations differ by jurisdiction and sector, but teams increasingly need to understand how information is collected, classified, used, shared, tracked, retained, deleted and audited. Financial systems may have specific reporting and audit duties. Health, public-sector and other regulated services may carry additional requirements for access, history, safety and accountability.

Some older practices made sense in their original setting. An application might keep authorisation rules or decisions in its own tables because that was the available way to operate. A team might delete records because storage was expensive and retention had not yet become a visible obligation. Those choices cannot be treated as timeless engineering truths. Today, deletion rights may need to be balanced with duties to retain records for legal, financial, safety or audit reasons. Data minimisation and a right to request erasure do not mean that every record can be destroyed immediately; they mean that the purpose, authority, retention period, access, sharing and deletion path must be understood and recorded.

The consequences are no longer limited to an embarrassing incident or a difficult migration. Companies can face substantial fines, loss of accreditation, enforcement action, contractual consequences and loss of public trust when they mishandle protected information or cannot explain what their systems did. The responsibility is shared across the organisation, but software teams are part of the chain: a design that makes records impossible to classify, correct, retain, retrieve or delete safely creates risk that cannot be solved by a policy document after the fact.

The era in which a team could plead ignorance of these responsibilities is ending. That does not mean every developer must become a lawyer or compliance specialist. It does mean that the right specialists must be involved, the relevant obligations must be treated as design inputs and the service must retain evidence of the decisions made. The engineering effort should be proportionate, but the consequences of avoiding it are proportionate too.

## What responsible engineering adds

Responsible engineering is not the addition of ceremony for its own sake. It is the deliberate work needed to make a service understandable, dependable and able to change. The amount of work should match the service's scope and consequences, but the responsibilities do not disappear merely because the service is small or the deadline is close.

Responsible engineering makes these questions part of the design rather than discoveries made after failure. The team needs to know what the service promises, which boundary carries each responsibility and what must remain protected, accurate, available and recoverable. It needs to see its dependencies and failure conditions, decide what evidence will show that the service behaves as intended and distinguish what can safely wait from what must be understood now. It also needs to leave enough knowledge for the people who will operate and maintain the service after the original builders move on, including a way for someone outside the original team to challenge its assumptions.

These responsibilities do not require every service to become a high-rise. They help the team choose an appropriate structure rather than accepting a weak one by default.

## Returning to the building picture

The building comparison is useful because it makes hidden relationships easier to see. Foundations, formwork, shared services, safe routes, inspections and maintenance all point toward responsibilities that software can also carry. The comparison should then return us to concrete software decisions: contracts, boundaries, security, persistence, testing, operations, recovery and evidence.

The [Building Metaphor](../shared/reference/building-metaphor.md) explains those relationships. [The Structure Before the Feature](./the-structure-before-the-feature.md) explains how to decide what must be understood before construction and what can be built in stages. [Speed is not the same as agility](./design-before-build-and-wgf.md) explains why visible motion and safe adaptability are not the same thing.

## Related guidance

- [The Current State](./current-state.md)
- [What This Guidance Gives](./what-this-guidance-gives.md)
- [Design Before Build and WGF](./design-before-build-and-wgf.md)
- [The Building Metaphor](../shared/reference/building-metaphor.md)
