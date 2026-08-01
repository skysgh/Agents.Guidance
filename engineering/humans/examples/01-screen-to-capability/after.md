# After: Screen Request Becomes Storage Design

The team treats the page request as conceptual evidence about a capability, not as the complete logical or physical model. The business analyst makes the provider's meaning, decisions and recognised states clear without being asked to design tables. Developers and architecture then define what the service must represent and do before choosing how to implement it.

Business analysis contributes the meaning of a provider, relevant decisions and the states users recognise. Developers and architecture identify the boundary contract, logical model, mappings and persistence intention. Security identifies visibility and approval rules. Testers identify the behaviours and denied paths that must be proved, while remaining alert when the test design can only express the capability through storage structure. Operations identifies readiness, diagnostics and recovery needs.

The design records:

- the provider capability and responsible boundary;
- the external read projection and explicit commands;
- valid states and transitions;
- access and classification rules;
- mapping between boundary, application and persistence models;
- governed query operations;
- intended relationships, including those deferred from construction;
- schema and startup participation; and
- tests and WGF consequences for what goes first.

The first screen can still be built. It is now one consumer of a capability rather than the accidental author of the whole system. Later construction has a place to fit.

## One small implementation shape

The following is an illustrative C#-like skeleton, not a framework prescription. It shows the relationship between a logical model, an application contract, a persistence port and a test. The transport request, response view model and ORM entity would be mapped at their respective boundaries.

```csharp
public sealed record ProviderId(Guid Value);

public sealed class Provider
{
	public ProviderId Id { get; }
	public string Name { get; private set; }

	public Provider(ProviderId id, string name) => (Id, Name) = (id, name);

	public void Rename(string name) => Name = RequireName(name);

	private static string RequireName(string name) =>
		string.IsNullOrWhiteSpace(name) ? throw new InvalidOperationException() : name;
}

public interface IProviderRepository
{
	Task<Provider?> Get(ProviderId id, CancellationToken cancellationToken);
	Task Save(Provider provider, CancellationToken cancellationToken);
}

public sealed class RenameProvider(IProviderRepository repository)
{
	public async Task Execute(ProviderId id, string name, CancellationToken cancellationToken)
	{
		var provider = await repository.Get(id, cancellationToken)
			?? throw new KeyNotFoundException();
		provider.Rename(name);
		await repository.Save(provider, cancellationToken);
	}
}
```

The corresponding test can exercise the logical rule without a database:

```csharp
[Fact]
public void Rename_rejects_an_empty_name()
{
	var provider = new Provider(new ProviderId(Guid.NewGuid()), "Original");

	Assert.Throws<InvalidOperationException>(() => provider.Rename(" "));
}
```

The example is intentionally small. A real slice would add authorisation, audit, mapping, persistence, diagnostics, failure policy and operational evidence where the capability requires them. Those concerns belong in the design record and the boundary contracts; they should not be inferred from the first screen.
