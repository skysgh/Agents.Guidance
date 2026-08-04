# Quality Perspectives

Quality is not one property that can be added at the end of development. It is the degree to which a service, its information and its use achieve the outcomes that matter in their context.

A service can be functionally correct and still be poor quality for its users. It may be accurate but too slow, available but unsafe, secure but impossible to understand, or maintainable for developers while producing information that people cannot trust. Quality therefore needs several connected perspectives.

Three ISO/IEC SQuaRE models provide a useful practical relationship:

- **ISO/IEC 25010** describes qualities of the system or software product.
- **ISO/IEC 25012** describes qualities of the data and information the system creates, stores, transforms or provides.
- **ISO/IEC 25022** provides measures for quality in use: what people and organisations achieve, experience and risk when they use the system and its information in a real context.

These are related perspectives, not three interchangeable names for the same quality. System quality can enable or restrict data quality and quality in use. Data quality can enable or undermine quality in use. Human outcomes also depend on context, training, process, accessibility, policy, environment and the actions of people and connected organisations. The relationship is useful, but it is not a simple one-way formula.

## The quality relationship

```text
system and software qualities
        |
        v
ability to create, protect, transform and present information
        |
        v
data quality in its context
        |
        v
what people and organisations can achieve and experience in use
```

The arrows mean "can enable or constrain", not "automatically produces". A fast system can present incorrect data quickly. Accurate data can still be unusable if the interaction is inaccessible or the decision process is confusing. A usable interface cannot compensate for a system that loses records or exposes confidential information.

The practical design question is:

> Which system qualities and data qualities must be present for the people and organisations using this service to achieve the intended outcome without unacceptable risk?

## Product quality: ISO/IEC 25010

ISO/IEC 25010 provides a model for judging the system or software product itself. The exact characteristics and terminology should follow the edition adopted by the organisation, but the commonly used product-quality areas include the following.

### Functional suitability

The system provides the functions needed for the intended tasks, and those functions produce correct and complete results for the relevant purpose. A service that has every requested screen but cannot complete the underlying decision does not have functional suitability.

Ask which capabilities are needed, whether the result is correct, whether important cases are covered and whether the system avoids claiming to have done work it did not complete. Evidence may include functional tests, domain examples, decision records, contract tests and reconciliation.

### Performance efficiency

The system uses time and resources appropriately for its workload. This includes response time, throughput, capacity, concurrency, memory, storage, network use and the cost of work that users or operators can observe.

Performance is a quality only in relation to a workload and context. A five-second response may be acceptable for a long report but unacceptable for a safety-critical interaction. Evidence should use representative data, concurrency, dependency behaviour and peak conditions rather than one developer's local response time.

### Compatibility

The system can coexist and exchange information with other systems or components without unacceptable interference. Compatibility includes shared environments, protocols, interfaces, data formats, versions and resource use.

An integration that connects once but cannot manage version change, duplicate delivery, incompatible data or shared-resource contention is not adequately compatible. Evidence includes contract tests, compatibility policies, versioned exchanges, reconciliation and failure tests.

### Usability and accessibility

People can recognise what the system offers, learn it, operate it, avoid or recover from errors and complete their tasks with appropriate satisfaction and accessibility. Accessibility is part of usable quality for people with different abilities, devices, languages and ways of interacting.

Usability is not proved by asking the team whether a screen looks clear. Use representative people and tasks, keyboard and assistive-technology checks, error recovery, content review, observation and measures of completion and confusion. A technically correct control that a person cannot find or operate is a quality failure.

### Reliability

The system performs consistently over time and continues or recovers its intended service when faults occur. Reliability includes maturity, availability, fault tolerance and recoverability in the adopted quality vocabulary.

Define what must remain available, what may degrade, what can be retried, what must be recovered and what evidence proves restoration. A service that is available only while an external dependency behaves perfectly has not defined its reliability boundary.

### Security

