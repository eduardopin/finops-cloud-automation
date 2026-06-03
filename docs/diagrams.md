# FinOps Visual Diagrams

These diagrams show how cost signals move from cloud usage into review, action and governance. They are intentionally generic so teams can adapt them to their AWS account model, tagging standard and approval process.

## Operating Loop

```mermaid
flowchart LR
  usage[AWS usage and billing signals] --> collect[Collect cost and usage data]
  collect --> allocate[Allocate by account, tag and service]
  allocate --> analyze[Analyze variance, waste and commitments]
  analyze --> decide[Decide actions with service owners]
  decide --> act[Apply approved optimization actions]
  act --> measure[Measure savings, risk and reliability impact]
  measure --> usage

  security[Security and compliance review] -. guardrails .-> decide
  sre[SRE reliability review] -. risk checks .-> act
```

## Cost Data Flow

```mermaid
flowchart TD
  subgraph AWS["AWS accounts"]
    cur[Cost and Usage Report]
    ce[Cost Explorer API]
    tags[Resource tags]
    budgets[AWS Budgets]
  end

  subgraph Automation["Repository automation"]
    scripts[Cost review scripts]
    policies[Cloud governance policies]
    examples[Example budget and tag models]
  end

  subgraph Review["Engineering review"]
    showback[Showback summary]
    exceptions[Exception register]
    backlog[Optimization backlog]
  end

  cur --> scripts
  ce --> scripts
  tags --> scripts
  budgets --> scripts
  scripts --> showback
  policies --> exceptions
  examples --> backlog
  showback --> backlog
  exceptions --> backlog
```

## Tagging Governance

```mermaid
flowchart TB
  request[New workload or resource request] --> standard[Tagging standard]
  standard --> required{Required tags present?}
  required -- no --> reject[Return for owner, service, environment and cost center]
  required -- yes --> deploy[Deploy resource]
  deploy --> scan[Scheduled tag scan]
  scan --> compliant{Compliant?}
  compliant -- yes --> allocate[Allocate cost to owner and service]
  compliant -- no --> notify[Notify owner and create remediation item]
  notify --> exception{Approved exception?}
  exception -- yes --> expiry[Track expiry date]
  exception -- no --> remediate[Remediate or remove unused resource]
  expiry --> scan
  remediate --> scan
```

## Automation Decision Model

```mermaid
flowchart LR
  signal[Cost anomaly, idle resource or missing tag] --> classify[Classify finding]
  classify --> risk{Operational risk}
  risk -- low --> auto[Automated safe action]
  risk -- medium --> approve[Owner approval required]
  risk -- high --> review[Architecture and reliability review]

  auto --> evidence[Record evidence and result]
  approve --> action[Approved remediation]
  review --> decision[Document decision and trade-off]
  action --> evidence
  decision --> evidence
  evidence --> changelog[Update runbook, backlog or changelog]
```

## Review Use

Use these diagrams during repository review to check that examples and scripts support a closed operating loop: collect data, allocate cost, decide action, apply the change and measure the result. Any automation that changes infrastructure should keep an explicit approval path when reliability, security or customer impact is uncertain.
