[Up](../readme.md)

# Before: Magic Strings for Routes and Permissions

A controller, authorisation attribute, policy registration and client call each contain strings such as:

```csharp
"api/rest/social/v1/personas"
"Social.Persona.Read"
"Social.Persona.Update"
```

The strings are easy to type and easy to copy. They are also easy to mistype.

The same meaning may appear with different spelling, casing or separators. A permission token is changed in one place and a search-and-replace misses another. A route prefix changes and one endpoint or client continues using the old path. A test passes because it uses the same wrong literal as the implementation. A controller path, permission name, storage location and diagnostic category are all treated as isolated text instead of being part of a coherent vocabulary.

The resulting errors are small and expensive:

- authorisation fails only for some paths;
- routes stop matching after a deployment;
- policies are registered under one name and requested under another;
- clients and tests drift from the service;
- storage or diagnostic locations become inconsistent; and
- searching for one value does not reveal the whole dependency tree.

The problem is not text itself. The problem is that shared meaning has no named, navigable source.
