<p align="center"><img src="./assets/banner.svg" alt="FinOps Cloud Automation" width="100%" /></p>

<p align="center">
  <img src="https://img.shields.io/badge/Portfolio-Utility%20Repository-111827?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Docs-Ready-22C55E?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Public-Sanitized-0EA5E9?style=for-the-badge" />
</p>

## Purpose

Cost governance, tagging policy, shutdown automation, budget review and cloud optimization patterns.

This repository is part of a public infrastructure leadership portfolio. It is designed to be useful, clean and easy to review.

## Contents

| Folder | Purpose |
|---|---|
| `docs/` | Standards, operating model and architecture notes. |
| `runbooks/` | Operational procedures and response templates. |
| `templates/` | Reusable patterns for teams. |
| `scripts/` | Small utilities and automation starters. |
| `.github/workflows/` | CI/CD and quality checks. |

## Operating model

```mermaid
flowchart LR
  A[Need] --> B[Standard]
  B --> C[Template]
  C --> D[Automation]
  D --> E[Review]
  E --> F[Operational use]
```

## Reviewer guide

- Start with `docs/operating-model.md`.
- Review `templates/` for reusable patterns.
- Review `runbooks/` for operational maturity.
- Review `.github/workflows/quality.yml` for repository discipline.

## Public safety

No employer code, no credentials, no customer data, no private diagrams and no internal hostnames.
