# Deployment Diagram

```
                         Internet
                            │
                            ▼
                 ┌──────────────────┐
                 │ Azure Front Door │
                 │ (WAF + Routing)  │
                 └────────┬─────────┘
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
  ┌──────────────────┐     ┌──────────────────┐
  │ Azure CDN        │     │ Azure Container    │
  │ Web Application  │     │ Apps               │
  │ (Static)         │     │ API + Pipeline     │
  └──────────────────┘     └────────┬─────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    ▼                 ▼                 ▼
          ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
          │ PostgreSQL   │  │ Redis        │  │ Key Vault    │
          │ (Flexible)   │  │ (Cache)      │  │ (Secrets)    │
          └──────────────┘  └──────────────┘  └──────────────┘
                                      │
                                      ▼
                            ┌──────────────────┐
                            │ Azure Monitor    │
                            │ + Log Analytics  │
                            └──────────────────┘
```
