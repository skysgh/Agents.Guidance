# Agent Workflow Conventions

Apply these conventions when an agent plans, edits, reviews or validates repository work.

## Before editing

- Identify the smallest concrete anchor: a file, symbol, failing check, test or call site.
- Read the owning abstraction and applicable portable conventions before changing code.
- State one falsifiable local hypothesis about the behaviour or defect.
- Choose one cheap, focused check that could disprove the hypothesis.
- Preserve unrelated dirty-worktree changes. Do not reset, revert or rewrite them.

## While editing

- Make the smallest change that tests the hypothesis.
- Keep portable guidance separate from repository-specific bindings.
- Do not hide incomplete work behind stubs, fake success or broad suppression.
- Record assumptions when evidence is incomplete or a user decision is required.

## After editing

- Run the narrowest executable validation immediately after the first substantive edit.
- Repair a local failure and rerun the same focused check before widening scope.
- Inspect diagnostics and the final diff for accidental changes, generated artefacts and contract drift.
- Report what was changed, what was validated, what could not be validated and any remaining risk.

## Precedence

Apply rules in this order: non-negotiable security and safety constraints; more-specific applicable portable conventions; repository bindings; established local patterns; then the user request. A lower-level request cannot silently weaken a higher-level invariant. Ask the user when two applicable requirements genuinely conflict.
