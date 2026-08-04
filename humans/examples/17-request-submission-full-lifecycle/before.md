# A request status journey is treated as a screen feature

A service team is asked to add a request form and a status page before the next reporting deadline. The visible work looks small: accept the form, show a status value and send a notification.

The team does not first agree what the status values mean. `Submitted`, `Received` and `Accepted for processing` are treated as interchangeable labels. The database stores the latest string, the browser displays it, and a notification worker reuses the same model for its own decisions.

The delivery plan also leaves several boundaries implicit:

- duplicate submissions and receipt timeouts have no authoritative outcome;
- the source and receiving systems have no stable cross-system scenario identity;
- test data has no classification, retention period or deletion method;
- Support cannot distinguish an applicant report from an operational diagnosis;
- Operations cannot tell technical intake delay from a legitimate business state;
- a changed status contract has no consumer, compatibility or rollback plan; and
- retirement means stopping deployment, without deciding what happens to records, routes, credentials, queues or support commitments.

The first release appears successful until a dependency slows down. An applicant submits twice, Support sees two plausible statuses, Operations sees a generic error rate and the processing team cannot say which receipt is authoritative. A later status change requires a data repair, a notification change and a consumer migration that nobody planned.

The problem was not that the team moved quickly. The problem was that it promised a lifecycle without making its authorities, contracts, evidence and residual obligations visible.
