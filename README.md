<p align="center"><img src="assets/overview.svg" alt="Trading System V4.0 engineering portfolio" width="100%" /></p>

# Trading System V4.0

**Separating a simulated protection from evidence that an integration implements it.**

Developed state-aware portfolio simulation and comparative stress research, with an audit that distinguished historical arithmetic from integration behavior. These results belong to an earlier audited V4 snapshot.

| Project lens | Evidence type | Implementation | Public artifacts |
|---|---|---|---|
| Stateful simulation and risk analysis | Historical simulation and preserved audits | Private | Architecture, methods, aggregate results |

**Explore:** [System design](docs/ENGINEERING.md) · [Measurement methodology](docs/METHODOLOGY.md) · [Detailed results](docs/RESULTS.md) · [Machine-readable metrics](metrics.json)

## The engineering problem

A protection can exist in a simulator while an integration lacks the state needed to use it. A performance table alone cannot demonstrate that the surrounding system behaves the same way.

## System at a glance

The diagram is a conceptual view of the research workflow. It describes logical responsibilities, not a deployment topology or an executable trading specification.

```mermaid
flowchart LR
    A[Historical market inputs] --> B[Calendar and coverage checks]
    B --> C[Private decision component]
    C --> D[Historical execution model]
    D --> E[Chronological portfolio replay]
    E --> F[Whole-position accounting]
    E --> G[Adverse equity marks]
    F --> H[Aggregate report]
    G --> H
    I[Declared cost scenario] --> D
    J[Audit and sensitivity comparisons] --> H
    classDef private fill:#172338,color:#ffffff,stroke:#64748b
    class C private
```

## Engineering dimensions

| Dimension | What the project examines | Why it matters |
|---|---|---|
| Temporal integrity | Which information exists at each research step | Reduces future-information leakage |
| State evolution | How earlier events affect later eligibility and equity | Prevents treating dependent decisions as isolated observations |
| Execution assumptions | Costs, adverse marks and minute-bar limitations | Makes reported performance interpretable |
| Measurement | Consistent position counts, net results and drawdown definitions | Avoids misleading headline comparisons |
| Evidence discipline | Preserved snapshots, controls and explicit limitations | Separates reproducible output from unsupported claims |

## Historical evidence snapshot

**January 2–October 1, 2026 · minute-bar simulation · snapshot audited October 13, 2026.** These are inspected development results, not prospective performance.

> **Version boundary:** the results describe an earlier audited V4 configuration. Later V4 revisions are not measured by this table. Historical simulation and integration behavior were not equivalent in the audit.

| Scenario | Net P&L | Maximum drawdown* | Positions | Win rate | Profit factor |
|---|---:|---:|---:|---:|---:|
| Audited legacy replay | $6,375.68 | $1,240.08 | 109 | 56.88% | 1.73 |
| Causal-calendar sensitivity | $5,961.08 | $1,240.08 | 108 | 56.48% | 1.68 |
| Causal + execution stress | $5,506.28 | $1,263.24 | 108 | 55.56% | 1.64 |

\* Maximum drawdown uses the highest prior end-of-day equity minus adverse intraday marked equity, not the highest intraday equity. Net P&L is after the modeled costs described in [Methodology](docs/METHODOLOGY.md). No new replay was run for this presentation update.

![Aggregate historical simulation results](performance.png)

## A finding that changed the interpretation

The audit found simulation/integration parity gaps. The historical drawdown numbers are measurements of the replay, not proof of equivalent operational protection.

## Evidence and boundaries

| Supported here | Not established by this showcase |
|---|---|
| Aggregate figures checked against preserved research artifacts | Future returns or independent out-of-sample effectiveness |
| Explicit historical cost and drawdown definitions | Tick-accurate fills, latency or queue priority |
| Separately labeled sensitivity scenarios | Complete operational reliability |
| High-level engineering responsibilities | A reproducible public trading policy |

The public material omits implementation details and decision logic. No prospective paper or live results are published. Research-period selection and model uncertainty remain material limitations.

## Reading guide

- **[Engineering](docs/ENGINEERING.md):** component responsibilities, logical data contracts, sequencing and assurance gaps.
- **[Methodology](docs/METHODOLOGY.md):** metric definitions, effective cost assumptions and interpretation limits.
- **[Results](docs/RESULTS.md):** complete preserved tables and derived comparisons.
- **[Metrics JSON](metrics.json):** compact, machine-readable aggregate values.

## Portfolio context

[Version 2.0](https://github.com/miahaa/trading-system-v2-showcase) · [Version 3.0](https://github.com/miahaa/trading-system-v3-showcase) · [Version 4.0](https://github.com/miahaa/trading-system-v4-showcase) · [Version 7.0](https://github.com/miahaa/trading-system-v7-showcase)

These projects use different configurations, datasets and research objectives. Their results are not a controlled version ranking. Historical simulation results do not predict future returns.
