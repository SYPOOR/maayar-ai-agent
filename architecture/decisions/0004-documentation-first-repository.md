# ADR-0004: Documentation-First Public Repository

## Status

Accepted

## Context

Maayar requires a public GitHub presence for investors, competition judges, technical reviewers, and potential partners. Publishing production source code would expose proprietary risk models, prompt engineering, and implementation details that constitute core intellectual property.

## Decision

We will maintain a **documentation-first public repository** that publishes architecture, workflows, system design, and product vision — while keeping production implementation private.

The repository structure will intentionally resemble enterprise architecture repositories (OpenAI, Anthropic, Stripe, HashiCorp) rather than typical open-source code repositories.

## Consequences

### Positive

- Demonstrates architectural maturity to reviewers without IP exposure
- Enables community documentation contributions
- Creates a professional public face for the project
- ADRs and diagrams serve as institutional knowledge

### Negative

- Reviewers cannot audit implementation directly from the public repo
- Documentation must be actively maintained to stay synchronized with production
- Risk of perception that the project is "docs only" without deeper diligence

### Neutral

- Production code may be open-sourced selectively in the future

## Alternatives Considered

| Alternative | Reason Not Selected |
|-------------|---------------------|
| Full open source | IP exposure unacceptable during development |
| Private repository only | No public visibility for judges/investors |
| Code with heavy obfuscation | Unprofessional, still exposes structure |

## References

- [NOTICE.md](../../NOTICE.md)
- [Contributing Guidelines](../../CONTRIBUTING.md)
