# Traceability and Evidence

Traceability shows how the reason for work remains connected to what is designed, built, tested, operated and accepted. It is not a demand to link every sentence to every artefact. It is a way to prevent meaning, authority and evidence from disappearing between roles.

## The useful chain

For a material capability, a reader should be able to follow a chain such as:

```text
Driver
  -> Stakeholders and affected people
    -> Objective
      -> Outcome and measures
        -> Business, User, System and Transitional requirements
          -> Use case or flow
            -> Capability and Domain
              -> Contract and acceptance predicate
                -> Implementation and deliverables
                  -> Tests, operational evidence and acceptance
```

The chain is not always one-to-one. One driver may support several outcomes. One outcome may require several capabilities and deliverables. A transitional requirement may support an existing capability rather than a new one. The point is to preserve the relationship and reason for each decision.

## What to trace

Trace a requirement when it carries material meaning, risk or consequence. Record enough to answer:

- Where did it come from?
- Whose need, authority or consequence does it represent?
- What outcome or obligation does it protect?
- Which capability, Domain, system or boundary owns it?
- Which contract or predicate expresses it?
- Which implementation, data, content, trust, manual or operational deliverable fulfils it?
- Which test, review, measurement or operational record proves it?
- Who accepts the result, and within what authority?
- What assumptions, exclusions, conflicts or deferrals remain?

The record may use requirement identifiers, decision records, use-case references, model links, contract names, test case references, delivery registers or a combination. Choose a form that people will maintain and that reviewers can follow.

## Evidence types

Different claims need different evidence:

- **Meaning evidence:** stakeholder examples, definitions, policy sources, SME records and resolved decisions.
- **Requirement evidence:** approved statements, constraints, acceptance conditions, assumptions and exclusions.
- **Design evidence:** Domain and capability models, boundary maps, contracts, state models, flows and architecture decisions.
- **Implementation evidence:** code, configuration, migrations, registered participants, deployment artefacts and content.
- **Functional evidence:** unit, integration, contract, workflow and acceptance tests.
- **Quality evidence:** performance, accessibility, security, privacy, compatibility, resilience, recovery and data-quality results.
- **Transition evidence:** migration reconciliation, training readiness, pilot results, parallel-running decisions, rollback rehearsal and retirement approval.
- **Operational evidence:** readiness, monitoring, incident, backup, restore, recovery, support and maintenance records.
- **Governance evidence:** ownership, approvals, risk decisions, deliberate divergences, review dates and residual-risk acceptance.

A screenshot or successful demonstration may be useful evidence for one visible interaction. It does not prove security, accessibility, migration, recovery, operational readiness or long-term maintainability unless those claims have been separately examined.

## Predicates

An acceptance predicate is a statement that can be evaluated as true or false under stated conditions. It gives a test, review or measurement something precise to check.

Examples:

- Given an authorised assessor and a submitted application with the required evidence, recording an approval creates one auditable decision linked to the correct evidence version.
- Given an unauthorised participant, restricted evidence is not returned through the normal read, search, export or notification paths.
- Given an interrupted submission, retrying the operation does not create a second business submission and the operator can determine the resulting state.
- Given the agreed migration set, every accepted source record is reconciled to a target record or has an explained, owned rejection.
- Given a required dependency is unavailable, readiness is false and the service reports the affected capability and recovery path.

A predicate should name its subject, context, precondition, expected result and relevant failure or safety condition. The exact form may be a test, scenario, property, review question or operational check.

## Evidence and acceptance authority

The person who supplies evidence is not always the person who can accept the result. Distinguish:

- the SME who explains how work is performed;
- the BA who records and tests meaning;
- the Product Owner who orders and accepts product outcomes within delegated authority;
- the business or policy owner who confirms business authority or obligation;
- the architect or technical lead who confirms structural and technical coherence;
- the tester who produces independent or repeatable test evidence;
- the security, privacy, records or assurance specialist who confirms their applicable concerns;
- the operator or maintainer who confirms supportability, readiness and recovery; and
- the sponsor or accountable owner who accepts residual organisational risk when that is within their authority.

Do not use a test pass to impersonate a policy decision. Do not use a Product Owner acceptance to erase a security, records or operational obligation that sits outside their authority.

## Deferrals and negative evidence

Trace what is deliberately not done as well as what is delivered. A deferred capability or requirement should identify:

- its intended place and responsible boundary;
- the reason for deferral;
- affected systems, people, deliverables and risks;
- the condition or date that triggers review;
- the evidence needed before construction or release; and
- the owner and realistic capacity for resolving it.

Evidence can also show that a path is intentionally unavailable. A denied access test, rejected state transition, prevented duplicate, failed readiness check or blocked unsafe deletion may be positive evidence of a requirement being satisfied.

A vague backlog item is not traceability. It does not tell a future team whether the missing work was forgotten, rejected, deferred, owned elsewhere or technically impossible.

## Keep the record usable

Traceability fails when it becomes a ceremonial matrix nobody can understand or update. Keep each link purposeful and use names people can recognise. Prefer a small set of durable references over copying whole requirements into every tool.

Review traceability when:

- the driver, outcome or authority changes;
- a Domain, capability or contract moves;
- a requirement is added, split, rejected or deferred;
- an affected person or connected system is discovered;
- a migration, release or operational condition changes;
- a test or incident reveals that a predicate is incomplete; or
- a deliverable, owner or evidence source is retired.

The record should help a new participant understand why the system behaves as it does and what evidence supports continued reliance on it.

## Handoff questions

Before declaring a capability or requirement complete, ask:

- Can a reader trace its reason, meaning, owner, contract, implementation and evidence?
- Are the affected people, authorities and acceptance roles represented correctly?
- Are functional, quality, transitional and operational claims covered?
- Do predicates test the important successful, denied, invalid, interrupted and recovery paths?
- Are deliverable systems, data, content, trust, discovery, manuals and operational records included?
- Are deferrals, residual risks, assumptions and review conditions visible?
- Can operations and maintenance continue without the original BA or developer reconstructing the reasoning from memory?

## Related guidance

- [Business Analyst Guidance](./readme.md)
- [Drivers, Stakeholders, Objectives and Outcomes](./drivers-stakeholders-objectives-outcomes.md)
- [BUST Requirements](./bust-requirements.md)
- [Use Cases and Flows](./use-cases-and-flows.md)
- [Stakeholder Roles](../../reference/catalogues/stakeholder-roles.md)
- [Domains and Capabilities](../../reference/catalogues/domains-and-capabilities.md)
- [Deliverable Systems](../../reference/catalogues/deliverable-systems.md)
- [Deliverables](../../reference/catalogues/deliverables.md)
- [Deliverables Checklist](../../reference/checklists/deliverables.md)
- [Guidance for Product Owners](../product-owners/readme.md)
- [Guidance for System Design Architects](../../orientation/guidance-for-system-design-architects.md)
