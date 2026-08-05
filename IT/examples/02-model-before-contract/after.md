[Up](../readme.md)

# After: Concrete Model Before Contract

The team starts from the capability that consumers need, not from the first class that happens to hold data.

A narrow contract states the supported operations, inputs, results, errors and lifecycle. The application service implements the use-case behaviour. The domain and persistence models can retain their own responsibilities. Mapping makes translation explicit. The repository exposes the governed persistence policy rather than becoming the public model.

The developer is still central: implementation work tests whether the proposed contract is coherent, implementable and useful. If the contract is awkward, the slice provides evidence to refine it before more consumers depend on it.

The result is not an interface beside every class. It is a stable capability boundary where substitution, testing, mapping, security and discovery have a reason to exist.
