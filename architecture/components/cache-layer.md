# Cache Layer

Redis-based caching within the Data Platform Layer.

---

## Cache Domains

| Domain | TTL | Purpose |
|--------|-----|---------|
| Geospatial API responses | 6 hours | External climate/precipitation data |
| Capability outputs | Minutes | Session-scoped reuse |
| Session state | Session lifetime | Pipeline runtime state |
| Rate limits | Rolling window | API throttling |

---

## Architecture

```
  Capability Modules ──▶ Redis ◀── Pipeline Runtime
  External APIs      ──▶ Redis
  API Gateway        ──▶ Redis (rate limits)
```

---

## Invalidation

- Geospatial cache: invalidated on farm boundary change
- Capability cache: scoped to assessment session
- Composite risk output: always computed fresh (not cached)

→ [Data Platform](../../technology/data-platform.md)
