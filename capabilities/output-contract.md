# Domain Output Contract

Standardized output contract for all Maayar capability modules.

---

## Signal Object Structure

```
  DomainSignal
  ├── capability_id          (identifier)
  ├── risk_dimension         (domain category)
  ├── signal_strength        (normalized 0–1)
  ├── confidence             (capability confidence 0–1)
  ├── factors[]              (decomposable risk factors)
  │   ├── name
  │   ├── description
  │   ├── weight
  │   ├── value
  │   └── severity
  ├── provenance             (data source attribution)
  │   ├── data_sources[]
  │   ├── processing_version
  │   └── metadata
  └── timestamp              (ISO 8601)
```

---

## Field Definitions

### DomainSignal

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `capability_id` | string | Yes | Capability module identifier |
| `risk_dimension` | enum | Yes | `geospatial`, `crop_context`, `operational`, `disease_exposure` |
| `signal_strength` | float (0–1) | Yes | Normalized domain risk intensity |
| `confidence` | float (0–1) | Yes | Capability confidence in signal accuracy |
| `factors` | array | Yes | Decomposable risk factors (minimum 1) |
| `provenance` | object | Yes | Data source and processing attribution |
| `timestamp` | ISO 8601 | Yes | Signal generation timestamp |

### RiskFactor

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Factor identifier |
| `description` | string | Human-readable description |
| `weight` | float (0–1) | Contribution weight within domain |
| `value` | float | Raw or normalized factor value |
| `severity` | enum | `low`, `moderate`, `elevated`, `critical` |

---

## Validation Rules

The Intelligence Layer validates all capability outputs before forwarding to Classification Services:

1. Schema conformance
2. Required field completeness
3. Value range validation (0–1 for strength and confidence)
4. Timestamp freshness
5. Minimum one risk factor present

---

## Contract Stability

The output contract is a **stable interface** between the Intelligence Layer and Classification Services. Capability implementations may evolve internally without breaking downstream processing, provided output contract compliance is maintained.
