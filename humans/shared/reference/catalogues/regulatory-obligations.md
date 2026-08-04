# Regulatory and Obligation Domains

A service operates inside laws, regulations, sector rules, organisational policies, contracts and recognised standards. The names differ between countries, jurisdictions and industries. The underlying objectives often recur.

This catalogue gives those recurring objectives a shared engineering shape. It is not a list of laws, a substitute for legal advice or a claim that one country's source applies everywhere. A named source is evidence that a duty may exist; the team must still identify the actual scope, authority, interpretation, exceptions and evidence required for the service.

## The common pattern

For each obligation, distinguish:

- **Source:** the law, regulation, regulator direction, contract, policy, standard or public promise that creates or explains the expectation;
- **scope:** the people, information, process, system, sector, jurisdiction and time period to which it applies;
- **objective:** what must be protected, enabled, prevented, recorded or made fair;
- **duty:** which organisation, role, boundary or supplier is responsible;
- **capability:** what people, process, software, infrastructure or evidence fulfils the duty; and
- **evidence:** how the organisation can show that the duty was understood, operated, reviewed and handled when it failed.

The same objective may be fulfilled by several parts of the wider system. A digital service may own only one capability or evidence path while the organisation remains accountable for the whole outcome.

## Recurring domains

Recurring obligation domains are recognition aids. They overlap, and a service may need only some of them. The examples are representative rather than universal legal classifications.

### Purpose, fairness and lawful use

The service has a clear and authorised purpose. It does not collect, decide, restrict, charge, rank or share more than the purpose and authority justify. People can understand the important consequences of the service, and decisions can be challenged or corrected where the context requires it.

This domain commonly includes lawful basis or authority, purpose limitation, minimisation, fairness, transparency, consent, legitimate interest, automated decision safeguards, complaints and redress. Privacy and data-protection law is one common source, but organisational policy, public-sector duty, contract and sector regulation can create related obligations.

### Personal information: collection, use and sharing

Information about identifiable people is collected, used, disclosed, transferred and retained for an understood purpose. The service can support the rights and controls that apply to the people represented in the information.

Common capabilities include notices, consent or authority records, classification, access and correction, export, controlled sharing, minimisation, protection of copies and deletion or irreversible anonymisation where required. See [Data Deletion Guidance](../../../development/data-deletion-guidance.md) for the special relationship between erasure, retention, history and evidence.

### Tracking, cookies and online observation

The service makes browser storage, cookies, device identifiers, analytics, advertising tags, fingerprinting, location use and other tracking visible and controllable where the applicable rules require it. It distinguishes necessary operation from measurement, personalisation, advertising or cross-site observation.

The implementation should record the purpose, authority or consent state, expiry, provider, data shared, withdrawal behaviour and effect on service use. A cookie banner is not proof that tracking is lawful or that withdrawal works. Check the actual jurisdiction, device, audience and provider arrangement.

### Records, accountability and official evidence

The organisation can show what decision, transaction, communication or change occurred, under whose authority, using which information and at what time. Records remain trustworthy, retrievable and understandable for the period and purpose that apply.

This domain commonly includes public-records or archives duties, financial and tax records, audit trails, decision reasons, version history, provenance, chain of custody, freedom-of-information or transparency duties and accountable administration. An application log is not automatically an official record, and a backup is not automatically an archive.

### Retention, disposal, legal hold and history

Information is kept for a justified period, protected while it must remain, and disposed of safely when disposal is permitted. Conflicting duties are made visible rather than resolved by a blanket delete or retain rule.

The design must account for authoritative records and copies in caches, indexes, exports, reports, messages, warehouses, archives, backups and provider systems. It should distinguish deletion, irreversible anonymisation, de-identification, restriction, archival and legal hold, and record who can authorise each action.

### Security, identity and resilience

People, information, services and infrastructure are protected from unauthorised access, alteration, loss, disruption and misuse. The service remains trustworthy when credentials, dependencies, operators, suppliers or environments fail or are attacked.

Common sources include government security manuals such as NZISM, information-security frameworks, sector controls, contractual security schedules and organisational policies. Common capabilities include identity, authentication, authorisation, secrets and keys, classification, secure defaults, vulnerability handling, audit, incident response, backup, recovery and continuity. The named framework is not the control itself; the service still needs applicable controls and evidence.

### Accessibility and inclusion

People with different abilities, devices, languages, circumstances and ways of interacting can understand and complete the relevant outcome. The service does not make an essential service unavailable because its interaction assumes one body, browser, language, connection or assistive technology.

WCAG is a common technical reference. Accessibility or disability legislation, public-sector standards, procurement conditions and organisational commitments may create the actual duty. Evidence should include representative tasks, keyboard use, assistive technology, content, error recovery and the contexts the service claims to support.

### Understandable, usable and trustworthy service

People can recognise the responsible service, understand what is being asked or decided, complete the task, recover from errors and tell official communication from deception. The service does not use confusing design, hidden conditions or misleading identity to obtain an outcome.

