# Systems Within Systems

This paper explains the wider system that surrounds a digital service. A service is never responsible only for the code in its repository. It operates inside an enterprise, a legal and regulatory environment, and a network of people and systems that depend on what it does.

The word **system** is polysemous: it has different related meanings at different levels. A system may be a physical arrangement, a logical arrangement, a digital arrangement or a combination of people, policies, processes, information and technology. The boundary must therefore be qualified: system for whom, at which level, for what purpose and under whose authority?

This guidance uses **polysystem** as a reminder that one system can be understood as a participating part of several wider systems at the same time. The term is not a licence to blur boundaries. Each system still needs a clear purpose, boundary, authority, obligations, capabilities, lifecycle and evidence. The point is to see the relationships between systems without pretending that the digital service is the whole world in which it operates.

## The nested picture

A digital service commonly sits within a structure like this:

```text
international alliance and treaty system
        -> national legal system
            -> sector, regulatory and accreditation system
                -> organisational principles and policy system
                    -> enterprise processes, people and physical resource system
                        -> business service and operating system
                            -> digital solution and data system
                                -> digital system and service capabilities
                                    -> web application
                                        -> runtime or application server
                                            -> operating system, container or virtual machine
                                                -> compute and virtual network
                                                    -> physical network, host and facility
                                                        -> cloud account, subscription or tenant governance
```

The arrows do not mean that every relationship is a simple parent-child dependency. A digital system may support several business services. A regulatory duty may apply directly to a process, a physical record and a digital service. An international alliance may define shared obligations without owning the national or organisational implementation. The picture is a way to ask which wider system gives a requirement its authority and which system must provide the evidence that it has been met.

### The web application is not the hosting system

For a web developer, the application in the repository is only one participant in the deployed system. It runs inside a runtime or application server, which depends on an operating system, container or virtual machine. That execution environment depends on compute, network segments and security controls. Those controls operate within virtual networks and physical networks, which are provided by hosts, facilities and cloud or infrastructure providers. The deployment is also governed by an account, subscription, tenant, region or organisational resource boundary with its own policies, quotas, identities, operators and billing responsibilities.

These relationships are not always one straight containment chain. A cloud account or subscription governs resources; a virtual network connects them; a runtime executes the application; and physical infrastructure hosts the underlying services. They are different systems with different owners and failure modes. A web developer does not need to implement every layer, but must understand that application behaviour depends on them and that a complete service obligation may cross them.

This is why application teams need to ask about more than code and endpoints: where does the application run, which runtime and operating-system assumptions does it make, which network paths and trust zones does it use, which account or subscription controls it, who can operate each layer, what happens when a layer is unavailable and which evidence proves that the deployed service is secure, available and recoverable?

There are also cross-cutting relationships. A person may act through several interfaces. A policy may constrain both a business process and a technical integration. A physical storage facility may support a digital system while remaining subject to its own safety, access and retention obligations.

## Every system carries obligations and capabilities

A system is not only a collection of components. It is an arrangement that must do something responsibly.

- **Obligations** are what the system must preserve, provide, prevent, record or make possible because of a contract, policy, law, safety need, relationship or promise.
- **Duties** are the responsibilities assigned to an actor, boundary or system for meeting those obligations.
- **Capabilities** are the repeatable abilities through which the system fulfils its duties.
- **Evidence** shows that an obligation was understood, a duty was assigned, a capability operated and a failure was handled.

For example, a privacy obligation may create duties to minimise collection, restrict access, retain information for a justified period, support correction or deletion and record protected use. The digital service then needs capabilities such as classification, authorisation, secure storage, audit, export, retention and deletion. The capability is not the obligation itself. It is one part of the evidence-bearing arrangement that fulfils the obligation.

An obligation can belong to a wider system while a digital service carries part of the duty. That is why a development team cannot dismiss privacy, data protection, storage, audit or recovery as someone else's concern merely because the original requirement came from law, policy or an external partner.

## Digital systems operate inside enterprise systems

A digital system is usually a technical part of a wider enterprise system. The enterprise system includes people, roles, processes, decisions, physical resources, information, partners, policies and digital solutions.

The digital service may automate one capability, but the enterprise remains responsible for the wider outcome. A service may therefore need to preserve a hand-off to a person, a record kept outside the service, a physical control, a policy decision, a regulatory report or a downstream archive. The code cannot be considered complete until those relationships are understood.

This also explains why a digital service may have several interfaces. The public anonymous experience, external consumer interface, internal provider interface, support interface and monitoring or maintenance interface are different ways the wider system participates in the service. Their contracts, information needs, safety controls and duties may differ even when they reach related capabilities.

