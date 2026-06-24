# ADR-0006: Microsoft Azure as Cloud Platform

## Status

Accepted

## Context

Maayar requires a cloud platform supporting containerized workloads, managed databases, caching, secrets management, and global CDN delivery. The platform must support GPU workloads for self-hosted model inference and comply with enterprise security requirements.

## Decision

We will deploy Maayar on **Microsoft Azure** using Container Apps, managed PostgreSQL, Azure Cache for Redis, Key Vault, and Azure Monitor.

## Consequences

### Positive

- Integrated managed services reduce operational overhead
- Enterprise-grade security and compliance certifications
- Azure Container Apps supports scale-to-zero for cost optimization
- Strong GPU VM offerings for model inference (NC-series)

### Negative

- Vendor lock-in to Azure-specific services
- Azure pricing complexity requires active cost management
- Some team members may have stronger AWS/GCP experience

### Neutral

- Architecture abstracts cloud provider at the container level where possible

## Alternatives Considered

| Alternative | Reason Not Selected |
|-------------|---------------------|
| AWS | Comparable but team preference and existing Azure credits |
| Google Cloud | Strong AI tooling but less integrated managed database offering |
| Self-hosted / on-prem | Operational burden too high for current team size |

## References

- [Azure Infrastructure](../../technology/infrastructure/azure.md)
- [Deployment Topology](../diagrams/deployment-topology.md)
