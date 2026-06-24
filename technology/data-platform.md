# Data Platform

Data storage, caching, and persistence architecture.

---

## Data Platform Components

```
  ┌─────────────────────────────────────────────────────────┐
  │                   DATA PLATFORM LAYER                    │
  │                                                          │
  │  ┌──────────────────┐       ┌──────────────────┐        │
  │  │ PostgreSQL       │       │ Redis            │        │
  │  │ (Persistent)     │       │ (Cache/Session)  │        │
  │  └──────────────────┘       └──────────────────┘        │
  └─────────────────────────────────────────────────────────┘
```

---

## PostgreSQL — Persistent Store

| Data Domain | Description |
|-------------|-------------|
| Farm profiles | Farm configuration and infrastructure records |
| Assessments | Assessment history and results |
| Domain signals | Capability output records |
| Audit logs | Lifecycle event history |
| Session checkpoints | Assessment Core state recovery |

**Deployment:** Azure Database for PostgreSQL (Flexible Server)

---

## Redis — Cache Layer

| Cache Domain | TTL | Purpose |
|--------------|-----|---------|
| Geospatial API responses | 6 hours | Reduce external API calls |
| Crop reference lookups | 24 hours | Reference data caching |
| Session state | Session lifetime | Pipeline runtime state |
| Rate limiting | Rolling window | API throttling |

**Deployment:** Azure Cache for Redis

---

## Data Flow

```
  Write Path:  Pipeline ──▶ PostgreSQL (assessments, signals, audit)
  Read Path:   Pipeline ──▶ Redis (cache check) ──▶ PostgreSQL (fallback)
  Cache Path:  External API ──▶ Redis ──▶ Pipeline
```

→ Architecture: [../architecture/data-acquisition-layer.md](../architecture/data-acquisition-layer.md)
