# Role meanings are separated and mapped

The team recognises that `Role` is polysemous. The BA records the competing meanings and brings the business, access, security, technical and Support authorities into the decision. The team keeps the familiar word where it helps people, but qualifies it at each boundary.

The resulting distinctions are explicit:

- **Business role:** the real-world appointment or responsibility, such as an authorised approver for a particular organisation or decision type. Its authority, appointment, expiry and revocation belong to the organisation or policy owner.
- **Access-context role:** the context in which a person is acting for a resource, organisation, workspace or request. It is evaluated for the relevant situation and does not itself create the underlying business appointment.
- **System authorisation role:** a configured permission grouping used by the system to allow or deny operations. It is one input to authorisation, not proof that the person is the business authority for every resource.
- **Implementation role:** what a software component does, such as `ApprovalCoordinator` or `ApprovalPolicyEvaluator`. It is not a human role and must not be used as evidence of user authority.

The approval contract now evaluates the actor, action, request, organisation, decision type, current state and applicable business authority. It maps the business appointment and access context to the system policy without treating a configured permission as universal approval authority. The UI can explain the human role, while the API enforces the actual resource and context checks.

Support receives distinct information for changing an appointment, changing access, changing a system permission and correcting an implementation defect. Testing covers the allowed path and wrong organisation, wrong request, expired appointment, missing context, denied permission and component-boundary cases. Audit records identify the actor, authority context, resource, decision and policy result without confusing the labels.

## Evidence

- Each meaning has an owner, lifecycle and authority boundary.
- The approval contract states the actor, action, resource, context and policy conditions.
- A system authorisation role cannot approve outside its permitted organisation or request context.
- Appointment, access, permission and implementation changes have separate support and maintenance paths.
- Tests and audit evidence distinguish human authority from configured permission and software behaviour.

## What changed afterwards

The team did not ban the word `Role`. It stopped pretending that one label was one concept. Qualified meanings and explicit mappings let people use familiar language while keeping business authority, access context, system permission and implementation responsibility separate.
