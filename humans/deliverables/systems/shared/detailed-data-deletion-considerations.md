[Up](readme.md)

# Detailed Data Deletion Considerations

This paper addresses digital data. It is about rows, fields, objects, files, indexes, caches, backups, logs and derived datasets. It is not a general rule about paper records, physical media or other disposal regimes.

A deletion request reaches the database, but the same personÔÇÖs information also appears in a search index, an event, an export, a notification, a backup and a support record. Removing one row may leave the person identifiable elsewhere, while deleting every related fact may destroy evidence the organisation has a duty to preserve. The difficult part is not the delete statement. It is understanding the identity, purpose, copies and consequences across the whole system.

This is engineering guidance, not legal advice. The applicable law depends on the data, the purpose, the organisation, the people affected, the sector, the storage locations and the jurisdictions involved. A real service or high-consequence decision needs the relevant legal, records, privacy and business authorities as well as engineering evidence.

The [Data Deletion Guidance](./data-deletion-guidance.md) gives the plain-language answer and stakeholder questions. This paper provides the deeper reasoning, legal patterns and technical tests behind that guide.

Deletion also changes what an organisation can know about its own history. Removing funding records changes totals and outcomes. Removing student records can make earlier years look as if they had no students. Removing old social messages can make gradual service adoption look sudden. These are not only storage or privacy effects: they can create false reports and lead people to make decisions from an incomplete past.

## The position

Physical deletion is not the universal legal test for digital data.

The strongest defensible engineering position is:

> Preserve useful digital history, evidence and aggregate value where the surviving data is no longer personal information, the remaining data cannot reasonably be linked to an individual, and no applicable law, order, contract or recordkeeping rule requires destruction.

This position does not mean that a system may keep personal information forever. It means that the team should separate the legal protection of people from the physical destruction of database storage.

When personal information is no longer permitted or needed, the preferred order is:

1. Remove the personal representation and its usable linkage paths.
2. Irreversibly anonymise or de-identify the remaining digital record when it still has lawful value.
3. Put data beyond use or restrict it while a lawful retention duty, legal hold or technical disposal window applies.
4. Physically delete or securely erase the relevant digital content when the applicable rule requires it or when no defensible de-identification route remains.

Physical deletion is not the default merely because it is easy to describe. Anonymisation is not a label for hiding a record while keeping a practical route back to a person.

## The controlling distinction

The legal question is usually not "Did the database row disappear?" It is closer to:

- Is the information still about an identified or reasonably identifiable person?
- Can the information still be linked to an individual by this organisation, a recipient or a reasonably available additional dataset?
- Can the information be used to single out, infer facts about or make decisions about that person?
- Is the organisation still required or permitted to retain the identifiable form?
- Does another law, court order, legal hold, contract or records regime require retention or destruction?

A record may remain in digital storage while its personal-data representation is removed. For example, a historical event may retain its time period, category, outcome and non-identifying measures after the person reference, free text and unique combination of attributes have been removed. Whether this is lawful depends on the identifiability assessment and the applicable rule. The fact that the record remains searchable or backed up does not answer that question by itself.

## Use the terms precisely

| Term | Meaning for engineering | What it does not prove |
| --- | --- | --- |
| Physical deletion | Removing the relevant digital content from the system or storage medium so it cannot be retrieved in the ordinary or required technical sense. | That every copy, derivative or legal obligation has been handled. |
| Logical deletion | Hiding or marking a record as deleted while the content remains recoverable. | That personal information has been erased or anonymised. |
| Erasure | A legal outcome in which the applicable personal information is removed, no longer retained or otherwise dealt with as the relevant law requires. | That an entire business record must always be destroyed. |
| Anonymisation or de-identification | Transforming information so it is no longer about an identified or reasonably identifiable individual in the relevant context. | That removing one name or foreign key is enough. |
| Pseudonymisation | Replacing identifiers while retaining a separate key or another practical route to attribution. | That the information is anonymous or outside a personal-data regime. |
| Aggregation | Combining information so that the output describes a group or population rather than an individual. | That small groups, rare combinations or source data are safe. |
| Retention | Keeping information because a purpose, legal duty, recordkeeping rule, legal hold or other authorised reason continues. | That retention permits unrelated use or indefinite storage. |
| Disposal | The authorised lifecycle action for a record. It may include transfer, destruction, alteration, de-identification or another legally recognised outcome. | That disposal always means deleting every byte. |

An encrypted record is still a record that can be recovered with the key. A hash of an identifier may still be a persistent or linkable identifier. A random replacement identifier is still pseudonymous if a mapping table, event history or other data can reconnect it to the person.

