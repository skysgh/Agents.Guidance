# AGENTS.GUIDANCE Repository Assessment (2026-08-02)

## EXECUTIVE ASSESSMENT
**Status**: Strong intellectual foundation with substantive operational and governance gaps. Near-best for architecture thinking; not yet best for serious-system engineering in regulated, multi-team, multi-system contexts.

**Verdict**: Best-in-class on problem decomposition, domain modeling, lifecycle thinking, and examples. Missing half of what "serious systems" need for production readiness, security, compliance, and operational control.

---

## SUBSTANTIVE STRENGTHS

### 1. Architectural Foundation (Excellent)
- [engineering/humans/reference/catalogues/](deliverable-systems.md) - Distinct systems concept (delivery, service, consumer, testing, cross-system-test-context)
- [engineering/humans/reference/catalogues/ldms.md](ldms.md) - Clean logical deployment module boundary thinking
- [engineering/humans/development/layers.md](layers.md) - Layers, logical building blocks well-explained
- [engineering/humans/development/contracts.md](contracts.md) - Contracts as boundary formwork
- Conceptual/logical/physical model separation (ANSI/SPARC properly applied)

### 2. Example Gallery (Strong)
- 17 before/after cases in [engineering/humans/examples/](examples/)
- Concrete problems (screen-to-design drift, contract formwork, ambiguity in state, entity lifecycle)
- Visible how decisions cascade when structure is missing
- Real tracing of impact across teams/boundaries
- Example index by role/problem added (acknowledged in audit)

### 3. Stakeholder Mapping (Comprehensive)
- 10+ distinct role routes (BA, PO, Product Manager, Architect, Tech Lead, Developer, Tester, Support, Operator, Maintainer, Service Provider)
- Shared Requirements crossing handoffs (not siloed)
- Governance specialists recognized but under-treated
- Audit identified gaps and recommended treatment (H-03, M-01)

### 4. Legal/Regulatory Awareness (Good)
- [engineering/humans/orientation/legal-context.md](legal-context.md) - Jurisdiction mapping, obligation framing
- [engineering/humans/reference/catalogues/regulatory-obligations.md](regulatory-obligations.md) - Catalog of recurring domains (purpose, PII, tracking, records, retention, security, accessibility, fairness, safety, sector duties, financial, cross-border)
- Acknowledges this is not legal advice; team must map actual sources
- Data protection as first-order architectural concern

### 5. Development Guidance (Solid)
- [engineering/agents/conventions/foundations/principles.md](principles.md) - 7 core principles with ISO 25010 grounding
- Principles touch evolvability, ontology, scale, dependencies, boundary technology, policy
- Agent conventions for code/C#/Python/TS, projects, platform services, testing, operations, dependencies, accessibility, performance
- Not overly prescriptive; gives intent first

### 6. Quality and Deliverables Thinking (Advanced)
- [engineering/humans/reference/catalogues/deliverables.md](deliverables.md) - Data, content, addressing, certificates, discovery, operations, maintenance, evidence as deliverables
- Omission test: "What must exist outside code repo for real operator/consumer/recovery process?"
- Distinguishes deliverable systems from deliverables from SDD/SAD/TDD
- Cross-system test context as shareable, versioned, portable resource

### 7. Evidence of Reflection
- Audit conducted: FINDINGS, LIFECYCLE TRACE, COVERAGE MATRIX
- Acknowledged gaps (Operations "lighter," Support "lighter," Specialist controls "under-treated," Decision records needed)
- Deferred work explicitly recorded with severity and trigger conditions
- Not claiming completion; grading its own work

---

## SUBSTANTIVE GAPS

### GAP 1: Operations Depth (Substantive)
**Severity**: High for serious systems
**Where**: [engineering/humans/stakeholders/operators/](operators/), [engineering/humans/stakeholders/maintainers/](maintainers/)
**What's There**:
- Readiness, observability, recovery *concepts*
- References to agent conventions (operations.md)
- Links to readiness table (platform-services.md)

