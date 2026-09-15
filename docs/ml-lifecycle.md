# ML decisions in a trading scenario

[README](../README.md) | [Українська](uk/ml-lifecycle.md)

The ML research is organized around individual decisions: whether to enter, where to place an entry, whether to increase the position, and which TP distance to choose. This is not a claim of a single autonomous controller for all actions. A model evaluates the situation, and a decision rule determines whether to use an alternative or retain the baseline action.

## Pre-entry

The task is to evaluate an entry using information available at a defined decision boundary. Candidates differ in their features, models, and admission rules.

As an example, I use a historical rolling walk-forward experiment comparing against the baseline strategy and reporting results by time window. The candidate presented in the report had a positive aggregate offline result, but improvement did not occur in every window. The conclusion recorded the need for a separate live-shadow evaluation. This example demonstrates the methodology; its result applies to a particular historical experiment and illustrates the potential of this direction.

## Scale-in

The task is to determine when increasing position size is preferable to baseline management. The code includes an APP decision interface and off/shadow/execute modes. APP refers to the context in the zone where price approaches a specified level; the exact boundary is defined by the experiment.

In one offline study, I compare the baseline action with scale-in on matched opportunities. It uses a fixed snapshot from before the corresponding execution and temporal train/calibration/test windows.

## TP-range

The task is to select a TP distance from defined alternatives. I investigate two approaches: a decision at entry and a decision in a defined APP context after entry.

These studies use matched scenarios and only features available before the decision. Both are offline studies. Substituting an alternative trade outcome within a fixed dataset is not equivalent to a full replay.

## Entry-depth

I arrived at this direction through comparisons of variants with fixed stops. The model's direct action in the first experiment is to retain the baseline entry or select one of the deeper limit order levels.

The experiment compares geometric features with an expanded context. Regressors estimate the net PnL improvement of alternative entries relative to the baseline; if the predicted improvement does not meet the selection rule, the baseline is retained. Feature snapshots are tied to scenario creation, not future execution.

The first result showed a weak positive signal, but its uncertainty allows for no advantage. Drawdown did not automatically improve either. The training sample is limited by the selection of scenarios with completed alternatives. A full replay of the new policy was not performed within this experiment.

Status: early research, not transferred to the runtime. This selects the initial entry level; it is not a model that moves the stop while a position is open.

## Shared evaluation principles

- Record the point in time at which features are available.
- Separate training, validation, and testing chronologically.
- Select thresholds on validation data, not test results.
- Compare the model with the baseline action and account for the cost of missed opportunities.
- Evaluate results by time window and drawdown, not only total PnL.
- Distinguish OOS evaluation on dates already studied historically from a new independent holdout.
- Check shadow integrity and execution alignment separately.

These principles guide the organization of the research. Completed checks are recorded separately for each experiment.
