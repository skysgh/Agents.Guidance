# Data Deletion Guidance

Privacy laws and related rules have raised a practical question for every organisation that stores information about people: when should a system remove personal information, and how should it do that safely?

This question is not only about database storage. A deletion decision affects privacy, legal compliance, reporting, history, evidence, safety, care, education, public accountability and the people who rely on the service. It needs a shared answer from the people who understand the law, the records, the service, the data and the technology.

This is international engineering guidance, not legal advice. The applicable answer depends on the country, sector, purpose, people affected, storage locations, contracts and the exact record involved.

## Why not delete?

Deleting a record does more than remove a person from a system. It can change every report, chart, trend and decision that uses the record. Once the record is gone, later readers may mistake missing history for a historical fact.

For example:

- **Funding:** deleting old funding records changes reported totals and can make earlier funding rounds, recipients or outcomes disappear. A team may conclude that funding was lower, more concentrated or more effective than it really was.
- **Students and teachers:** deleting student records after an arbitrary seven-year period can make earlier years appear to contain no students. A chart may then suggest that the number of children per teacher increased dramatically, when the apparent increase is really the point at which the records stopped being retained.
- **Social messages and service use:** deleting older messages can make a service look as if people began using it seven years ago and reached full use almost immediately. The real history may have been a gradual increase over many years.

The same problem appears in health, care, employment, customer support, research, operations and public services. **No retained record is not the same as no historical event.** Reports must distinguish “zero” from “no data retained”.

Deleting the identifiable part of a record while preserving a truthful, non-identifying history may avoid this damage. Deletion is not neutral, and it should not be the first technical response simply because it is easy to describe.

## Why it may not be permitted to be deleted

A request to delete is not automatically a right to destroy the whole record. Another obligation may require the record to remain available, trustworthy or recoverable.

| Record context | Why deletion may be limited | Practical first question |
| --- | --- | --- |
| Government or public records | Records rules may require complete and accurate records, authorised disposal, transfer to an archive or continued public accountability. | Is disposal authorised under the applicable records schedule or records authority? |
| Commercial, financial or employment records | Tax, accounting, employment, consumer, safety, fraud, audit or litigation rules may require retention. | What retention period, legal hold or evidence duty applies? |
| Social, education, health or care records | Safeguarding, continuity of care, professional, education or social-support rules may require a trustworthy history. A required Record of Care is an example of a record that may need to remain available. | Would deletion damage a legal, safety, care, education or accountability duty? |
| Evidence, disputes and investigations | A court order, legal hold, investigation or claim may prevent alteration or destruction. | Has the hold or investigation been cleared by the responsible owner? |
| Ordinary service records | The purpose may have ended, or a privacy framework may provide a right to erasure or disposal, subject to exceptions. | Is the information still needed, and does a lawful exception require it to remain? |

These categories overlap. The same organisation may be a public body, employer, education provider, care provider and service operator at the same time. A country name alone cannot answer the question. The actual record, purpose, sector and applicable rule matter.

## Why delete?

Deletion can be the correct outcome. Personal information should not be retained just because storage is cheap or because nobody has yet decided what to do with it.

Deletion, erasure or an equivalent outcome may be necessary when:

- the lawful purpose has ended and no retention exception applies;
- an applicable privacy rule requires personal information to be removed;
- a contract, court order, regulator or records authority requires destruction;
- the information creates an unacceptable security, identity or safety risk;
- the person is entitled to removal and anonymisation cannot meet the applicable requirement;
- the information is too detailed, unique or sensitive to anonymise reliably; or
- the organisation cannot prove that a continuing identifiable form is lawful and necessary.

The question is not “delete or do nothing”. The question is **what must stop being identifiable, what may lawfully remain, and what outcome does the applicable rule require?** Do not retain personal information forever. Do not destroy useful or required history without checking what the destruction will change.

## How can we delete without deleting the useful record?

### TL;DR

**Yes. Genuine, irreversible anonymisation can be sufficient under the GDPR, California CCPA, Australian APP 11.2 and New Zealand Privacy Act.** It can remove the personal information while preserving a useful historical record.

