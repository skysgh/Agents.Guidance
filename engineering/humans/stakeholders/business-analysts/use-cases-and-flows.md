# Use Cases and Flows

Use cases and flows help people understand how capabilities are used together to achieve an outcome. They are useful bridges between requirements and design, but they are not substitutes for Domains, capabilities, contracts, predicates or operational evidence.

## Use case

A use case describes a goal-oriented interaction between an actor and a system or capability. It explains what the actor is trying to achieve, the context, the expected result and the important alternatives or failures.

A useful use case identifies:

- the actor or connected system and its authority;
- the goal and intended outcome;
- the entry condition and relevant starting state;
- the information and capabilities involved;
- the normal steps and meaningful alternatives;
- invalid, denied, interrupted and dependency-failure paths;
- the resulting state, record, communication or evidence; and
- quality, transition and operational conditions that matter.

The actor is not always a person at a screen. It may be a support worker, operator, scheduled process, connected service or recovery procedure. A person affected by the outcome may also need representation even when they are not the actor.

Do not write a use case as a list of interface clicks. The interface is one physical representation of a conceptual interaction. The use case should preserve the goal, responsibility, rule and consequence when the interface, channel or connected system changes.

## Flow

A flow coordinates two or more capabilities, decisions or participants into a recognisable journey. Examples include preparing and submitting a request, assessing evidence, approving a decision, issuing a payment, publishing information or recovering an interrupted process.

A flow should state:

- the outcome that the whole journey is meant to achieve;
- the capabilities and Domains it coordinates;
- the handoff between each participant;
- the information, authority and contract crossing each boundary;
- the ordering, waiting, retry and compensation behaviour;
- the points where a human or system decision is required;
- the effect of partial success, rejection, duplication or outage; and
- the evidence that the journey completed or requires intervention.

A flow is not a super-capability that owns every rule. The capabilities retain their own meaning, data, state, permissions and contracts. The flow coordinates them and records the journey-level responsibility.

## A practical structure

For a material use case or flow, record:

```text
Name and purpose
Actors, affected people and authority
Driver, objective and outcome
Starting conditions and assumptions
Capabilities, Domains and contracts involved
Normal path
Alternative and exception paths
State, data, notification and evidence effects
Quality, security, privacy and accessibility conditions
Transition and operational conditions
Open questions, exclusions and deliberate deferrals
Acceptance predicates and test evidence
```

The structure can be a page, model, scenario table, decision record or linked set of artefacts. Use the smallest form that preserves the meaning and allows another role to continue safely.

## Discover the real journey

Ask people to describe what they are trying to achieve and what happens around the visible interaction:

- What starts the work?
- What must be known before the first action?
- Who checks or decides each important point?
- What information is created, copied, transformed or handed over?
- Which states are visible to which participants?
- What happens when the next person or system is unavailable?
- What does the person do when the service rejects, times out or duplicates the work?
- Which notifications, documents, reports or support actions are part of the outcome?
- How is completion recognised, and who can reopen or correct it?
- What must be retained, deleted, anonymised or made available later?

Workarounds are important evidence. A manual spreadsheet, email confirmation, phone call or support escalation may represent a missing capability, a policy control, a temporary transition or an unsafe bypass. Do not copy it into the new flow without understanding its purpose and authority.

## State and handoff discipline

Many use cases fail because they describe actions without states. For every meaningful transition, ask:

- What state is the subject in before the action?
- Who or what owns the decision to change it?
- Which conditions must be true?
- What record, event, notification or audit evidence is produced?
- What happens if the action is repeated or interrupted?
- Can the transition be reversed, corrected or appealed?
- Which other capability is allowed to observe or act on the new state?

A handoff should name the provider, consumer, contract, authority, data classification, timing and failure behaviour. “Send it to finance” is a useful business phrase, but it is not enough to design a dependable cross-system handoff.

## Flow and vertical slice relationship

A vertical slice carries one owned capability through its relevant boundaries. A flow coordinates several such slices.

For example, an application flow may coordinate:

- an applicant's preparation capability;
- an evidence capability;
- a submission capability;
- an assessment capability;
- an approval capability; and
- a notification or payment capability.

The flow may need ordering, correlation, status, retry and recovery. It should not move the evidence rules into the submission coordinator or make the notification system the owner of approval state. Use [Vertical Slices](../../development/vertical-slices.md) and [Horizontal Flows](../../../agents/conventions/capabilities/flows.md) for the engineering consequences.

## Quality and failure paths

A convincing happy path is only one part of a use case. Include the paths that expose the real service obligation:

- missing or conflicting information;
- denied or changed authority;
- invalid state transition;
- duplicate or retried action;
- dependency delay or outage;
- partial completion;
- notification failure;
- lost connection or interrupted session;
- recovery by an operator or support person;
- privacy, classification or data-minimisation constraint;
- accessibility or language need; and
- migration, rollback or retirement condition.

Each path should lead to a meaningful result, safe failure, explicit operator action or visible unresolved question. “An error occurs” is not an outcome.

## Handoff questions

Before a use case or flow moves into architecture, development or testing, ask:

- Is the actor's goal and the affected person's consequence clear?
- Are the participating capabilities and Domains named?
- Does each handoff have a responsible provider, consumer and contract?
- Are state, authority, data, evidence and failure behaviour explicit?
- Does the flow coordinate rather than duplicate capability rules?
- Can the normal, denied, invalid, interrupted and recovered paths be tested?
- Which transitional and operational deliverables are required?
- What remains assumed, disputed, excluded or deferred?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [Elicitation](./elicitation.md)
- [Functional and Quality Requirements](./functional-and-quality-requirements.md)
- [Domains and Capabilities](../../reference/catalogues/domains-and-capabilities.md)
- [Sites, Flows, Views and Components](../../reference/catalogues/sites-flows-views-components.md)
- [Vertical Slices](../../development/vertical-slices.md)
- [Horizontal Flows](../../../agents/conventions/capabilities/flows.md)
- [Guidance for System Design Architects](../../orientation/guidance-for-system-design-architects.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
