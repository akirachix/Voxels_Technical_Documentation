# Features

> Mara Guard combines field-proven IoT hardware, on-device AI, and ranger-facing apps into one cohesive detection-to-response system. Below is a stakeholder-friendly tour of every capability.

---

## 1. Field & Edge Intelligence

Built to survive the Mara — no grid, no cellular, no humans in the loop.

- **Always-on movement detection** — Microwave radar arrays monitor boundary perimeters up to 6 m deep, filtering out rain, dust, fog, and thermal distortion.
- **On-device YOLOv8 inference** — A Raspberry Pi 5 host runs an optimized convolutional neural network locally, classifying predators in ~12 ms from signal ingestion.
- **Layered autonomous countermeasures** — On threat validation, the node fires dual startle-defense circuits: a high-lumen spotlight to disorient nocturnal tracking and a high-decibel horn held until the zone is clear.
- **Empirical precision** — A strict 60 % confidence threshold via an anchor-free detection head ignores non-threatening movement (wind-blown brush, herding dogs, livestock cattle).
- **Solar-powered autonomy** — A solar panel matrix charges a central battery bank so the node operates indefinitely in off-grid terrain.

## 2. Wireless Telemetry & Gateway

Detection data moves from the field to the cloud without commercial cellular.

- **Long-range LoRa radio** — Active incident logs are packaged into compact binary packets and broadcast over point-to-point LoRa radio link arrays.
- **ESP32 + Wi-Fi gateway** — A paylink gateway bridges the field node to the wider system over Wi-Fi.
- **MQTT pub/sub** — Standardized JSON payloads flow through explicit topics, decoupling producers from consumers.
- **Offline queueing** — If the gateway uplink drops, the Train Analysis Module buffers packets locally and replays them on reconnect.

## 3. Backend API & Data Persistence

Secure, well-typed, and easy to integrate with.

- **FastAPI service** — Async REST endpoints with auto-generated OpenAPI 3.0 documentation.
- **JWT authentication** — HS256 tokens delivered via HTTPOnly cookie or `Authorization: Bearer …` header; 30-minute expiry.
- **PostgreSQL + SQLAlchemy 2.0** — Typed ORM models for rangers, detections, and telemetry, with Alembic migrations.
- **Redis caching** — Short-lived password-reset codes with TTL, plus graceful in-memory fallback.
- **Humanized validation errors** — Pydantic v2 schemas turn invalid input into friendly `422` messages clients can render directly.

## 4. Ranger-Facing Surfaces

Tools that fit how rangers actually work — at a desk and in the field.

- **Ranger dashboard / PWA** — Real-time intrusion lists, historic trend timelines, predator densities, and INA219 battery voltage records.
- **Flutter mobile app** — On-brand entry point, recent activity feed, secure signup, and live status from the field.
- **Proactive alerting** — Verified detections surface instantly so rangers can intervene before an incident escalates.
- **Device health at a glance** — Per-node battery level, last seen, and active/inactive flag.
- **Historical review** — Confidence score, lion count, and timestamp for every detection — auditable after the fact.

## 5. Outcomes & Metrics

Designed to demonstrate impact to conservation partners and donors.

- **North Star Metric** — Number of human-lion conflict incidents prevented, measured through field-node detections.
- **First Proactive Intervention** — Time from high-threat alert to ranger acknowledgement within the target response window.
- **Daily Active Ranger Retention** — Percentage of trained rangers still monitoring alerts 30, 60, and 90 days after onboarding.

---

> Ready to build the edge node hardware stack? [Jump to the Getting Started Guide](getting-started.md).
