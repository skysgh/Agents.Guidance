[Up](./readme.md)

# Sites


A site is a curated surface through which a defined group or connected system reaches the information and capabilities provided by a service. The word site describes the responsibility and experience being offered. It does not describe whether the surface is delivered through a browser, a mobile application, an API, a partner integration or another technical platform. Platform decisions come before this catalogue and remain separate from the site decision.

A site exists when a group needs a coherent selection of system-managed information and capabilities for its responsibility. Not every stakeholder needs a site of its own. A group may use an existing site when its purpose, information needs and available capabilities remain coherent with the other people using that site. A new site becomes useful when combining the groups would make the experience confusing, expose information that is irrelevant or unsafe for the audience, or make the groupÔÇÖs work difficult to perform.

A site is therefore not a security boundary by omission. Hiding a capability from a user experience does not secure it. Authentication and authorisation must still be enforced by the responsible system boundary. A site is a deliberate curation of what the group needs to see and do, with the permissions, validation, audit and policy controls that make those capabilities safe. The site reduces clutter and accidental exposure; it does not replace security controls.

Sites can share backend capabilities and services. Separate sites do not imply separate business logic, separate databases or separate deployments. They may use the same backend while presenting different flows, views, language, data projections and actions. Conversely, a single site may use several services or LDMs. The boundary is chosen from the responsibility being served, not from a presumption about the number of applications or deployments.

## The site families

The public site is for people who need deliberately open information, discovery, registration or other capabilities that do not require an established authenticated relationship. Public does not mean that every piece of information is public. The site should expose only information and actions that the service has intentionally made available without an authenticated context.

The consumer site is for people or organisations that consume the service. It may support applications, requests, purchases, submissions, status tracking, documents, decisions or other consumer capabilities. The consumer view should use the language and information needed to complete that responsibility rather than exposing the internal arrangements used to provide the service.

The partner site is for another organisation or system that works with the service. A partner may need a user experience of its own, or it may need an API so that it can build its own experience. These are both partner interfaces. Providing a stable, usable interface for another system is interoperability: the service can work with another system through an understood contract instead of requiring that system to reproduce private implementation details.

The reseller or intermediary site is for a group that helps another person or organisation use the service. Examples may include a teacher supporting a student, an adviser supporting an applicant or an agent acting for a customer. The intermediary needs capabilities and information about the work it is helping to perform, but should not automatically receive every provider, support or maintenance capability. Where different intermediary groups have materially different responsibilities, separate sites or carefully bounded site areas may be appropriate. A teacher-facing experience should not be crowded with the material needed by students, senior staff or system maintainers.

The provider site is for the people who provide the service and make the business decisions that give it meaning. It may support assessment, fulfilment, communication, approval, scheduling, case work, content management or other provider responsibilities. Provider information is not simply a larger version of the consumer view. It often contains different concepts, states, decisions and obligations.

The support site is for people who help consumers, partners or providers use the service. It may provide investigation, guided assistance, correction, replay or communication capabilities. Support work must operate within its permitted authority and should make consequential actions, explanations and audit evidence visible. Support should not become an unrestricted back door into provider or maintenance capabilities.

The operations site is for people responsible for the running service. It may present readiness, health, queues, failures, dependency state, throughput, alerts and controlled operational actions. Operations information is about keeping the service running and recovering it safely, not about carrying out ordinary provider or consumer work.

The maintenance site is for people who change, repair or administer the technical service. It may expose controlled configuration, diagnostics, migrations, discovery, dependency checks, deployment information or recovery actions. Maintenance capabilities are particularly sensitive because they can change the conditions under which other sites operate. They should be curated for the maintenance responsibility and protected by the systemÔÇÖs security controls, not merely hidden from ordinary navigation.

These families are a recognition aid rather than a fixed list. A service may combine public and consumer responsibilities, may provide a partner API without a partner user experience, or may separate operations and maintenance more sharply than the catalogue examples suggest. The important decision is to make the responsibility and the information and capabilities needed for it understandable.

## A site has an internal shape

A site is a collection of flows. A flow is a collection of views that guide a recognisable journey or responsibility. A view is a collection of components that presents, collects or organises information for one point in that flow. A component has one primary presentation responsibility: it is a collection component, an input component or an output component. These responsibilities should not be blended inside one component merely because the screen happens to contain all three kinds of information.

This relationship is explored in [Sites, Flows, Views and Components](./sites-flows-views-components.md). That document goes further into interface structure and is deliberately separated from this first catalogue so that the site decision remains clear.

## Site and system boundaries

A site may be delivered by a web application, mobile application, desktop application, API, message endpoint, command surface or another technical interface. Those are platform and delivery choices. The site catalogue records the responsibility being served and the information and capabilities curated for it; it does not prescribe the delivery technology.

A site may call a shared backend service, several backend services or a partner system. The interface contract should state what the site can request and what it receives. The backend remains responsible for enforcing authentication, authorisation, validation, business rules, data classification, audit and lifecycle policy. A siteÔÇÖs curated experience is an aid to safe and understandable use, not a substitute for those controls.

The Architect maps the site landscape. The Tech Lead ensures that the sites can reach coherent capabilities without private copies of shared rules. The Developer implements the flows, views and components within the contracts and boundaries already established.

For practical review prompts, use the [site and interface checklist](../checklists/sites-and-interfaces.md).
