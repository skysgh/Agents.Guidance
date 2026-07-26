# Frontend Security Conventions

Apply these conventions to browser applications and client-side build output.

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
