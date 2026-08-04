# Sponsor Guidance

The status report says the service is on time and within budget. Then a user cannot complete an important request, the operator cannot tell whether a dependency is failing and the maintainer discovers that nobody can safely change the data model. The visible delivery is real, but it is not yet the service the organisation thought it was buying.

This is where the Sponsor's perspective begins. A Sponsor protects the organisation's commitment to a service. They make sure the organisation has a justified purpose, an accountable owner, suitable authority and enough resources to deliver, operate, change and retire the service responsibly.

The Sponsor is not simply the person who supplies money. They are the person, group or authority able to ask whether the organisation is getting what it agreed to pursue, within the constraints it accepted, with evidence strong enough to support continuation. They do not personally design the architecture, order the backlog, write the code or perform the tests. They make sure those responsibilities exist, have capable owners and are not allowed to disappear when delivery pressure rises.

If you are deciding whether to invest, continue, release, intervene or retire, this route gives you the questions and handoffs to examine. It is about holding the promise to account, not taking over the specialist work that makes the promise dependable.

## The Sponsor's central question

The Sponsor asks:

> Are we delivering the service we committed to, for the people and obligations that justified it, within the agreed constraints, with the qualities and evidence needed to trust it?

That question applies before investment, during discovery and delivery, at release, throughout operation and at retirement. It also applies when the service does not deliver what someone reasonably thought was their due: a user waiting for an outcome, an operator needing recoverability, a monitoring team needing useful signals, an assurance function needing evidence or a maintainer needing a changeable system.

## Three responsibilities that must stay distinct

The responsibilities often meet, but they are not interchangeable:

- **Sponsor:** protects the organisational commitment, funding, authority, risk acceptance and whole-life accountability. They ask whether the organisation should continue, change direction, intervene or stop.
- **Product Manager:** protects product purpose, value, viability, strategic fit and longer-term direction within budget, capacity, obligations and risk. They help choose the objectives worth pursuing.
- **Product Owner:** protects clarity and near-term value by ordering outcomes, foundations and evidence within delegated authority. They help decide what should be delivered next and what must be true before it can be accepted.

The Sponsor does not replace these roles. The Product Manager does not silently become the Sponsor when a strategic or organisational decision is difficult. The Product Owner does not make an incomplete delivery acceptable by moving an unmet responsibility into a backlog without an owner, consequence and decision date.

## What the Sponsor should expect

The exact thresholds depend on the service. The expectation is that each material claim has a responsible owner, a context, a threshold and evidence.

### A justified and bounded commitment

The Sponsor should be able to see:

- the outcome, obligation or problem that justifies the service;
- the people, communities, customers and internal groups that depend on it;
- the scope of the promise and the important exclusions;
- the budget, schedule, capacity, supplier and dependency constraints;
- the whole-life cost of delivery, operation, support, maintenance, change and retirement;
- the value, avoided harm or obligation served by that cost; and
- the conditions that would cause continuation, intervention, replanning or retirement.

Value should materially exceed whole-life cost and risk. A fixed numerical multiple is not a universal rule: legal duties, public value, safety, equity and avoided harm may matter alongside financial return. The Sponsor should still reject a promise whose value cannot plausibly justify its cost and consequences.

## The promise over the service life

The Sponsor should expect the evidence to change as the service moves through its life:

- **Before investment:** the purpose, affected people, obligation, value, whole-life cost, constraints and accountable owner are clear enough to justify commitment.
- **During discovery and delivery:** assumptions become decisions, responsibilities become requirements and designs, and important risks receive owners and evidence rather than optimistic status.
- **Before release:** intended function, relevant qualities, operational readiness, support, recovery, security, accessibility and specialist controls are demonstrated under the conditions that matter.
- **In operation:** actual use, incidents, complaints, cost, capacity, availability, support demand and change impact are compared with the promise.
- **At major change or retirement:** compatibility, migration, records, communication, continuity, residual risk and the return or disposal of entrusted data are decided and evidenced.

The Sponsor does not need every artefact in every checkpoint. They do need a truthful account of what is known, what is not yet proven, who owns the gap and what decision follows.

### A service people can trust

The Sponsor should expect the team to make relevant quality responsibilities explicit, not hide them behind a general statement such as "high quality". Depending on context, this includes:

