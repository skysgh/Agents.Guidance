[Up](../readme.md)

# Product pressure removes the foundation

A Product Owner is asked to release a new application journey before the reporting deadline. The visible work is a form, a submit button and a status page. The team agrees to defer the difficult parts: duplicate submission handling, an audit trail, accessibility review, support information, operational alerts, recovery behaviour and a migration plan for existing records.

The work is described as "the application feature". No one records which foundations are missing, who owns them or what condition would reopen the decision. The Product Owner is told that the team can add them later.

The first release appears successful. A user submits twice during a slow dependency call and two records are created. Support cannot explain which record is authoritative. Operations sees only a generic error rate and cannot tell whether work is stuck or duplicated. Testing cannot reproduce the production state because the test data and dependency failure conditions were never defined. Maintenance later discovers that the status values are stored in several incompatible forms, so correcting the duplicate behaviour requires a data repair and a contract change.

The visible feature was delivered, but its missing foundations became work for users, Support, Operations, Testing and Maintenance. The cost was transferred rather than removed. Because the transfer was known and had no owner, trigger or credible repayment capacity, the omission became technical theft.

## Evidence

- No recorded foundation or scope decision.
- No owner or trigger for the deferred work.
- No duplicate or dependency-failure test evidence.
- No Support, Operational or Maintenance information for the new behaviour.
- No authoritative status contract or recovery path.
