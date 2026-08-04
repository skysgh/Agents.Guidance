# Pipeline Development and Infrastructure as Code

A service can be healthy today and still be difficult to release tomorrow. The person who knows how the environment was created may be unavailable. A second environment may have a slightly different identity, network rule or certificate. A recovery exercise may discover that the pipeline can build the application but cannot recreate the resources it depends on.

Pipeline developers work on that part of the delivery. Their code may create infrastructure, assemble artifacts, promote environments, apply policy, rotate configuration or coordinate recovery. It may not look like application code, but it has authority over real systems and can carry real security, availability, cost and operational consequences.

The work often spans several codebases: pipeline definitions, environment definitions, service code, client code and test code or test context. The runner executes or applies them; it does not make them one codebase or one system. The environment produced by an environment-definition codebase is another boundary again.

## Start with the outcome

Before choosing a language, provider or runner, the team needs to know what the flow is trying to achieve. A pipeline is not automatically one universal sequence called ÔÇ£the pipelineÔÇØ. Different outcomes may need different flows, participants, permissions, evidence and recovery paths.

| Flow | Outcome | What is not assumed |
| --- | --- | --- |
| **Delivery** | Turn an approved change into a known, tested and releasable version, then make its introduction and result visible. | Every delivery needs the same deployment target, data movement or release shape. |
| **Restoration** | Restore an agreed backup or recovery point to a specific date, establish a usable state and preserve evidence of what was restored. | Restoration is only copying files, or that the newest backup is automatically the correct one. |
| **Fail-over switching** | Move service use to available capacity within the service's recovery and availability promise, then observe, reconcile and decide how to return. | A separate new area, region or environment is mandatory when recovery within the existing zone can meet the SLA. |
| **Rollback or repair** | Return to a known safe version or correct a failed change without hiding what happened. | Rollback is always safe, complete or possible without data reconciliation. |
| **Environment rebuild** | Recreate an environment or its required foundations from known definitions and evidence. | Rebuilding a resource is the same as restoring its data, identity, configuration or operational meaning. |

These flows may share tools, but their objectives are different. A delivery flow may publish a new version. A restoration flow may bring an earlier state back for a defined date. A fail-over flow may switch traffic without creating a new area at all. The right design follows the outcome, the service promise, the cost of failure and the time available to recover.

## Delivery flow without choosing a technology first

A delivery flow can be understood before anyone says Azure, AWS, Terraform, PowerShell or Bash. One possible shape is:

1. **Retrieve:** obtain the approved code, dependencies, configuration and definitions at known revisions.
2. **Compile or build:** turn the source into the forms needed for qualification and delivery.
3. **Static testing:** inspect source, dependencies, configuration and generated material for the defects and risks that can be found without running the service.
4. **Package:** create identifiable artifacts with provenance, version, checksums and the information needed to reproduce or inspect them.
5. **Protect existing state:** back up existing data or other recoverable state where the change and recovery decision require it.
6. **Publish to BT:** publish to the project-specific BT target or boundary. The meaning of `BT` belongs to the project vocabulary and should be expanded there rather than guessed here.
7. **Rehydrate:** provide the target with the approved data, configuration, reference state or test context it needs. Rehydration is distinct from deploying code.
8. **Dynamic testing:** exercise the running result, its boundaries, security, quality conditions, failure behaviour and relevant user or operator journeys.
9. **Release decision:** preserve the evidence, unresolved variance, approval or deferral, and the identity of the version that may proceed.

The sequence is a way to make the delivery objective visible. Some services will need migration, compatibility checks, communication, approval, signing, promotion or staged exposure between these steps. Those additions belong to the flow's conditions and evidence, not to an assumed provider-specific recipe.

## Restoration flow to a specific date

A restoration flow starts with a recovery objective: a known date or point, a destination, the people who may authorise the restoration and the condition that makes the restored state useful. A technology-neutral shape is:

1. identify the requested date, scope and reason;
2. identify the backup, journal, replica or other recovery material that can represent that point;
3. verify its provenance, integrity, classification and access authority;
4. restore it to the approved destination or recovery boundary;
5. apply the required incremental changes to reach the requested date;
6. re-establish compatible schema, configuration, keys, identities and dependencies;
7. reconcile the restored state with connected systems and known transactions;
8. run integrity, security, functional and operational checks; and
9. preserve what was restored, what could not be restored, who accepted the result and what remains uncertain.

