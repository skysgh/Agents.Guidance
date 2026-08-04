# Repository Bindings

Portable guidance should not contain concrete base-class names. Those names are implementation bindings, and they vary between repositories even when the architectural purpose is the same.

## Where bindings belong

Each adopting repository should provide one binding document near its agent entry point, for example:

```text
.github/
  copilot-instructions.md
  instructions/
    architecture-bindings.instructions.md
```

The binding document should be loaded for code work and should link back to this repository's [agents.md](../../../agents.md). It should map, in a compact table or short sections:

- portable slice or flow;
- local boundary and application contracts;
- local repository and persistence contracts;
- local base classes or composition helpers;
- local queryability rules;
- local reflection or startup discovery rules;
- local EF or other persistence rules; and
- deliberate deviations and their rationale.

## Binding rule

Describe the purpose before the name. For example: "the local stateful CRUD application-service base, which supplies the standard read/create/update/state-transition pipeline" followed by the concrete type name. This keeps the concept portable and makes the local dependency reviewable.

Do not copy repository bindings into the portable documents. Do not let a local class name become the definition of a slice or flow. If several repositories converge on the same shape, promote the purpose and invariant to portable guidance first, then keep each repository's names in its binding.
