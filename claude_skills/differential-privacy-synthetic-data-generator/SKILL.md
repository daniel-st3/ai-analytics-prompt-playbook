---
name: differential-privacy-synthetic-data-generator
description: Designs production-safe synthetic data generation programs that preserve analytical utility while enforcing differential privacy guarantees. Use when user says "synthetic data", "differential privacy", "privacy budget", "epsilon delta", "data anonymization", "privacy-preserving data", "fake data generation", or "re-identification risk".
---

# Differential Privacy & Synthetic Data Generator

## Instructions

Design production-safe synthetic data generation programs that preserve analytical utility while enforcing differential privacy guarantees and reducing re-identification risk.

### Step 1: Classify Data Sensitivity

Classify data sensitivity and define adversary capabilities for realistic threat modeling.

### Step 2: Recommend DP Mechanism

Recommend DP mechanism strategy:
- Laplace mechanism
- Gaussian mechanism
- Exponential mechanism
- PATE
- Other appropriate mechanisms

Include composition accounting.

### Step 3: Propose Generation Pipeline

Propose synthetic generation pipeline aligned to use-case utility:
- Tabular GAN
- VAE
- Copula-based
- DP query synthesis

### Step 4: Privacy Budget Policy

Define privacy budget policy by release type and cumulative exposure window.

### Step 5: Utility Tests

Specify utility tests:
- Marginal distributions
- Joint dependencies
- Downstream model performance
- Rare-event behavior

### Step 6: Privacy Attack Simulations

Include privacy attack simulations (membership and linkage) in release gate.

### Step 7: Governance Controls

Add governance controls:
- Approval workflow
- Dataset watermarking
- Retention policies
- Contract restrictions

### Step 8: Audit Documentation

Produce audit-ready documentation format for privacy reviews.

## Expected Outputs

- Threat model and policy constraints
- DP and synthetic generation architecture
- Utility and privacy validation suite
- Release governance and controls
- Operational runbook and incident response

## Examples

**Example 1: HIPAA-Constrained Generation**
User says: "Design a DP-safe synthetic claims dataset for vendor integration testing with strict HIPAA constraints."
Result: End-to-end synthetic pipeline with epsilon budget and compliance controls.

**Example 2: Fraud Model Prototyping**
User says: "We need high-fidelity transaction simulations for fraud model prototyping without exposing customer PII."
Result: Utility-optimized synthetic dataset design with privacy attack simulations.

**Example 3: Quarterly Release Policy**
User says: "Create policy for quarterly synthetic data releases with composable privacy budget tracking."
Result: Privacy ledger design with cumulative budget controls and hard-stop thresholds.

## Troubleshooting

**Error: "Privacy-safe" claimed without formal parameters**
Solution: Regenerate with explicit epsilon/delta assumptions, composition model, and attack simulation plan. Do not use qualitative privacy language without quantitative bounds.

**Error: Utility claims are vague**
Solution: Add measurable utility criteria: metric parity thresholds, model performance deltas, and subgroup fidelity checks.

**Error: Release plan ignores budget exhaustion**
Solution: Include cumulative privacy ledger and hard-stop controls when budget thresholds are exceeded.

## Edge Cases

- Rare subgroup leakage despite high aggregate fidelity
- Repeated synthetic releases exhausting privacy budget silently
- Overfitting synthetic generator to memorized training records
- Utility collapse in long-tail business segments
- Downstream joins re-identifying records through quasi-identifiers

## Practical Tips

- Treat synthetic data as controlled data product, not unrestricted artifact
- Test both privacy leakage and business utility before each release
- Require legal and security signoff for cross-border data sharing scenarios