The result may be a recovered live service, a controlled investigation environment, a reporting copy or a test context. The purpose and access conditions determine the safe path. Restoration should not silently expose protected information or overwrite the current authoritative state.

## Fail-over switching without a mandatory new area

Fail-over is a response to a service condition, not a trophy for having created another environment. A service may meet its recovery promise by recovering within the current zone, switching to warm capacity, routing to another zone, using a replica, operating in a degraded mode or temporarily restricting work. A new area is one possible design, not a universal requirement.

The flow needs to make visible:

- the condition that makes switching necessary;
- the service level, recovery time and information-loss promise that governs the decision;
- the capacity and readiness of the candidate target;
- the authority to switch, communicate and restrict unsafe operations;
- the treatment of in-flight work, duplicates, queues, caches and external effects;
- the observation and reconciliation that show whether the target is serving correctly; and
- the decision to remain there, repair the original zone or return when doing so is safe.

If the existing zone can return within the agreed SLA and the service can preserve or reconcile its state, that may be the more parsimonious and maintainable design. The evidence must support that claim under representative failure conditions; familiarity with a multi-area pattern is not evidence by itself.

## Flows before technology

The useful order for future pipeline guidance is:

1. the objective and completion condition;
2. the people, systems, authority and information involved;
3. the technology-neutral steps and handoffs;
4. the evidence produced at each step;
5. failure, partial success, retry, reconciliation and recovery behaviour;
6. the service-level, cost, security, maintainability and reversibility constraints;
7. the mapping to provider, infrastructure language, shell, runner and environment; and
8. the detailed tests, checklists, examples and project records.

This page deliberately stops at the foundation. The later pipeline work should flesh out each flow with triggers, inputs, outputs, identities, permissions, data classification, environment boundaries, evidence retention, timing, failure modes, operator actions and project-specific examples. Delivery, Restoration, Fail-over Switching, Rollback and Environment Rebuild should remain separate flows unless their objectives and evidence genuinely converge.

## Later: express the flow in tools and providers

Pipeline development commonly combines three kinds of expression:

- **Declarative infrastructure:** describes the resources and desired properties that should exist. The provider determines how to create or change them.
- **Typed infrastructure programming:** uses a general-purpose language and a provider library to describe infrastructure, often generating a declarative template or deployment plan.
- **Imperative orchestration:** uses PowerShell, Bash or another scripting language to connect steps, select environments, call tools, pass bounded values, collect results and stop safely when a condition fails.

These forms cooperate, but they do not have the same responsibility. A shell script that calls a deployment command is not the infrastructure model. A TypeScript CDK program is not automatically the service's domain model. A template that declares a storage account does not decide the business meaning of the data stored there.

## A route when the platform is unfamiliar

The first useful knowledge is not a list of provider commands. It is the shape shared by most infrastructure work:

```text
desired resources and relationships
  -> provider or tool model
    -> preview, plan or change description
      -> authorised execution
        -> actual resources and state
          -> evidence, drift awareness and recovery
```

The names change between platforms, but the questions remain recognisable. What resources should exist? Which account, subscription, tenant, region or scope owns them? Which identity may change them? Which dependencies determine order? What will change before anything is applied? Where is the state of the environment recorded? What happens when the change is only partly successful?

That gives a person who knows Azure a way into AWS or Terraform without treating unfamiliar vocabulary as a new kind of engineering. The provider names and command syntax can be learned after the responsibility is visible.

### The provider map

| Area | Azure | AWS | Cross-provider option |
| --- | --- | --- | --- |
| Resource declaration | ARM JSON or Bicep | CloudFormation JSON/YAML | Terraform configuration, commonly HCL |
| Typed authoring | Bicep has its own declarative language | AWS CDK supports TypeScript, JavaScript, Python, Java, C# and Go | Pulumi and similar tools use general-purpose languages |
| Provider execution | Azure Resource Manager, Azure CLI or Az PowerShell | CloudFormation, AWS CLI or SDKs | Provider plugins and the selected tool's plan/apply workflow |
| Access control | Azure identities, roles, subscriptions and resource scopes | AWS IAM principals, roles, policies, accounts and regions | The provider's identity and policy model still applies |
| Preview or change evidence | ARM what-if and deployment records | CloudFormation change sets and stack events | Terraform plan and apply records |

This is a map, not a recommendation to support every platform or tool. The chosen route should follow the organisation's provider commitments, team capability, exit needs, security model, cost and evidence requirements.

### Terraform

