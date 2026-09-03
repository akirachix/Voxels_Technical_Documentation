# Security

> Mara Guard handles sensitive field data — ranger identities, livestock-owner locations, and real-time predator activity. This page summarizes how every layer of the system keeps that data safe.

---

## 1. Authentication & Access

- **Token-based auth (JWT, HS256)** — Every protected request carries a JWT signed with `SECRET_KEY`. Tokens are read from an HTTPOnly `access_token` cookie or `Authorization: Bearer …` header.
- **30-minute expiry** — Short-lived tokens limit the blast radius of any leaked credential.
- **Bcrypt password hashing** — Passwords are never stored in plain text; login and password reset both go through the same hashing layer.
- **Rate-limited endpoints** — Brute-force protection on register, login, forgot-password, and verify-reset-code so attackers can't iterate over credentials or codes.

## 2. Authorization

- **Ranger-scoped routes** — Detection and telemetry endpoints are gated by the `get_current_ranger` dependency; only authenticated rangers can write or read system data.
- **HTTPOnly cookies** — Set on login with `SameSite=Lax`, so credentials aren't exposed to JavaScript on the page.
- **No role escalation** — The current public surface does not expose admin-only mutations; the `/rangers/` list endpoint requires auth and returns the ranger set, not role data.

## 3. Input Validation

- **Pydantic v2 schemas** — Types, lengths, and ranges are enforced at the edge (e.g. confidence `0.0–1.0`, battery `0–100`, password ≥ 6 chars, reset code exactly 6 chars).
- **Humanized 422 responses** — Clients receive a `detail` field they can render directly (e.g. *"Email: Please enter a valid email address."*).
- **Database check constraints** — Even if validation is bypassed, the database itself rejects out-of-range values.

## 4. Transport & Deployment

- **TLS in transit** — Served behind Heroku's HTTPS endpoint, so browser clients always talk to the API over TLS.
- **CORS allowlist** — Origins are restricted to a comma-separated `ALLOWED_ORIGINS` list; methods and headers are explicitly enumerated.
- **CI/CD with no standing credentials** — GitHub Actions deploys to Heroku from `main` using a deploy-only API key stored in GitHub Secrets.
- **Heroku-managed secrets** — The PostgreSQL connection string and JWT secret key live in Heroku config vars, never in source.

## 5. Data Safety

- **SQLAlchemy 2.0 repositories** — All database access goes through the repository layer; no raw SQL or string concatenation.
- **Short-lived reset codes** — Six-digit password-reset codes are stored in Redis with a short TTL and verified against the email + code pair before any password change.
- **Secrets out of code** — DB URL, JWT key, SMTP credentials, and CORS allowlist are read from environment variables via `pydantic-settings`.
- **Encrypted at rest** — Sensitive fields (e.g. `password_hash`) are stored only as bcrypt hashes; never as plain text.

## 6. Out of Scope (For Now)

- **Refresh tokens, 2FA, and a formal audit log** are not implemented in the current release.
- These are tracked as future work and would slot into the same JWT / rate-limit infrastructure without changing the public API surface.

---

> For the full backend API surface, see the [Backend Reference](backend.md).
