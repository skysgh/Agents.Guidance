# Human Documentation Rewrite Plan

This plan governs the gradual rewrite of the guidance for wide human consumption while preserving precise agent instructions.

## Aim

Make the engineering ideas understandable before requiring technical vocabulary. The human route should help business analysts, developers, testers, operations, security roles and delivery stakeholders contribute to one shared design. The agent route should remain compact, precise and task-selective.

The recurring teaching model is a high-rise building:

- bedrock is dependable evidence;
- foundations are contracts, security, lifecycle and other structural necessities;
- vertical shafts carry capabilities through layers;
- slabs provide stable boundaries and platform services; and
- horizontal flows connect capabilities and adapt them for each tenant or user experience.

## Rules for every rewrite

1. Preserve technical meaning unless a deliberate design change is recorded.
2. Explain the concept before naming the technical term.
3. Define each necessary technical term when it first appears.
4. Use short, translation-friendly sentences.
5. Explain the consequences of inclusion, omission and deferral.
6. State how each relevant role contributes evidence.
7. Distinguish what is designed, built and deferred.
8. Link to the precise agent or implementation rule without copying the whole explanation.
9. Add a before-and-after example when the subject is difficult to recognise.
10. Validate links, terminology, technical accuracy and whitespace before marking a batch complete.

## Reading layers

Each subject should have three layers where the subject warrants them:

1. **Human orientation**: why the subject matters, in plain language.
2. **Portable pattern**: the reusable design and its invariants.
3. **Agent or binding rule**: the precise action required for a task or repository.

The human layer may use more words. The agent layer must not load those words by default.

## Batch sequence

### Batch 1: Entry and writing rules

- [Human start](./README.md)
- [Human writing style](../reference/writing-style.md)
- [Agent gateway](../../agents/readme.md)
- root README and root agent entry point

Status: in progress. Gateways and writing contract created.

### Batch 2: Problem and purpose

- [Current state](../orientation/current-state.md)
- [Stakeholder outcomes](../orientation/what-this-guidance-gives.md)
- [Design Before Build and WGF](../orientation/design-before-build-and-wgf.md)
- [Developer orientation](../../agents/conventions/development/developers-need-to-know.md)

Status: existing human papers available; review for style-contract compliance.

### Batch 3: Foundational platform subjects

- principles and constraints;
- contracts and structural models;
- configuration and settings;
- startup and discovery;
- access, security and data protection;
- schema, mapping and caching.

Status: existing documents and examples available; subject review required.

### Batch 4: Capability and journey subjects

- vertical slices;
- horizontal flows;
- stewardship and deferred design;
- queryability;
- API lifecycle.

Status: existing documents and examples available; subject review required.

### Batch 5: Developer and operational subjects

- code organisation and language conventions;
- testing and automation;
- operations and readiness;
- dependencies and framework isolation;
- accessibility and frontend security;
- completion gates.

Status: agent alignment and human routing complete; independent technical review pending. Existing MB and BASE human rationale remains in the documentation repository and is linked from the precise instruction layer.

### Batch 6: Repository and MB bindings

- repository bindings;
- MB human explanations;
- MB precise instructions;
- BASE implementation bindings.

Status: begin only after portable human and agent layers are stable.

## Batch protocol

Each prompt batch should follow this sequence:

1. Read this plan and the current register.
2. Select only the assigned batch.
3. Analyse the selected documents without editing.
4. Identify technical meaning, audience, terminology, examples and link risks.
5. Rewrite the human layer using the writing contract.
6. Align the agent layer without duplicating the human explanation.
7. Review the result from a non-specialist, developer, tester and operations perspective.
8. Validate links, terminology, technical consistency and whitespace.
9. Update the register with completed work and unresolved questions.
10. Stop at the batch boundary so the next prompt can review a clean unit.

## Completion rule

The registry rewrite is complete only when each document is classified, its audience is explicit, its human and agent layers are intentional and aligned, its terminology is defined, its links resolve, its technical meaning has been reviewed and unresolved questions are recorded.

For the progress counter, **complete means both Human and Agent documents are complete for the subject**. A human rewrite may be marked `human-complete` while the corresponding agent alignment is still pending. That is progress, but it is not completion of the subject.
