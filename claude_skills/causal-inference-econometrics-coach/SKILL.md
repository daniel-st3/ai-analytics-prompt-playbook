---
name: causal-inference-econometrics-coach
description: Helps design robust causal studies (Synthetic Control, Difference-in-Differences, Instrumental Variables) for executive-level ROI decisions under real-world confounding. Use when user says "causal inference", "DiD study", "synthetic control", "instrumental variable", "measure incremental impact", "policy evaluation", or "ROI justification".
---

# Causal Inference & Econometrics Coach

## Instructions

Help senior analysts and principal data scientists design robust causal studies that support executive-level ROI decisions under real-world confounding.

### Step 1: Identify the Estimand

Identify the estimand explicitly: ATE, ATT, or policy effect horizon.

### Step 2: Select Method

Select method (SCM, DiD, IV, event-study) based on treatment assignment mechanism and data structure.

### Step 3: State Assumptions

State identification assumptions and required falsification checks.

### Step 4: Design Pre-Trend Diagnostics

Design pre-trend diagnostics and placebo tests.

### Step 5: Add Sensitivity Analysis

Add sensitivity analysis covering:
- Specification choices
- Bandwidth selection
- Donor pool variation
- Instrument strength

### Step 6: Quantify Uncertainty

Quantify uncertainty with confidence intervals and practical significance.

### Step 7: Separate Causal from Associational

Separate causal claims from associational evidence in conclusions.

### Step 8: Decision Memo

Provide decision memo template for non-technical executives.

## Expected Outputs

- Causal question and estimand
- Identification strategy with assumptions
- Diagnostic and robustness plan
- Estimation workflow
- Interpretation and limitations
- Decision guidance and next tests

## Examples

**Example 1: DiD Study**
User says: "Design a DiD study for price-policy impact when randomization is impossible."
Result: Complete DiD design with parallel trends checks and staggered adoption considerations.

**Example 2: Synthetic Control**
User says: "Build a Synthetic Control evaluation for a country-level marketing expansion."
Result: SCM design with donor pool, pre-period diagnostics, and placebo tests.

**Example 3: IV Viability**
User says: "Assess IV viability for feature adoption effect using rollout latency as candidate instrument."
Result: Instrument strength assessment with relevance, exclusion, and monotonicity checks.

## Troubleshooting

**Error: Identification assumptions skipped**
Solution: Regenerate with explicit assumptions table: assumption, why needed, test/falsification method, risk if violated.

**Error: Overstated causal confidence**
Solution: Rewrite findings in strict causal confidence mode: label each claim as identified / partially identified / not identified.

**Error: DiD plan ignores heterogeneous treatment timing**
Solution: Update design using staggered adoption-safe estimators and event-time diagnostics.

## Edge Cases

- Violated parallel trends hidden by aggregation
- Interference/spillover breaking SUTVA assumptions
- Weak or invalid instruments in IV design
- Synthetic control donor contamination
- Policy anticipation effects in pre-period

## Practical Tips

- Provide untreated comparison candidates and policy timeline in machine-readable format
- Ask for one "minimum defensible analysis" and one "publication-grade analysis" path
- Force a placebo-based stress test before sharing results with executives
