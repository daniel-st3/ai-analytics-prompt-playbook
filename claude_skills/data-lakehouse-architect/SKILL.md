---
name: data-lakehouse-architect
description: Designs and hardens Iceberg/Delta Lakehouse architectures for high-scale analytical workloads with partition evolution, compaction, file sizing, and cost/performance control. Use when user says "lakehouse architecture", "Iceberg tables", "Delta Lake", "partition evolution", "compaction strategy", "small files problem", "Z-ordering", or "open table format".
---

# Data Lakehouse Architect (Iceberg/Delta)

## Instructions

Design and harden Iceberg/Delta Lakehouse architectures for high-scale analytical workloads.

### Step 1: Workload Decomposition

Start with workload decomposition: read patterns, write patterns, SLA, and concurrency profile.

### Step 2: Table Format Design

Propose table format-specific design (Iceberg/Delta) including:
- Partition spec
- Sort order
- Clustering strategy
- File size targets

### Step 3: Partition Evolution Policy

Define partition evolution policy with explicit trigger thresholds and rollback criteria.

### Step 4: Compaction Strategy

Design compaction strategy:
- Bin-pack vs sort-aware compaction
- Small-files remediation cadence
- Impact on streaming readers

### Step 5: Metadata Optimization

Add metadata optimization:
- Manifest pruning
- Stats collection
- Snapshot retention
- Vacuum policies

### Step 6: CDC and Merge Guidance

Provide merge/upsert guidance for CDC and late-arriving records.

### Step 7: Cost-Performance Tradeoffs

Include cost-performance tradeoff table with expected p95 improvements and compute overhead.

### Step 8: Operational Runbook

End with runbook: rollout, validation, monitoring, and incident response.

## Expected Outputs

- Current-state diagnosis
- Proposed lakehouse architecture
- Table design matrix (by domain)
- Maintenance plan (compaction/retention)
- Validation and SLO checks
- Risk register and rollback plan

## Examples

**Example 1: File Explosion Remediation**
User says: "Our Iceberg tables hit 20M files and Trino query latency exploded. Design remediation with minimal downtime."
Result: Immediate compaction plan + long-term partition evolution strategy.

**Example 2: CDC Migration**
User says: "We're moving Delta tables from daily batch to micro-batch CDC merges; define partition and compaction policy."
Result: CDC-optimized table design with merge frequency and file-size controls.

**Example 3: Multi-Engine Plan**
User says: "Give a multi-engine plan for Spark write + Trino read + BI serving with predictable p95 latency."
Result: Engine-aware table design with interoperability and caching strategy.

## Troubleshooting

**Error: Non-existent engine capabilities referenced**
Solution: Use only capabilities supported by the specified stack. Tag uncertain features as "requires version validation" and provide fallback design.

**Error: File-count pressure ignored**
Solution: Recompute design using table telemetry: rows/day, files/day, avg file size, query p95. Output explicit file-size targets and compaction frequency.

**Error: Partition advice causes scan regressions**
Solution: Provide counterfactual analysis: current vs proposed partition spec, with estimated scan pruning impact per top 5 query patterns.

## Edge Cases

- Partition evolution causing historical query inconsistency
- Excessive snapshot growth and metadata planning bottlenecks
- Concurrent writers creating commit contention
- Compaction interfering with streaming readers
- Z-ordering or clustering overfitting one query class while regressing others

## Practical Tips

- Always provide one week of query logs and file-distribution metrics before redesign
- Request both "stabilize in 7 days" and "optimize in 90 days" plans
- Ask for per-domain maintenance policies; one-size compaction is usually wrong
