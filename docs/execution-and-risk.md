# Execution, risk, and shadow

[README](../README.md) | [Українська](uk/execution-and-risk.md)

## Execution

The system includes broker adapters and tools for tracking the order lifecycle. The logic covers entries, position increases, exits, protective orders, and reconciliation of local state with broker state. Specific behavior depends on the strategy and its configuration.

## Layers of risk control

- Execution admission: disabling trading, a kill switch, and symbol restrictions.
- Execution exposure: position count, order size, per-symbol exposure, and total exposure.
- Strategy state: pauses after stops, session drawdown limits, and protection of accumulated profit.
- Open-position protection: stop mechanisms and exit synchronization.

These are mechanisms implemented in the risk manager. This does not mean they are all active in every setup or that they eliminate the risk of losses.

## Shadow

Alternative strategies can process current events on separate paper accounts. Reports compare them with actual execution while preserving the distinction between simulated and broker results.

Separate AI services record decisions and outcomes, while simulation of alternative scenarios helps investigate the consequences of rejected entries. The AI infrastructure also has modes that affect admission.

As an example, I use a historical Full Strategy Shadow Comparison report with summaries of actual and shadow trades, closing reasons, risk events, and a processing integrity section covering event counts, skipped events, the remaining queue, and the last error.
