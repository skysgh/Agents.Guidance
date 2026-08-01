# Contracts and Formwork

A contract is a shared agreement between a provider and a consumer. It says what the provider offers, what the consumer may rely on, what the provider needs and how failure is expressed.

A contract can be behavioural, such as a service or repository capability, or structural, such as a model shape required by mapping, schema, validation or discovery infrastructure. A type named `IThing` is not automatically a useful contract. The agreement must protect a real relationship.

## Contracts are formwork

In the building metaphor, contracts are formwork and jigs. Formwork holds concrete in the intended shape while it sets. A jig helps repeated work produce parts that fit the same boundary.

The contract is not the finished object and it is not every private implementation detail. It is the stable shape that lets the implementation develop without making each caller guess. It exposes what must be known at the boundary and leaves room for the responsible implementation to change behind it.

A contract written too late allows objects, screens or providers to become accidental authorities. A contract written too broadly becomes another implementation to maintain. Good formwork is precise where the load is real and open where the implementation is allowed to vary.

## What a useful contract answers

A useful contract makes these questions answerable:

- What capability or structural rule does it provide?
- Which LDM and domain own its meaning, data and lifecycle?
- Who consumes it, and what may each consumer rely upon?
- Which inputs, outputs, states and side effects are meaningful?
- Which identity, authorisation and classification rules apply?
- What happens when the request is invalid, duplicated, delayed, unavailable or partially successful?
- What correlation, diagnostics, audit and recovery evidence is required?
- How can the implementation be replaced or evolved without changing the consumer's meaning?

The answers do not all need to appear as method signatures. Some belong in the contract's documentation, tests, mapping rules or operational agreement. They must be visible somewhere that the consumer and owner can use.

## Behavioural contracts

A service, repository, broker, handler or registry may need a behavioural contract. The contract should express the operation in terms useful to its consumer and owning domain, not in terms of an accidental provider API.

For example, a repository contract may provide a governed request read or a state-changing operation. It should not require callers to know the ORM, table layout or remote storage client. A broker may expose the external operation and its failure meaning without allowing vendor types to become the business model.

A service is not a contract merely because it is stateless. The contract is the protected capability around the service.

## Structural contracts

A model may implement a structural contract because generic infrastructure needs a stable property or convention. Examples include an identity, enabled state, title and description, classification marker or schema contribution.

Structural contracts should be created only when a real consumer uses the convention. Do not force unrelated concepts into one interface to increase apparent reuse. A common shape must not erase a meaningful difference in lifecycle, authority or security.

## Contracts and mappings

Different consumers often need different shapes. A transport request, application command, domain object, persistence record and response view model may all represent related information without being the same contract.

Mapping is the deliberate translation between those representations. It protects the logical model from a screen, provider or database becoming the accidental source of meaning. It also gives security and classification decisions a visible point where information may be included, removed, redacted or transformed.

## Contracts and tests

A contract is only dependable when its important promises can be tested. Tests should cover valid and invalid inputs, allowed and denied access, meaningful state changes, failure and retry behaviour, mapping boundaries and compatibility where consumers depend on the contract over time.

A discovered contract that is never invoked is not a working capability. An interface with no real consumer or substitution need may be ceremony rather than formwork.

## When not to abstract

Do not create a contract merely because a class exists. A local implementation may be clearer when:

- there is no meaningful consumer boundary;
- no substitution, discovery, schema, mapping or policy rule needs an abstraction;
- the type is a small value or cohesive private implementation detail; and
- adding an interface would obscure rather than protect responsibility.

The test is not whether the code contains an interface. The test is whether the agreement makes a real relationship safer to understand, change, test or replace.

## The human and agent views

This paper teaches the reasoning behind contracts and their relationship with objects and implementations. The [agent code convention](../../agents/conventions/development/code-csharp.md) and [agent constraints](../../agents/conventions/foundations/constraints.md) state the precise rules that apply when implementing them.

## Related guidance

- [Human Development Guidance](./readme.md)
- [LDM Layers and Contents](./layers.md)
- [Constants](./constants.md)
- [The Building Metaphor](../reference/building-metaphor.md)
- [The Structure Before the Feature](../orientation/the-structure-before-the-feature.md)
- [Code Conventions](../../agents/conventions/development/code-csharp.md)
- [Development Constraints](../../agents/conventions/foundations/constraints.md)
- [Vertical Slices](../../agents/conventions/capabilities/slices.md)
