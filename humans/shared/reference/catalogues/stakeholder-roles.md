# Stakeholder Roles

A [stakeholder](../glossary.md#stakeholder) is a person, group, organisation or connected system that can affect the service, is affected by it, depends on its result, supplies knowledge or evidence, or has authority over an obligation the service must fulfil. A [role](../glossary.md#role-is-polysemous) is a responsibility perspective: the kind of knowledge, decision, work or evidence a participant contributes.

A role is not necessarily a job title, a team, a person or a system boundary. One person may carry several roles. One role may be shared by several people or teams. A title may cover different responsibilities in different organisations. The useful question is therefore not "Who has the right title?" but "Which responsibility is present, who can represent it, what authority does that representative have and what evidence can they provide?"

This catalogue gives a Stakeholder Analyst (Business Analyst), architect, technical lead, developer or reviewer a way to identify the people and groups whose knowledge is needed. It does not turn every role into a mandatory meeting, a fixed organisation chart or a promise that one person can supply every answer.

Analysis must cover every material stakeholder and user group, including people who do not use the service directly and specialist roles that keep it safe and dependable. Depending on the service, this may include consumers, represented subjects, beneficiaries, providers, support, Operations, Maintenance, Monitoring, Change Control, Security, Privacy, Records, assurance, suppliers and connected systems. The analyst records which perspectives are represented, which are missing and who has authority to resolve each question.

## From stakeholder to SME to design evidence

A Stakeholder Analyst (Business Analyst) helps a team discover whose knowledge is needed. The analyst identifies stakeholder and user groups, finds suitable Subject Matter Experts (SMEs), checks that the selected people are representative and elicits the concepts, desires, needs, constraints, decisions and consequences that those groups can explain.

**Elicit** means drawing out knowledge that may be tacit, distributed or difficult to express. An SME may know what a decision means in practice without already having a complete requirement. They may describe exceptions, workarounds, evidence, timing, hand-offs, language, risks or consequences that a short request does not mention. Elicitation is not simply asking someone to approve a screen. It is a structured effort to understand the world the service must support.

The analyst helps turn that material into definitions that the wider team can examine. A definition may describe a concept, actor, relationship, state, rule, capability, obligation, acceptance condition, data item, outcome or measure. These definitions are requirements when the organisation adopts them as something the service must satisfy, but the initial desire and the final requirement should not be treated as identical. A desire may conflict with another obligation, exceed the available authority, be unsafe, be unaffordable or need further clarification.

The path is collaborative:

1. Stakeholders explain the work, outcomes, obligations and consequences they recognise.
2. The Stakeholder Analyst identifies representative SMEs across the relevant stakeholder and user groups and elicits the conceptual language and distinctions behind those accounts.
3. The Stakeholder Analyst records and tests definitions, including conflicts, assumptions, exclusions and unresolved questions.
4. Architects abstract those definitions into a coherent system design with explicit boundaries, dependencies and responsibilities that can survive changes in the business and organisation.
5. Technical leads recognise that abstraction, check whether it is achievable with the available team, technology, dependencies and constraints, and plot the path through delivery boundaries, contracts, readiness decisions and logical building blocks.
6. Developers implement the prepared contracts and behaviours, while testers, operations, security, assurance and other specialists provide evidence that the solution remains true and dependable.

No stage is a one-way translation that removes the earlier participants. Developers may discover that a definition cannot be implemented safely. Testers may expose an ambiguity. Operations may identify a lifecycle condition. The BA and relevant SMEs then help refine the meaning, while the architect protects the wider relationships and obligations.

### The architect is not the universal IT SME

The architect is an integrator and facilitator of specialist knowledge, not the organisation's default representative for every technical responsibility. An architect may map the relationships, identify missing input, ask useful questions and make the resulting boundaries visible. That does not make the architect an SME for Operations, Maintenance, Monitoring, Change Control, Security, Privacy, Records, assurance, Support, Supplier or Delivery responsibilities.

Those specialist roles must supply or validate their own operational knowledge, authority, constraints, failure consequences and evidence. A person may genuinely hold more than one role, but that must be true in the organisation and supported by evidence; title proximity or architectural seniority is not representation. Unavailable specialist input is an explicit gap, assumption or risk, not permission for the architect to silently invent the answer.

## How to represent a role

When a role matters to a capability, record more than its name. Identify:

- **Purpose:** what responsibility the role carries in this service or decision.
- **Knowledge:** what the role knows from practice, policy, technical operation, lived experience or formal authority.
- **Authority:** which decisions the role may make, recommend, approve, reject or merely inform.
- **Inputs:** what information, evidence or constraints the role needs.
- **Outputs:** what definition, decision, action, record or evidence the role contributes.
- **Consequences:** who or what is affected when the role's responsibility is missed or misunderstood.
- **Boundaries:** what the role should not be expected to own merely because it is nearby.
- **Representation:** which people, teams, communities or systems the SME represents, and where that representation may be incomplete.

This prevents vague statements such as "works with stakeholders" from hiding the real contribution. A useful description says what the role knows, what it decides, what it supplies, what it receives and where its responsibility ends.

## Business, product and decision roles

### Sponsor

The sponsor provides organisational backing for the work. They help establish why the service matters, what outcome or obligation justifies investment, which risks require senior attention and who has authority to resolve conflicts that cross teams or budgets. A sponsor may secure funding, remove organisational blockers and accept a residual business risk within their authority.

The sponsor is not automatically the product owner, business owner, architect or operational owner. They should not approve technical detail merely because they approved the investment. Their useful contribution is authority over purpose, priority, organisational risk and escalation, together with a willingness to ensure that the service has people and resources for its whole life.

### Business owner

The business owner is accountable for the business capability or service outcome from the organisation's perspective. They understand the process, obligation, benefit, risk and consequences the service is meant to support. They help decide what the organisation must preserve, what trade-offs are acceptable and what outcome counts as useful.

The business owner may provide or nominate SMEs, resolve conflicts between business needs, accept business-level residual risk and confirm that the delivered capability supports the intended responsibility. They are not automatically the person who operates the software, approves every transaction or owns the technical architecture. Those responsibilities need their own representatives and evidence.

### Service provider

The Service Provider is accountable for providing an agreed [service capability](../glossary.md#service) to its consumers and stakeholders. They ensure that the service has an owner, a consumer promise, suitable people and boundaries, required evidence, support arrangements, operational controls, maintenance capacity and a route for change or retirement.

Service Provider accountability does not make the provider the SME for every responsibility. Support remains the first point of contact for end users. Operations runs and recovers the live service. Maintenance Developers and other maintenance owners investigate and change the occupied service or its infrastructure under controlled authority. The Service Provider ensures those responsibilities are present, connected and resourced.

### Product owner

The Product Owner is a steward of product value and clarity. They bring stakeholder and organisational needs into a shared conversation, help ensure that elicitation includes the people with relevant knowledge and authority, and connect the resulting understanding to a sequence of valuable, testable outcomes. They make priority and scope decisions within delegated authority, clarify which result is needed next and ensure that accepted work still represents the product's purpose.

The Product Owner does not need to be the SME for every concern. Their influence is used well when it brings the right SMEs and decision-makers into elicitation and acceptance, makes competing meanings visible and helps the team progress from a superficial visible request toward enduring responsibilities, logical decomposition and lower-risk delivery. They may prioritise a need without possessing the detailed knowledge of a regulated process, integration, operational procedure or accounting control.

### Product manager

The Product Manager is a far-seeing steward of the product's objectives within constraints. They connect product purpose, users, value, viability, strategic fit, investment and longer-term outcomes to budget, schedule, organisational capacity, obligations and risk. Their responsibility is not to promise everything that would be desirable. It is to help the organisation choose objectives it can pursue responsibly and understand the consequences of those choices over the product's life.

In some organisations the Product Manager also acts as Product Owner. In others, the Product Owner turns the Product Manager's direction into near-term ordered outcomes for a delivery team, including the foundations, decisions and evidence needed to make the outcomes real. The Product Manager protects the longer view; the Product Owner arranges the next valuable and achievable path. Both roles benefit when the distinction between objectives and outcomes remains visible.

The titles are not universal. Record who has authority for strategy, product purpose, investment, priority, scope, acceptance and day-to-day ordering. Do not assume that a Product Owner can make Product Manager decisions, or that a Product Manager has the detailed authority or availability needed for every backlog decision.

### Customer, service user and affected person

A customer or service user experiences the service directly or consumes its result. They can explain goals, language, context, accessibility needs, expectations, workarounds and the consequences of delay or error. An affected person may never use the interface but may still be represented in the information, decision or outcome, such as a person whose record is held or whose entitlement is assessed.

Their contribution is evidence about real use and consequence, not a request to dictate the implementation. A service may need to protect their interests even when another role has authority to operate it. The BA should distinguish direct users, represented subjects, beneficiaries, applicants, recipients and people affected by decisions rather than treating all of them as one generic customer.

### Subject Matter Expert

An SME supplies detailed knowledge of a responsibility, process, policy, system, data set, profession or affected population. An SME may be a practitioner, operator, accountant, regulator, support worker, domain specialist, technical specialist or experienced user. They explain what terms mean in context, which exceptions matter, how decisions are made, what evidence is required and what failure costs.

An SME represents a bounded source of knowledge, not necessarily every person in the stakeholder group. The BA should record who the SME represents, what perspective they bring, what authority they have and which perspectives still need to be heard. A confident individual is not automatically a representative one.

## Analysis and design roles

### Business analyst

The BA discovers and structures the problem before the team chooses its implementation. They identify stakeholder groups, find and work with SMEs, elicit conceptual desires and needs, clarify language, expose differences between similar requests, trace obligations and record definitions, assumptions, acceptance conditions and unresolved questions.

The BA helps the group move from "someone needs this" to a shared account of what the service must recognise, remember, decide, provide, prevent and prove. They do not merely transcribe requests, and they do not own the technical architecture alone. They work with architects to make the definitions designable and with developers and testers to make them precise enough to implement and verify.

A BA should not be expected to invent missing policy, speak for every stakeholder, approve technical risk or convert an unresolved conflict into a false requirement. When the evidence is incomplete, the correct output is a visible assumption, open decision or deliberate deferral.

### System design architect

The system design architect makes the whole service landscape understandable at the scale of people, connected systems, platforms, sites, capabilities, dependencies, obligations and major delivery boundaries. They ask what the service must support, which wider systems constrain it, which boundaries own the responsibilities and what evidence must cross between them.

They turn stakeholder and SME definitions into an architecture map. That map may include platforms, sites, flows, components, external dependency categories, Logical Deployment Modules, logical layers, domain components, authority, data exchanges, lifecycle, security, availability, recovery and downstream obligations. The system design architect decides enough structure for technical leadership to proceed without inventing the whole again, but does not prescribe every class, provider option or project folder.

The system design architect is not automatically an enterprise architect, solution architect, data architect or integrations architect. Their focus is the coherent design of the service and its relationships with the surrounding systems. They consult the other architect roles where their concerns affect that whole.

### Enterprise architect

The enterprise architect considers how capabilities, information, technology, operating models and investment fit across the organisation. They help identify shared principles, strategic dependencies, organisational boundaries, portfolio duplication, target direction, constraints and consequences that are invisible from one service alone.

They may define or advise on enterprise standards, reference architectures, technology strategy, capability maps, transition direction and cross-portfolio decisions. They do not replace the system design architect's responsibility for understanding one service in enough detail to make it buildable. An enterprise direction is a constraint or decision input; it is not proof that a local service design is coherent.

### Business architect

The business architect describes the organisation's business capabilities, value streams, operating model, responsibilities, policies and desired outcomes independently enough to compare them with current organisational arrangements. They help connect strategy and business intent to the capabilities and changes that a service may support.

They are concerned with what the organisation must be able to do and how responsibilities, decisions and outcomes fit together. They are not automatically the owner of detailed software requirements, domain implementation or user-interface design. Their work gives the BA and system design architect a wider business frame and can reveal when a proposed digital capability is compensating for an unresolved organisational problem.

### Data architect

The data architect considers information across its lifecycle and across system boundaries. They help define information concepts, authority, stewardship, classification, lineage, quality, retention, sharing, integration, analytical use, archival and deletion or anonymisation consequences.

They distinguish conceptual information meaning from logical structures and physical stores. They help prevent a database schema, message payload, warehouse table or vendor object from becoming the organisation's accidental definition of a business concept. They do not automatically own every domain rule or every query. The data architect works with domain SMEs, BAs, system design architects, security, privacy, records and implementation teams to make information responsibilities explicit.

### Integrations architect

The integrations architect designs the relationships between services, partners, platforms and other systems. They clarify which system is authoritative for which information or decision, what capabilities are exchanged, how identity and trust work, what protocol and message contracts are needed, how versioning and compatibility are managed and what happens during delay, duplication, rejection, partial success or outage.

They treat integration as a relationship between meanings and responsibilities, not merely a connection between endpoints. They help define cadence, volume, ordering, correlation, reconciliation, replay, monitoring and ownership. They do not automatically own the internal domain model of either participant or decide that a shared database is an acceptable interface. Their job is to protect the boundary and the meaning that crosses it.

### Security architect

The security architect makes security, trust, identity, authorisation, privacy, threat, resilience and evidence concerns visible in the design. They help identify protected resources, actors, trust boundaries, attack paths, control objectives, secrets, key material, audit needs and safe failure behaviour.

They advise on controls and assurance, but security is not a separate layer that can be bolted on after the service meaning is decided. The business owner, BA, system design architect, developers, testers and operations staff still own the decisions and implementation within their boundaries. The security architect should not be expected to compensate for unclear ownership or to approve a design whose obligations are not stated.

### Solution or application architect

A solution or application architect shapes a particular solution or product into a coherent set of applications, services, interfaces, modules and deployment relationships. They connect stakeholder outcomes and enterprise constraints to a buildable solution, often at a level between enterprise direction and detailed technical leadership.

The title varies widely. In one organisation this role may overlap heavily with system design architecture; in another it may focus on a portfolio of applications or a vendor-based solution. The responsibility should be named rather than assumed from the title. A solution architect should make the boundary, decision authority, assumptions and relationship to system design architecture explicit.

### Platform, infrastructure or cloud architect

The platform or infrastructure architect designs the technical ground on which services run: compute, networking, runtime, identity integration, environments, storage foundations, observability, resilience, capacity and operational support. A cloud architect applies the same responsibility within cloud accounts, subscriptions, tenants, regions and managed services.

They make platform capabilities and constraints visible to service architects and technical leads. They do not automatically decide the business meaning of the service or force every capability into the platform's preferred product shape. A platform choice remains responsible only when its security, availability, cost, support, exit and recovery consequences fit the service's actual needs.

### Domain architect

A domain architect focuses on a substantial business or technical problem space and the relationships among its capabilities, concepts, policies, information and lifecycle. They help keep a domain coherent across several products or services when the domain's rules and language have consequences beyond one delivery team.

They may work closely with business architects, data architects, BAs and system design architects. They should not turn a domain label into an automatic application, database or team boundary. The useful boundary is the responsibility, meaning and reason for change that the domain must preserve.

## Developer families

Developer is a family name. The families below describe different primary responsibilities, not a ranking and not sealed job titles. A team should be honest about when one person is carrying several families, because overlap can be valuable while sustained overload creates gaps in security, testing, operations, integration or maintenance.

### System or application developer

A system developer creates or extends the capabilities that make a service useful. They turn logical building blocks and contracts into application behaviour, domain models, mappings, persistence policies, interfaces, vertical slices and failure handling. They need enough whole-system understanding to preserve meaning across conceptual, logical and physical boundaries.

They are not expected to make every architectural or business decision alone. They are responsible for raising unclear ownership, unsafe assumptions and contracts that cannot be implemented or tested. A system developer should be able to explain where a capability belongs, which boundary owns it and what evidence shows that it works.

### Front-end developer

A front-end developer builds the service consumer system through which people or other consumers reach the service. For a browser SPA, this includes assets, browser execution, client-side state, views, interaction flows, component assemblies and calls to service interfaces. They make the client-side journey understandable, accessible, usable, secure and recoverable while preserving the service system's authority over business rules, authorisation, durable state and audit.

They work with the service-side developer and architect across the contract boundary. The front-end developer may coordinate the consumer-side horizontal flow more completely because that is where several capabilities become one human journey, but they do not absorb the rules or state ownership of the participating capabilities. They make waiting, failure, retry, cancellation, unsaved work, stale data and return conditions visible, and they provide evidence for functional behaviour, accessibility, usability, security, integration, performance and quality in use.

Component responsibility should remain clear. A component may collect input, present output, arrange a collection of inputs or outputs, arrange other collections or assemble a focused interaction from those parts. It is not automatically a business boundary or an authorisation authority. See [Front-end Developer Guidance](../../../stakeholders/deliverers/developers/front-end.md) for the consumer-system route, including WCAG, focused interactions, browser security and protected cookie sessions.

### Integration developer

An integration developer implements the contracts designed between systems. They configure or build adapters, clients, message handlers, transformations, authentication, scheduling, correlation, retry, idempotency, reconciliation, observability and recovery behaviour.

They must understand both the transport and the meanings that travel through it. A successful HTTP response or accepted message does not prove that the receiving system has accepted the intended business meaning. Integration developers work with integrations architects, domain SMEs, data architects, operations and testers to preserve authority, lifecycle and failure semantics.

### Test developer

A test developer creates automated evidence for functional and quality claims. They turn contracts, definitions, risks, acceptance conditions and failure expectations into maintainable static and dynamic tests. They check successful outcomes as well as invalid input, denied access, bad state transitions, duplicate work, dependency failure, startup gaps, recovery and data-lifecycle behaviour.

Test developers are not merely the last gate after coding. They help expose ambiguous definitions and boundaries that cannot be tested cleanly. They do not own product acceptance or business meaning alone; business SMEs and product roles must help confirm that the behaviour tested is the behaviour needed.

### Environment and pipeline developer

An environment and pipeline developer makes build, deployment and operational environments repeatable. Their work may include infrastructure as code, build pipelines, artifact promotion, environment configuration, identity and secret integration, network routes, observability, scaling, release controls and recovery automation.

Their infrastructure code may be declarative, such as Bicep, ARM or CloudFormation, or authored through a typed infrastructure framework such as AWS CDK. PowerShell, Bash and other bounded tools may coordinate the surrounding provider commands and evidence. The distinction between resource declaration and imperative orchestration remains important: neither the language nor the wrapper removes the need for provenance, bounded authority, secret protection, repeatability, rollback and recovery.

The term **DevOps** is a portmanteau rather than a precise single job. It can describe a culture of shared responsibility, a team, a platform capability or a person who develops environments and pipelines. It should not hide the fact that environment and pipeline development is substantial work. The same person may also perform integration development, security engineering, operations or system development, but asking one person to carry all of those responsibilities indefinitely creates a capacity and assurance risk.

### Maintenance developer

A maintenance developer changes an occupied service while preserving the behaviour, compatibility, evidence and recovery that existing users and connected systems rely on. They investigate unfamiliar code, identify consumers and hidden dependencies, make narrow changes, repair defects, renew dependencies, manage migrations and leave the service easier to understand.

Maintenance is not lesser development. It requires a different risk posture because the service is already relied upon. The maintenance developer should be involved in design decisions that affect long-term support and should not be expected to reverse undocumented architectural choices without time to investigate their consequences.

## Testing, operations and service continuity roles

### Manual tester

A manual tester explores the service as a person, operator or connected participant would. They examine real journeys, language, accessibility, confusing states, unexpected combinations, visual or interaction problems, evidence, permissions and consequences that scripted checks may miss.

Manual testing is not a lesser form of automation. It is valuable when behaviour, context, usability, exploration or human judgment matters. Manual testers should receive clear definitions and risk context, but they should also be able to report when the written definition does not match a credible user's situation. They do not replace automated regression coverage for repeatable checks.

### Automation tester

An automation tester designs and maintains repeatable checks that provide fast evidence at the appropriate boundary. They may work with browser, API, contract, integration, performance, security, accessibility or recovery automation. They help the team choose what can be checked deterministically and what still requires human exploration.

Automation testers are responsible for useful evidence, not for creating a large number of brittle scripts. They should make test data, environment assumptions, classification, timing, cleanup and failure diagnosis explicit. Automation can confirm that the system repeats a behaviour; it cannot by itself decide whether the behaviour represents the right human or business outcome.

### Operations specialist

Operations keeps the live service available, observable, secure and recoverable. Operations staff manage readiness, health, incidents, capacity, dependency conditions, alerts, runbooks, controlled interventions, release coordination and recovery evidence. They know what is actually supportable in the environment, not merely what the design claims.

Operations should be involved before delivery so that dependencies, diagnostics, failure modes, access, escalation and recovery are designed rather than discovered during an incident. Operations does not own every application defect or business decision. The development team must build safe behaviour and useful signals; operations must be able to use them.

### Support role

Support is the first human point of contact for end users, normally Tier 1 in an organisation that uses numbered support tiers. A Service Provider may also offer Tier 0 self-service or automated assistance, but that must not replace human help where the user needs it. Support staff help people understand and use the service, investigate reported problems, perform permitted lookup or guided actions, communicate impact and route the problem to the responsible boundary. They need curated Support Manuals or Information, known symptoms, supported responses, escalation routes and links to authoritative evidence.

Support should not receive unrestricted maintenance access merely to resolve a difficult case. Support must respect privacy, impersonation, normal authorisation, audit and data-minimisation controls. A support report may be delivered to the Service Provider and/or Operations, then to Maintenance Developers when further technical investigation or change is needed.

### Support tiers

Tier labels vary by organisation and should be defined by the Service Provider. A common arrangement is Tier 0 for optional self-service, Tier 1 for the first human Support contact, Tier 2 for deeper Service Provider or Operations investigation and Tier 3 for Maintenance Developers or other specialist technical owners. The number identifies the depth of investigation and authority needed, not the seniority or worth of the person involved.

The handoff must preserve the user report, affected capability, impact, evidence, privacy classification, current owner, action already taken and return or escalation condition. Tier 2 may examine operational state and coordinate permitted recovery; Tier 3 may investigate and change code, schema, dependencies, configuration or infrastructure under controlled authority. Neither tier should make Support the substitute for its own specialist responsibility.

### Operations role

Operations staff run, observe and recover the live service. They manage readiness, health, incidents, capacity, dependency conditions, alerts, runbooks, controlled interventions, release coordination and recovery evidence. They provide Support with current service status and operational findings when those affect user reports.

Operations needs its own Operational Manuals or Information. Operations does not own every application defect, user conversation or maintenance change, and operational access must not become unrestricted business or maintenance authority.

### Organisational or infrastructure maintenance role

An organisational or infrastructure maintenance role preserves the hosting, network, platform, provider, facility or shared technical arrangements on which a service depends. This role may belong to a Service Provider, platform team, supplier or other maintenance owner. Its contract, maintenance window, failure route, evidence and escalation path must be explicit.

### Maintenance developer

A Maintenance Developer investigates and changes an occupied service when Support, Operations, Testing or another responsible role cannot resolve the issue within its authority. They may change application code, configuration, schema, dependencies or service infrastructure under controlled change authority. They preserve compatibility, evidence, rollback and recovery while repairing defects, renewing dependencies, managing migrations or retiring a capability.

Maintenance Developers need their own Maintenance Manuals or Information. Maintenance is not a general-purpose support shortcut, and a technically possible correction is not automatically a permitted business correction.

### Service desk and customer support

Service desk and customer support roles provide the human route through which users report difficulty and receive help. They know the language users use, the recurring confusion, the impact of delays and the difference between a technical failure and an unclear process.

They contribute evidence about usability, communication, operational impact and support cost. They should have curated capabilities that respect the authority and privacy of the person they are helping. A support interface is not automatically allowed to bypass the service's normal authorisation, audit or data-minimisation controls.

## Governance, assurance and control roles

### Financial auditor

A financial auditor examines whether financial records, controls, transactions, authorisations, reconciliations, evidence and reporting can be trusted for the relevant purpose. They may be internal or external, and their independence and formal authority depend on the engagement.

They help define what must be recorded, who may approve or change it, how duties are separated, how totals reconcile, how corrections are represented and how evidence can be retrieved. An auditor does not design the application alone and does not automatically require every internal event to be treated as a financial record. The organisation must understand the applicable accounting, control and audit obligations and assign them to responsible boundaries.

### Records, privacy and information governance

Records, privacy and information-governance roles advise on lawful purpose, classification, minimisation, access, retention, records status, correction, export, deletion, anonymisation, archival and evidence. They help identify what must be preserved and what should not be retained.

They work with BAs, data architects, security, system design architects, developers, testers and operations because lifecycle decisions cross storage, caches, indexes, messages, reports, warehouses, archives and backups. They do not own the whole implementation or replace the business authority that decides the service purpose.

### Risk, compliance and assurance

Risk, compliance and assurance roles identify obligations, control expectations, material risks and evidence needed to demonstrate that the service is acceptable. They may review security, accessibility, resilience, financial controls, regulatory duties, supplier risk or operational readiness.

Their contribution is strongest when it is specific: which obligation applies, what control or outcome is expected, which boundary can provide it and what evidence will be accepted. They should not be treated as a final approval ritual whose only input is a completed product. Nor should engineering teams treat an assurance observation as a technical solution without understanding the underlying obligation.

### Scrum Master or delivery facilitator

A Scrum Master or delivery facilitator helps the team work effectively within its chosen delivery method. They protect useful collaboration, make impediments visible, improve feedback loops, help the team inspect and adapt its way of working and reduce process noise that prevents people from doing responsible work.

Scrum uses the Scrum Master accountability. Kanban does not require a Scrum Master; a team may instead name a flow facilitator, delivery manager, service delivery manager or another person with explicit responsibility for flow, policies, blockers, feedback and improvement. Neither role owns product priority, business requirements, architecture or technical implementation merely because they facilitate the conversations.

If no facilitator is assigned, the team and sponsoring organisation must explicitly name who will perform the necessary work or record the unassigned responsibility as a delivery risk. It should not silently default to the Product Owner, architect or most senior developer. One person may hold both product and flow responsibilities in a small team, but the accountabilities and conflicts must remain visible.

The facilitator can help ensure that the right BA, SME, architect, developer, tester, operations and decision-maker are present when a decision requires their knowledge.

### Release Manager

A Release Manager coordinates the movement of an approved change through environments and into service. The organisation should use this full title for the responsibility even when no dedicated job exists. The Release Manager checks release readiness, consults blackout and brownout windows, confirms dependency and expiry conditions, coordinates communication, records approval and preserves rollback or recovery evidence.

This role consults the enterprise-referred technology, system, obligation and integration registries and maintains or uses project-produced component, expiry, schedule, release and evidence registries. It does not replace the Product Owner's outcome and scope authority, the architect's design authority, Operations' live-service responsibility, Security's control authority or the technical lead's implementation responsibility.

The Change Manager remains a distinct and important partner. Change Management assesses the change's organisational and service impact, required approvals, timing, communication, dependency on other changes and readiness to introduce it. The Release Manager coordinates the approved release path; the Change Manager governs the change decision and its wider impact. The same person may hold both responsibilities, but the two accountabilities should remain visible.

In a small team, Operations, a Change Manager, a delivery facilitator or another named person may carry the Release Manager responsibility. The assignment and any conflicts must remain visible; the organisation should not silently default the work to the Product Owner, architect or most senior developer.

### Procurement, supplier and commercial roles

Procurement and commercial roles help the organisation acquire services, products, suppliers and support under appropriate financial, contractual, security, licensing and exit conditions. They know commitments, service levels, renewal terms, liability, pricing, ownership and supplier obligations that technical teams may not see.

They should be involved when a dependency or supplier shapes the system's lifecycle. A technical evaluation should still establish the capability, boundary, data, failure, support and exit consequences; procurement approval is not architectural evidence by itself.

## How roles meet around a capability

For a substantial capability, the team should be able to say:

- which stakeholder groups depend on the outcome or carry consequences;
- which SMEs represent their knowledge and how that representation was checked;
- which BA elicited and clarified the conceptual needs, definitions and conflicts;
- which business or product role has authority over purpose, priority and acceptance;
- which architect roles contributed constraints, boundaries and specialist design;
- which technical lead turned those decisions into implementable structure;
- which developers own system, integration, environment, testing and maintenance work;
- which testers provide human and automated evidence;
- which operations and support roles can run and assist the service;
- which security, privacy, records, audit and assurance roles define or verify obligations; and
- where decisions, evidence, unresolved questions and deliberate deferrals are recorded.

This is not a demand that every role attend every meeting. It is a way to find the missing perspective before the absence becomes an implementation assumption.

## Related guidance

The distinction between phases, role families and affected stakeholders is introduced in [Phases, Roles and Stakeholders](../../../orientation/phases-roles-and-stakeholders.md). The route for a system design architect is explained in [Guidance for System Design Architects](../../../orientation/guidance-for-system-design-architects.md), while the technical-lead and developer routes show how the resulting structure becomes delivery and code.

The lifecycle phases in [SDLC](./sdlc.md) provide the time-based frame in which these responsibilities recur. The [Qualities](./qualities.md) catalogue connects the quality of the system, its data and the experience people have when using it.
