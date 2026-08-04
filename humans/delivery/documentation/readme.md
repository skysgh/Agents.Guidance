# Documentation in Delivery

Documentation is part of delivery when people need information to understand, use, operate, support, change, assure or retire the outcome. It is not decoration added after the code. It carries meaning that may not fit safely inside a screen, interface, configuration file or deployment pipeline.

## Why it matters

When useful knowledge is missing, people fill the gap with memory, guesswork or private instructions. A service may still build and run, but the next person may not know what a decision means, how an operator should respond, which dependency is trusted, what a user has been promised or how an old record should be treated. That creates avoidable support cost and makes change less safe.

Documentation also has a lifecycle. It can become inaccurate when a contract changes, a dependency expires, an operating route moves, a policy changes or a responsibility is transferred. A document without a responsible maintainer and a review condition can give false confidence.

## What we mean by documentation

Documentation is information deliberately prepared for a reader, decision or activity. It may include user help, operational manuals, support information, architecture decisions, interface descriptions, data and integration explanations, security and recovery procedures, release information, evidence descriptions and maintenance knowledge.

Not every note needs to become a formal document. The useful question is whether a person or team needs the information to make a material decision, perform a recurring activity, understand a boundary or recover from a failure. The form should fit the reader, consequence, change rate and required evidence.

The [Deliverables catalogue](../../shared/reference/catalogues/deliverables.md) describes documentation as part of the wider delivered outcome. The [Human Documentation Writing Style](../../reference/writing-style.md) explains how human-facing guidance should introduce meaning, terminology, consequences and routes. The [Documentation Register](../../maintenance/documentation-register.md) records significant changes to this repository's guidance; it is not a substitute for a project's own documentation set.

## How to develop it

Start with the activity or decision that the documentation must support:

- identify the reader and what they need to do, decide, understand or prove;
- identify the responsible boundary and the authority behind the information;
- state the scope, assumptions, dependencies and consequences of being wrong;
- choose a form that the reader can find and use at the required moment;
- connect the document to the contract, system, deliverable, registry or evidence it describes;
- name the maintainer, review condition, lifecycle and retirement treatment; and
- test the route with the people who must rely on it, including during failure or handover.

Keep descriptive teaching separate from project-specific evidence where that helps readers. A catalogue can explain a recurring kind of thing. A project document can record the actual decision, configuration, responsibility or procedure. Do not copy a changing enterprise source into a project document without preserving its source, version or effective date.

## Questions to consider

Use the relevant [Engineering Checklists](../../shared/reference/checklists/readme.md) after understanding the subject. The [Deliverables Checklist](../../shared/reference/checklists/deliverables.md) helps check whether the outcome includes the documentation and operational material it needs. Subject checklists help with security, dependencies, interfaces, obligations and other evidence that documentation may need to describe.

Ask:

- Who will use this, and at what point in the work or lifecycle?
- What wrong decision, failed action or lost knowledge would this prevent?
- Which source or authority makes the information trustworthy?
- Who can change it, who reviews it and how will staleness be detected?
- Does it describe a general concept, a project decision, a live procedure or evidence of something done?
- Can the intended reader find and understand it under normal pressure?
- What happens when the service, dependency, policy, responsibility or document itself is retired?

This route is the human entry point. The catalogue and checklists remain the detailed reference surfaces, and project teams remain responsible for producing the documentation their outcome requires.

## Related guidance

- [Delivery Guidance](../readme.md)
- [Deliverables](../../shared/reference/catalogues/deliverables.md)
- [Human Documentation Writing Style](../../reference/writing-style.md)
- [Engineering Checklists](../../shared/reference/checklists/readme.md)
- [Documentation Register](../../maintenance/documentation-register.md)
- [Documentation and Workflow Conventions](../../../agents/conventions/documentation/readme.md)
