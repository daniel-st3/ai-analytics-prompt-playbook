---
name: unstructured-data-pipeline-designer
description: Designs enterprise pipelines that transform massive unstructured text columns (tickets, transcripts, notes, docs) into governed structured signals using Snowflake Cortex or Databricks Mosaic. Use when user says "unstructured data pipeline", "text extraction", "Cortex pipeline", "Mosaic extraction", "entity extraction", "sentiment analysis pipeline", "NLP pipeline", or "structured from unstructured".
---

# Unstructured Data Pipeline Designer (Cortex/Mosaic)

## Instructions

Design enterprise pipelines that transform massive unstructured text columns into governed structured signals using native warehouse AI capabilities.

### Step 1: Segment Pipeline Layers

Segment pipeline by:
1. Ingestion
2. Normalization
3. Extraction
4. Validation
5. Serving

### Step 2: Schema Contract

Define schema contract for extracted JSON outputs with strict validation rules.

### Step 3: Prompt Templates

Design prompt templates for deterministic extraction and taxonomy consistency.

### Step 4: Chunking Strategy

Add chunking/windowing strategy for long documents and conversation threads.

### Step 5: Quality Framework

Include quality framework:
- Precision/recall against labeled set
- Schema compliance rate
- Drift detection

### Step 6: Cost and Latency Optimization

Optimize cost and latency with batching, caching, and adaptive reprocessing.

### Step 7: Privacy Controls

Add privacy controls for sensitive text and redaction pre-processing.

### Step 8: Rollback Strategy

Define rollback and reprocessing strategy for model-version upgrades.

## Expected Outputs

- Pipeline architecture
- Extraction schema and prompt strategy
- Quality and validation plan
- Cost/latency optimization plan
- Governance and privacy controls
- Operations and incident runbook

## Examples

**Example 1: Support Ticket Extraction**
User says: "Design Cortex pipeline for 2B support ticket comments with entity extraction and sentiment rollups by product line."
Result: End-to-end pipeline with chunking, extraction prompts, and quality monitoring.

**Example 2: Transcript Processing**
User says: "Build Mosaic-based transcript processing that emits validated JSON for compliance and BI consumption."
Result: Schema-enforced extraction pipeline with compliance controls.

**Example 3: Extraction Regression**
User says: "Our extraction outputs became inconsistent after model update; design regression framework and rollback policy."
Result: Regression testing framework with version-aware rollback procedures.

## Troubleshooting

**Error: Extraction without schema enforcement**
Solution: Regenerate with strict JSON schema validation and rejection/retry strategy for malformed outputs.

**Error: Model output quality unverified**
Solution: Add labeled evaluation set design, per-field precision/recall targets, and drift alert thresholds.

**Error: Privacy controls are weak**
Solution: Insert pre-extraction redaction and post-extraction leak checks for sensitive entities.

## Edge Cases

- Schema drift in extracted JSON across model versions
- Hallucinated entities causing downstream metric contamination
- Long-context truncation silently dropping critical evidence
- Topic/sentiment classifier drift after policy or product changes
- PII leakage in generated summaries or extracted fields

## Practical Tips

- Version prompts, schemas, and model IDs as a single release artifact
- Store raw, extracted, and validated layers separately for auditability
- Track per-domain extraction quality to avoid aggregate-metric masking
