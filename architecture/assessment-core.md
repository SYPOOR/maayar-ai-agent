# Assessment Core

Architecture of the Assessment Core — the central lifecycle manager for risk assessments.

---

## Purpose

The Assessment Core manages the **complete lifecycle** of a risk assessment session, from intake validation through result delivery. It serves as the coordination point between the API Gateway, Intelligence Layer, Classification Services, and Decision Support Layer.

---

## Lifecycle States

```
  ┌────────┐     ┌────────────┐     ┌─────────────┐     ┌──────────────┐
  │ INTAKE │────▶│ VALIDATED  │────▶│ PROCESSING  │────▶│ CLASSIFYING  │
  └────────┘     └────────────┘     └─────────────┘     └──────┬───────┘
       │                                                    │
       ▼                                                    ▼
  ┌────────┐                                          ┌──────────────┐
  │ REJECTED│                                         │  COMPLETED   │
  └────────┘                                          └──────────────┘
                                                             │
                                                             ▼
                                                      ┌──────────────┐
                                                      │  DELIVERED   │
                                                      └──────────────┘
```

---

## Responsibilities

| Responsibility | Description |
|----------------|-------------|
| **Session initialization** | Create assessment session from validated intake |
| **Pipeline coordination** | Sequence Data Acquisition → Intelligence → Classification → Decision Support |
| **State persistence** | Checkpoint session state to Data Platform |
| **Error routing** | Direct failures to appropriate handling paths |
| **Result assembly** | Compose final assessment package for delivery |
| **Audit logging** | Record lifecycle events with timestamps and metadata |

---

## Assessment Session Model

| Field | Description |
|-------|-------------|
| `session_id` | Unique assessment identifier |
| `farm_context` | Boundary, crop type, operational metadata |
| `status` | Current lifecycle state |
| `capability_signals` | Collected domain signals from Intelligence Layer |
| `classification` | Output from Classification Services |
| `decision_output` | Final decision support package |
| `metadata` | Timestamps, partial flags, version information |

---

## Integration Points

```
  API Gateway ──────▶ Assessment Core ◀────── Data Platform
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
        Data Acquisition  Intelligence  Classification
                           Layer        Services
                                            │
                                            ▼
                                    Decision Support
```

---

## Design Constraints

| Constraint | Implementation |
|------------|----------------|
| Idempotent intake | Duplicate requests produce consistent sessions |
| Deterministic pipeline | Same inputs produce same architectural flow |
| Recoverable state | Checkpoints enable session resumption |
| Auditable transitions | Every state change is logged |

→ Pipeline workflow: [../workflows/risk-assessment-pipeline.md](../workflows/risk-assessment-pipeline.md)
