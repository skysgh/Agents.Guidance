[Up](./readme.md)

# Configuration and Settings


## Purpose

This document explains why a service needs to distinguish values that help construct the application from choices that people or organisations may manage while the application is running.

## The short version

Configuration helps the building open and operate. Settings are choices available inside the building. They may belong to a user, workspace, organisation or other context, and they may be validated, inherited, protected and changed through the product.

Both may look like key-value pairs. They are not the same responsibility.

Imagine a team adding a setting that lets an organisation choose how long a service waits before closing an inactive case. The value belongs to the organisation and can be changed through the product. The same team also needs a connection target and a secret store location so the service can start. If both values are placed in one untyped collection, the product may expose a deployment secret as an editable setting, or treat a user choice as though it can only change during deployment.

The values may look identical in a configuration file. Their sources, permissions, lifecycles and failure consequences are different. The distinction becomes important when someone needs to change one without redeploying the service, protect another from users and operators, or explain where the effective value came from.

## Configuration

Configuration provides values needed to assemble or operate a service. Examples include connection targets, feature switches needed during startup, provider options and deployment settings.

Configuration is usually supplied by controlled sources such as deployment settings, environment variables, secret stores or host configuration. It should be bound into a typed object, checked early and made available through a clear contract.

In technical language, this is often called typed configuration or options binding. The practical idea is simple: the service should receive a named set of values with known meaning, rather than repeatedly looking up unexplained text keys.

## Settings

Settings are choices that the product may expose, manage or resolve for a user, workspace, organisation or other context. A setting may need a title, description, type, default, validation rule, classification, permission, inheritance rule and effective-value explanation.

A setting is not only its current value. The system may need to explain where the value came from, who may change it, which broader value it overrides and what happens when it is locked or reset.

## Why the distinction matters

If configuration and settings are mixed together, startup values may be exposed as though users can edit them, user choices may be read like immutable deployment configuration, secrets may be treated like ordinary settings, permissions and inheritance may be missing, changes may occur at unsafe times and services may depend on a raw key-value store instead of a meaningful contract.

The distinction is a form of safety. It tells the team which values belong to construction, which belong to product behaviour and which require protected sources.

## How the roles contribute

Business roles describe which choices should be manageable and by whom. Developers define typed contracts and safe resolution behaviour. Testers check defaults, overrides, validation, permissions and reload behaviour. Operations checks deployment sources, secrets, readiness and recovery, while security checks classification, exposure and change authority.

No single role needs to know every detail. The contract brings the views together.

## What is designed, built and deferred

The design should identify the distinction even if the full settings view or provider integration is deferred. It should record which values are configuration, which are settings, which source supplies each value, which boundary has lifecycle responsibility for it and what safe default applies.

Build priority can then be decided with WGF. A small first release may bind configuration without exposing user-managed settings. That is a staged implementation, not permission to mix the two concepts and leave the later design ambiguous.

## Related guidance

- [Startup and discovery](../../agents/conventions/foundations/startup.md)
- [Data protection](../../agents/conventions/foundations/data-protection.md)
- [Human Documentation Writing Style](../../.agent-work/documentation/writing-style.md)
- [YAGNI versus WGF](./design-before-build-and-wgf.md)
