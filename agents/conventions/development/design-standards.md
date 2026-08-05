# Standards

Read this document when designing or reviewing a system, data model, service, interface or user-facing capability. Use the standards that apply to the capability; do not load the entire catalogue for a narrow implementation change.

For people-facing transport and browser security review prompts, read [Security in Transit Checklist](../../../IT/shared/reference/checklists/security-in-transit.md).

## Quality foundation

Treat these ISO/IEC standards as the top-level quality foundation for development decisions:

- **ISO/IEC 25010, Systems and software Quality Requirements and Evaluation (SQuaRE) - Product quality model**: defines product-quality characteristics such as functional suitability, performance efficiency, compatibility, usability, reliability, security, maintainability and portability.
- **ISO/IEC 25012, Data quality model**: defines data-quality characteristics and provides a vocabulary for judging data as it is created, stored, transformed and used.
- **ISO/IEC 25022, Measurement of quality in use**: provides measures for evaluating outcomes in the context of use, including effectiveness, efficiency, satisfaction, freedom from risk and context coverage.

Use these together: 25010 describes the quality of the product, 25012 describes the quality of the data it handles, and 25022 asks whether the resulting system works well for people and organisations in its real context. They are decision and measurement foundations, not a claim that every project must implement every measure.

References: [ISO/IEC 25010](https://www.iso.org/standard/78176.html), [ISO/IEC 25012](https://www.iso.org/standard/35736.html), [ISO/IEC 25022](https://www.iso.org/standard/35746.html).

Do **not** create novel standards or local rules without first considering relevant international and sector standards.

The following catalogue distinguishes mandatory foundations from standards that apply only when the application provides a particular capability.

# Transport and Addressing

HTTP Semantics ÔÇö RFC 9110

Use for all browser, API and service-to-service HTTP communication. Follow the defined meaning of methods, headers, caching and status codes.

HTTP/2 ÔÇö RFC 9113

Use as the normal minimum protocol for modern public web applications.

HTTP/3 ÔÇö RFC 9114

Use where supported by the hosting platform and clients, especially over unreliable or high-latency networks. Retain HTTP/2 compatibility.

TLS 1.3 ÔÇö RFC 8446

Use to protect HTTP and other network connections between devices and services. TLS provides confidentiality, integrity and endpoint authentication. TLS 1.2 should be retained only where legacy compatibility requires it. [TLS 1.3](https://www.rfc-editor.org/info/rfc8446)

URI ÔÇö RFC 3986

Use to identify web resources and API endpoints. Resource identifiers should remain stable and should not unnecessarily reveal implementation details.

Internationalised Resource Identifiers ÔÇö RFC 3987

Use where resource identifiers genuinely need non-ASCII characters. Prefer ordinary ASCII URIs where internationalisation provides no user benefit.

Web Linking ÔÇö RFC 8288

Use to express typed links between related resources, pages, canonical records and alternative representations.

Media Types ÔÇö RFC 6838 and the IANA Media Type Registry

Use `Content-Type` and `Accept` to identify and negotiate representations such as `application/json` and `application/problem+json`.

# Data Encoding and Serialisation

Unicode

Use as the character system for all user-readable information.

UTF-8 ÔÇö RFC 3629

Use as the default encoding for source code, APIs, configuration, documents and persisted text.

Unicode Normalisation

Use a documented normalisation form where user-entered text is compared, searched or constrained for uniqueness. Visually identical Unicode strings are not necessarily binary-identical.

JSON ÔÇö RFC 8259

Use as the default representation for browser-facing APIs and general-purpose system integration.

JSON Schema 2020-12

Use to describe and validate JSON documents, configuration, API payloads, generated forms and event contracts.

YAML 1.2

Use for author-created configuration where comments and a less syntactically dense format are valuable.

Do not use YAML as the normal machine-to-machine API format. Restrict accepted YAML features, because implicit typing, aliases and implementation differences can produce unexpected results.

XML

Use where required by an existing industry standard, document format or integration. It remains appropriate for namespace-rich documents, mixed content, digital signatures and established enterprise protocols.

XML Schema ÔÇö W3C XSD

Use to describe and validate XML documents.

Base64 ÔÇö RFC 4648

Use when small binary values must be represented in a text-only contract. Base64 is encoding, not encryption, and should not be used for large file transfers.

CSV ÔÇö RFC 4180

Use for simple tabular exchange and spreadsheet interoperability. Explicitly define headers, encoding, delimiters, dates and protection against spreadsheet formula injection.

# HTTP API Design

REST

Use as an architectural style for resource-oriented HTTP APIs that benefit from standard HTTP methods, representations, status codes and caching.

REST is not itself a formal technical standard. A design should identify the HTTP and representation standards it follows rather than claiming abstract ÔÇ£REST complianceÔÇØ.

OData 4.01 ÔÇö OASIS and ISO/IEC

Use where API consumers require standardised filtering, projection, ordering, expansion, paging, metadata and modification of queryable resource collections.

Do not adopt OData where a small, purpose-specific API would provide a simpler and safer contract. OData is a formal OASIS and ISO/IEC standard. [OData](https://www.odata.org/)

GraphQL Specification

Use where clients need to select and compose related data through a strongly typed schema, particularly where different clients need materially different response shapes.

GraphQL is an open, vendor-neutral specification governed by the GraphQL Foundation. It is not an ISO, IETF or W3C standard.

Problem Details for HTTP APIs ÔÇö RFC 9457

Use as the standard machine-readable HTTP API error format. Return the appropriate HTTP status code together with an `application/problem+json` document. RFC 9457 supersedes RFC 7807. [Problem Details](https://www.rfc-editor.org/info/rfc9457/)

OpenAPI Specification 3.1

Use to describe synchronous HTTP APIs for documentation, contract review, client generation, testing and compatibility checking.

OpenAPI describes the interface. It does not determine whether the interface is RESTful.

Protocol Buffers and gRPC

Use for controlled service-to-service communication where compact messages, generated contracts and streaming matter more than native browser interoperability.

CloudEvents

Use as the common event envelope where events cross independently developed systems.

AsyncAPI Specification

Use to document asynchronous, event-driven and message-based interfaces.

# Authentication and Authorisation

OpenID Connect 1.0

Use for authentication and federated sign-in: establishing who a person or software agent is and receiving identity claims.

OAuth 2.0 ÔÇö RFC 6749

Use for delegated authorisation and issuing access tokens that permit clients to access protected APIs.

OAuth is primarily an authorisation protocol. Use OpenID Connect when authentication is required. OAuth 2.1 remains an unfinished consolidation effort as of July 2026. [OAuth status](https://oauth.net/2/)

OAuth 2.0 Security Best Current Practice ÔÇö RFC 9700

Apply to every OAuth implementation. It consolidates current security guidance and deprecates unsafe historical flows.

Authorization Code with PKCE ÔÇö RFC 7636

Use for interactive browser, desktop and mobile clients. PKCE should be applied even where the client can otherwise hold a secret.

Bearer Tokens ÔÇö RFC 6750

Use when presenting OAuth access tokens to APIs. Keep bearer tokens short-lived, narrowly scoped and protected during transport and storage.

JSON Web Token ÔÇö RFC 7519

Use where a self-contained token containing signed claims is justified.

Do not use JWT merely because authentication is involved. Opaque tokens are often preferable where immediate revocation, minimal disclosure and central control matter.

JSON Web Signature ÔÇö RFC 7515

Use when a JSON-based value or token must have verifiable integrity and origin.

JSON Web Encryption ÔÇö RFC 7516

Use when token content must also remain confidential. Signing a JWT does not encrypt its claims.

WebAuthn ÔÇö W3C Recommendation

Use for passkeys and phishing-resistant, hardware-backed authentication.

# Transport and Browser Confidentiality

Content Security Policy

Use to restrict the scripts, styles, images, frames and network destinations that browser content may access.

HTTP Strict Transport Security ÔÇö RFC 6797

Use after confirming that the application and all relevant subdomains support HTTPS. It prevents browsers from downgrading connections to HTTP.

Secure Cookies

Use `Secure`, `HttpOnly` and an appropriate `SameSite` policy for session cookies. Prefer protected server-managed cookies over browser-accessible bearer-token storage.

Cross-Origin Resource Sharing

Use only where browser code must call a different origin. Allow explicit trusted origins, methods and headers. CORS is not authentication or authorisation.

Subresource Integrity

Use when fixed third-party scripts or styles are loaded externally and can be pinned to a known cryptographic hash.

OWASP Application Security Verification Standard

Use as the practical security requirements and verification baseline for application design, development and testing.

OWASP Top Ten

Use for awareness and review prompts. It is not a complete application security standard.

ISO/IEC 27001

Use where the organisation requires a governed information security management system or certification.

ISO/IEC 27002

Use as the associated catalogue of information security controls.

# Identifiers

Universally Unique Identifiers ÔÇö RFC 9562

Use UUIDs where identifiers must be generated independently without central sequencing.

UUID version 7

Prefer for new database record identifiers where time ordering improves database index locality. It should not replace an explicit, auditable creation timestamp.

UUID version 4

Use where random identifiers and the absence of embedded creation-time information matter more than index locality.

Sequential identifiers

Use internally where database sequencing is beneficial. Avoid exposing predictable identifiers where enumeration would disclose information or create a security risk.

# Dates, Times, Periods and Scheduling

ISO 8601-1:2019

Use for dates, times, durations and time intervals.

Durations use forms such as `P3D` for three days or `PT30M` for 30 minutes. Calendar periods and elapsed durations must remain distinct: ÔÇ£one monthÔÇØ is not a fixed number of seconds.

ISO 8601-2:2019

Use where extended intervals, uncertain dates, recurring intervals or formal date arithmetic must be exchanged. [ISO 8601 recurrence and intervals](https://www.iso.org/standard/70908.html)

RFC 3339

Use for timestamps exchanged through JSON and HTTP APIs. Include an explicit offset, normally UTC as `Z`, such as `2026-07-24T06:30:00Z`.

IANA Time Zone Database

Use named zones such as `Pacific/Auckland` for future or recurring local times. A fixed offset such as `+12:00` does not capture daylight-saving changes.

Date-only values

Use for birthdays, school dates, anniversaries and other civil dates that do not represent an instant. Do not manufacture a midnight UTC timestamp.

Time-only values

Use for recurring local activities that do not identify a particular date or global instant.

iCalendar ÔÇö RFC 5545

Use to exchange calendar events, tasks, recurrence rules, availability and invitations with calendar systems. [iCalendar](https://www.iana.org/go/rfc5545)

JSCalendar ÔÇö RFC 8984

Use where calendar information is exchanged primarily through JSON and full iCalendar interoperability is unnecessary.

POSIX `crontab`

Use the five-field POSIX form for simple server-side schedules.

There is no single universal cron-expression standard. Quartz, Hangfire, Kubernetes and cloud schedulers have differing field counts and extensions. Cron expressions should therefore be treated as scheduler-specific configuration, not as portable business recurrence contracts. [POSIX `crontab`](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/crontab.html)

Use iCalendar recurrence rules or an explicit domain recurrence model when schedules must be exchanged between systems or understood by users.

# Data Modelling and Storage

ANSI/SPARC Three-Schema Architecture

Use to separate external, conceptual and internal data representations.

The external schema describes consumer-specific views. The conceptual schema describes the logical information model. The internal schema describes physical persistence and optimisation.

Relational Model

Use for information requiring relationships, constraints, transactions, consistency and flexible querying.

SQL ÔÇö ISO/IEC 9075

Use as the governing language standard for relational data access while documenting the particular database dialect and extensions employed.

Database Normalisation

Use to prevent contradictory facts and inappropriate duplication in transactional data. Denormalise only for an identified and measured need.

ACID Transactions

Use where a set of changes must succeed or fail as a consistent unit.

Optimistic Concurrency

Use version values, ETags or equivalent concurrency tokens where more than one actor may update a resource.

Entity Tags ÔÇö HTTP Semantics

Use `ETag`, `If-Match` and `If-None-Match` for HTTP caching and optimistic concurrency.

# Internationalisation and Localisation

Language Tags ÔÇö BCP 47

Use tags such as `en-NZ` and `mi-NZ` to identify the language and, where relevant, regional variation of content.

This is the appropriate standard for ÔÇ£culture-country codesÔÇØ. A locale is not simply a country, and a country is not a language.

Country and Territory Codes ÔÇö ISO 3166-1

Use identifiers such as `NZ`, `AU` and `GB` for countries and territories.

Do not use country codes as proxies for language, currency, nationality, culture or legal jurisdiction.

Unicode Common Locale Data Repository

Use CLDR through the platformÔÇÖs internationalisation libraries to format dates, times, numbers, currencies, measurement units, plural forms and names appropriately for a locale. [Unicode CLDR](https://cldr.unicode.org/)

Unicode Locale Data Markup Language ÔÇö UTS 35

Use when locale rules and data must be represented or exchanged in a standard structured form. LDML is the earlier XML-shaped standard the user may have been recalling. [LDML](https://www.unicode.org/reports/tr35/)

Internationalization Tag Set 2.0 ÔÇö W3C ITS

Use to annotate HTML or XML content for translation and localisation processes, including whether content should be translated, terminology and directionality. [ITS 2.0](https://www.w3.org/TR/its20/)

XLIFF

Use when exchanging translatable source content, translations and localisation workflow metadata between translation systems.

Bidirectional Text ÔÇö Unicode Bidirectional Algorithm

Use when supporting right-to-left and mixed-direction text.

International phone numbers ÔÇö ITU-T E.164

Use for canonical storage and exchange of telephone numbers. Preserve display formatting and extensions separately.

Postal Addressing ÔÇö Universal Postal Union S42

Use where structured international postal-address interoperability is required. For ordinary applications, use a flexible country-aware model rather than assuming every address follows the same field sequence.

# Currency and Commerce

Currency Codes ÔÇö ISO 4217

Use three-letter codes such as `NZD`, `AUD`, `USD` and `EUR`. Store the currency with every monetary amount unless the surrounding contract supplies it unambiguously.

Decimal monetary representation

Represent money using decimal values or integer minor units. Do not use binary floating-point numbers.

CLDR currency formatting

Use to display currency symbols, decimal separators, digit grouping and symbol placement according to the userÔÇÖs locale. Currency and locale are separate: an `en-NZ` user may transact in `USD`.

ISO 20022

Use where the application exchanges financial messages with banks or payment institutions that support or require it.

Payment Card Industry Data Security Standard

Apply where the system stores, processes or transmits payment-card information. Prefer hosted payment components and tokenisation that reduce the applicationÔÇÖs PCI DSS scope.

# Presentation and Browser Technology

HTML Living Standard

Use semantic HTML as the foundation of browser interfaces. Native elements provide established behaviour, validation and accessibility.

CSS

Use standard CSS for presentation, responsive layout and visual adaptation.

CSS Color

Use CSS colour syntax and colour spaces for machine-readable colour definitions. This governs representation, not whether a colour choice is usable or accessible.

ECMAScript ÔÇö ECMA-262

Use as the standard governing JavaScript language behaviour.

TypeScript

Use for static type checking and safer development of substantial ECMAScript applications.

TypeScript is a Microsoft-maintained open-source language specification, not an ECMA standard. Its emitted runtime code must conform to the selected ECMAScript target.

Web Components

Use Custom Elements, Shadow DOM and HTML Templates where reusable browser-native components are required across framework boundaries.

# Accessibility and Colour

Web Content Accessibility Guidelines 2.2

Use WCAG 2.2 Level AA as the normal minimum accessibility target for modern web applications. The abbreviation is WCAG, not CGAG. [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/)

WAI-ARIA

Use ARIA to communicate semantics that native HTML cannot express.

Prefer native HTML elements wherever possible. ARIA changes the accessibility representation; it does not supply behaviour, keyboard handling or visual presentation.

WCAG colour contrast

Use WCAG contrast requirements for text, controls, focus indicators and meaningful graphical objects.

Do not use colour as the only means of communicating status, error, selection or required action.

CSS system colours and user preferences

Respect browser and operating-system preferences such as forced colours, reduced motion, increased contrast and preferred colour scheme.

# Privacy and Erasure

European Union General Data Protection Regulation

Apply where the application processes personal data within the GDPRÔÇÖs territorial scope. ÔÇ£EEC privacyÔÇØ should be replaced with ÔÇ£EU GDPRÔÇØ.

The GDPR governs lawful basis, transparency, purpose limitation, data minimisation, accuracy, retention, security, data-subject rights and accountability.

Right to Erasure ÔÇö GDPR Article 17

Support erasure when Article 17 applies, subject to its exceptions for legal obligations, public interest, freedom of expression, archival purposes and legal claims. [GDPR Article 17](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)

ÔÇ£DeleteÔÇØ should not automatically mean deleting the entire business record. A system may need to retain financial, contractual, security or evidential records while removing personal information that is no longer lawfully required.

However, soft deletion alone is not erasure. Erasure requires either physical deletion or effective, irreversible anonymisation so the person is no longer identifiable. Pseudonymisation, encryption, hiding a record and removing it from ordinary queries do not by themselves satisfy erasure while re-identification remains possible. [EU anonymisation guidance](https://www.edps.europa.eu/system/files/2021-04/21-04-27_aepd-edps_anonymisation_en_5.pdf)

The correct terms are anonymisation, de-identification and removal of personal information. ÔÇ£DeanonymisationÔÇØ means the opposite: reconstructing a personÔÇÖs identity.

New Zealand Privacy Act 2020

Apply where personal information is collected, held, used or disclosed in New Zealand.

Retention and disposal rules should reconcile privacy obligations with the Public Records Act 2005 and any applicable financial, education or public-sector retention requirements.

# Auditability and Records

ISO 15489-1:2016 ÔÇö Records Management

Use to govern the creation, capture, protection, retention and authorised disposal of records that provide evidence of business activity. [ISO 15489-1](https://www.iso.org/standard/62542.html)

ISO/IEC 27001 and ISO/IEC 27002

Use for security logging, event protection, access control, accountability and operational monitoring.

W3C Trace Context

Use to propagate trace identifiers across HTTP and service boundaries.

OpenTelemetry

Use for vendor-neutral collection and correlation of traces, metrics and logs.

Financial reporting and auditing standards

There is no single technical ÔÇ£financial auditabilityÔÇØ standard that tells a web application how to implement its audit trail. Applicable accounting and audit requirements depend on the jurisdiction, organisation and type of transaction.

A financially material system should record the actor, authority, action, subject, previous value, resulting value, timestamp, effective date, reason, source and correlation identifier. Records should be append-only or tamper-evident, access-controlled, retained under an approved schedule and reconcilable to source transactions.

Financial corrections should normally be made through reversals and replacement entries rather than destructive updates. Audit history should not contain unnecessary personal information merely because the operational record once did.

# API and Application Evolution

Semantic Versioning

Use for independently released packages and libraries where major, minor and patch compatibility promises can be honoured.

Deprecation HTTP Header ÔÇö RFC 9745

Use to signal that an HTTP resource or endpoint is deprecated.

Sunset HTTP Header ÔÇö RFC 8594

Use to communicate when a deprecated endpoint is expected to become unavailable.

Backward-compatible evolution

Prefer additive changes. Do not repurpose fields, change their meaning or make optional fields mandatory without a governed breaking change.

# Software Quality

ISO/IEC 25010

Use to define and assess quality characteristics including reliability, security, maintainability, usability, compatibility and performance efficiency.

ISO/IEC/IEEE 29119

Use where the organisation requires formally governed software testing processes and documentation. It is generally unnecessary as a development-team test convention unless external assurance requires it.

# Important Corrections

REST is an architectural style, not a formal standard.

GraphQL is an open governed specification, although not an ISO, IETF or W3C standard.

OData is a formal OASIS and ISO/IEC standard.

RFC 9457 is the current Problem Details standard.

OAuth concerns authorisation; OpenID Connect supplies authentication.

WCAG is the accessibility standard; WAI-ARIA supplements semantic HTML.

Cron has a limited POSIX baseline, but modern cron dialects are scheduler-specific.

A locale should be represented using BCP 47, not by joining a language and country code arbitrarily.

GDPR erasure may preserve a non-personal business record, but soft deletion or reversible pseudonymisation is not erasure.

ÔÇ£DeanonymisationÔÇØ means restoring identity; the intended terms are anonymisation or de-identification.



