# Geospatial Analysis

Environmental and climate exposure capability domain.

---

## Domain Scope

Analyzes **environmental and climate conditions** at the farm location to identify geospatial risk factors including precipitation patterns, temperature stress, solar radiation anomalies, and terrain characteristics.

| Attribute | Value |
|-----------|-------|
| **Risk dimension** | `geospatial` |
| **Primary inputs** | Farm boundary, climate APIs, precipitation data |
| **Output** | Domain signal with environmental risk factors |

---

## Analysis Scope

```
  Farm Boundary
       │
       ▼
  ┌─────────────────┐
  │ Spatial Context │  Coordinate envelope, terrain
  └────────┬────────┘
           ▼
  ┌─────────────────┐
  │ Climate Data    │  NASA POWER integration
  └────────┬────────┘
           ▼
  ┌─────────────────┐
  │ Precipitation   │  CHIRPS integration
  └────────┬────────┘
           ▼
  ┌─────────────────┐
  │ Risk Factor     │  Environmental signal generation
  │ Extraction      │
  └─────────────────┘
```

---

## Risk Factor Categories

| Category | Examples |
|----------|----------|
| Precipitation | Deficit, excess, variability, dry spell duration |
| Temperature | Heat stress, frost risk, growing degree days |
| Solar radiation | Insolation anomalies, cloud cover impact |
| Terrain | Elevation effects, slope drainage, aspect exposure |

---

## Data Dependencies

| Source | Data Provided |
|--------|---------------|
| NASA POWER | Solar radiation, temperature, humidity, wind |
| CHIRPS | Precipitation estimates (0.05° resolution) |

→ Integrations: [../technology/integrations.md](../technology/integrations.md)

---

## Output

Produces a `DomainSignal` with `risk_dimension: "geospatial"` containing environmental risk factors with full data provenance.