The system protects information and functions from unauthorised access or change and preserves accountability for consequential actions. Security includes confidentiality, integrity, authenticity, accountability and non-repudiation concerns where applicable.

Security quality is not just authentication. It includes authorisation at the responsible boundary, safe failure, secret handling, data minimisation, audit, protection of copies and recovery from compromise. Evidence includes denied-path tests, threat analysis, access reviews, audit inspection and incident exercises.

### Maintainability

The system can be analysed, changed, tested and adapted without disproportionate risk or effort. Maintainability includes modularity, reusability, analysability, modifiability and testability in the commonly used quality vocabulary.

Maintainability is not the same as making code short. It depends on meaningful boundaries, clear ownership, stable contracts, understandable models, observable behaviour, useful tests, controlled dependencies and records of why important decisions were made. A clever abstraction that only its author understands may reduce lines while damaging maintainability.

### Portability

The system can be moved, installed or adapted across the environments and platforms that matter to its lifecycle. Portability includes adaptability, installability and replaceability or coexistence concerns in the adopted quality vocabulary.

Portability is not a demand to support every platform. It is the ability to change or operate within the credible environments identified by the service's life, supplier relationships, recovery plans and exit obligations. Evidence includes repeatable deployment, environment checks, migration rehearsal and dependency replacement tests where those are required.

## Data quality: ISO/IEC 25012

ISO/IEC 25012 provides a vocabulary for judging data as information in its own right and in the context where it is used. Data quality is not only whether a database column accepts a value. It includes whether the information is fit for the decision, process or relationship that relies on it.

### Accuracy

The data correctly represents the real-world object, event, measurement or decision it claims to represent. Accuracy may require a source, method, validation, correction route or reconciliation process.

### Completeness

The data contains the information needed for its purpose. Completeness is contextual: an optional field may be complete when it is legitimately absent, while a missing approval reason may make a decision record incomplete.

### Consistency

The data does not contradict itself or the rules that govern related representations. Consistency may need to be considered across fields, records, services, reports, caches, messages and historical versions.

### Credibility and provenance

The data can be trusted for the use being made of it because its source, authority, collection method, transformation and history are understood. A value can be syntactically valid while lacking credible origin or current authority.

### Timeliness and freshness

The data is available when needed and current enough for the decision or activity. A value may be accurate when created but unsafe to use later if the context changes. Define freshness, expiry, update cadence and what the consumer should do when the value is stale.

### Accessibility and availability

Authorised people and systems can retrieve and use the data when the purpose requires it. This includes access paths, permissions, formats, searchability and dependency availability. Making data technically available to everyone is not the same as making it appropriately accessible.

### Compliance and confidentiality

The data is handled according to applicable rules, permissions, classification, consent, retention and sharing conditions. Confidentiality is not merely a property of storage; it applies to interfaces, exports, logs, notifications, caches, indexes, backups and downstream systems.

### Precision, understandability and traceability

The data has enough precision for its purpose, can be understood by its intended users and can be traced to its source, transformation, version or decision where that evidence matters. More decimal places or more fields do not automatically make information more useful.

### Recoverability and portability

The data can be restored, transferred or reused as required by the service's lifecycle. Recovery is not just restoring bytes. The team must know whether restored data remains coherent, authorised, current enough and connected to the required mappings and dependencies.

The adopted ISO/IEC 25012 edition and the organisation's data policy should determine the final attribute names and measurement definitions. The practical responsibility remains the same: identify what makes each information category trustworthy for its actual use, who stewards it, how it changes and what evidence supports the claim.

## Quality in use: ISO/IEC 25022

ISO/IEC 25022 concerns quality in use: the outcomes and experience of people or organisations using the system and its information in a particular context. It is not limited to whether users say they like the interface. It asks whether they can achieve the intended goals, what effort and satisfaction the use involves, what risks arise and whether the system remains appropriate across the contexts that matter.

Common quality-in-use areas include:

