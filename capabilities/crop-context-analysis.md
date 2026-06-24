# Crop Context Analysis

Crop-specific phenological and regional suitability capability domain.

---

## Domain Scope

Evaluates **crop-specific risk factors** based on declared crop type, current growth stage, regional suitability, and phenological timing relative to environmental conditions.

| Attribute | Value |
|-----------|-------|
| **Risk dimension** | `crop_context` |
| **Primary inputs** | Crop type, planting date, regional reference data |
| **Output** | Domain signal with agronomic risk factors |

---

## Analysis Scope

```
  Crop Type + Planting Date
       │
       ├──▶ Crop Calendar Lookup ──▶ Phenological Position
       │
       └──▶ Regional Suitability ──▶ Compatibility Score
                    │
                    ▼
           Risk Factor Extraction
```

---

## Risk Factor Categories

| Category | Examples |
|----------|----------|
| Phenological timing | Growth stage vs. seasonal conditions mismatch |
| Regional suitability | Crop-region compatibility score |
| Planting window | Early/late planting risk |
| Harvest timing | Predicted harvest window risk exposure |

---

## Data Dependencies

| Source | Data Provided |
|--------|---------------|
| Crop calendars | Planting/harvest windows, growth stages |
| Regional databases | Crop suitability by geography |
| Assessment context | Declared crop type and dates |

---

## Output

Produces a `DomainSignal` with `risk_dimension: "crop_context"` containing agronomic risk factors.