- **Security and protection:** entrusted data, identities, money and authority are protected, with appropriate privacy, access control, audit and safe failure.
- **Accessibility and inclusion:** relevant people can reach, understand and complete the service without avoidable barriers.
- **Functional suitability:** the service provides the intended information, objects, decisions or outcomes, including important exceptions and failure paths.
- **Data and information quality:** information is accurate enough for its use, complete enough for its purpose, timely, traceable, understandable and governed by an identified authority.
- **Availability and resilience:** the service remains usable under expected conditions and has an honest response to dependency failure, overload and disruption.
- **Recoverability and continuity:** people know how the service is restored, how data is protected or reconciled and what happens when recovery is incomplete.
- **Maintainability and changeability:** the organisation can diagnose, repair, improve, migrate and retire the service without losing meaning or creating unmanaged risk.
- **Compatibility and integration:** connected systems exchange the right meaning, with ownership, versioning, failure handling and reconciliation visible.
- **Observability and supportability:** operators, support, monitoring, assurance and control functions receive the information and access they need to do their work.
- **Parsimony and resource responsibility:** the design is no more complicated, expensive or resource-hungry than the responsibilities require, while retaining necessary foundations.

These concerns connect to the [Quality Perspectives](../../reference/catalogues/qualities.md) catalogue. The Sponsor should require the relevant specialists to define the context and evidence. They should not pretend to be the specialist who supplies it.

### Focused use, wherever it occurs

"Mobile ready" need not mean a mobile application. A useful Sponsor expectation is that important actions are focused, understandable and possible with the available attention, space, input method and connection. Designing for a small screen can expose a deeper requirement: one clear primary action, better data entry and less accidental combination of unrelated tasks. Mobile support may be the result, but it is not automatically the requirement.

### Bounded self-correction

The Sponsor should expect a dependable service to detect abnormal conditions, prevent or contain unsafe effects, retry operations that are safe to retry, reconcile uncertain outcomes, recover where possible and make uncertainty visible. It should learn from incidents and evidence. It must not silently invent or alter consequential business decisions merely because automation is available. Corrections with material meaning need rules, authority, audit and a human route where appropriate.

## Delivery against the promise

At each meaningful checkpoint, the Sponsor should ask for a comparison between what was promised, what was delivered, what evidence exists and what remains unresolved:

- What did we agree would be true by this point?
- What is true in the real service, not only in a demonstration?
- Which requirements, quality thresholds, operational controls or specialist needs are not met?
- What evidence supports the claim, under which conditions and with what limitations?
- Which variance is accepted, by whom, until when and with what consequence?
- Has anything been quietly removed, weakened, deferred or reinterpreted?
- Who is responsible for the missing outcome or evidence, and what authority do they need?
- What should change in scope, budget, schedule, design, ownership or direction?

This is not an invitation to micromanage delivery. It is a requirement that delivery claims remain answerable. A green status, completed ticket or deployed build is not evidence that the organisational promise has been met.

## The Sponsor's handoffs

The Sponsor should make the commitment and escalation path clear, then expect the roles below to supply their part:

- the **Product Manager** explains objectives, value, viability, constraints and longer-term choices;
- the **Product Owner** orders outcomes, foundations, acceptance and evidence for the next delivery path;
- the **Business Owner and Stakeholder Analyst** protect business meaning, affected people, obligations and representation;
- the **Architect** makes boundaries, dependencies, qualities and consequences coherent;
- the **Technical Lead and Developers** make the design achievable and implement the contracts and behaviours;
- **Testers and assurance specialists** challenge claims and produce independent or suitably rigorous evidence;
- **Operators, Support and Maintainers** show that the occupied service can be run, supported, recovered and changed; and
- **Security, Privacy, Records, Monitoring, Change Control, Finance and other relevant groups** supply the specialist controls, evidence and decisions their responsibilities require.

The Sponsor should be concerned when a handoff ends with "someone else owns it" but no named owner, authority, evidence or return path exists.

## When to intervene

Intervention is justified when:

- the service promise, owner or authority is unclear;
- delivery is reporting progress while agreed outcomes or evidence remain absent;
- a constraint is being treated as permission to break an unstated promise;
- security, privacy, accessibility, operational or data responsibilities have no capable owner;
- the whole-life cost or risk no longer supports the expected value;
- a supplier or dependency has become a single point of failure without an accepted response; or
- people are receiving less than the outcome, protection or service level the organisation committed to.

The Sponsor may then require clarification, additional evidence, a changed objective, a safer sequence, more capability, an explicit risk decision, a pause or retirement. Their job is not to force a team to claim success. It is to ensure the organisation makes an informed decision about the truth.

## Related guidance

- [Stakeholder Guidance](../readme.md)
- [Product Manager Guidance](../product-managers/readme.md)
- [Product Owner Guidance](../product-owners/readme.md)
- [Stakeholder Roles Catalogue](../../reference/catalogues/stakeholder-roles.md)
- [Quality Perspectives](../../reference/catalogues/qualities.md)
- [Shared Requirements](../../shared/requirements.md)
- [Software Development Lifecycle](../../reference/catalogues/sdlc.md)
