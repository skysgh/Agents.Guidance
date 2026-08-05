[Up](../readme.md)

# A BA exposes the authority before implementation

The BA does not treat `Submitted` as settled because several people use the same word. They ask each participant what the status means, what they may do next, what evidence they need and which event changes their authority.

The elicitation records competing accounts:

- The applicant means that they have released control of the request and cannot edit it without an allowed return path.
- The processing team means that the organisation has received the request and can begin work.
- Support needs to distinguish a completed submission from a submission that is not yet visible to the organisation.
- The system needs separate evidence for the applicant's submission, organisational receipt and processing acceptance.

The BA brings the conflict to the Product Owner, the business authority for processing and the relevant technical and operational SMEs. The decision is to distinguish the lifecycle and authority conditions rather than force them into one label:

- `Submitted` records the applicant's act and relinquishes applicant editing.
- `Received` records that the organisation has accepted the submission into its intake boundary.
- `Accepted for processing` records the processor's authority to begin the defined work.
- A returned or rejected outcome records why the request leaves the normal path and what authority is restored or ends.

The decision also defines the receipt contract, correlation identifier, retry and duplicate behaviour, notification meaning, Support wording, operational alert and recovery path. The BA records the authority, rationale, affected stakeholders, transitional consequence and acceptance predicates. Technical design can now map the meanings into contracts and storage without inventing them.

Testing can distinguish a submitted request waiting for receipt from a received request waiting for processing. Operations can observe intake delay without declaring the business request lost. Support can explain what the user knows and what the organisation has verified. The Product Owner can accept the outcome against explicit predicates rather than a screen label.

## Evidence

- Competing meanings and stakeholder accounts are recorded before implementation.
- Each state has an authority, entry condition, permitted actions and exit condition.
- The receipt contract defines correlation, retry, duplicate and failure outcomes.
- Acceptance predicates cover applicant control, organisational receipt, processing acceptance and delayed intake.
- Support, Testing and Operations receive language and evidence appropriate to their responsibilities.

## What changed afterwards

The BA did not decide the business meaning alone. They exposed the disagreement while it was still inexpensive to resolve, brought it to the responsible authority and carried the decision into requirements, contracts, design, tests and operational information. The team avoided building one ambiguous word into every boundary.
