# Architecture

[README](../README.md) | [Українська](uk/architecture.md)

The project is organized into functional subsystems. It has shared data models, broker interfaces, and separate replay, backtest, storage, and diagnostic components. Some responsibilities remain concentrated in large central components; this is a current architectural limitation.

## Conceptual flow

```text
Market data → metrics and patterns → trading scenario
                                           ↓
                              strategy rules / ML decisions
                                           ↓
                                 risk checks and execution
                                           ↓
                                     logs and reports

Recorded events → replay / backtest → comparisons and research
Current events  → shadow strategies → alternative outcomes
```

This is an overview of component roles, not a complete call graph. Not every strategy uses ML, and the point at which an ML decision is made depends on its task.

## Responsibilities

| Components | Role |
|---|---|
| UI and engine | Display, data collection, calculations, and signal processing |
| domain, features, signals | Events, features, and signal construction |
| algo | Strategy, AI service, and execution coordination |
| trading | Broker adapters, accounting, order normalization, and risk controls |
| replay, backtest | Event replay and strategy simulation |
| storage, audit | Persistence and event auditing |
| tools | Training, evaluation, exports, and diagnostics |

The AI workflow complements this structure: specialized chats receive shared context and local tasks. These chats are not Git branches or independent services.
