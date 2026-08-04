# Data Deletion Guidance

Privacy laws and related rules have raised a practical question for every organisation that stores information about people: when should a system remove personal information, and how should it do that safely?

This question is not only about database storage. A deletion decision affects privacy, legal compliance, reporting, history, evidence, safety, care, education, public accountability and the people who rely on the service. It needs a shared answer from the people who understand the law, the records, the service, the data and the technology.

This is international engineering guidance, not legal advice. The applicable answer depends on the country, sector, purpose, people affected, storage locations, contracts and the exact record involved.

An organisation removes old records to honour a deletion request. Months later, a report appears to show that earlier students, funding recipients or service users never existed. The deletion may have protected a person, but the surrounding system has lost the ability to explain its own history. Another service may face the opposite problem: keeping identifiable information after its purpose has ended.

The people making this decision need more than a database operation. They need a way to preserve lawful, useful history without preserving a personÔÇÖs identity where that identity is no longer needed or permitted.

## Why not delete?

Deleting a record does more than remove a person from a system. It can change every report, chart, trend and decision that uses the record. Once the record is gone, later readers may mistake missing history for a historical fact.

For example:

- **Funding:** deleting old funding records changes reported totals and can make earlier funding rounds, recipients or outcomes disappear. A team may conclude that funding was lower, more concentrated or more effective than it really was.
- **Students and teachers:** deleting student records after an arbitrary seven-year period can make earlier years appear to contain no students. A chart may then suggest that the number of children per teacher increased dramatically, when the apparent increase is really the point at which the records stopped being retained.
- **Social messages and service use:** deleting older messages can make a service look as if people began using it seven years ago and reached full use almost immediately. The real history may have been a gradual increase over many years.

The same problem appears in health, care, employment, customer support, research, operations and public services. **No retained record is not the same as no historical event.** Reports must distinguish ÔÇ£zeroÔÇØ from ÔÇ£no data retainedÔÇØ.

Deleting the identifiable part of a record while preserving a truthful, non-identifying history may avoid this damage. Deletion is not neutral, and it should not be the first technical response simply because it is easy to describe.

## Why it may not be permitted to be deleted

A request to delete is not automatically a right to destroy the whole record. Another obligation may require the record to remain available, trustworthy or recoverable.

Deletion may be limited by public-records rules; tax, accounting, employment, consumer, safety, fraud or audit duties; safeguarding and continuity-of-care needs; court orders, legal holds and investigations; contracts; or a continuing service purpose. These categories overlap, so assess the actual record, purpose, sector and applicable rule rather than relying on the country alone. The governing questions are: what must remain, why must it remain, and who can authorise its alteration or disposal?

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

The question is not ÔÇ£delete or do nothingÔÇØ. The question is **what must stop being identifiable, what may lawfully remain, and what outcome does the applicable rule require?** Personal information needs a continuing lawful and necessary purpose. Useful or required history needs protection from destruction that would change its meaning.

## How can we delete without deleting the useful record?

### TL;DR

**Yes. Genuine, irreversible anonymisation is sufficient under the GDPR, California CCPA, Australian APP 11.2 and New Zealand Privacy Act.** It removes the personal information while preserving a useful historical record.

| Regime | Can genuine anonymisation be sufficient? |
| --- | --- |
| European Union GDPR | **Yes.** Anonymous information is no longer personal data under the GDPR. |
| California CCPA | **Yes.** Genuine statutory deidentification can take the surviving information outside the CCPA definition of personal information. |
| Australia APP 11.2 | **Yes.** The rule expressly permits destruction **or** de-identification. |
| New Zealand Privacy Act | **Yes.** Once information is no longer about an identifiable individual, the privacy retention rule no longer applies to that surviving information. |

Here, ÔÇ£genuine anonymisationÔÇØ means that the surviving information is no longer reasonably capable of being associated with the person in the environment where it is held and used. No reasonably available method may identify, single out, link to or infer information about the person. Removing a name or assigning a new reusable ID is not enough where that ID allows records about one person to be linked with other records or information that can be associated with an identified or identifiable person. In that case, the ID remains pseudonymous personal information.


The important recognisition is that privacy frameworks do **not** say ÔÇ£physically destroy the recordÔÇØ. They usually say one of three things: destroy the personal information, destroy **or** anonymise it, or erase it subject to retention exceptions. That is the legal space for preserving useful history through correct, irreversible anonymisation: the personal information is no longer retained in identifiable form, while the non-identifying record may remain.

