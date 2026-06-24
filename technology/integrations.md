# Integrations

External data source integrations.

---

## Integration Architecture

```
  Data Acquisition Layer
       │
       ├──▶ NASA POWER API ──▶ Climate, solar, temperature data
       │
       └──▶ CHIRPS API ──────▶ Precipitation estimates
```

---

## NASA POWER

| Attribute | Value |
|-----------|-------|
| **Provider** | NASA Langley Research Center |
| **Data** | Solar radiation, temperature, humidity, wind |
| **Used by** | Geospatial Analysis capability |
| **Pattern** | Cache-aside with 6-hour TTL |

**Reference:** https://power.larc.nasa.gov/

---

## CHIRPS

| Attribute | Value |
|-----------|-------|
| **Provider** | Climate Hazards Center, UC Santa Barbara |
| **Data** | Precipitation estimates (0.05° resolution) |
| **Used by** | Geospatial Analysis capability |
| **Pattern** | Cache-aside with 6-hour TTL |

**Reference:** https://www.chc.ucsb.edu/data/chirps

---

## Integration Patterns

| Pattern | Description |
|---------|-------------|
| Cache-aside | Check Redis before external call |
| Bounding box queries | Query by farm coordinate envelope |
| Retry with backoff | Handle transient failures |
| Provenance tracking | Record source in domain signals |

---

## Attribution

External data sources are acknowledged in assessment provenance metadata per provider requirements.
