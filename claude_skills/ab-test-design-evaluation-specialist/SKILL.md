---
name: ab-test-design-evaluation-specialist
description: Designs and evaluates rigorous A/B experiments with proper power planning, guardrails, and anti-bias protections. Use when user says "design an experiment", "A/B test", "power analysis", "sample size calculation", "evaluate test results", "set guardrail metrics", or "check for Simpson's Paradox".
---

# A/B Test Design & Evaluation Specialist

## Instructions

Design and evaluate rigorous experiments with proper power planning, guardrails, and anti-bias protections.

### Step 1: Clarify Experiment Scope

Confirm the primary metric, guardrail metrics, and success criteria with the user.

Required inputs:
- Experiment hypothesis and metric hierarchy
- Baseline conversion/value metrics
- Traffic volume and segmentation constraints
- Desired minimum detectable effect (MDE)
- Business risk tolerance and test runtime constraints

### Step 2: Compute Statistical Design

Calculate sample size and duration from baseline, MDE, alpha, and power assumptions.

Always present all four parameters explicitly in a table:
| Parameter | Value |
|-----------|-------|
| Alpha     |       |
| Power     |       |
| Baseline  |       |
| MDE       |       |

CRITICAL: Do not proceed without all four parameters defined.

### Step 3: Specify Randomization Controls

Define randomization unit and contamination risk controls. Include:
- Randomization method and unit
- Network effect mitigation
- Novelty effect considerations

### Step 4: Define Peeking and Interim Rules

Specify no-peeking policy and interim analysis rules to prevent false positive inflation from repeated peeking.

### Step 5: Build Analysis Plan

Provide analysis plan with:
- Confidence intervals and practical significance checks
- Simpson's Paradox risk flagging and subgroup consistency review
- Instrumentation integrity and event logging validation checklist

### Step 6: Produce Decision Framework

Generate final recommendation framework: **ship**, **iterate**, or **stop**.

## Expected Outputs

- Hypothesis and metric contract
- Statistical design assumptions table
- Sample size and duration calculations
- Execution checklist
- Evaluation workflow
- Decision memo template

## Examples

**Example 1: New Feature Test**
User says: "Design an experiment to test new checkout flow with 4% baseline conversion."
Actions:
1. Clarify primary metric (conversion rate) and guardrails (revenue per session, page load time)
2. Compute sample size given baseline and target MDE
3. Define randomization at user level with cookie-based assignment
Result: Complete experiment protocol with timeline and monitoring plan

**Example 2: Post-Test Evaluation**
User says: "Evaluate this completed A/B test and check for Simpson's Paradox risks."
Actions:
1. Review test design for statistical validity
2. Analyze results with confidence intervals
3. Check subgroup consistency for paradox risks
Result: Decision memo with ship/iterate/stop recommendation

**Example 3: Guardrail Setup**
User says: "Help me set guardrail metrics to avoid revenue harm during feature rollout."
Actions:
1. Identify core business metrics at risk
2. Define acceptable degradation thresholds
3. Design monitoring and early-stop criteria
Result: Guardrail metric contract with alerting thresholds

## Troubleshooting

**Error: Statistical assumptions not explicit**
Cause: User provided incomplete parameters
Solution: Recompute design with explicit alpha, power, baseline, and MDE assumptions shown in a table. Do not proceed without all four.

**Error: Results interpreted from p-value alone**
Cause: Over-reliance on statistical significance without practical significance
Solution: Re-evaluate using effect size, confidence interval, and business impact thresholds.

## Edge Cases

- Repeated peeking inflating false positive rates
- Uneven traffic allocation due to rollout bugs
- Metric definition drift during experiment runtime
- Simpson's Paradox masking subgroup reversals
- Novelty effect and seasonality bias

## Practical Tips

- Always define one primary metric before opening the test
- Ask for a pre-registration template to reduce hindsight bias
- Request a "decision boundary" section for stakeholder alignment
