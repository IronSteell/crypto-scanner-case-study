# Practical development stories

[README](../README.md) | [Українська](uk/engineering-cases.md)

Below I describe problems encountered while developing the project, my decisions, and what I learned. This is my retrospective; historical diffs and verification tests for these specific fixes are not yet included in the case study.

## 1. Inconsistent data keys

**Problem.** The interface displayed incorrect data after an agent extended the code. In familiar sections of the code, I found a mismatch between the expected `trades24` and the new `trades24h` key.

**My decision.** Instead of asking generally for a UI fix, I started anchoring tasks to specific keys and functions. I split large tasks into local workstreams with relevant context.

**Lesson.** Consistent naming and precise data contracts matter even when individual code blocks look plausible. I consider loss of agent context a possible explanation, rather than a proven technical cause.

## 2. Logging pattern elements

**Problem.** While observing the market, I noticed the algorithm detected chart patterns that did not match my intended rules. Rephrasing the overall task repeatedly brought only partial improvement.

**My decision.** I proposed logging each element that the algorithm accepted as a valid part of a pattern. These records helped me locate mismatches and clarify the task for the agent.

**Lesson.** When an outcome is hard to explain, exposing intermediate decisions can provide a concrete basis for fixes.

## 3. Visual journals for trade review

**Problem.** Aggregate backtest numbers did not explain why the strategy entered, increased a position, or exited in a particular way.

**My decision.** I initiated supporting journals and visual trade analysis. I compared expected logic with the visible sequence of actions and formulated specific correction tasks.

**Lesson.** Diagnostic tools became part of my development process. Trade Chart Review helps compare expected behavior with strategy actions and define the next checks.

## 4. Controlling feature scope

Agents suggested complex additional methods for detecting market inefficiencies. I explored some of them, but later limited expansion to keep the scanner focused on its main purpose. I also questioned whether attractive report numbers had practical value for the intended scenario.

My lesson: AI suggestions need to be evaluated against the product's goal, and reasons for rejecting them should be recorded in the context for subsequent work.
