Apply these conventions to authentication, authorisation, identity, session, privacy and security-sensitive design decisions.

For the accessible review prompts, read [Security at Rest Checklist](../../../humans/reference/checklists/security-at-rest.md) and [Security in Transit Checklist](../../../humans/reference/checklists/security-in-transit.md).

### Identification
Design the system to not need their Name. Identify them by the uniqueness of the `sid`:`sub`

Note, however, 2FA requires disclosure of an email address. So...damned if you do, damned if you don't.


### Notifications

Never send out personal information in messages retrieved outside the audited environment of systems.

**Do Not:**

- `Hi {UserName},` Their Username may be deemed private information ('Spanky69', etc.)
- `Hi {Joe}` It identifies them within the small pool of users of that laptop.
- `Your balance is {balance}.` Their resources whether records or registries of finance, activity, support needs, etc. are private information. 
- `Your ID number is {nationalIdNumber}.` Absolutely not. 

**Instead:**

Provide them a quick one time temporary link to into the system to view the message waiting for them in an audited environment, such that operations on it it (View, Delete, Respond) can be developed and kept. 
- `Click {here} to view the latest information on your account.` No PI is provided.


### Secure & Http-Only Cookies

Authentication cookies must be Secure, HttpOnly and protected against cross-site request forgery. For browser SPAs using OIDC, identity is established and validated by OIDC but browser-to-service interaction uses the protected cookie session only. Do not persist access or ID tokens in localStorage, sessionStorage, IndexedDB, the Cache API or equivalent browser-controlled storage, and do not put them in URLs or logs. Development environments must use the same token storage and identity model as production. If local HTTPS or an identity provider is inconvenient, use a local development issuer, test identity provider or controlled development certificate. Do not fall back to client-stored bearer tokens.