## Disassociation is necessary but not sufficient

Removing the relationship between a record and its represented person or responsible party is often an important step. It is not the complete test.

A de-identification assessment should consider at least:

- direct identifiers such as names, email addresses, account numbers and government identifiers;
- free text, uploaded documents, images, audio, URLs, filenames and error details that identify a person;
- outbound emails, notifications, generated documents and attachments, including one-time or permanent URLs, access tokens and deep links; a one-time link is not safe merely because it expires if it still resolves to the invoice or other record after the name or person association has changed. Revoke or invalidate the link, or enforce current authorisation so that an old link cannot bypass the current permission check;
- stable replacement identifiers, hashes, tokens and record numbers that permit linkage;
- dates, times, locations, occupations, rare events and small groups that permit singling out;
- combinations of ordinary fields that become unique together;
- other data held by the organisation, suppliers, recipients or reasonably available third parties;
- whether the data can be used to infer sensitive facts about a person even without a name;
- search indexes, caches, exports, reports, logs, telemetry, replicas, backups and archives; and
- whether a person, operator or supplier can reconstruct the mapping from operational knowledge or retained keys.

The useful question is not whether one identifier was removed. It is whether a person can still be reasonably identified, singled out or linked in the environment in which the data is held and used. The answer must consider both technical means and organisational behaviour. A policy saying "do not re-identify" is valuable, but it does not cure a technically easy and routinely available re-identification path on its own.

## A digital design that preserves value

A defensible lifecycle can preserve a record without preserving the person's identity.

### Keep the personal representation separate

Keep identity, contact details, permissions, consent, sensitive attributes and other personal information in an owned and protected representation. Do not scatter them through event text, filenames, audit messages, search documents or integration payloads.

### Make the transformation explicit

Anonymisation or de-identification is an authorised lifecycle operation. It needs a responsible authority, trigger, policy version, scope, method, risk assessment, result and evidence. It should identify which stores and downstream recipients were covered.

Do not use a generic `deleted` flag when the system needs to distinguish active, restricted, retired, anonymised, destroyed, under legal hold and retained-for-lawful-purpose states.

### Remove the route back

Destroy or isolate the mapping material that would reconnect the surviving record to the person. If a mapping must remain for a lawful purpose, the result is pseudonymised, not anonymous, and must continue to receive personal-information controls.

### Transform all usable copies

Apply the lifecycle decision to the copies that the service controls: primary storage, object storage, search indexes, caches, exports, reports, queues, logs, telemetry, replicas, analytics stores and backups. Where immediate technical removal from a backup is not possible, define expiry, access restriction, restoration handling and proof that the personal form will not return to active use.

### Preserve non-personal evidence carefully

A surviving historical record should retain only the facts needed for its continuing purpose. Avoid keeping a detailed quasi-identifier set merely because it is technically interesting. A de-identified record can still create harm if it exposes a small group, a rare event or a sensitive pattern.

### Identity deletion and anonymous reassignment

There are two common ways to preserve useful history without retaining the personÔÇÖs identity:

1. **Delete the identity information.** Remove names, contact details, account identifiers and other direct identifiers, then remove mapping keys, free-text references, media, logs and other routes that could reconnect the record to the person.
2. **Reassign the record to a non-linkable anonymous identity.** Replace the person reference with a value that has no relationship to the person and cannot be used to join that personÔÇÖs records across systems or events. This can preserve the existence, category, date range or outcome of an event without preserving who experienced it.

The second pattern does not mean assigning a new stable customer number. A value that lets the organisation link records about one person with other records or information that can be associated with an identified or identifiable person remains pseudonymous personal information. That is pseudonymisation, not anonymisation, and the surviving data remains subject to personal-information controls. The jurisdictional sections below explain why the two genuine patterns can satisfy the relevant framework and where another legal duty can still require the identifiable record.

## Jurisdictional analysis

The following is a cross-jurisdiction engineering reading of selected privacy frameworks. The named jurisdictions are examples of different legal patterns, not an exhaustive list, country ranking or universal baseline. It is not a substitute for checking the actual statute, sector rule, contract, order or regulator guidance that applies to the service.

The direct answer for the four regimes covered by the front-door paper is **yes in every case**: genuine anonymisation is sufficient. The legal route differs. Under the GDPR and New Zealand Privacy Act, the result is no longer personal data or personal information. Under California law, it must meet the statutory conditions for deidentified information. Under Australian APP 11.2, de-identification is expressly an alternative to destruction. In every case, the transformation must be real rather than cosmetic, and another rule may still require the identifiable record to be preserved.

