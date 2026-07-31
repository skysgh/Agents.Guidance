# API Lifecycle

## Purpose

This document explains what changes when a service begins serving other people, teams or systems. A public contract is not only a successful response. It is a promise that must remain understandable and safe as the service changes.

## The short version

Before publishing a contract, decide what callers may ask for, what they may receive, what errors mean, how they may retry, how the contract will change and how protected information is handled.

The outside world may depend on the contract for years. A small-looking change can affect another team, a user interface, a report, a finance system or an automated process.

## The contract has more than one part

A useful consumer contract includes:

- accepted inputs and questions;
- returned information and its meaning;
- actions and state changes;
- errors and their remedies;
- permission and classification rules;
- limits such as paging, cost and rate;
- retry and idempotency behaviour;
- correlation and diagnostic information; and
- versioning, deprecation and migration expectations.

In technical language, this is an API lifecycle. The practical idea is that a contract has a beginning, a useful life and a managed change or retirement path.

## How the roles contribute

- business analysis explains the consumer outcome and meaning of the information;
- developers define a contract that can be implemented without exposing internal storage;
- testers check successful, invalid, denied, retried and concurrent use;
- operations checks limits, readiness, diagnostics and dependency failures;
- security checks authentication, authorisation and data classification; and
- delivery records compatibility, migration and deprecation decisions.

## Change safely

Prefer additive changes when possible. If a change may break a consumer, record the affected users or systems, the migration path, the deprecation period and the removal condition before releasing it.

A queryable read can allow consumers to shape an approved result without requiring a new fixed endpoint for every need. That flexibility still requires mapping, visibility rules, supported query operations and cost limits.

A command should make its state change clear. Where callers may retry, the command should be safe to repeat or use an idempotency key.

## What is designed, built and deferred

A contract may be designed before every client is known. Define the stable meaning, boundaries, security and change policy from the available evidence. Build the first consumer need, then extend the contract through the compatibility rules rather than allowing each client to invent a private version.

## Related guidance

- [Palette Technical Terms](../palette/technical-terms.md)
- [IQueryable and Governed Queryability](../../agents/conventions/foundations/iqueryable.md)
- [API lifecycle rules](../../agents/conventions/capabilities/api-lifecycle.md)
- [Stewardship and Deferred Design](./responsible-boundaries-and-deferred-design.md)
