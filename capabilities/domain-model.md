# Capability Domain Model

Conceptual domain model for Maayar capability modules.

---

## Domain Hierarchy

```
  Agricultural Risk Assessment
  │
  ├── Environmental Domain
  │   └── Geospatial Analysis
  │       ├── Climate exposure
  │       ├── Precipitation patterns
  │       └── Terrain characteristics
  │
  ├── Agronomic Domain
  │   └── Crop Context Analysis
  │       ├── Phenological timing
  │       ├── Regional suitability
  │       └── Growth stage alignment
  │
  ├── Operational Domain
  │   └── Operational Readiness
  │       ├── Infrastructure condition
  │       ├── Irrigation adequacy
  │       └── Input preparedness
  │
  └── Biological Domain
      └── Disease Exposure Analysis
          ├── Pathogen pressure
          ├── Environmental triggers
          └── Regional prevalence
```

---

## Domain Relationships

| Relationship | Description |
|--------------|-------------|
| Environmental → Biological | Climate conditions inform disease trigger analysis |
| Environmental → Agronomic | Climate alignment with crop phenology |
| Operational → Agronomic | Readiness affects crop management capacity |
| All → Classification | Independent signals aggregated downstream |

Capabilities analyze domains **independently**. Cross-domain correlation occurs only in Classification Services.

---

## Domain Signal Flow

```
  Capability Domain ──▶ Domain Signal ──▶ Classification Services
       (analysis)         (contract)         (aggregation)
```

Each domain produces exactly one signal object per assessment invocation.

→ Output specification: [output-contract.md](./output-contract.md)