Usability, content, branding, navigation and site shape may be governed by law or regulation in some contexts, and by policy, contract or service promise in others. Branding is not automatically a legal obligation. It can still be an important trust and accountability control, especially where people must recognise an official service, a decision maker, a payment request or a genuine communication.

### Consumer, administrative and procedural fairness

People receive the information, notice, opportunity, treatment and remedy required for the decision or transaction. Charges, terms, eligibility, ranking, refusal, suspension and appeal are not hidden behind an interface that makes the outcome impossible to understand or challenge.

This can include consumer protection, public-sector administrative fairness, financial conduct, complaints, dispute resolution, accessibility of notices and safeguards for automated or high-impact decisions. The service may need to preserve reasons, evidence, notification and review paths rather than only storing a final status.

### Safety, safeguarding and harm prevention

The service identifies and reduces foreseeable harm to people, property, health, rights, finances, information and continuity. It handles vulnerable people, dangerous states, high-impact decisions and unsafe failures with the controls and escalation the context requires.

Sector rules may apply to health, children, education, justice, benefits, employment, transport, critical infrastructure or other sensitive activities. Safety may require human review, separation of duties, warnings, limits, approvals, emergency behaviour, incident reporting and evidence that a risky action was understood and authorised.

### Sector, public-interest and environmental duties

Some obligations arise because of the activity the service supports rather than because it is software. Health, education, justice, social services, employment, housing, transport, elections, public benefits, critical infrastructure, environmental protection and regulated professions may each impose additional duties on people, processes, records, decisions, facilities or suppliers.

These duties may require qualifications, supervision, safeguarding, neutrality, public transparency, continuity, emissions or resource reporting, location controls, specialist records, human review or regulator access. Do not assume that a general privacy or security review covers them. Identify the activity-specific authority, the wider process it governs and the part of the digital service that must provide evidence.

### Financial, payment and tax responsibilities

Money, payment instructions, financial decisions, charges, refunds, benefits, payroll, tax information and financial records are accurate, authorised, traceable and handled according to the applicable regime.

This may involve payment-card rules, tax law, financial-conduct requirements, anti-fraud or anti-money-laundering controls, accounting records and reconciliation. A payment provider may perform part of the technical transaction, but the organisation still needs to understand authority, settlement, failure, refunds, evidence, disputes and retained records.

### Cross-border, sovereignty and suppliers

The organisation knows where information, people, processing, support, infrastructure and decision authority are located, and whether data or responsibility crosses a jurisdictional boundary. Suppliers and connected systems do not create an unexamined gap in security, privacy, records, access, continuity or exit responsibilities.

Common concerns include international transfers, data residency, government access, outsourcing, sub-processors, cloud regions, supplier assurance, contractual flow-down, portability, exit and deletion on termination. The service boundary should show what remains the organisation's responsibility after a supplier performs the mechanism.

### Content, intellectual property and permitted use

The organisation has the right to collect, store, transform, publish and share the content, data, software, images, documents and messages used by the service. The service respects licences, attribution, confidentiality, publication restrictions and takedown or correction duties where they apply.

This domain can affect uploaded documents, generated content, external datasets, fonts, maps, media, open-source components, training material, notifications and public responses. Technical access to a resource is not proof that the organisation may use or redistribute it.

## Sources differ; objectives connect

A privacy act in one country, a data-protection regulation in another and an organisational information policy may use different language while asking related questions about purpose, access, sharing, retention and evidence. A public-records law may create a different route to the shared objective of trustworthy institutional history. A security manual may be mandatory for one government agency and only a useful reference for another organisation.

Do not turn the examples in this catalogue into a universal compliance list. Map the actual sources first, then use these domains to ask what the service and the wider organisation must make true. Where a source creates a duty outside the digital service, record the boundary, hand-off and evidence rather than pretending that a software control completes the obligation alone.

## Relating regulation to quality

Regulatory and organisational obligations often become quality requirements, but the two vocabularies answer different questions. Regulation asks what must be protected, enabled, prevented, recorded or made fair. [Quality Perspectives](./qualities.md) asks how well the service, information and real-world use achieve the intended outcome.

For example, accessibility may be a legal duty and a quality-in-use concern. Security may be a regulatory control and a system-quality characteristic. Accurate, traceable records may support accountability and data quality. Capture the source and duty separately from the quality target and its evidence.

## Related guidance

- [Delivery Guidance](../../../delivery/readme.md) places obligations alongside the systems, material, responsibilities and evidence that make an outcome real.
- [Legal and Regulatory Context](../../../orientation/legal-context.md) explains how to map jurisdictions and delivery context.
- [Regulatory and Obligation Checklist](../checklists/regulatory-obligations.md) provides practical review prompts.
- [Systems Within Systems](../../../orientation/systems-within-systems.md) shows how duties cross enterprise, legal, organisational and digital boundaries.
- [Stakeholder Roles](./stakeholder-roles.md) explains who supplies knowledge, authority and evidence.
- [Quality Perspectives](./qualities.md) explains the relationship between obligations, qualities and evidence.
- [Data Deletion Guidance](../../../development/data-deletion-guidance.md) explains retention, deletion and anonymisation decisions in detail.
