# Done

Apply this checklist to every change, selecting only the validation steps relevant to the affected files and behaviour.

Validate work in increasing scope before declaring it complete.

1. Verify that all applicable conventions have been followed.
2. Check diagnostics for every changed file.
3. Run focused tests for the changed behaviour.
4. Build the affected project or logical module.
5. Run the repository’s complete build task, even when focused builds have passed.
6. Run all applicable static and dynamic tests.
7. Where persistence has changed, verify migrations and pending model changes in both design-time and running-host contexts.
8. Inspect the final diff for unrelated changes, accidental contract drift, unexplained values, duplication and unintended generated artefacts.
9. Report what changed, what was validated, what could not be validated and any remaining limitation.

Treat warnings as errors. Correct relevant warnings rather than broadly suppressing them. Use the narrowest justified source-level suppression only when the warning is understood and correction would make the implementation less accurate or maintainable.

Work is complete only when the reachable behaviour is implemented through the appropriate architectural boundaries; applicable security, auditing, data and mapping conventions have been followed; no stub or knowingly incomplete implementation has been presented as complete; and all required validation has passed.

For a capability or cross-cutting change, completion evidence MUST show the intended contract, stewarding boundary, participating objects and services, relevant startup or registry participation, access and security decisions, mapping and persistence policy, tests, and any deliberate deferrals. A general statement that the team "already does this" is not evidence for the current capability.

If required validation fails or cannot be performed, report the work as incomplete or blocked, explain why and recommend corrective action.
