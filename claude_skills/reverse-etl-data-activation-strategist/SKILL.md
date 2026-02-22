---
name: reverse-etl-data-activation-strategist
description: Designs safe, reliable reverse ETL patterns from warehouse models to operational tools (Salesforce, HubSpot, Braze, Zendesk) with idempotency and API quota control. Use when user says "reverse ETL", "data activation", "warehouse to CRM", "sync to Salesforce", "HubSpot sync", "operationalize scores", or "audience activation".
---

# Reverse ETL & Data Activation Strategist

## Instructions

Design safe, reliable reverse ETL patterns from warehouse models to operational tools with idempotency, API quota control, and contract-based activation governance.

### Step 1: Define Source and Destination Grain

Define source-of-truth model grain and destination object grain.

### Step 2: Key Mapping

Design key mapping and identity resolution strategy.

### Step 3: Idempotent Upsert Logic

Build idempotent upsert logic with deterministic sync keys.

### Step 4: API-Aware Batching

Include API-aware batching, throttling, backoff, and dead-letter handling.

### Step 5: Suppression and Consent

Add suppression/consent logic and compliance-safe field controls.

### Step 6: Reconciliation Queries

Provide reconciliation queries for source-vs-destination parity.

### Step 7: Alerting and Runbook

Define alerting and on-call runbook for failed syncs.

### Step 8: Phased Rollout

Output phased rollout plan with blast-radius controls.

## Expected Outputs

- Activation objective and constraints
- Data contract and field mapping
- Sync mechanics (idempotency/retries)
- Monitoring and reconciliation plan
- Rollout and rollback strategy
- Governance controls

## Examples

**Example 1: Churn Score Activation**
User says: "Design reverse ETL sync for churn-risk scores from BigQuery to Salesforce contacts."
Result: Complete sync architecture with field mapping, idempotency, and reconciliation.

**Example 2: API Limit Redesign**
User says: "We hit HubSpot API limits daily; redesign sync pattern with guaranteed eventual consistency."
Result: Rate-aware batching strategy with backpressure and DLQ handling.

**Example 3: Activation Governance**
User says: "Create activation governance to prevent stale segment pushes to outbound campaigns."
Result: Freshness validation gates with kill-switch and replay capabilities.

## Troubleshooting

**Error: API quotas ignored**
Solution: Rebuild sync strategy with explicit QPS limits, batch sizes, and retry budgets.

**Error: Idempotency is not deterministic**
Solution: Define canonical sync key and conflict-resolution policy with replay-safe behavior.

**Error: Reconciliation is weak**
Solution: Add source-vs-destination parity SQL plus discrepancy triage workflow.

## Edge Cases

- Upsert mismatch creating duplicate CRM entities
- Late-arriving source updates overwriting newer operational states
- API rate-limit bursts causing partial segment activation
- Schema drift in destination objects breaking sync silently
- Consent flag lag causing prohibited downstream activation

## Practical Tips

- Force every activation flow to include a kill switch and replay plan
- Start with one destination object before broad schema sync
- Keep consent and suppression columns in the sync contract, not in app-only logic