| Jurisdiction | Legal shape relevant to digital data | Strong engineering consequence |
| --- | --- | --- |
| European Union | The GDPR is concerned with personal data about an identified or identifiable person. GDPR Article 4(1) and Recital 26 use direct and indirect identifiability, including reasonably likely means. Recital 26 says the principles do not apply to anonymous information or information made anonymous so the person is no longer identifiable. Article 5(1)(e) limits storage, and Article 17 provides a right to erasure subject to exceptions. Pseudonymised data remains personal data where attribution is possible. | Do not delete useful history merely to make a row disappear. First test whether the remaining data can be made genuinely anonymous and whether all accessible linkage paths are removed. Treat pseudonymised, encrypted, masked and logically deleted data as personal data. Where Article 17 applies, remove the personal data and controlled copies or make the data effectively anonymous only where that satisfies the actual legal and factual circumstances. Preserve records required for legal claims, legal obligations, public interest, archival or other Article 17 exceptions. |
| United States | The United States has no single comprehensive federal private-sector deletion rule. Requirements are sectoral and state-based. The Fair Credit Reporting Act requires disposal rules for consumer information; the federal disposal rule recognises destruction or electronic erasure so information cannot practicably be read or reconstructed. HIPAA recognises de-identification methods for protected health information. FTC enforcement can also attach to misleading privacy or deletion promises. | Do not claim that US law universally requires or universally rejects digital deletion. Identify the sector and state. Preserve non-personal de-identified data where the applicable regime recognises it, but satisfy rules that require destruction or erasure of identifiable consumer information. Do not promise "deleted" when the service only hides or pseudonymises data. |
| California | The CCPA gives consumers a right to request deletion of personal information, subject to exceptions. It defines personal information broadly to include information reasonably capable of being associated with or linked to a consumer. It excludes deidentified information, but only where the business takes reasonable measures against association, publicly commits to keep and use it in deidentified form and prevents recipients from reidentifying it. | Retain useful digital history only after the surviving representation meets the statutory deidentified conditions. Removing a customer ID is not enough if other fields, hashes, free text, data held elsewhere or unique combinations can link the record. For a deletion request, delete or transform the personal information and address service providers, contractors, third parties and derived stores as required; use the statutory exceptions only for the permitted purpose. |
| Australia | Australian Privacy Principle 11.2 requires an APP entity, when personal information is no longer needed for an APP purpose, to take reasonable steps to destroy it or ensure that it is de-identified. Exceptions include Commonwealth records and information required to be retained by Australian law or a court or tribunal order. OAIC guidance expressly discusses de-identification, all copies, backups, putting electronic information beyond use and irretrievable destruction. | This is direct support for the non-physical-first position. Choose destruction or de-identification based on the facts and risk. If de-identification is appropriate, actively assess and manage re-identification risk. If it is not possible to reduce that risk appropriately, destroy the personal information or use the limited beyond-use approach described by the OAIC. |
| New Zealand | Privacy Act 2020 information privacy principle 9 limits retention of personal information to no longer than required for the lawful purposes for which it may be used. New Zealand does not generally create a GDPR-style universal erasure right in the Privacy Act. Public-sector records are also subject to the Public Records Act 2005, which requires authorised recordkeeping and controls disposal of public records. | Do not retain identifiable personal information without a continuing purpose. Preserve de-identified digital history where it is no longer personal information and another rule permits it. For public records and regulated records, obtain the required disposal authority; privacy minimisation does not authorise an engineer to destroy a record that records law requires the organisation to preserve. |

### European Union

**Answer: yes.** Genuine anonymisation is sufficient under the GDPR because anonymous information is no longer personal data. That is the legal basis for retaining a historical event, measure or aggregate after removing the personÔÇÖs identity and every reasonably available route back to that person.

