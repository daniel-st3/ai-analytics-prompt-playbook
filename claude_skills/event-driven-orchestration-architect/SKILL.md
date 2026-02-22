---
name: event-driven-orchestration-architect
description: Designs decoupled, event-driven data orchestration where pipeline execution is triggered by object creation events, Kafka topics, CDC streams, or webhooks instead of rigid cron schedules. Use when user says "event-driven pipeline", "replace cron", "Kafka orchestration", "EventBridge trigger", "CDC pipeline", "webhook automation", or "real-time orchestration".
---

# Event-Driven Orchestration Architect

## Instructions

Design decoupled, event-driven data orchestration where pipeline execution is triggered by object creation events, Kafka topics, CDC streams, or webhooks instead of rigid cron schedules.

### Step 1: Model Events as Contracts

Model events as first-class contracts:
- Schema definition
- Producer ownership
- Delivery semantics
- SLOs

### Step 2: Define Trigger Routing

Define trigger routing architecture (broker, bus, subscription, filter policies).

### Step 3: Design Idempotent Consumers

Design idempotent consumers with deduplication keys and replay-safe behavior.

### Step 4: Reliability Controls

Include:
- Backpressure controls
- Retry tiers
- Dead-letter handling with triage ownership

### Step 5: Ordering Guarantees

Specify ordering guarantees and partitioning strategy where sequence correctness matters.

### Step 6: Dependency Orchestration

Add dependency orchestration logic for fan-in/fan-out and event correlation.

### Step 7: Build Observability

Build observability model:
- Event lag
- Consumer health
- Contract violations
- Replay volume

### Step 8: Migration Path

Provide migration path from cron to hybrid and then fully event-driven operation.

## Expected Outputs

- Event architecture blueprint
- Contract and schema model
- Reliability controls (idempotency/retry/replay)
- Dependency and sequencing logic
- Monitoring and incident management
- Migration and rollout plan

## Examples

**Example 1: Cron to EventBridge**
User says: "Redesign our Airflow cron pipeline into EventBridge-triggered ingestion + transformation with replay safety."
Result: Hybrid migration plan with event contracts and idempotency controls.

**Example 2: Kafka CDC**
User says: "Create Kafka-triggered orchestration for CDC updates with exactly-once-like downstream behavior."
Result: CDC event pipeline with deduplication and ordering guarantees.

**Example 3: Webhook Backpressure**
User says: "We have webhook bursts causing missed SLAs; design backpressure and dead-letter triage model."
Result: Backpressure architecture with DLQ triage and alerting.

## Troubleshooting

**Error: Delivery semantics ignored**
Solution: Regenerate with explicit delivery guarantees by stage (at-most-once/at-least-once/effectively-once) and required idempotency controls.

**Error: Deduplication strategy incomplete**
Solution: Provide deterministic dedupe keys and replay behavior for each consumer and sink.

**Error: Migration plan too risky**
Solution: Split into phased hybrid model with canary triggers and rollback switch to cron fallback.

## Edge Cases

- At-least-once delivery causing duplicate side effects
- Out-of-order events breaking aggregate correctness
- Event schema evolution causing downstream consumer failures
- Trigger storms overwhelming compute pools
- Silent dead-letter accumulation masking systemic breakage

## Practical Tips

- Publish event contracts in version-controlled registry
- Keep DLQ review and replay procedures as on-call requirements
- Measure trigger-to-ready latency as a first-class SLO
