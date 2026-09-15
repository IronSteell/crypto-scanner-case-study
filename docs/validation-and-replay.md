# Validation and diagnostic reports

[README](../README.md) | [Українська](uk/validation-and-replay.md)

## Backtest Summary

The summary report shows trade counts, wins and losses, fees, PF, drawdown, the closed PnL curve, and a breakdown by session. Run Snapshot includes version information and source code and configuration hashes for comparing runs.

The example selected for the case study demonstrates the reporting tool. It does not represent all strategies or the best result.

## Trade Chart Review

The report combines a summary with individual trade charts: local price movement, broader market context, entry and exit markers, partial fills, and changes to position protection. Grouping by outcome and closing reason is available.

For diagnosis, it is important to see the sequence of actions and execution geometry, not just final PnL.

## Comparison after a live session

Full Strategy Shadow Comparison separates actual execution from alternative paper strategies. Comparing aggregate figures is useful for an initial overview, but conclusions about execution differences require matching specific scenarios, decision times, and fills.

## Replay and event ordering

Research ordering by event timestamps can differ from the exact order in which the live worker processes events. The `arrival` mode exists for this reason and requires the corresponding `runtime_arrival` log.

## Limits of the evidence

- Syntax checks do not establish the correctness of trading logic.
- A successful individual backtest does not establish a consistent advantage in new market conditions.
- Offline comparisons of alternative trades do not always account for their effect on subsequent admissions.
- Shadow demonstrates alternative behavior but does not guarantee the same prices and fills as real orders.