The GDPR gives the strongest reason to distinguish personal data from the bytes that once contained it. The definition in [Article 4(1)](https://eur-lex.europa.eu/eli/reg/2016/679/oj) includes direct and indirect identification. [Recital 26](https://eur-lex.europa.eu/eli/reg/2016/679/oj) says that the principles do not apply to anonymous information or information rendered anonymous so the data subject is not or is no longer identifiable, taking account of reasonably likely means of identification.

That is not permission to call pseudonymisation anonymisation. [Article 4(5)](https://eur-lex.europa.eu/eli/reg/2016/679/oj) describes pseudonymisation as processing that prevents attribution without additional information. If the additional information or another practical route can reconnect the data, the data remains personal data.

[Article 17](https://eur-lex.europa.eu/eli/reg/2016/679/oj) creates a right to erasure, but it also contains exceptions. An organisation may need to retain information to comply with a legal obligation, perform a task in the public interest, exercise freedom of expression, support archiving or research, or establish, exercise or defend legal claims. [Article 5(1)(e)](https://eur-lex.europa.eu/eli/reg/2016/679/oj) still requires storage to be limited to what is necessary for the purpose.

The engineering conclusion is narrow but powerful: when the legal duty is about personal data, an irreversible transformation that leaves no reasonably available route to identify the person can preserve non-personal value without preserving the personal data. That conclusion must be demonstrated for the actual data environment. It is not satisfied by hiding a row, encrypting it, retaining a key, removing one foreign key or keeping identifying text in an audit log.

### United States

There is no single US answer. Federal privacy obligations are divided among sectoral laws, federal agency rules, state laws, contracts and enforcement against misleading practices.

The [Fair Credit Reporting Act disposal provision](https://www.law.cornell.edu/uscode/text/15/1681w) requires regulations for the proper disposal of consumer information. The [FTC disposal rule](https://www.ecfr.gov/current/title-16/chapter-I/subchapter-F/part-682/section-682.3) expressly includes destruction or erasure of electronic media so the information cannot practicably be read or reconstructed. This is a real digital destruction constraint, but it applies to the covered consumer-information context. It is not a universal rule for every US digital record.

For protected health information, [HIPAA de-identification](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164/subpart-E/section-164.514) recognises both the safe-harbor removal method and expert determination. Properly deidentified information is treated differently from protected health information under that rule. A health service must still consider other laws, contracts, research conditions, state law and whether the data has actually met the selected method.

The US position therefore supports a disciplined argument, not a universal slogan. Where a sectoral rule requires identifiable consumer information to be destroyed or erased, meet that rule. Where the data is genuinely outside the relevant personal-information definition, preserving it may be lawful and useful. Do not infer either result from the fact that the data is digital.

### California

**Answer: yes.** Genuine deidentification is sufficient under the CCPA. The surviving record must meet the statutory conditions, not merely have its name field removed.

The [CCPA right to delete](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?sectionNum=1798.105.&lawCode=CIV) applies to personal information and has exceptions, including completing a transaction, security, research, internal compatible uses and compliance with a legal obligation. It also requires attention to service providers, contractors and third parties.

The [CCPA definitions](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?sectionNum=1798.140.&lawCode=CIV) define personal information by reasonable association or linkage, and exclude deidentified information. The exclusion is conditional: the business must take reasonable measures to prevent association, publicly commit to maintain and use the information in deidentified form and contractually bind recipients to the same protections.

California therefore gives a strong legal basis for preserving a genuinely deidentified digital record, but it rejects the weak version of the argument. A record is not deidentified simply because its owner column is null. If a stable token, rare combination, free text field, source dataset or recipient can reasonably link it back to a consumer, it remains within the risk of personal information.

### Australia

**Answer: yes.** De-identification is expressly permitted as a solution under APP 11.2. An APP entity may destroy the personal information or ensure that it is de-identified when it is no longer needed for an APP purpose.

[APP 11.2](https://www.oaic.gov.au/privacy/australian-privacy-principles/australian-privacy-principles-guidelines/chapter-11-app-11-security-of-personal-information) is unusually clear for this question. When an APP entity no longer needs personal information for an APP purpose, it must take reasonable steps to **destroy or de-identify** it, subject to the stated records and retention exceptions.

The OAIC guidance also says that the obligation applies to copies held by the organisation, including archived copies and backups. It defines destruction as information that can no longer be retrieved, discusses putting electronic data beyond use where irretrievable destruction is not possible, and says de-identification may be more appropriate where the information retains value. It also requires active assessment and management of re-identification risk.

This is the clearest support for the position in this paper: Australian privacy law does not force the organisation to destroy useful digital information where a reasonable and effective de-identification route meets the obligation. It does require the organisation to use that route honestly, address copies and backups, and destroy the personal information when de-identification cannot reduce the risk appropriately.

### New Zealand

**Answer: yes.** Genuine anonymisation is sufficient under the Privacy Act because the Act regulates personal information, meaning information about an identifiable individual. Once the surviving historical record is no longer about an identifiable individual, IPP 9 does not require that non-personal record to be discarded.

[Privacy Act 2020, section 22, information privacy principle 9](https://www.legislation.govt.nz/act/public/2020/31/latest/whole.html) limits retention of personal information to no longer than is required for the purposes for which it may lawfully be used. The principle is about continuing necessity and purpose, not a universal command to erase an entire digital record on request.

This gives a clear New Zealand implementation pattern. While the record is needed to operate a service for an identifiable person, it is held as personal information with the corresponding access, correction, security and retention controls. When that person-level purpose ends, the service can:

1. preserve the historical event, outcome, category, period or aggregate needed for a continuing lawful purpose;
2. remove names, identifiers, free text, media, mappings, stable person tokens and other routes back to the individual;
3. transform every controlled copy, including indexes, reports, logs, exports and backups; and
4. reclassify the surviving representation as an anonymous historical record for internal governance and reporting.

The last step is a change in the data's representation and accountable responsibility inside the system. It is not a legal transfer of responsibility to an ÔÇ£anonymous personÔÇØ. It means that the retained record is no longer managed as information about the original individual because it no longer identifies, singles out or links to that individual. A new stable ID that still joins the person's events would not achieve this; it would remain pseudonymous personal information.

This can satisfy IPP 9 without erasing the historical event record. A report can still count the event, measure the outcome and show the trend, while the agency no longer keeps the person's identity for a purpose that has ended. The agency must still check whether the Public Records Act, a sector rule, a legal hold, a contract, a court order or another obligation requires the identifiable record to remain.

New Zealand's public records regime matters just as much for public offices. The [Public Records Act 2005](https://www.legislation.govt.nz/act/public/2005/40/latest/whole.html) requires full and accurate records and restricts disposal without authority. Its disposal model can include transfer, alteration, destruction, sale or discharge. Privacy minimisation and recordkeeping preservation therefore have to be reconciled rather than treated as one automatically defeating the other.

The engineering position is to remove or de-identify personal information when the lawful purpose ends, preserve genuinely non-personal history where it remains useful, and obtain the required records authority before altering or destroying a public record. A system must not use a privacy label as an excuse for unauthorised destruction.

## When to give in

Fight for preservation of digital value first. Give in to physical or technical destruction only when one of these conditions applies:

- an applicable law, order, legal hold, contract or records authority requires destruction or erasure of the identifiable content;
- the retained representation is still personal information because it can reasonably be linked, singled out or used to infer facts about a person;
- a regulator, court, customer or data subject is entitled to the identifiable record in a form that anonymisation cannot satisfy;
- the data is too sparse, unique, detailed or sensitive for re-identification risk to be reduced appropriately;
- a downstream copy, backup, log, key or supplier-controlled store preserves a practical route back to the person; or
- the organisation cannot prove what was transformed, where the copies were, who authorised the action and why the result meets the applicable rule.

Even then, do not delete more than the rule requires. Remove the personal information and the routes that make it personal. Preserve permitted non-personal facts, evidence and aggregate value separately when doing so is lawful and safe.

## Evidence of a defensible outcome

For every digital data lifecycle decision, keep evidence of:

- the jurisdiction, sector and legal or contractual source considered;
- the original data categories and their identifiers or linkage risks;
- the continuing purpose or the reason that purpose ended;
- the selected outcome: retain, restrict, put beyond use, destroy, anonymise or de-identify;
- the method and the risk assessment, including uniqueness and linkage analysis;
- the stores, copies, backups, indexes, exports and recipients covered;
- the mapping keys or identity links removed, destroyed or retained under authority;
- the legal hold, archival or records-management decision;
- the test that attempts to identify or link a person fail within the relevant environment; and
- the responsible authority, approval, timestamp, policy version and follow-up review date.

The goal is not to produce a reassuring delete event. The goal is to prove that the service stopped retaining personal information where required while preserving only the digital value that the law and the organisation still permit it to keep.

## Conclusion

This is not avoidance or a clever relabelling exercise. It is an achievable solution that fits the objectives and obligations defined by different stakeholders: privacy may require the personal representation to stop being retained, while service, records, reporting and accountability representatives may need the truthful historical event to remain. Privacy advice is an important input, but it is not the whole decision or an automatic veto over other lawful obligations. The engineering task is to reconcile the matrix, satisfy all applicable duties where genuine anonymisation can do so, and prove that the retained record is no longer personal information.

## Related guidance

- [Shared System Concerns](./readme.md)
- [Data Deletion Guidance](./data-deletion-guidance.md)
- [Vertical Slices: Common Shafts](../service/vertical-slices.md)
- [Cross-Cutting Services](../../../development/cross-cutting-services.md)
- [System LDM Services](../service/services.md)
- [Legal and Regulatory Context](../../../foundations/legal-context.md)
- [Guidance for Developers](../../../foundations/guidance-for-developers.md)
- [Guidance for Tech Leads](../../../foundations/guidance-for-tech-leads.md)
- [Guidance for System Design Architects](../../../foundations/guidance-for-system-design-architects.md)
- [Data Protection Conventions](../../../../agents/conventions/foundations/data-protection.md)