**What's Missing**:
- **Observability contracts**: Which metrics, logs, traces at which boundaries? How does operator know if system is healthy, degraded, failed?
- **Runbook templates**: Patterns for incident response, escalation, recovery procedures
- **Failure modes**: Catalog of likely failures (database unavailable, auth provider down, queue backed up, etc.) and cascading effects
- **Readiness verification**: How does an operator check the service is actually ready to handle traffic?
- **Audit/evidence**: Access logs, decision logs, change records—what's captured, at what granularity, how long retained?
- **Capacity and degradation**: How to model, predict, and handle overload? Circuit breakers, shedding, graceful failure?
- **Recovery procedures**: With compensation, rollback, data reconciliation logic

**Current state**: Operators get principles and links. Not enough to run a serious system. Audit acknowledged this is "intentionally staged" but deferred.

### GAP 2: Access Control & Authorization Patterns (Substantive)
**Severity**: Critical for serious systems handling sensitive work
**Where**: [engineering/agents/conventions/foundations/data-protection.md](data-protection.md) mentions "Authorise every read and write at the owning boundary"
**What's There**:
- Principle that authorization should happen at service boundary
- Data protection checklist touches classification and access
- Concept of "who may act on classified resource"

**What's Missing**:
- **Role/permission architecture patterns**: RBAC, ABAC, trait-based? How to model for maintainability? Inheritance vs delegation?
- **Delegation and approval workflows**: How does a manager approve on behalf of staff? How does that flow through systems?
- **Access control testing**: What must tests verify (positive and negative paths, boundary cases)?
- **Audit trail precision**: What must be logged? "`User X read record Y at time Z`" or include context, classification, approval chain, changes made?
- **Cross-system authorization**: If User A from System A needs to act on data in System B, how is that negotiated and audited?
- **Secrets and credential lifecycle**: Key rotation, mfa, session/token expiry, lockout, recovery

**Current state**: "Do authorization at the boundary" is correct but incomplete. Missing patterns and evidence procedures.

### GAP 3: Security Architecture (Substantive)
**Severity**: High
**Where**: Scattered (legal-context.md, data-protection.md, but no security architecture document)
**What's There**:
- Data handling, access, verification guidelines in conventions
- Classification concept
- Encryption mentioned (in transit, at rest)

**What's Missing**:
- **Threat modeling**: How to identify what threats matter? No STRIDE, attack tree, or similar guidance.
- **Security design patterns**: Encryption, signing, validation, escrow, audit, attestation. Which boundary owns which control?
- **Certificate and key management lifecycle**: Issuance, rotation, revocation, what happens when compromised?
- **Cryptographic agility**: How to change algorithms/key sizes without breaking deployed systems?
- **Secret management beyond vault reference**: Handling service-to-service secrets, API keys, tokens
- **Security testing**: Penetration testing, fuzzing, access control testing, data minimization verification
- **Dependency security**: Vulnerability scanning, update strategy, supply chain risk

**Current state**: Data protection as principle is sound. Security architecture guidance missing.

### GAP 4: Governance & Control Structure (Substantive)
**Severity**: High for "serious systems" in regulated organizations
**Where**: Absent
**What's There**: Nothing on:
- Who approves architectural changes?
- Who decides breaking changes, deprecations?
- How do security, compliance, operations specialists escalate conflicts?
- What's a quality gate? Who owns readiness? Who signs off?
- Change advisory boards, release gates, rollback authority?
- Dispute resolution when regulatory obligations conflict with performance targets?

**Current state**: Stakeholder roles and shared requirements cover handoffs. Missing: who has authority to say "stop; this is a blocker" and what process follows?

### GAP 5: Evidence & Verification (Substantive)
**Severity**: High for compliance and serious systems
**Where**: [engineering/humans/reference/checklists/](checklists/) has some good prompts, but no systematic evidence framework
**What's There**:
- Checklists for deliverables, regulatory obligations, ldms, security-at-rest, security-in-transit
- Principle that evidence must exist

