# A current student record becomes the identity

A school service is asked to show which students belong to which schools. The team creates one `Student` record with `PersonId`, `SchoolId` and a current status. The record is treated as the identity of the person in the service, and the school relationship is updated whenever the person changes school.

The first screen works. Later, the service must answer which school a person attended on a past date, who authorised a withdrawal, whether two memberships overlapped, and how a cross-system student identifier maps to a person. The current `SchoolId` has overwritten the earlier relationship. A withdrawn student cannot be distinguished from a person who was never enrolled, and a school move appears to change the student's identity.

The conceptual phrase "student at a school" was physicalised as one record. The team did not separate the enduring person and institution from the transient membership.

## Evidence

- `Student` is used for person identity, student classification and school membership.
- There are no effective dates or reliable historical membership records.
- Withdrawal has no independent authority, state or audit meaning.
- A school change changes the current record instead of ending one relationship and starting another.
- Cross-system tests cover only the current screen and cannot verify historical membership or identity preservation.
