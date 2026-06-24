# معيار (Maayar)

### Multi-Skilled AI Agent for Agricultural Risk Assessment

An AI-powered system that combines geospatial, environmental, and agricultural intelligence to generate the **X Risk Score** and support agricultural risk assessment.

---

## System Architecture

```text
                         ┌───────────────┐
                         │     User      │
                         └───────┬───────┘
                                 │
                                 ▼
                    ┌─────────────────────┐
                    │       Agent X       │
                    │ Central Orchestrator│
                    └─────────┬───────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼

┌────────────────┐  ┌────────────────┐  ┌────────────────┐
│   Geospatial   │  │ Crop Context   │  │ Farm Readiness │
│     Skill      │  │     Skill      │  │     Skill      │
└────────┬───────┘  └────────┬───────┘  └────────┬───────┘
         │                   │                   │
         └───────────────────┼───────────────────┘
                             │
                             ▼

                  ┌─────────────────────┐
                  │ Disease Risk Skill  │
                  └──────────┬──────────┘
                             │
                             ▼

               ┌──────────────────────────┐
               │ Risk Classification Engine│
               └────────────┬─────────────┘
                            │
                            ▼

                   ┌─────────────────┐
                   │  X Risk Score   │
                   │     (0-100)     │
                   └────────┬────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼

   Recommendations      Reports           Alerts
```

---

## Core Skills

| Skill                      | Purpose                                   |
| -------------------------- | ----------------------------------------- |
| Geospatial Skill           | Location and climate analysis             |
| Crop Context Skill         | Crop-specific risk factors                |
| Farm Readiness Skill       | Operational preparedness assessment       |
| Disease Risk Skill         | Disease probability and severity analysis |
| Risk Classification Engine | Aggregates results and calculates risk    |

---

## Outputs

* X Risk Score (0–100)
* Risk Classification
* Advisory Recommendations
* Automated Reports
* Risk Alerts

---

## Technology Stack

### AI & Orchestration

* Qwen 3
* Qwen 2.5-VL
* LangGraph

### Backend

* Flask

### Frontend

* React

### Database

* PostgreSQL
* Redis

### Infrastructure

* Docker
* Microsoft Azure

### External Data Sources

* NASA POWER API
* CHIRPS API

---

## Team

TEAM X