**What's Missing**:
- **Evidence strategies by claim**: "All PII is encrypted" - what's the test? Read a production record? Check logs? Schema inspection?
- **Audit trail verification**: How to prove a user's access was properly authorized? How to detect unauthorized access?
- **Compliance testing**: How to test GDPR right-to-erasure works? How to test data retention policy is enforced?
- **Readiness evidence**: What proves a service is ready for production traffic?
- **Testing strategy for security/compliance**: Automated, manual, frequency, who runs?
- **Evidence preservation**: Logs rotated; who's keeping the 3-year audit trail?

**Current state**: "Collect evidence" is in the guidance. "Here's how to systematically collect it" is missing.

### GAP 6: Cross-System Integration & Coordination (Substantive)
**Severity**: Medium-High for services with multiple LDMs or external integrations
**Where**: [engineering/humans/reference/catalogues/deliverable-systems.md](deliverable-systems.md) covers systems concept; missing operational coordination
**What's There**:
- Distinct systems (delivery, service, consumer, testing, cross-system-test-context)
- Contract concept; API lifecycle mentioned
- Cross-system test context system (portable, neutral, with translators)

**What's Missing**:
- **API/contract versioning at scale**: What's the deprecation path? How long do you support old versions? How do you coordinate breaking changes?
- **Deployment coordination**: Blue-green, canary, staged rollout? How to coordinate across multiple LDMs or services?
- **Contract testing strategy**: Where does the test live? Who owns passing the test? How is failure detected and escalated?
- **Data consistency patterns**: CAP theorem, eventual consistency, compensation, reconciliation procedures
- **Cross-system tracing/correlation**: How does an operator trace a request across System A → System B → System C?
- **Failure propagation**: If System B is unavailable, what should System A do? Timeout? Fallback? Cascade failure?
- **Cross-system test context realization**: Good concept; how is it actually maintained and translated in practice?

**Current state**: Concept is sound. Operational practices missing.

