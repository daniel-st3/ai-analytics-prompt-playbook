---
name: data-warehouse-migration-architect
description: Refactors legacy SQL pipelines (stored procedures, monolithic scripts) into modular warehouse and dbt-ready models with validated grain and metric parity. Use when user says "warehouse migration", "stored procedure refactor", "SQL Server to Snowflake", "legacy SQL migration", "BigQuery migration", "parity checks", or "deprecate legacy tables".
---

# Data Warehouse Migration Architect

## Instructions

Refactor legacy SQL pipelines into modular warehouse + dbt-ready models with validated grain and metric parity.

### Step 1: Inventory Legacy Components

Inventory legacy components and classify by business criticality.

### Step 2: Map to Modular Models

Map legacy procedures into staged modular models with explicit ownership.

### Step 3: Define Grain

Define grain for every output table before rewriting logic.

CRITICAL: Grain must be explicitly defined before any SQL rewrite begins.

### Step 4: Parity Testing Strategy

Create parity testing strategy comparing old vs new outputs:
- Row-level sampling
- Aggregate KPI parity
- Edge-period reconciliation

### Step 5: Dialect Translation

Include dialect translation guidance for target warehouse.

### Step 6: Incremental Cutover Plan

Design incremental cutover plan with rollback checkpoints.

### Step 7: SLA Validation

Add SLA and performance validation before final switch.

### Step 8: Communication Plan

Produce communication plan for analysts and dashboard owners.

## Expected Outputs

- Migration scope and priorities
- Legacy-to-modern mapping table
- Refactor plan by phase
- Grain/parity validation checklist
- Cutover and rollback plan
- Operational risk register

## Examples

**Example 1: Stored Procedure Migration**
User says: "Convert this SQL Server stored proc revenue logic into dbt models for Snowflake."
Result: Phased migration plan with dialect translation and model decomposition.

**Example 2: Parity Validation**
User says: "I need parity checks before deprecating legacy mart tables."
Result: Comprehensive parity testing suite with row-level and aggregate checks.

**Example 3: Zero-Downtime Migration**
User says: "Design a phased migration that avoids executive dashboard downtime."
Result: Cutover plan with parallel running, rollback checkpoints, and stakeholder communication.

## Troubleshooting

**Error: Platform features assumed that are unavailable**
Solution: Limit recommendations to the specified target platform. Mark unsupported features and provide alternatives.

**Error: Parity checks are too weak**
Solution: Expand validation to include row-level sampling, aggregate KPI parity, and edge-period reconciliation.

## Edge Cases

- Hidden side effects in stored procedures
- Implicit temp-table assumptions not portable to target platform
- Legacy timezone logic creating KPI drift
- Join cardinality shifts after normalization
- Cutover windows with incomplete historical backfill

## Practical Tips

- Start with one high-value domain to prove migration pattern
- Ask for a dependency graph before coding changes
- Keep rollback artifacts live until two full reporting cycles pass
