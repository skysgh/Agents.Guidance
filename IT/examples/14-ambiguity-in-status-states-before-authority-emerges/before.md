[Up](../readme.md)

# A shared status hides different authorities

A Product Owner asks for an application to show that a request is `Submitted`. The applicant, processing team and Support staff all use the word, so the team treats it as an obvious state.

The developer models `Submitted` as one enum value and adds a single transition from draft. The screen, API, notifications and Support information all use the same label. No one asks what the word means to each participant, who owns the request after the transition or whether the applicant can still change it.

The applicant means "I have released the request to the organisation." The processing team means "we have received and accepted it for work." Support means "the user says they sent it, so we should find it." The system needs a separate authority boundary: submission may relinquish applicant editing without proving that processing has received or accepted the request.

When the processing queue is delayed, the applicant sees `Submitted`, the processor sees nothing, and Support cannot tell whether the request is missing, waiting or accepted. The team adds exceptions to the enum and endpoint rather than resolving the underlying meanings. The implementation has hardened an unresolved business and operational question.

## Evidence

- One status label has competing stakeholder meanings.
- The state does not distinguish applicant control, receipt, processing acceptance or visibility.
- No authority owns the meaning of the transition.
- No failure behaviour exists for delayed or missing receipt.
- Screen, API, notification and Support language repeat the ambiguity.