### GAP 7: Performance Testing & Cost (Substantive)
**Severity**: Medium for production systems
**Where**: [engineering/agents/conventions/foundations/principles.md](principles.md) has "Prepare for scale; spend as little as needed" principle
**What's There**:
- Principle with good rationale (measure, don't speculate)
- References AWS/Azure cost-optimization pillars

**What's Missing**:
- **Performance testing strategy**: Load testing, stress testing, soak testing? At what SLA thresholds?
- **Cost modeling**: How to estimate operating costs? Where are the biggest levers?
- **Degradation patterns**: Circuit breakers, graceful failure, overload shedding, rate limiting?
- **Acceptable latency/throughput by capability**: Is a 1-second read acceptable? For which operations?
- **Measurement and tracking**: Metrics for cost and performance; dashboards; alerts

**Current state**: Principle is right. Implementation and evidence procedures missing.

### GAP 8: Database Schema & Migration Safety (Substantive)
**Severity**: Medium-High for relational systems
**Where**: [engineering/agents/conventions/development/code-csharp.md](code-csharp.md) exists but missing schema guidance
**What's There**: Some EF Core guidance in examples (schema development patterns shown in examples)
**What's Missing**:
- **Schema design conventions**: Naming, constraints, keys, relationships—how to keep them maintainable?
- **Migration patterns**: Zero-downtime migrations, rollback safety, backwards-compatibility in schema changes
- **Physical vs logical model**: How to evolve schema without breaking application logic?
- **Deletion vs soft-delete**: Rules for when each is appropriate
- **Historical data and auditing**: How to retain history while keeping schema sane?

**Current state**: Some via examples; missing systematic guidance.

### GAP 9: Monitoring & Diagnostic Contracts (Substantive)
**Severity**: Medium
**Where**: Mentioned in principles (diagnostics, observability) but not detailed
**What's There**:
- System LDM services reference table mentions "Diagnostics: Reports composition, health, failure, correlation and operational evidence"
- Platform services list includes Diagnostics (#2 in readiness order)

**What's Missing**:
- **What must a diagnostic capability expose?** Health, readiness, startup log, dependency checks?
- **Correlation and tracing**: How to trace a request across LDMs/services?
- **Metrics and alerting**: Which metrics matter for which capabilities? At what thresholds do you alert?
- **Structured logging contracts**: What fields must be present? How to prevent PII in logs?

**Current state**: Concept present; detailed contracts missing.

### GAP 10: Navigation & Search (Polish → UX Impact)
**Severity**: Low for engineering value; Medium for adoption
**Where**: [engineering/humans/examples/readme.md](examples/readme.md) acknowledged in audit (M-02)
**Audit findings**:
- M-02: Examples organized by case number, not reader question (cross-indexing deferred)
- M-03: Decision-record format not provided (deferred pending governance format decision)
- Specialist control routes not consistently discoverable

**Impact**: A serious-system practitioner using this corpus non-sequentially (jumping to a specific problem) may miss relevant examples, guidance, or specialist routes. Needs: search index, problem-to-example mapping, decision-record template.

---

## IMPLEMENTATION MATURITY BY AREA

| Area | Maturity | Notes |
|------|----------|-------|
| Domains & LDMs | Production-ready | Clear thinking, examples, layer concepts solid |
| Contracts & APIs | Production-ready | Good on interfaces; API lifecycle mentioned |
| Deliverables framing | Production-ready | Catalogs, checklists, systems thinking |
| Stakeholder routes | Near-complete | 10 roles mapped; specialist controls under-treated |
| Regulatory/Legal | Good | Catalog is useful reference; not substitute for legal advice |
| Data protection | Good | Principles clear; implementation depth missing |
| Operations | Acknowledged as "lighter"/deferred | Readiness table exists; runbooks, failure modes, audit procedures missing |
| Access control | Foundational | Principle present; patterns and testing strategies missing |
| Security architecture | Sparse | Data protection exists; threat modeling, crypto, secrets, testing missing |
| Governance & escalation | Absent | No routes, no control matrices, no approval workflows |
| Evidence & verification | Foundational | Checklists good; testing procedures and proof strategies missing |
| Performance & cost | Foundational | Principle good; testing and modeling missing |
| Cross-system integration | Partial | Systems concept solid; operational coordination, versioning, tracing missing |
| Development conventions | Partial | Code guidance for major languages; migration, schema, observability contracts incomplete |
| Navigation/search | Deferred | Acknowledged in audit; impacts adoption for non-sequential readers |

---

## ASSESSMENT CONCLUSION

**Best for**:
- Teams learning to think about domains, boundaries, contracts, lifecycle
- Architects designing service structure, LDMs, layers
- Organizations wanting to protect business meaning through deliberate logical models
- Serious systems needing to reason about deliverables beyond code
- Regulatory/compliance awareness (legal context, regulatory obligations catalog)

**Not ready for**:
- Teams that need prescriptive operations runbooks, incident response, escalation
- Systems with complex access control requirements (healthcare, finance, government)
- Regulated systems needing security architecture patterns and compliance verification
- Multi-team organizations needing governance structures and approval workflows
- Systems requiring performance testing strategies or cost optimization guidance
- Multi-system integrations needing deployment coordination and contract management

**Gaps are substantive, not polish**:
- Operations, access control, security architecture, governance, evidence/verification, performance testing, cross-system coordination are missing half or more of their needed guidance
- These gaps matter for "serious systems" in production, regulated contexts
- Audit already identified most gaps and deferred work explicitly

**Near-best, not yet best**:
- Intellectual foundation (domains, contracts, lifecycle) is first-rate
- Examples and stakeholder thinking are excellent
- Gaps are addressable with systematic additions to operations, security, governance, and verification domains
- Not a question of fixing poor thinking; it's expanding coverage into missing operational/control territories
