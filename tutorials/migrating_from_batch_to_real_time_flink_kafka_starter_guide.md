## Migrating from Batch to Real-Time: A Flink & Kafka Starter Guide

## Overview
This guide is for staff-level practitioners migrating from daily dbt batch pipelines to event-driven streaming materialized views using Kafka + Flink. The target is not “streaming theater.” The target is reliable, governable, low-latency serving with clear semantics under late data, replay, and schema evolution.

You will design and validate:
- Kafka topic strategy (keys, partitions, retention, compaction),
- Flink stateful processing (event-time windows, watermarks, state TTL),
- real-time materialized view semantics,
- and operational controls (backfills, exactly-once boundaries, incident triage).

The tutorial uses strict model roles:
- **Claude** for architecture contracts and migration risk control,
- **ChatGPT (o1/o3 + ADA)** for edge-case reasoning and executable simulation code,
- **Gemini** for source-grounded synthesis across architecture docs/runbooks.

## Prerequisites
1. Existing batch KPI pipeline and documented metric definitions.
2. Kafka cluster access and topic management privileges.
3. Flink runtime (managed or self-hosted) and checkpoint storage configured.
4. Data contracts for event schema and late-arrival policy.

Optional local stack bootstrap (for sandbox testing):
```bash
mkdir batch-to-realtime-migration
cd batch-to-realtime-migration
# add docker compose with kafka + schema registry + flink if needed
```

## Step-by-Step

### Step 1: Define semantic parity target between batch and stream
Before writing any streaming code, define exactly what “equivalent KPI” means versus current dbt output. Many failed migrations come from ambiguous event-time interpretation, not engine issues.

Key decisions:
- event-time vs processing-time authority,
- window close policy,
- acceptable late-arrival threshold,
- reconciliation horizon with batch baseline.

#### Using Claude for this step
```text
<context>
We are migrating daily dbt KPI pipeline to Kafka + Flink real-time materialized view.
</context>
<schema>
Paste current KPI SQL definitions, event schema, and SLA targets.
</schema>
<task>
Define semantic parity contract between batch and stream outputs.
</task>
<rules>
Specify event-time authority, lateness handling, and reconciliation strategy.
</rules>
```

#### Using ChatGPT for this step
```text
Phase 1 (o1/o3): reason through edge cases before execution:
- out-of-order events
- late arrivals
- duplicate events
- timezone normalization
Phase 2: generate parity-check checklist and test harness outline.
```

#### Using Gemini for this step
```text
Use attached KPI docs, batch SQL, and architecture notes.
Generate source-grounded semantic parity document with unresolved-risk list.
```

#### Troubleshooting / Handling AI Hallucinations
If AI collapses event-time and processing-time semantics:
```text
Regenerate with explicit distinction: event_time, ingestion_time, processing_time,
and show how each affects KPI windows and reconciliation.
```

### Step 2: Design Kafka topic contracts and partitioning
Define topics by domain and processing responsibility, not by team convenience. Set key strategy to preserve ordering where required. Partition count should reflect throughput + key cardinality + consumer parallelism constraints.

Design checklist:
- key schema and ordering guarantees,
- partition count evolution policy,
- retention/compaction alignment with replay and audit needs,
- dead-letter topic contract.

#### Using Claude for this step
```text
<context>
Need Kafka topic strategy for real-time KPI materialized views.
</context>
<task>
Design topic/key/partition/retention contract with replay and DLQ policy.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then output partition sizing worksheet and key skew risk checks.
```

#### Using Gemini for this step
```text
Using attached throughput logs and schema docs, build source-grounded topic design and scaling plan.
```

#### Troubleshooting / Handling AI Hallucinations
If keying strategy ignores skew and hotspot risk:
```text
Recompute with key cardinality distribution and producer rate profile.
Output hotspot mitigation options and tradeoffs.
```

### Step 3: Implement Flink processing with event-time and state TTL
Build Flink job around explicit event-time windows, watermark strategy, and state lifecycle. State TTL is not optional in long-running jobs; it is your memory and correctness control boundary.

Implementation concerns:
- watermark lag tuned by lateness distribution,
- exactly-once boundary assumptions,
- checkpoint interval and recovery budget,
- state backend growth and TTL policy.

#### Using Claude for this step
```text
<context>
Design Flink stateful aggregation for real-time KPI materialized views.
</context>
<task>
Specify watermark, windowing, state TTL, and checkpoint strategy.
</task>
<rules>
Include late-data update behavior and replay policy.
</rules>
```

#### Using ChatGPT for this step
```text
Phase 1: o1/o3 reasons through edge cases (state blowup, watermark lag, duplicate replay).
Phase 2: generate implementation pseudocode and validation test cases.
```