Terraform is a provider-oriented infrastructure-as-code tool. Its configuration language is declarative: resources and relationships describe the desired infrastructure rather than a step-by-step procedure. Providers connect Terraform to platforms and services, including Azure and AWS. Its familiar workflow is **write, plan, apply**.

Terraform also introduces an important operational object: state. State helps Terraform compare the declared configuration with the environment and calculate a change. It can contain sensitive resource details, so its storage, access, locking, backup, versioning, recovery and separation between environments need deliberate protection. State is part of the pipeline system's evidence and operational risk; it is not a reason to treat Terraform's view as the business authority for the service.

Terraform can be a useful cross-provider choice when the organisation genuinely benefits from one workflow across several providers or services. It also adds provider-plugin, state, module, version and drift-management responsibilities. A tool that reduces provider-specific syntax can still increase the importance of platform expertise at the boundaries it manages.

### Linux, Bash and PowerShell

Many pipeline runners execute on Linux, where Bash or another POSIX-style shell is common. A Windows-based team may meet the same pipeline through PowerShell, a hosted runner or a container. The important differences are practical:

- command names, paths and quoting rules differ;
- environment variables and process status are exposed differently;
- pipelines and error propagation need explicit testing;
- file permissions, executable files, line endings and case sensitivity can change behaviour; and
- signals, temporary files, credentials and cleanup need to work in the runner's operating environment.

PowerShell knowledge transfers well at the level of variables, arguments, processes, exit status, structured output and error handling. Bash requires a separate comfort with shell expansion, quoting, command substitution, pipelines, permissions and the fact that a visually simple command line can change meaning when an input contains spaces or special characters.

The pipeline developer does not need to memorise every Linux command before contributing. A small, repeatable runner example can reveal the environment, available tools, identity, working directory, shell options, network reachability and failure behaviour. That evidence is more useful than assuming that a script which worked on a developer's Windows machine will behave the same way on a Linux runner.

### AWS access before AWS services

AWS introduces a large vocabulary of services, but the first boundary is usually identity and scope. AWS Identity and Access Management (IAM) controls which authenticated principals may perform which actions on which resources. The AWS Command Line Interface (CLI) exposes AWS service APIs through a shell on Windows, Linux or macOS.

For a person coming from Azure, the useful translation is not that one role name equals another. It is that a deployment needs an explicit account, region, identity, policy and resource scope. A pipeline identity should have only the permissions needed for its stage, and the organisation should be able to see which identity made a change. AWS IAM eventual consistency and provider-specific failure behaviour also belong in readiness and recovery thinking.

The same principle applies in Azure. Subscriptions, resource groups, managed identities, role assignments and deployment scopes are not merely setup details; they are part of the pipeline's authority and evidence.

## Azure: ARM and Bicep

Azure Resource Manager (ARM) is the deployment and management boundary for Azure resources. ARM templates describe resources and properties in JSON. **Bicep** is Azure's domain-specific language for declaring those resources in a more concise, typed and reusable form. Azure documents Bicep as a declarative language and describes it as a transparent abstraction over ARM JSON templates.

Bicep is therefore not a replacement for C# or TypeScript application development. It is a provider-specific infrastructure language. A pipeline may compile or validate Bicep, preview changes with an Azure what-if operation, deploy it through ARM, and use PowerShell or Bash around those actions for authentication, environment selection, evidence and failure handling.

The useful separation is:

```text
Bicep or ARM template
  -> declares Azure resources and desired properties
PowerShell, Bash or pipeline task
  -> validates, previews, authenticates, deploys and records evidence
Azure Resource Manager
  -> evaluates and applies the resource deployment
```

The pipeline still needs to make resource identity, scope, dependencies, permissions, secrets, naming, location, policy, drift, rollback and recovery visible. A successful template deployment does not prove that the resulting service is secure, available or fit for its users.

## AWS: CloudFormation and CDK

AWS CloudFormation is AWS's declarative infrastructure service. A CloudFormation template describes resources and their properties, and a stack provides a managed unit for creating, updating and deleting the declared resources.

AWS Cloud Development Kit (CDK) offers a different authoring experience. A developer writes infrastructure using a supported general-purpose language and the AWS Construct Library. CDK then synthesizes a CloudFormation template for deployment. AWS officially supports TypeScript, JavaScript, Python, Java, C# and Go for CDK. TypeScript was the first supported CDK language, and AWS develops the CDK itself in TypeScript, which explains why many examples use TypeScript.

