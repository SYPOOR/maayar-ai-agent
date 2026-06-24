# Disease Exposure Analysis

Pathogen pressure and environmental disease trigger capability domain.

---

## Domain Scope

Assesses **disease and pest pressure risk** by correlating environmental conditions with known pathogen triggers, regional disease indices, and crop susceptibility profiles.

| Attribute | Value |
|-----------|-------|
| **Risk dimension** | `disease_exposure` |
| **Primary inputs** | Climate data, disease indices, crop susceptibility |
| **Output** | Domain signal with biological risk factors |

---

## Analysis Scope

```
  Climate Conditions ──┐
  Crop Context ────────┼──▶ Trigger Correlation ──▶ Risk Factor Extraction
  Disease Indices ─────┘
```

---

## Risk Factor Categories

| Category | Examples |
|----------|----------|
| Fungal pressure | Humidity + temperature disease triangle conditions |
| Bacterial risk | Moisture exposure, wound entry conditions |
| Pest pressure | Seasonal pest index, crop attractiveness |
| Vector-borne disease | Vector habitat suitability indicators |
| Regional outbreak proximity | Nearby reported disease events |

---

## Data Dependencies

| Source | Data Provided |
|--------|---------------|
| Geospatial signal | Temperature, humidity, precipitation patterns |
| Crop context signal | Growth stage, crop susceptibility |
| Disease indices | Regional historical prevalence data |

---

## Output

Produces a `DomainSignal` with `risk_dimension: "disease_exposure"` containing biological risk factors.
