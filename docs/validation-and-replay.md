# Validation and diagnostic reports

[README](../README.md) | [Українська](uk/validation-and-replay.md)

## Backtest Summary

The summary shows trade counts, wins and losses, fees, profit factor, drawdown, closed-PnL curves, and session-level results. The Run Snapshot records version information and source/configuration hashes to help identify and compare runs.

The example selected for demonstration illustrates the reporting tool. It does not represent every strategy or the best result. The normalization basis for percentage drawdown must be checked separately: the reported percentage should not automatically be interpreted as drawdown of the entire trading account.

## Trade Chart Review

The report combines a summary with individual trade charts: local price action, broader market context, entry and exit markers, partial fills, and protection changes. Trades can be grouped by outcomes and closing reasons.

Diagnosis requires the sequence of actions as well as final PnL. Levels labeled as calculated or estimated should not be presented as confirmed broker orders.

## Post-session comparison

Full Strategy Shadow Comparison separates actual execution from alternative paper strategies. Aggregate comparisons help with an initial review, but conclusions about execution differences require matching individual scenarios, decision times, and fills.

## Replay and event ordering

Research ordering by event timestamps can differ from the order in which the live worker processed events. Arrival mode requires a corresponding runtime_arrival journal. Missing historical information cannot be reliably reconstructed just by rearranging ordinary records.

## Limits of the evidence

- A syntax check does not establish correctness of trading logic.
- A successful individual backtest does not establish a stable advantage on new market data.
- Offline comparisons of alternative trades do not always capture their effects on subsequent admission and the portfolio.
- Shadow runs show alternative behavior but do not guarantee the same prices or fills as real orders.
- Public illustrations may show only part of a report; their scope and any omitted private details should be labeled.
