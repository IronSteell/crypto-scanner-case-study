# ML decisions in a trading scenario

[README](../README.md) | [Українська](uk/ml-lifecycle.md)

ML research focuses on separate decisions: whether to enter, where to place an entry, whether to increase a position, and which take-profit distance to choose. This is not a claim of a single autonomous controller for all actions. Models produce estimates; a decision policy determines when to use an alternative or retain the baseline action.

## Pre-entry

The task is to evaluate an entry using information available at a defined decision boundary. Candidates differ in features, models, and admission policies.

One example is a historical rolling walk-forward experiment comparing a candidate with the baseline strategy across time windows. The candidate's aggregate offline result was positive, but not every window improved. The conclusion required a separate live-shadow evaluation. This illustrates the methodology; the result applies to that particular historical experiment.

## Scale-in

The task is to decide when increasing a position is preferable to baseline management. The code includes an APP decision interface and off/shadow/execute modes. APP refers to the context of price approaching a specified zone; each experiment defines its exact boundary.

In one offline study, I compare the baseline action with scale-in on matched opportunities. It uses a frozen snapshot before the relevant execution and temporal train/calibration/test windows. This experiment does not export a runtime model or reproduce all subsequent portfolio interactions.

The existence of an integration path does not mean that this particular candidate is used for actual orders.

## TP-range

The task is to choose a take-profit distance from defined alternatives. I investigate two approaches: a decision at entry and a decision in a specified APP context after entry.

These studies use matched scenarios and features available before the decision. Both are offline studies. Substituting an alternative trade outcome within a fixed dataset is not equivalent to replaying the full policy with position limits, occupied positions, and cooldowns.

## Entry-depth

This direction grew out of comparisons between variants with fixed stops. In the first experiment, the model's action is to retain the baseline entry or choose one of the deeper limit-order levels.

The experiment compares geometric features with an expanded context. Regressors estimate the net PnL improvement of alternative entries over baseline. If the predicted improvement does not pass the selection rule, baseline is retained. Feature snapshots are tied to scenario creation, not future execution.

The first result showed a weak positive signal, but its uncertainty still allows for no advantage. Drawdown did not automatically improve either. The training sample is limited by selection of scenarios with completed alternatives; unfilled orders and unfinished positions require separate treatment. A full replay of the new policy was not performed as part of this experiment.

Status: early research, without runtime deployment. This is an initial-entry selection model, not a model that moves the stop of an open position.

## Evaluation principles

- Define when each feature becomes available.
- Separate training, validation, and testing in time.
- Select thresholds on validation data, not test results.
- Compare against the baseline action and account for missed opportunities.
- Evaluate time-window results and drawdown, not only total PnL.
- Distinguish out-of-sample evaluation on previously studied dates from a new independent holdout.
- Check shadow integrity and execution alignment separately.

I use these principles to organize research. For each experiment, I record the checks performed and unresolved limitations separately.