| Regime | Can genuine anonymisation be sufficient? |
| --- | --- |
| European Union GDPR | **Yes.** Anonymous information is no longer personal data under the GDPR. |
| California CCPA | **Yes.** Genuine statutory deidentification can take the surviving information outside the CCPA definition of personal information. |
| Australia APP 11.2 | **Yes.** The rule expressly permits destruction **or** de-identification. |
| New Zealand Privacy Act | **Yes.** Once information is no longer about an identifiable individual, the privacy retention rule no longer applies to that surviving information. |

Here, “genuine” means that no reasonably available method can identify, single out, link to or infer information about the person. Removing a name or assigning a new reusable ID is not enough. A reusable ID can still be pseudonymous personal information if it allows records about one person to be linked together.

This is an engineering orientation, not a claim that anonymisation overrides a separate legal, records or contractual duty to retain an identifiable record. The supporting paper explains the legal reasoning for each jurisdiction and how to test the result.

The important correction is that most privacy frameworks do **not** say “physically destroy the record”. They usually say one of three things: destroy the personal information, destroy **or** anonymise it, or erase it subject to retention exceptions. That is the legal space for preserving useful history through correct, irreversible anonymisation: the personal information is no longer retained in identifiable form, while the non-identifying record may remain.

- **United States:** the Fair Credit Reporting Act disposal provision and the FTC Disposal Rule, 16 CFR 682.3, apply to covered consumer information. The rule requires proper disposal and gives destruction or electronic erasure so information cannot practicably be read or reconstructed as examples of compliant measures. This is a sector-specific disposal rule, not a requirement to destroy every US historical record, and the rule's examples are not exclusive.
- **European Union:** GDPR Article 17 creates a right to erasure, but allows exceptions for legal obligations, public-interest tasks, expression, archiving or research, public health and legal claims. Genuine anonymisation may take the surviving information outside the personal-data scope, but pseudonymised or linkable information does not.
- **California:** the CCPA right to delete generally concerns personal information and has exceptions, including legal obligations, security, compatible internal use and certain research. Deidentified information is treated differently only when the statutory safeguards are met.
- **Australia:** Australian Privacy Principle 11.2 expressly requires reasonable steps to **destroy or de-identify** personal information that is no longer needed for an APP purpose, subject to records and retention exceptions. It is not a destruction-only rule.
- **New Zealand:** Privacy Act 2020 information privacy principle 9 limits retention, but the Privacy Act does not create a general GDPR-style erasure right. Public Records Act requirements and authorised disposal rules can control public records.

These examples do not support the broad statement that countries generally require physical destruction. The direct answer above is about whether genuine anonymisation can be sufficient. The detailed paper then explains the limits, including records duties, legal holds, sector rules and cases where the data cannot be anonymised safely.

Genuine anonymisation means that the surviving information is no longer reasonably capable of being associated with the person in the environment where it is held and used. It is not achieved merely by removing a name.

### Methods

Use one or more of these methods, according to the record and its continuing purpose:

1. **Separate the personal representation.** Keep identity, contact details, permissions, consent, sensitive attributes and other personal information separate from the historical event, outcome or measure that has continuing value.
2. **Remove direct identifiers.** Remove names, email addresses, account numbers, government identifiers, addresses, phone numbers and other values that directly identify a person.
3. **Remove the route back.** Destroy or isolate mapping keys, lookup tables, stable replacement identifiers and other practical ways to reconnect the surviving record to the person. If a key remains usable, the result is pseudonymisation, not anonymisation.
4. **Clean content and copies.** Check free text, uploaded documents, images, audio, filenames, URLs, logs, notifications and integration payloads. A hidden name in a note can defeat the whole transformation.
5. **Generalise or reduce detail.** Replace exact dates with periods, precise locations with broader areas, and rare categories with safer groups where this prevents singling out while preserving useful trends.
6. **Aggregate.** Keep counts, rates, ranges, totals or trend measures rather than individual-level records. Protect small groups and rare combinations from revealing a person or sensitive fact.
7. **Transform events carefully.** Preserve the fact that an event occurred, its permitted time period, category and non-identifying outcome while removing the person reference and identifying detail.
8. **Handle every controlled copy.** Apply the decision to databases, warehouses, reporting stores, search indexes, caches, replicas, queues, exports, archives, supplier systems, backups and disaster-recovery copies. Define what happens if a backup is restored.
9. **Test reassociation.** Try to identify, single out or link a person using the surviving data, other data available to the organisation or supplier, retained operational knowledge and realistic future combinations.

