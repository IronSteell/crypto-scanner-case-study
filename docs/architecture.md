# Architecture

[README](../README.md) | [Українська](uk/architecture.md)

The project is organized into functional subsystems. It has shared data models, broker interfaces, and separate replay, backtest, storage, and diagnostic components. Some responsibilities remain within large central components.

## Conceptual flow

```text
Market data → metrics and patterns → trading scenario
                                           ↓
                               strategy rules / ML decisions
                                           ↓
                                risk checks and execution
                                           ↓
                                    logs and reports

Recorded events → replay / backtest → comparison and research
Current events  → shadow strategies → alternative outcomes
```

This is an overview of component roles, not an exact map of every call. Not every strategy uses ML, and the position of a particular ML decision depends on its task.

## Responsibilities

| Components | Role |
|---|---|
| UI and engine | Data collection, display, calculations, and signal processing |
| domain, features, signals | Events, features, and signal generation |
| algo | Coordination of strategies, AI services, and execution |
| trading | Broker adapters, accounting, order normalization, and risk |
| replay, backtest | Replay and strategy simulation |
| storage, audit | Event persistence and auditing |
| tools | Training, evaluation, export, and diagnostics |

The AI-agent workflow complements this division: separate specialized chats receive shared context and local tasks. These chats are not Git branches or independent services.
