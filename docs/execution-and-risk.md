# Execution, risk, and shadow

[README](../README.md) | [Українська](uk/execution-and-risk.md)

## Execution

The system includes broker adapters and order lifecycle tracking. Its logic covers entries, position increases, exits, protective orders, and reconciliation of local and broker state. Actual behavior depends on the strategy and configuration.

## Risk control layers

- Execution admission: trading disablement, kill switch, and symbol restrictions.
- Execution exposure: position count, order size, per-symbol exposure, and total exposure.
- Strategy state: pauses after stops, session drawdown limits, and protection of accumulated profit.
- Open-position protection: stop mechanisms and exit synchronization.

These are implemented mechanisms. This does not mean that all are active simultaneously in every setup or that they eliminate the risk of losses.

## Shadow

Alternative strategies can process current events on separate paper accounts. Reports compare them with actual execution while retaining the distinction between simulated and broker outcomes.

Separate AI services record decisions and outcomes, while alternative-scenario simulation helps investigate rejected entries. The AI infrastructure also includes modes that affect admission, so not all AI modes are unconditionally shadow-only.

One historical Full Strategy Shadow Comparison provides summaries of actual and shadow trades, closing reasons, risk events, and processing integrity: event counts, dropped events, remaining queue size, and the last error. No dropped events in a particular report does not prove system-wide correctness or equivalent execution.
