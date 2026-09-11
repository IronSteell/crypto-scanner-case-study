# Crypto Scanner

English | [Українська](README.uk.md)

**A personal Python project for crypto market scanning, trading strategy research, and execution analysis, developed with AI coding agents.**

I'm Kyrylo Symonov. I have been developing this project since February 2026. This case study describes the system's capabilities, my decisions, and how I work. Private strategy parameters, the full source code, and trading logs are not included in this documentation package.

## From a practical need to a tool

While scalping, I kept trading journals and analyzed my results. I gradually developed my own trading rules, but could not find the combination of signals I needed in the tools available to me. That led me to build my own scanner.

The project grew from signal detection into testing trading logic on recorded data, order execution, comparing alternative strategies, and researching ML decisions. I use it personally; it does not yet have external users.

## Main capabilities

| Subsystem | Purpose |
|---|---|
| Market scanner | Collect market data, calculate metrics, and detect signals using defined rules |
| Recording and replay | Store events and replay them to investigate algorithm behavior |
| Backtest Lab | Compare strategy variants and analyze results by trade and session |
| Execution and risk | Manage orders and positions with configurable limits and protective mechanisms |
| Shadow strategies | Run alternatives on separate paper accounts and compare them with actual execution |
| Trade Chart Review | Inspect trades on charts, including entries, exits, context, and closing reasons |
| ML research | Evaluate decisions at specific points in a trading scenario's lifecycle |

## Four ML research directions

These are four types of decisions, not four equally mature or simultaneously deployed models.

| Direction | Decision | Status of the experiment or integration described |
|---|---|---|
| **Pre-entry** | Allow or reject an entry using the context available at decision time | Training, temporal evaluation, and scoring integration exist; a historical candidate produced a positive offline result |
| **Scale-in** | Increase the position or retain baseline management | APP decision integration and separate offline studies exist; activation depends on the model and configuration |
| **TP-range** | Choose a take-profit distance from the alternatives under study | Offline studies cover decisions at entry and in a defined context as price approaches a target zone |
| **Entry-depth** | Retain the baseline limit entry or select a deeper level | Early model experiment; a robust advantage has not been established, and it has not been moved to live execution |

Entry-depth focuses on choosing the depth of a limit entry. See [ML lifecycle](docs/ml-lifecycle.md) for details and evaluation limits.

## My contribution and use of AI

I define the domain rules and expected behavior, break down tasks, agree on component structure, and check the results. AI agents implement most of the code. I read familiar sections of Python code myself and continue developing my technical foundations.

I also use AI to help draft documentation and edit it before publication. It reflects my experience and understanding of the project.

I organized seven specialized workstreams in separate chats, with shared and local instructions. I use conventions for naming, targeted searches, backups, and reporting changes. I control feature scope to keep the project useful for its practical purpose.

During debugging, I initiated logging of individual pattern elements and visual trade journals. This helped move from a general observation that something was wrong to a specific mismatch in data or logic. See the [engineering cases](docs/engineering-cases.md).

## How I evaluate results

The project uses event logs, replay, backtests, temporal model evaluation, shadow comparisons, and visual trade review. Feature availability at decision time and differences between simulation and actual execution are considered separately.

A positive offline result does not establish readiness for live trading. Example reports illustrate the analysis tools and individual experiments; they do not establish consistent profitability of the system.

## Further reading

- [Architecture and data flow](docs/architecture.md)
- [Four ML research directions](docs/ml-lifecycle.md)
- [Execution, risk, and shadow](docs/execution-and-risk.md)
- [Validation, replay, and reports](docs/validation-and-replay.md)
- [Practical debugging stories](docs/engineering-cases.md)

This package documents the project; it is not an executable demo. A video walkthrough is being prepared.

## Example reports

Selected real outputs illustrate the reporting and review tools, not consistent profitability. The reports come from different runs and should not be treated as a single experiment.

- [Full Strategy Shadow Comparison](reports/shadow-comparison.html)
- [Trade Chart Review — 13 trades](reports/trade-charts.html#winners)
- [Historical pre-entry ML research](reports/pre-entry-research.html)

GitHub displays HTML source rather than the interactive report. Download an HTML file using **Download raw file**, then open it in your browser.

### Backtest Summary example

![Backtest Summary example](assets/backtest-summary.png)
