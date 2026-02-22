---
name: n8n-workflow-architect
description: Transforms process ideas into robust n8n workflows with reliability and governance built in. Use when user says "n8n workflow", "n8n automation", "build n8n flow", "n8n node design", "workflow automation", "Slack alert workflow", "n8n error handling", or "n8n retry logic".
---

# n8n Workflow Architect

## Instructions

Transform process ideas into robust n8n workflows with reliability and governance built in.

### Step 1: Define Objective

Begin with workflow objective and strict success criteria.

### Step 2: Design Node Sequence

Design node sequence with data contract for each node.

### Step 3: Idempotency Strategy

Include idempotency strategy to prevent duplicate actions.

### Step 4: Error Handling

Add:
- Retry logic
- Fallback branch
- Dead-letter path for repeated failures

### Step 5: Human Approval Gates

Mark any human approval gate required before external actions.

### Step 6: Test Plan

Provide test plan for:
- Happy path
- Degraded path
- Hard-failure path

### Step 7: MVP First

Deliver MVP first, then version-2 hardening upgrades.

## Expected Outputs

- Workflow objective
- Node sequence map
- Data contracts per node
- Error handling and retries
- Approval and escalation logic
- Test matrix
- MVP vs hardening roadmap

## Examples

**Example 1: Daily KPI Summary**
User says: "Design an n8n flow that computes daily KPIs and sends a Slack summary with one recommended action."
Result: Complete workflow with data fetching, computation, formatting, and Slack delivery nodes.

**Example 2: Anomaly Alerts with Approval**
User says: "I need anomaly alerts, but manager approval is required before escalation."
Result: Alert detection workflow with human-in-the-loop approval gate.

**Example 3: Incident Triage**
User says: "Create a dashboard incident triage workflow with severity routing."
Result: Severity-aware routing workflow with escalation paths and DLQ handling.

## Troubleshooting

**Error: Duplicate triggers or replayed events**
Solution: Add idempotency keys and deduplication checks at workflow entry point.

**Error: Downstream API rate limits**
Solution: Add rate-limiting nodes with exponential backoff and queue management.

## Edge Cases

- Duplicate triggers or replayed events
- Partial payloads with missing required fields
- Downstream API rate limits and timeouts
- Stale source data leading to false alerts
- Credential/permission failure mid-workflow

## Practical Tips

- Provide one real payload per source node
- Specify SLA (for example: "summary must deliver by 9:00 AM local time")
- Ask Claude for both "workflow diagram text" and "test matrix" in one run