Encryption, hashing, masking, logical deletion, access restriction and random replacement identifiers may reduce exposure, but they do not automatically anonymise information. If a person can still be linked, inferred or singled out, continue to apply personal-information controls.

## New Zealand example: change the retained representation

New Zealand's information privacy principle 9 says an agency must not keep personal information for longer than is required for the purposes for which it may lawfully be used. That objective can be met without damaging a truthful historical event record.

When a person-level purpose ends, the service can remove the person's identity and every usable route back to it, while retaining the non-identifying event, outcome, category, period or aggregate needed for history and reporting. The personal-information representation is then retired. The surviving record is governed as an anonymous historical record rather than as information about that person.

In internal system terms, this may be recorded as a change in data classification and accountable ownership from a person-linked record to an anonymous historical dataset. It is not a legal transfer of ownership to an “anonymous person”. It is a controlled change to what the retained data represents. The result is lawful only if the surviving data is genuinely no longer about an identifiable individual and no records, legal, contractual or sector rule requires the identifiable form to remain.

## The stakeholder and obligation check

Privacy specialists are one stakeholder, not the sole decision-maker. Their advice may correctly identify a privacy risk or a personal-information obligation, but “because I said so” is not a complete assessment of what the organisation must do. The proposed response must also be tested against records, safety, care, service, reporting, contractual, regulatory, public-accountability and affected-community obligations.

The same caution applies in every direction. A records or service owner cannot use historical value as a reason to keep identifiable information when the continuing purpose has ended. A technology owner cannot use implementation difficulty as a reason to ignore a lawful requirement. Each stakeholder can identify a real obligation and still be unaware of another obligation that changes the correct outcome.

Build the decision as a matrix of requests and consequences:

| Stakeholder or obligation | Question to resolve |
| --- | --- |
| Privacy and affected individuals | What information must stop identifying, singling out or linking to a person? |
| Law, regulation, contracts and courts | What outcome is required: destruction, erasure, anonymisation, restriction, retention or something else? |
| Records and public accountability | What history or evidence must remain, in what form, and who may authorise its alteration or disposal? |
| Service, safety, care and education | What record is needed to protect people, provide continuity or learn from past events? |
| Reporting, research and governance | What measures, trends and comparisons must remain truthful? |
| Technology and operations | Which stores, copies, keys, suppliers and backups are affected, and what methods can actually achieve the required outcome? |

No row automatically wins. The accountable decision-maker must reconcile the obligations, record the trade-offs and select the least destructive outcome that satisfies them. Technologists should explain the available implementations and their consequences. Privacy specialists, legal advisers and records professionals should state the obligations they are responsible for, but none should be expected to know or decide every consequence outside their discipline.

## A shared decision

Before changing a record, the people responsible for the service, records, privacy, reporting and affected communities should agree on:

- the personal information that must stop being identifiable;
- the history, measures and evidence that must remain truthful;
- the rule and purpose that control the decision;
- the selected outcome: retain, restrict, anonymise, aggregate, put beyond use or destroy;
- the stores and copies covered;
- the residual risk and review date; and
- how reports will distinguish “zero”, “not applicable” and “no data retained”.

The aim is a result that protects people and still tells the truth about the service's history.

## Conclusion

This is not avoidance, and it is not being cute with the wording of a deletion obligation. It is a practical way to meet the objectives and obligations defined by different stakeholders: stop keeping personal information when it is no longer needed, preserve truthful historical evidence where it has continuing value, and implement the result in a way that privacy, records, legal, service and technology owners can inspect and defend. Privacy input matters, but it is one part of that decision rather than a veto over the whole matrix.

## Further reading

The [Detailed Data Deletion Considerations](./digital-data-lifecycle.md) paper explains the legal patterns, identifiability tests, copy handling and evidence behind this guide. It is supporting material, not the first read.

## Related guidance

- [Human Development Guidance](./readme.md)
- [Vertical Slices: Common Shafts](./vertical-slices.md)
- [Legal and Regulatory Context](../orientation/legal-context.md)
- [Data Protection Conventions](../../agents/conventions/foundations/data-protection.md)
