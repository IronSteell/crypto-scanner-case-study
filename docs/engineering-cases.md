# Practical stories from the project's development

[README](../README.md) | [Українська](uk/engineering-cases.md)

Below I describe problems I encountered while developing the project, my decisions, and what I learned. This is my retrospective; historical diffs and verification tests for these particular fixes are not yet included in the case study.

## 1. Inconsistent key names

**Problem.** The interface displayed data incorrectly after an agent generated code. While reading the code, I found a naming mismatch between the expected `trades24` and the `trades24h` that was used.

**My decision.** Instead of asking generally for a UI fix, I began tying tasks to specific keys and functions. I split large tasks into focused workstreams with the relevant context.

**Lesson.** Agents' context windows are finite, so consistent naming and the exact data path need attention. I consider an agent's loss of context a possible explanation for the error.

## 2. Logging pattern elements

**Problem.** While observing the market, I saw the algorithm detect chart patterns that did not match my intent. Rephrasing the overall task repeatedly only brought it part of the way toward the intended behavior.

**My decision.** I proposed logging every element the algorithm accepted as a valid part of a pattern. I used those records to locate mismatches and refine the task for the agent.

**Lesson.** When an outcome is difficult to explain, making the algorithm's intermediate decisions visible helps. This provided a concrete basis for corrections.

## 3. Visual journals for trade verification

**Problem.** Aggregate backtest numbers did not explain why the strategy entered, increased a position, or exited in a particular way.

**My decision.** I initiated the creation of supporting journals and visual trade analysis. I compared the expected logic with the visible sequence of actions and formulated specific correction tasks.

**Lesson.** Diagnostic tools became part of my development process. Trade Chart Review helps compare expected behavior with strategy actions and define the next checks more precisely.

## 4. Controlling feature scope

Agents suggested additional ways to find market inefficiencies. I explored some of them but later limited expansion to stay focused on the scanner's main task. I also checked whether report figures that an agent found appealing had practical value for the direction I wanted to pursue.

My conclusion: AI suggestions need evaluation to keep the project from becoming a pile of features. Reasons for rejecting suggestions should also be recorded in the context for future work.
