# Operational Readiness

Farm preparedness and infrastructure capability domain.

---

## Domain Scope

Evaluates **operational preparedness** of the farm for the current growing season, including infrastructure condition, irrigation capacity, soil preparation status, and resource availability.

| Attribute | Value |
|-----------|-------|
| **Risk dimension** | `operational` |
| **Primary inputs** | Farm profile, readiness indicators, user context |
| **Output** | Domain signal with operational risk factors |

---

## Analysis Scope

```
  Farm Profile + Readiness Indicators
       │
       ├──▶ Infrastructure Assessment
       │
       ├──▶ Irrigation Adequacy Analysis
       │
       └──▶ Input Preparedness Review
                    │
                    ▼
           Risk Factor Extraction
```

---

## Risk Factor Categories

| Category | Examples |
|----------|----------|
| Irrigation | System capacity vs. crop water requirements |
| Soil preparation | Tillage, amendment, compaction status |
| Infrastructure | Storage, equipment, access condition |
| Input availability | Seed, fertilizer, pesticide readiness |

---

## Data Dependencies

| Source | Data Provided |
|--------|---------------|
| Farm profiles | Infrastructure records, irrigation systems |
| User indicators | Current season readiness status |
| Geospatial signal | Water availability cross-reference |

---

## Output

Produces a `DomainSignal` with `risk_dimension: "operational"` containing operational readiness risk factors.
