# Classification Services

Architecture of risk classification, normalization, and tier assignment.

---

## Purpose

Classification Services transform heterogeneous domain signals from the Intelligence Layer into **unified, classified risk assessments** suitable for decision support output.

---

## Processing Pipeline

```
  Domain Signals (1–4 capability domains)
       │
       ▼
  ┌─────────────┐
  │ Normalize   │  Map domain signals to common scale
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │ Weight      │  Apply domain-specific weighting
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │ Aggregate   │  Combine weighted domain scores
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │ Classify    │  Assign risk tier
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │ Decompose   │  Generate dimensional breakdown
  └──────┬──────┘
         ▼
  Classification Result ──▶ Decision Support Layer
```

---

## Input Requirements

| Requirement | Policy |
|-------------|--------|
| Signal format | Standardized domain signal contract |
| Minimum domains | At least one valid capability signal |
| Confidence threshold | Signals below threshold flagged or excluded |
| Freshness | Timestamps within acceptable assessment window |

---

## Risk Tier Model

| Tier | Description | Typical Response |
|------|-------------|------------------|
| **Low** | Signals within acceptable thresholds | Routine monitoring |
| **Moderate** | Elevated signals in one or more domains | Review and plan mitigation |
| **Elevated** | Significant risk across multiple domains | Active intervention recommended |
| **Critical** | Severe signals with high confidence | Immediate action required |

> Tier boundaries and weighting parameters are proprietary configuration values not published in this repository.

---

## Output Schema

| Field | Description |
|-------|-------------|
| `overall_tier` | Composite risk classification |
| `domain_scores` | Per-capability classified scores |
| `contributing_factors` | Ranked risk factors by impact |
| `confidence` | Classification confidence level |
| `partial` | Whether assessment used degraded inputs |
| `metadata` | Version, timestamps, capability participation |

---

## Design Properties

| Property | Guarantee |
|----------|-----------|
| **Determinism** | Same signals produce same classification |
| **Auditability** | Every tier decomposes to contributing factors |
| **Configurability** | Weights adjustable without architectural change |
| **Degradation** | Operates on partial signals with adjusted confidence |

→ Decision output: [decision-support-layer.md](./decision-support-layer.md)
