---
name: rag-pipeline-evaluator-llm-as-judge
description: Designs rigorous RAG evaluation systems that measure retrieval quality, context precision, grounding fidelity, and hallucination rates using deterministic metrics and LLM-as-a-judge protocols. Use when user says "RAG evaluation", "LLM-as-a-judge", "retrieval quality", "hallucination detection", "grounding check", "RAG benchmark", or "copilot quality gate".
---

# RAG Pipeline Evaluator (LLM-as-a-Judge)

## Instructions

Design rigorous RAG evaluation systems that measure retrieval quality, context precision, grounding fidelity, and hallucination rates.

### Step 1: Define Evaluation Dimensions

Define evaluation dimensions:
- Retrieval recall
- Context precision
- Answer grounding
- Hallucination severity

### Step 2: Separate Offline and Online Evaluation

Separate offline benchmark evaluation from online production monitoring.

### Step 3: Design Judge Rubric

Design LLM-as-a-judge rubric with explicit criteria and calibration examples.

### Step 4: Deterministic Checks

Add deterministic checks:
- Citation match
- Source overlap
- Contradiction detection

### Step 5: Regression Suite

Build regression suite for retriever/reranker/chunking changes.

### Step 6: Risk-Weighted Thresholds

Include risk-weighted thresholds by use case criticality.

### Step 7: Release Gate Policy

Specify release gate policy (block/warn/pass) with escalation path.

### Step 8: Dashboard Schema

Provide dashboard schema for longitudinal quality tracking.

## Expected Outputs

- Evaluation objectives and risk tiers
- Metric framework
- Judge rubric and calibration plan
- Regression test design
- Release gate policy
- Monitoring and incident playbook

## Examples

**Example 1: Retriever Comparison**
User says: "Design an LLM-as-a-judge framework to compare two retrievers for legal-policy Q&A."
Result: Complete evaluation framework with rubric, benchmarks, and statistical comparison methodology.

**Example 2: Grounding Focus**
User says: "Our RAG bot is fluent but wrong; create a grounding-focused benchmark and gate policy."
Result: Grounding-specific evaluation with citation requirements and hard release gates.

**Example 3: Weekly Regression**
User says: "Build quality metrics for weekly regression after embedding model upgrades."
Result: Automated regression pipeline with trend tracking and alerting.

## Troubleshooting

**Error: Only subjective metrics recommended**
Solution: Rebuild with deterministic + judge metrics side-by-side, including thresholds and failure examples.

**Error: Judge rubric is under-specified**
Solution: Provide scoring anchors with concrete pass/fail examples for each dimension.

**Error: Release gates are too permissive**
Solution: Tighten policy by risk tier and require citation-grounding minimums for high-stakes domains.

## Edge Cases

- Judge model bias toward fluent but ungrounded answers
- Benchmark leakage from training or prompt overfitting
- Retrieval recall high but context precision low
- Domain drift causing false confidence in stale sources
- Multi-hop questions failing despite high single-hop metrics

## Practical Tips

- Keep a locked benchmark set for release gating and a rotating set for drift detection
- Calibrate judge prompts quarterly against human adjudication
- Track false-positive and false-negative rates of judge decisions