- **Effectiveness:** can the person complete the intended task and achieve the intended result?
- **Efficiency:** what time, effort, cognitive load, resources or support does the task require?
- **Satisfaction:** does the experience meet the person's expectations and leave them able and willing to use the service appropriately?
- **Freedom from risk:** does use avoid unacceptable risk to people, information, property, finances, health, rights, service continuity or the wider organisation?
- **Context coverage:** does the result remain suitable across the people, devices, environments, languages, workloads, accessibility needs and operating situations that the service claims to support?

Quality in use belongs to the real context. A laboratory test, synthetic dataset or expert review can provide valuable evidence, but it does not replace observation of representative tasks and conditions where the outcome matters.

## Following one outcome through the three perspectives

Suppose a person submits an application and needs to know whether it has been received.

- **Quality in use:** the person can submit it confidently, understand the result and find trustworthy status without unnecessary effort or risk.
- **Data quality:** the submission has the correct identity, complete required information, credible receipt time, consistent status and traceable evidence.
- **System quality:** the interface is usable and accessible, the service handles the request correctly, the storage is reliable, the status is available, the integration is compatible, access is secure and the system can be maintained and recovered.

The same outcome can be examined from an operator's perspective. Operations needs accurate and timely health information, usable controls, reliable alerts, secure access, compatible dependencies and maintainable runbooks. A customer's quality in use and an operator's quality in use are different contexts, even when they depend on some of the same data and system qualities.

## Quality is a responsibility shared across roles

BAs and SMEs explain what a successful and safe outcome means in context. Product and business roles decide which outcomes and trade-offs matter. Architects connect quality goals to boundaries, dependencies, data flows and lifecycle. Data architects and stewards define authority, lineage and data-quality expectations. Security, privacy, accessibility, finance, audit and assurance roles identify obligations and evidence. Developers and environment or pipeline developers implement the controls and observable behaviour. Test developers and manual testers produce evidence. Operations and maintenance teams show whether the quality survives real use and change.

No single role can prove every quality perspective. A product owner can accept a priority decision but cannot manufacture missing security evidence. A tester can show that a scenario passes but cannot decide whether the scenario represents every affected group. An architect can identify a quality dependency but cannot claim that a deployed service meets it without implementation and operational evidence.

## Quality claims and evidence

For each important capability, record:

- the person, organisation or system whose outcome matters;
- the context in which the quality is required;
- the system qualities that enable the outcome;
- the data qualities that the outcome relies upon;
- the quality-in-use result that should be achieved;
- the trade-offs and unacceptable risks;
- the measure, test, observation or other evidence that supports the claim;
- the responsible boundary and steward; and
- what happens when the quality target is missed or the context changes.

A quality target without a context is usually too vague to test. ÔÇ£Fast,ÔÇØ ÔÇ£secure,ÔÇØ ÔÇ£accurate,ÔÇØ ÔÇ£usableÔÇØ and ÔÇ£maintainableÔÇØ become useful only when the team states for whom, for what task, under which conditions, to what level and with what evidence. [Availability, Capacity and Resilience](../../development/availability-capacity-and-resilience.md) provides the focused control path for turning reliability and performance claims into service targets, design decisions, operational signals and assurance evidence.

## Related guidance

- [Delivery Guidance](../../delivery/readme.md) connects quality, evidence and responsibility to the wider delivered service.
The [Stakeholder Roles](./stakeholder-roles.md) catalogue identifies the people who provide quality expectations and evidence. [Software Development Lifecycle](./sdlc.md) places quality decisions and evidence across Discovery, Definition, Design, Development, Delivery, Operations, Maintenance and Decommissioning. [Conceptual, Logical and Physical Models](./conceptual-logical-physical-models.md) explains why a quality claim may be expressed differently by a consumer, logical domain model and physical implementation.

The agent-facing [Standards](../../../agents/conventions/development/design-standards.md) records the adopted ISO/IEC quality foundation and links to the standards themselves.
