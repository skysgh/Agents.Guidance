# Guidance for Dependable Services

Software helps people work, decide, connect and reach services. Its value is measured by the outcome it makes possible and by the care taken with the people, records and decisions that depend on it.

This repository helps teams make services understandable, dependable and able to change. Product, analysis, architecture, development, testing, operations, support and maintenance each contribute to that result, within real limits of time, money, capability and risk.

A service is more than its code. It also includes users, data, dependencies, configuration, evidence, failure behaviour and the responsibilities that keep it useful after release. The guidance connects those parts without asking one role to carry the whole design.

There is no required reading order. A useful next question might be:

- [Where can I find a short, story-led way into the guidance?](./humans/foundations/ways-into-guidance.md)
- [How does the shared guidance fit together?](./humans/readme.md)
- [What belongs in a usable and supportable delivered outcome?](./humans/deliverables/readme.md)
- [What problem or role feels closest to my work?](./humans/examples/readme.md)

The [repository assessment](./.agent-work/assessments/repository-assessment-2026-08-02.md) records the current strengths and the serious gaps that still need dedicated guidance. It is an honest boundary around this repository, not a claim that the material alone makes a regulated system ready for production.

## One body of guidance

This repository is one connected body of delivery guidance expressed for two audiences:

- [Human Guidance](./humans/readme.md) explains meaning, consequences, roles, examples and routes through the work.
- [Agent Guidance](./agents/readme.md) states compact conventions, invariants, decision rules and validation requirements.

The two expressions should agree. Human pages explain why a rule matters and show how it appears in a real situation. Agent conventions make the rule easy to apply consistently during delivery work.

## Routes through delivery

The guidance can be entered through the responsibility that is most useful at the time:

- **Delivery team roles**: product, analysis, architecture, development, testing, operations, support and maintenance each carry part of the service promise.
- **Product management and lifecycle**: keep value, obligations, evidence, change, release and retirement connected rather than treating delivery as a feature queue.
- **Architecture**: make systems, boundaries, capabilities, contracts, dependencies, data meaning and failure behaviour explicit before implementation hides them.
- **Technical leadership and development**: turn the design into achievable increments with coherent logical deployment modules, layers, startup, persistence, integration and operational evidence.
- **Quality**: define quality in use, test the boundaries that matter and retain evidence that supports acceptance and later change.
- **Assurance**: connect security, privacy, legal, accessibility, resilience, recovery and audit obligations to accountable decisions and evidence.
- **Operating**: treat support, monitoring, incidents, maintenance, migration and retirement as part of the service, not as work that begins after release.

The [foundations](./humans/foundations/readme.md), [deliverables](./humans/deliverables/readme.md), [system perspectives](./humans/deliverables/systems/readme.md), [stakeholder responsibilities](./humans/stakeholders/readme.md), [examples](./humans/examples/readme.md) and [reference material](./humans/shared/reference/readme.md) provide the detailed paths.

## Structures for enduring value

The guidance keeps several distinctions visible because collapsing them creates expensive ambiguity:

- a service is larger than its codebase;
- a system boundary is not automatically a repository, project, deployment or team boundary;
- conceptual, logical and physical models answer different questions;
- delivery, service, integration, client and testing systems have different responsibilities;
- catalogues describe shared concepts, checklists prompt evidence and subject material explains how the ideas meet real work;
- a platform-composed or no-code solution is an implementation approach, not a separate kind of system.

Repository assessments, audits, plans and handovers are kept under [.agent-work](./.agent-work/), separate from the published human and agent guidance.