- **United States:** the Fair Credit Reporting Act disposal provision and the FTC Disposal Rule, 16 CFR 682.3, apply to covered consumer information. The rule requires proper disposal and gives destruction or electronic erasure so information cannot practicably be read or reconstructed as examples of compliant measures. This is a sector-specific disposal rule, not a requirement to destroy every US historical record, and the rule's examples are not exclusive.
- **European Union:** GDPR Article 17 creates a right to erasure, but allows exceptions for legal obligations, public-interest tasks, expression, archiving or research, public health and legal claims. Genuine anonymisation may take the surviving information outside the personal-data scope, but pseudonymised or linkable information does not.
- **California:** the CCPA right to delete generally concerns personal information and has exceptions, including legal obligations, security, compatible internal use and certain research. Deidentified information is treated differently only when the statutory safeguards are met.
- **Australia:** Australian Privacy Principle 11.2 expressly requires reasonable steps to **destroy or de-identify** personal information that is no longer needed for an APP purpose, subject to records and retention exceptions. It is not a destruction-only rule.
- **New Zealand:** Privacy Act 2020 information privacy principle 9 limits retention but does not create a general GDPR-style erasure right. Where the Public Records Act 2005 applies, its recordkeeping and authorised-disposal requirements supersede the retention outcome under IPP 9.

### Methods

Use one or more of these methods, according to the record and its continuing purpose:

1. **Separate the personal representation.** Keep identity, contact details, permissions, consent, sensitive attributes and other personal information separate from the historical event, outcome or measure that has continuing value.
2. **Remove direct identifiers.** Remove names, email addresses, account numbers, government identifiers, addresses, phone numbers and other values that directly identify a person.
3. **Remove the route back.** Destroy or isolate mapping keys, lookup tables, stable replacement identifiers and other practical ways to reconnect the surviving record to the person. If a key remains usable, the result is pseudonymisation, not anonymisation.
4. **Clean content and copies.** Check free text, uploaded documents, images, audio, filenames, outbound emails, notifications, messages, attachments, URLs, logs and integration payloads. Find every one-time or permanent URL, token and deep link sent to a recipient or supplier. A one-time link is not safe merely because it expires: if it still resolves to the invoice or other record after the name has changed, the recipient may be brought back to a record that no longer belongs to them. Revoke or invalidate the link, or enforce current authorisation so that possession of an old link cannot bypass the current permission check. A link or token is not authorisation. A hidden name in a note can defeat the whole transformation.
5. **Generalise or reduce detail.** Replace exact dates with periods, precise locations with broader areas, and rare categories with safer groups where this prevents singling out while preserving useful trends.
6. **Aggregate.** Keep counts, rates, ranges, totals or trend measures rather than individual-level records. Protect small groups and rare combinations from revealing a person or sensitive fact.
7. **Transform events carefully.** Preserve the fact that an event occurred, its permitted time period, category and non-identifying outcome while removing the person reference and identifying detail.
8. **Handle every controlled copy.** Apply the decision to databases, warehouses, reporting stores, search indexes, caches, replicas, queues, exports, archives, supplier systems, backups and disaster-recovery copies. Define what happens if a backup is restored.
9. **Test reassociation.** Try to identify, single out or link a person using the surviving data, other data available to the organisation or supplier, retained operational knowledge and realistic future combinations.

Encryption, hashing, masking, logical deletion, access restriction and random replacement identifiers may reduce exposure, but they do not anonymise information. If a person can still be linked, inferred or singled out, continue to apply personal-information controls.

## New Zealand example: change the retained representation

Under New Zealand's information privacy principle 9, an agency must not retain personal information longer than required for its lawful purposes. When a person-level purpose ends, the service can retire that representation by removing the person's identity and every usable route back to it while retaining the non-identifying event, outcome, category, period or aggregate needed for history and reporting. Internally, this changes the data classification and accountable responsibility from a person-linked record to an anonymous historical dataset. It changes what the retained data represents; it is not a legal transfer to an ÔÇ£anonymous personÔÇØ.

## Outcome

The outcome protects people and still tells the truth about the service's history while meeting the applicable legal requirements.

It stops retaining personal information when requested and required, while preserving truthful historical evidence where it may lawfully remain, and is implemented so that its reasoning and consequences can be inspected and defended.

## Specialists

Privacy specialists, records professionals, legal advisers, service representatives and technology representatives each provide essential input. None of them decides the whole outcome merely by asserting authority from their own discipline.

## Conclusion

Irreversible anonymisation is not avoidance, and it is not being clever with the wording of a deletion obligation. It is the correct way for an accountable decision-maker to reconcile competing requirements and remain responsible for the outcome.


## Further reading

The [Detailed Data Deletion Considerations](./detailed-data-deletion-considerations.md) paper explains the legal patterns, identifiability tests, copy handling and evidence behind this guide. It is supporting material, not the first read.

## Related guidance

- [Shared System Concerns](./readme.md)
- [Vertical Slices: Common Shafts](../service/vertical-slices.md)
- [Legal and Regulatory Context](../../../orientation/legal-context.md)
- [Data Protection Conventions](../../../../agents/conventions/foundations/data-protection.md)