That does not mean AWS infrastructure development is moving entirely to TypeScript. The provider's deployment model remains CloudFormation-based, and the authoring language is a team and system decision. TypeScript may be a sensible default where the team benefits from its CDK examples, typing and ecosystem. Python, Java, C# or Go may be appropriate when the team's capability, existing tooling, provider library use or support model makes them the stronger long-term choice.

The relationship can be pictured as:

```text
TypeScript, Python, Java, C#, Go or JavaScript
  -> AWS CDK constructs and application code
    -> synthesized CloudFormation template
      -> CloudFormation stack and AWS resources
```

The generated template and deployment plan remain important evidence. The source language does not remove the need to inspect what infrastructure will be created, what permissions it requests and how a change or rollback behaves.

## C#, Python, TypeScript, PowerShell and Bash

The repository's C# default concerns production service-side code. It does not make C# the required language for every pipeline task. A pipeline developer may reasonably use:

- **Bicep or ARM JSON** for Azure resource declaration;
- **CloudFormation JSON or YAML** for AWS resource declaration;
- **TypeScript, Python, Java, C#, Go or JavaScript** for AWS CDK where the CDK support and team capability fit;
- **PowerShell or Bash** for local and pipeline orchestration, provider CLI calls, environment coordination and evidence handling; and
- **Python or another bounded tool language** for generation, analysis, migration or specialised automation where its lifecycle and support are clear.

The decision follows the execution boundary. A short script that prepares a deployment is not governed like a continuously operated service, but a script with production credentials or permission to alter networks, identities, storage or DNS is still security-critical engineering. The language may be lightweight; the responsibility is not.

## Imperative wrappers need engineering too

PowerShell and Bash are often the visible glue around declarative infrastructure. Their most important qualities are not clever syntax. They are predictable exit behaviour, safe quoting, explicit inputs, bounded permissions, secret-safe output, repeatable execution, useful diagnostics and a clear response to partial success.

A wrapper should make it possible to understand:

- which environment and account or subscription it targets;
- which source, template, module or artifact it uses;
- which identity performs each action;
- how a dry run, preview or plan is obtained;
- what happens when one step succeeds and the next fails;
- whether a retry is safe or needs reconciliation;
- how logs and evidence avoid secrets and unnecessary personal information; and
- how an operator returns to a known state.

The wrapper should not quietly contain the organisation's infrastructure model in a long sequence of provider commands. When the desired resources and relationships are durable, declarative and reviewable, they belong in the infrastructure definition or typed construction layer. Imperative steps remain useful for coordination, migration, approval, repair and provider operations whose meaning cannot be expressed safely as a resource declaration.

## What pipeline developers contribute

Pipeline developers connect architecture and service needs to a repeatable delivery path. They help make environments, identities, resources, artifacts and release evidence reproducible. They expose where an infrastructure choice changes service availability, security, cost, recovery or exit conditions.

They work with:

- architects and technical leads on environment, dependency and responsibility boundaries;
- service and front-end developers on configuration, startup, migrations, assets and runtime assumptions;
- security and privacy specialists on identities, permissions, secrets, network paths and sensitive output;
- testers on qualification environments, test data, previews and evidence retention;
- operations on readiness, observability, rollback and recovery; and
- Product and Sponsor roles when cost, risk, release scope or residual delivery exposure changes.

Pipeline development is successful when a capable person who did not create the original environment can understand what will change, why it will change, what evidence supports it and how to recover when the change does not behave as intended.

## Related guidance

- [Pipeline System Guidance](./readme.md)
- [Deliverable Systems](../../../shared/reference/catalogues/deliverable-systems.md#1-delivery-system)
- [Delivery Guidance](../../readme.md)
- [Selecting a Language and Framework](../../../orientation/language-and-framework-selection.md)
- [External Dependencies](../../../shared/reference/catalogues/external-dependencies.md)
- [Testing System Guidance](../tests/readme.md)
- [Security in Transit Checklist](../../../shared/reference/checklists/security-in-transit.md)
- [Security at Rest Checklist](../../../shared/reference/checklists/security-at-rest.md)

## Provider references

- [Microsoft: What is Bicep?](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview)
- [AWS: Supported programming languages for the AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/languages.html)
- [AWS: What is CloudFormation?](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
- [HashiCorp: What is Terraform?](https://developer.hashicorp.com/terraform/intro)
- [AWS: What is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [AWS: What is the AWS Command Line Interface?](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
