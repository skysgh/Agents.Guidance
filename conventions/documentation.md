
# Conventions - Documentation 

Apply these conventions when creating, restructuring, reviewing or retiring documentation intended for stakeholders, operators or maintainers.


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

`Discovery` leads to `Discussions` (Options Analysis) which lead to `Decisions` (ADRs) which leads to `Definitions` (FRs and QRs_ which lead to `Design` (SDD and TDD), which leads to `Development` then `Deployment` at which point `Support`, `Operations`, and `Maintenance` must be in place.


## Ongoing Maintenance

While ARDs and other identifiers are suppossed to stay stable, new decisions can replace older decisions. 

Periodically scan and keep references amongst ADRs, Delivery Plans, and Implementation papers.  