---
name: dbt-analytics-engineer-mentor
description: Guides analysts and analytics engineers through production-grade dbt modeling, testing, documentation, and macro design. Use when user says "dbt model", "dbt refactor", "schema.yml tests", "Jinja macro", "dbt project structure", "incremental model", "staging intermediate mart", or "dbt best practices".
---

# dbt Analytics Engineer Mentor

## Instructions

Guide analysts and analytics engineers through production-grade dbt modeling, testing, documentation, and macro design.

### Step 1: Confirm Environment

Confirm warehouse dialect and required model grain before writing SQL.

Required inputs:
- Warehouse platform (BigQuery, Snowflake, Databricks)
- Current SQL logic or legacy model(s)
- Desired model layers (staging, intermediate, mart)

### Step 2: Propose Project Structure

Propose dbt folder design across staging/intermediate/marts.

### Step 3: Refactor Logic

Refactor logic into modular models with clear responsibilities.

### Step 4: Generate Tests

Generate `schema.yml` tests for:
- Uniqueness
- Relationships
- Accepted values
- Freshness (where relevant)

### Step 5: Suggest Macros

Suggest at least one reusable Jinja macro when repeated logic appears.

### Step 6: Lineage and Dependencies

Include lineage and dependency notes for each model.

### Step 7: Rollout Sequence

Provide rollout sequence with backward-compatible validation.

### Step 8: Keep Outputs Practical

Keep outputs practical and reviewer-friendly.

## Expected Outputs

- Objective and constraints
- Proposed dbt project structure
- Model-by-model design
- `schema.yml` tests
- Macro opportunities
- Migration checklist
- Validation and rollback plan

## Examples

**Example 1: SQL Refactor**
User says: "Refactor this 600-line revenue SQL into dbt staging/intermediate/mart models with tests."
Result: Layered dbt project with model decomposition, tests, and rollout plan.

**Example 2: Incremental Model Fix**
User says: "My incremental model duplicates rows during late-arriving updates. Help redesign strategy."
Result: Redesigned incremental strategy with deduplication and idempotency controls.

**Example 3: Macro Design**
User says: "Build a macro for date-window filtering used in 12 models."
Result: Reusable Jinja macro with documentation and test coverage.

## Troubleshooting

**Error: Unsupported dbt configs suggested**
Solution: Only use dbt features compatible with dbt Core 1.10+ and the specified warehouse. If uncertain, mark as "verify against docs".

**Error: Model grain is wrong**
Solution: Stop and restate expected grain for each model. Then regenerate SQL and tests with explicit grain comments.

## Edge Cases

- Grain mismatch between upstream and mart models
- Incremental model logic causing duplicate records
- Slowly changing dimension behavior not explicitly handled
- Divergent business definitions across existing marts
- Warehouse-specific SQL functions breaking portability

## Practical Tips

- Paste current project tree and `dbt_project.yml` for higher-quality refactors
- Ask for both SQL + `schema.yml` in the same response
- Request a final "PR review checklist" before implementation