## Conceptual, logical and physical systems

The nested picture must not be confused with the conceptual, logical and physical views of one system.

- The **conceptual view** describes what a wider system means, needs and recognises as an outcome.
- The **logical view** describes the capabilities, responsibilities, relationships, states, policies and contracts that carry that meaning.
- The **physical view** describes how people, processes, software, storage, infrastructure and facilities make those responsibilities real.

The views can be applied at each level. An enterprise may have a conceptual service promise, a logical operating model and a physical arrangement of people, sites and technology. A digital service may have a conceptual capability, a logical domain and a physical implementation of interfaces, application code and storage.

Do not allow a physical implementation at one level to erase the logical responsibility at another. A database table does not replace a records-retention duty. An endpoint does not replace a service promise. An identity-provider claim does not replace an authorisation decision. A warehouse copy does not replace source ownership. A backup does not automatically satisfy archiving.

## Obligations cross boundaries

When an obligation crosses a system boundary, the architecture must make the crossing explicit.

Ask:

1. Which wider system creates or expects the obligation?
2. Which actor or boundary has the duty to fulfil it?
3. Which digital or physical capability performs the duty?
4. Which data, decision or event crosses the boundary?
5. Which interface or dependency carries the exchange?
6. What classification, authority, retention and consent rules apply?
7. What evidence proves the exchange, decision or outcome?
8. What happens when the other system is unavailable, rejects the exchange or changes its contract?

The answers may divide responsibility. One system may own a business decision, another may provide identity, another may store an archive and another may produce a regulatory report. The architecture should preserve those distinctions instead of hiding them behind a convenient integration class or a shared database.

## What this means for privacy and data

Privacy and data protection are wider-system obligations. A digital service may be one place where information is collected or processed, but the duty can span the reason for collection, the people involved, the enterprise process, the storage locations, the interfaces, the downstream copies, the retention period and the deletion or correction path.

The technical team therefore needs to know:

- why the information exists and which wider purpose authorises it;
- which system and boundary is the steward;
- who may see, change, export, copy or delete it;
- where secure and open representations may exist;
- which caches, search indexes, reports, warehouses and archives receive copies;
- how access and changes are audited;
- how retention, correction, deletion and recovery interact; and
- which failure or dependency outage changes the safe behaviour.

Treating one database as the whole data system is a common way to lose these obligations. Copies and derived projections remain part of the protection problem even when they live in another service or platform.

## The architect and the tech lead

The architect makes the wider system legible. They identify the systems that constrain or depend on the service, translate obligations into architectural constraints and required capabilities, assign duties to boundaries and define the evidence that will demonstrate compliance and dependable operation.

The tech lead makes that architecture real in delivery. They choose and coordinate the technical mechanisms, keep platform and feature boundaries coherent, ensure dependencies are available and tested, and guide developers when a wider obligation is not negotiable. The tech lead may help refine an architectural decision, but must not silently weaken an obligation because the local implementation is inconvenient.

Developers then implement the contracts, mappings, controls, storage, interfaces and recovery paths that fulfil the assigned duties. They should be able to ask which wider obligation a boundary serves and what evidence proves it, rather than treating privacy, audit, retention or secure storage as unexplained ceremony.

## A practical review

For a new capability or material change, draw the smallest useful polysystem map. Include:

- the wider legal, regulatory, policy and enterprise systems that constrain the work;
- the business service and physical process the digital system supports;
- the digital interfaces and stakeholder groups involved;
- the internal domains, platform capabilities and storage boundaries;
- the external dependencies and downstream systems;
- the obligations, duties, capabilities and evidence at each crossing; and
- the failure, recovery, retention and change conditions that could alter the design.

Then ask whether the proposed implementation is merely functional or whether it fulfils the duties assigned to the service within the wider system. A service is not complete when its local code works if the wider process cannot operate safely, prove what happened or honour the obligations that gave the service its purpose.

## Related guidance

- [What Architects Need to Know](./architects-need-to-know.md)
- [Legal and Regulatory Context](./legal-context.md)
- [What Tech Leads Need to Know](./tech-leads-need-to-know.md)
- [What Developers Need to Know](./developers-need-to-know.md)
- [What This Guidance Gives](./what-this-guidance-gives.md)
- [Data Protection Conventions](../../agents/conventions/foundations/data-protection.md)
- [Development Principles](../../agents/conventions/foundations/principles.md)
- [Guidance Glossary](../reference/glossary.md)