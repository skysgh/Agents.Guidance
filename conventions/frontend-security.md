# Frontend Security Conventions

Apply these conventions to browser applications and client-side build output.

For the accessible explanation of browser security as a boundary, read [Human Guidance](../HUMAN/README.md).

## Purpose

Browser code is a door into the service. It displays information, accepts actions and communicates with other systems. A browser application therefore needs the same careful protection as any other boundary.

## The short version

Do not place secrets in places a browser user or injected script can read. Treat every external value, link, message and dependency as something that needs a clear trust decision. Test the paths where identity expires, state changes fail, content is untrusted or protected information might leak.

In technical language, these are frontend security controls. The practical idea is to keep the door safe while still allowing people to use the building.

- Keep credentials and tokens out of localStorage, sessionStorage, URLs and client logs.
- Use secure, HttpOnly cookies for authentication tokens where cookies are the chosen transport.
- Protect state-changing cookie-authenticated requests against CSRF.
- Encode untrusted text by context and avoid unsafe HTML, script, URL and style injection.
- Use a restrictive Content Security Policy and Trusted Types where supported and practical.
- Do not load third-party scripts, frames, fonts or analytics without an explicit trust and privacy decision.
- Treat source maps, error reports and client telemetry as potentially sensitive outputs.
- Validate redirect, download, postMessage and external-link targets.
- Keep dependency and bundle changes reviewable; do not hide executable code in generated assets.
- Test authentication expiry, logout, CSRF, XSS, clickjacking, unsafe redirects and sensitive-data leakage.

Browser code is a security boundary even when it contains no server code.
