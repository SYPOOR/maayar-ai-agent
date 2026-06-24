# Data Acquisition Strategy

Data ingestion, enrichment, and caching workflow.

---

## Acquisition Workflow

```
  User Context                    External APIs
  (Farm boundary,                 (NASA POWER,
   crop type, etc.)                CHIRPS)
       │                               │
       ▼                               ▼
  ┌─────────────┐              ┌─────────────┐
  │ Validate &  │              │ Integration │
  │ Normalize   │              │ Adapters    │
  └──────┬──────┘              └──────┬──────┘
         │                            │
         └──────────┬─────────────────┘
                    ▼
           ┌───────────────┐
           │ Cache Check   │──── Hit ────▶ Return Cached
           └───────┬───────┘
                   │ Miss
                   ▼
           ┌───────────────┐
           │ Fetch & Store │
           └───────┬───────┘
                   ▼
           Enriched Assessment Context
```

---

## Data Source Matrix

| Source | Type | Refresh | Cache TTL |
|--------|------|---------|-----------|
| User intake | Real-time | Per request | N/A |
| Farm profiles | Persistent | On update | Session |
| NASA POWER | External API | On demand | 6 hours |
| CHIRPS | External API | On demand | 6 hours |
| Crop reference | Reference data | Periodic | 24 hours |

---

## Validation Gates

| Gate | Check |
|------|-------|
| Coordinate validation | Bounds within valid geographic ranges |
| Schema conformance | Required fields present and typed correctly |
| API response validation | External data matches expected structure |
| Freshness check | Data timestamps within assessment window |

---

## Failure Handling

| Failure | Response |
|---------|----------|
| Invalid user input | Reject at intake; return validation errors |
| External API timeout | Retry with backoff; proceed if capability tolerates |
| Cache unavailable | Direct API fetch; increased latency |
| All enrichment fails | Abort if no capabilities can execute |

→ Architecture: [../architecture/data-acquisition-layer.md](../architecture/data-acquisition-layer.md)
