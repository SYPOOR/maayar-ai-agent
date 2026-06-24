# Data Acquisition Layer

Architecture of data ingestion, enrichment, and caching strategy.

---

## Purpose

The Data Acquisition Layer is responsible for gathering, validating, and enriching assessment data from user-provided context and external integrations before capability modules execute.

---

## Acquisition Flow

```
  User-Provided Context
  (Farm boundary, crop type, readiness indicators)
       │
       ▼
  ┌─────────────────┐
  │ Validate &      │
  │ Normalize       │
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐     Cache Hit?     ┌─────────────┐
  │ Enrichment      │───────────────────▶│ Return      │
  │ Orchestrator    │                    │ Cached Data │
  └────────┬────────┘                    └─────────────┘
           │ Cache Miss
           ▼
  ┌─────────────────────────────────────────┐
  │         External Integrations           │
  │  ┌─────────────┐    ┌─────────────┐    │
  │  │ NASA POWER  │    │ CHIRPS      │    │
  │  │ (Climate)   │    │ (Precip.)   │    │
  │  └─────────────┘    └─────────────┘    │
  └────────────────┬────────────────────────┘
                   │
                   ▼
           ┌─────────────┐
           │ Cache Store │
           │ (Redis)     │
           └──────┬──────┘
                  │
                  ▼
           Enriched Assessment Context
                  │
                  ▼
           Intelligence Layer
```

---

## Data Sources

| Source | Type | Consumed By |
|--------|------|-------------|
| User intake | Farm boundary, crop type | All capabilities |
| Farm profiles | Historical and infrastructure data | Operational Readiness |
| NASA POWER API | Climate, solar, temperature | Geospatial Analysis |
| CHIRPS API | Precipitation estimates | Geospatial Analysis |
| Crop reference data | Phenology, regional calendars | Crop Context Analysis |
| Disease indices | Regional prevalence data | Disease Exposure Analysis |

---

## Caching Strategy

| Data Category | Cache TTL | Invalidation Trigger |
|---------------|-----------|---------------------|
| Geospatial API responses | 6 hours | Farm boundary change |
| Crop reference lookups | 24 hours | Crop type change |
| Farm profile data | Session lifetime | Profile update |

---

## Data Classification

| Classification | Storage | Retention |
|----------------|---------|-----------|
| User-provided | Persistent store | Account lifetime |
| Enriched (API) | Cache + assessment record | Cache TTL / assessment lifetime |
| Computed (signals) | Persistent store | Assessment lifetime |
| Ephemeral (session) | Cache | Session lifetime |

→ Workflow: [../workflows/data-acquisition-strategy.md](../workflows/data-acquisition-strategy.md)  
→ Integrations: [../technology/integrations.md](../technology/integrations.md)
