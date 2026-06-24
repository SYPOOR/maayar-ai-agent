# Acquisition Data Flow

```
  Farm Context ──▶ Data Acquisition Layer
                         │
                    Cache Check ──▶ Hit ──▶ Return
                         │ Miss
                         ▼
                  External APIs (NASA POWER, CHIRPS)
                         │
                         ▼
                    Cache Store
                         │
                         ▼
                  Enriched Context ──▶ Intelligence Layer
```