#### Using Gemini for this step
```text
Use attached job specs and incident notes.
Produce source-grounded Flink config recommendations with risk tiers.
```

#### Troubleshooting / Handling AI Hallucinations
If AI recommends unrealistic exactly-once guarantees:
```text
State explicit transactional boundaries and sink semantics.
Label guarantees as at-least-once / effectively-once / exactly-once with required prerequisites.
```

If TTL policy is too generic:
```text
Recalculate TTL from business replay window, compliance retention needs, and state growth telemetry.
```

### Step 4: Build real-time materialized view serving layer
Decide where the materialized view lives (stream-native store, warehouse sink table, or serving index). Ensure consistent update semantics and consumer-facing freshness contracts.

Serving checklist:
- snapshot + changelog consistency,
- idempotent upsert model,
- consumer query patterns and cache policy,
- fallback path to batch truth table during incidents.

#### Using Claude for this step
```text
Design serving strategy for real-time KPI materialized view with fallback-to-batch during streaming incidents.
Include consistency model and consumer contract.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then produce serving-layer validation checks and reconciliation SQL templates.
```

#### Using Gemini for this step
```text
Use attached BI consumption patterns and SLA docs to generate source-grounded serving design with freshness tiers.
```

#### Troubleshooting / Handling AI Hallucinations
If serving design ignores consumer contract:
```text
Regenerate with explicit consumer SLA matrix: latency, completeness, consistency, degradation behavior.
```

### Step 5: Parallel run and reconciliation with batch
Run batch and stream in parallel long enough to observe weekly seasonality and failure regimes. Measure divergence by KPI, segment, and lateness class.

Parallel-run checks:
- absolute and relative KPI deltas,
- divergence under delayed ingestion spikes,
- replay-induced correction behavior,
- end-of-day close reconciliation.

#### Using Claude for this step
```text
Create parallel-run acceptance criteria and migration go/no-go thresholds.
Include reconciliation governance and sign-off workflow.
```

#### Using ChatGPT for this step
```text
Use o1/o3 reasoning first.
Then generate reconciliation analysis scripts and divergence alert thresholds.
```

#### Using Gemini for this step
```text
Using attached run logs and KPI reports, produce source-grounded readiness assessment.
```

#### Troubleshooting / Handling AI Hallucinations
If AI suggests cutover without divergence evidence:
```text
Block cutover recommendations until divergence metrics are shown over required observation window.
Provide missing evidence checklist.
```

### Step 6: Cutover, rollback, and operations hardening
Cutover is an operations event, not a code merge. Define rollback trigger, ownership, and communication protocol in advance.

Hardening checklist:
- on-call playbook for lag/state/checkpoint failures,
- topic schema evolution contract testing,
- capacity policy for partition expansion,
- monthly replay drill and disaster recovery rehearsal.

#### Using Claude for this step
```text
Generate production cutover + rollback runbook for batch-to-stream KPI migration.
Include ownership matrix and escalation SLAs.
```

#### Using ChatGPT for this step
```text
Use o1/o3 first to reason through failure blast radius.
Then output operational checklist, incident templates, and post-cutover audit plan.
```

#### Using Gemini for this step
```text
Use attached runbooks and org escalation docs to produce source-grounded operating model.
```

#### Troubleshooting / Handling AI Hallucinations
If AI operational plan lacks failure drills:
```text
Add required game-day scenarios: broker outage, checkpoint corruption, schema-breaking event, and sink unavailability.
```

## Advanced Failure Modes and Recovery Prompts

### Late-arriving data corrupts downstream KPIs
```text
Given this lateness distribution and watermark config,
propose corrected event-time strategy and compensating update policy.
```

### Kafka partition imbalance causes consumer lag
```text
Using partition-level throughput and key-frequency histograms,
recommend repartitioning or key redesign with migration plan.
```

### Flink state growth threatens job stability
```text
Diagnose state growth drivers and redesign TTL/window/checkpoint settings
while preserving metric semantics.
```

### Batch vs stream semantic drift under month-end closes
```text
Build a reconciliation framework for month-end close windows,
including correction policy and executive reporting guardrails.
```

## Using Claude
Use Claude for migration contracts, risk boundaries, and operational governance artifacts.

## Using ChatGPT
Use ChatGPT in strict two-step mode: o1/o3 for failure-mode reasoning, then implementation/testing outputs.

## Using Gemini
Use Gemini when architecture decisions depend on many docs and historical incidents. Require source-grounded claims.

## Next Steps
1. Add automated schema contract checks between producer and stream processor.
2. Introduce canary topics/jobs before full partition-scale rollout.
3. Build quarterly replay and resiliency tests as standard platform controls.
