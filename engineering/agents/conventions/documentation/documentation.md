
# Conventions - Documentation 

Apply these conventions when creating, restructuring, reviewing or retiring documentation intended for stakeholders, operators or maintainers.

For the human-facing writing contract, apply [Human Documentation Writing Style](../../../humans/reference/writing-style.md). It requires concept-first explanations, plain and translation-friendly language, consistent terminology, role-inclusive examples and a clear separation between human explanation and compact agent rules.


## Role Based First

There is no use developing documentation for consumption by a stakeholder with no experience or expertise in the matter. 

Therefore, organise documentation by Stakeholder Role at the first level:


```
01.Sponsors/		# Sponsors
11.Consumers/		# Service Consumers
12.Providers/		# Service Providers
21.Supporters/		# Tier 1 Supporters
22.Operators/		#
23.Maintainers/		# 
24.Developers/		# Implementation 
31.QA/				#
32.C&A/				# 
41.Analysts/		# BAs
42.Architects/		# Architects
51.Change/			#  
61.Delivery/
```

## Secondary Levels

...depend on the role. Not everyone is involved with Discovery, for example. 

However, there is a general overall sequence to consider.

`Discovery` leads to `Discussions` (Options Analysis) which lead to `Decisions` (ADRs), `Definitions` (FRs and QRs) and, where procurement or market response is involved, a controlled `Solution Architecture Document` (SAD). Respondents may provide `Solution Design Documents` (SDDs). Once a solution is accepted, `Technical Design Documents` (TDDs) are developed for the relevant work and referenced from work items, decisions, contracts, tests and evidence. This leads to `Development` and then `Deployment`, at which point `Support`, `Operations` and `Maintenance` must be in place.


## Registers

See also [Registries](../development/registries.md) - a special live document set of documentation.


## Ongoing Maintenance

While ARDs and other identifiers are suppossed to stay stable, new decisions can replace older decisions. 

Periodically scan and keep references amongst ADRs, Delivery Plans, and Implementation papers.

## Navigable File References

When referring to another local Markdown file, source file, configuration file, image, or other repository file, use a full Markdown link with a useful label and a relative navigable target:

```markdown
[Development Principles](../foundations/principles.md)
```

Do not leave a file path as plain text when a relative link can be provided. Do not put a file reference only inside code backticks, such as `` `../foundations/principles.md` ``. Code formatting is appropriate for commands, symbols, keys and literal values, but it is not a substitute for a navigable document link.

The link target must be relative to the document containing it, use the repository's actual path and preserve the correct filename casing. Link labels should describe the destination rather than repeat an opaque filename where a clearer human label is available.

External references should also use labelled Markdown links when they are intended for readers to follow. Keep raw URLs only where a machine-readable value or protocol syntax genuinely requires one.

## Link Maintenance

Documentation maintenance MUST include a link review when files are moved, renamed, retired or added, and periodically during documentation work:

- find local links whose targets no longer exist and update them when the destination is known;
- find file references written only inside code backticks and convert them to labelled relative links;
- check links in the changed document and its immediate neighbouring index or loader documents;
- preserve anchors and update them when headings change; and
- avoid replacing a broken link with a plausible but unverified path.

When a broken link cannot be resolved immediately, record it in the adopting repository's documentation governance register rather than silently deleting it. The register should include the source file, displayed reference, attempted target, reason it remains unresolved, owner or responsible area, date identified and the next action. A repository may use a dedicated `LINK-REGISTER.md` under its governance or maintenance documentation area, or an existing broken-link register if one already exists.

Link maintenance is complete only when the changed documentation has no newly introduced broken local links, or every unresolved link is recorded in that register.