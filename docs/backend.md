# Backend

> The Mara Guard backend is a production FastAPI service — typed, secured, and auto-documented. It powers ranger accounts, real-time lion detections, and field-node telemetry, exposed through a clean REST surface.

**Live API:** [Swagger UI](https://maraguard-3686f239afe8.herokuapp.com/docs) · [ReDoc](https://maraguard-3686f239afe8.herokuapp.com/redoc) · [OpenAPI Spec](https://maraguard-3686f239afe8.herokuapp.com/openapi.json)

---

## 1. Overview

- **Framework** — FastAPI on Python 3.12, with async I/O and auto-generated OpenAPI 3.0 docs.
- **Title / Version** — `Mara Guard` · `0.1.0`.
- **Auth** — JWT (HS256) delivered via HTTPOnly `access_token` cookie or `Authorization: Bearer …` header.
- **CORS** — Allowlist-driven via the `ALLOWED_ORIGINS` environment variable.
- **Validation** — Pydantic v2 schemas with humanized 422 error messages.
- **Database** — PostgreSQL + SQLAlchemy 2.0 + Alembic.
- **Cache** — Redis (with graceful in-memory fallback).

## 2. Project Structure

```text
Voxels_Backend/
├── main.py                 # FastAPI app, middleware, exception handlers
├── database.py             # Engine, SessionLocal, Redis client
├── requirements.txt
├── alembic.ini
├── alembic/versions/       # Initial migration
└── maraguardAPI/
    ├── core/              # config.py, dependencies.py (get_current_ranger)
    ├── models/            # SQLAlchemy ORM models
    ├── schemas/           # Pydantic request/response models
    ├── routers/           # API routes (ranger, detection, telemetry_logs)
    ├── repositories/      # Data-access layer
    └── services/          # Business logic and orchestration
```

The request flow is **Router → Schema → Service → Repository → DB**, with Redis used for short-lived reset codes and SMTP used to deliver them.

## 3. Setup & Installation

```bash
git clone https://github.com/akirachix/Voxels_Backend.git
cd Voxels_Backend
python -m venv env && source env/bin/activate
pip install -r requirements.txt
cp .env.example .env       # fill in DATABASE_URL, SECRET_KEY, MAIL_*
alembic upgrade head
python main.py             # or: uvicorn main:app --reload
```

The API runs on `http://localhost:8000`. Interactive docs are at `/docs` and `/redoc`.

## 4. Environment Variables

| Variable | Description | Default |
| --- | --- | --- |
| `DATABASE_URL` | PostgreSQL connection string | `postgresql://postgres:postgres@localhost:5432/maraguard_db` |
| `SECRET_KEY` | JWT signing secret | _required_ |
| `ALGORITHM` | JWT algorithm | `HS256` |
| `ACCESS_TOKEN_EXPIRE_MINUTES` | Token lifetime | `30` |
| `REDIS_URL` | Redis connection string | `redis://localhost:6379` |
| `MAIL_USERNAME` | SMTP username (password reset) | _required_ |
| `MAIL_PASSWORD` | SMTP password / app password | _required_ |
| `MAIL_FROM` | Sender address | _required_ |
| `MAIL_PORT` | SMTP port | `587` |
| `MAIL_SERVER` | SMTP host | `smtp.gmail.com` |
| `ALLOWED_ORIGINS` | Comma-separated CORS allowlist | `http://localhost:3000,http://192.168.100.95:3000` |

## 5. Authentication & User Management — `/rangers`

- **`POST /rangers/register`** — Register a new ranger. Returns `201` with a `RangerResponse`.
- **`POST /rangers/login`** — Login. Returns a JWT and sets the `access_token` HTTPOnly cookie.
- **`GET /rangers/me`** — Current ranger profile (auth required).
- **`GET /rangers/`** — List all rangers (auth required).
- **`POST /rangers/forgot-password`** — Send a 6-digit reset code via SMTP.
- **`POST /rangers/verify-reset-code`** — Verify the 6-digit code.
- **`POST /rangers/reset-password`** — Reset the password with code + new password.

## 6. Detection Management — `/detection` (auth required)

- **`POST /detection`** — Log a new lion detection event.
- **`GET /detection?date_captured=YYYY-MM-DD`** — List detections, optional date filter.

## 7. Telemetry Management — `/telemetry` (auth required)

- **`POST /telemetry/`** — Create a telemetry log. Returns `201` with `TelemetryLogResponse`.
- **`GET /telemetry/`** — List all telemetry logs.
- **`PATCH /telemetry/{log_id}`** — Update a telemetry log (e.g. battery level).
- **`DELETE /telemetry/{log_id}`** — Delete a telemetry log.

## 8. Data Models

### 8.1 `rangers`
| Field | Type | Constraint |
| --- | --- | --- |
| `ranger_id` | Integer | PK, autoincrement, indexed |
| `first_name` | String(100) | NOT NULL |
| `last_name` | String(100) | NOT NULL |
| `email` | String(100) | NOT NULL, UNIQUE |
| `password_hash` | String(255) | NOT NULL (bcrypt) |

### 8.2 `detections`
| Field | Type | Constraint |
| --- | --- | --- |
| `detection_id` | String(36) | PK (UUID) |
| `log_id` | String(36) | NOT NULL |
| `time_captured` | DateTime | NOT NULL |
| `confidence_score` | Numeric(3,2) | `0.00 – 1.00` (CHECK) |
| `lion_count` | Numeric(5,0) | `≥ 0`, default `0` (CHECK) |

### 8.3 `Telemetry_logs`
| Field | Type | Constraint |
| --- | --- | --- |
| `log_id` | String(36) | PK (UUID), indexed, auto-generated |
| `ranger_id` | String(36) | NOT NULL |
| `datetime` | DateTime | NOT NULL, default `utcnow()` |
| `battery_level` | Numeric(10,2) | `0 – 100` (CHECK) |

## 9. Cross-Cutting Concerns

- **CORS** — Origins are read from `ALLOWED_ORIGINS`. Credentials enabled; methods `GET, POST, PUT, PATCH, DELETE, OPTIONS`; headers `Content-Type`, `Authorization`.
- **Auth** — `get_current_ranger` reads the JWT from cookie first, then header. Tokens are HS256-signed; `sub` carries the ranger id.
- **Validation** — Custom handlers turn Pydantic errors into humanized `detail` strings (e.g. *"Email: Please enter a valid email address."*).
- **Database** — Engine uses `pool_pre_ping=True` for dead-session recovery. Schema is Alembic-managed.
- **Redis (optional)** — If the connection fails on startup, the app logs the error and continues with `redis_client = None`.

## 10. Testing

End-to-end tests run with Playwright:

```bash
playwright test
```

## 11. Code Standards

- **Naming** — `snake_case` for variables, functions, and files; `PascalCase` for classes and models.
- **Structure** — Routers, schemas, services, and repositories each in their own file.
- **Commits** — Conventional Commits (`feat:`, `fix:`, `docs:`, …).

## 12. Deployment

- **Platform** — Heroku (staging & production).
- **Branch** — Auto-deploys from `main` via GitHub Actions (`.github/workflows/deploy.yml`).
- **Runtime** — `Procfile` runs `uvicorn main:app --host 0.0.0.0 --port $PORT`.
- **Migrations** — CI step `heroku run alembic upgrade head` after deploy.
- **Scaling** — Automatic via Heroku dynos.
- **Rollback** — Re-deploy a previous release from the Heroku dashboard.

---

> For the security model and threat-mitigation approach, see the [Security page](security.md).
