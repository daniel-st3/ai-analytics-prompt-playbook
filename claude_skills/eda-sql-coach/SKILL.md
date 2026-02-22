---
name: eda-sql-coach
description: Converts unclear analytics questions into validated SQL, EDA outputs, and decision-ready notes. Use when user says "write SQL", "EDA analysis", "SQL coach", "debug SQL", "KPI query", "data exploration", "validate query", or "SQL interview practice".
---

# EDA & SQL Coach

## Instructions

Convert unclear analytics questions into validated SQL, EDA outputs, and decision-ready notes.

### Step 1: Confirm Business Objective

Start by confirming business objective, decision owner, and expected table grain.

### Step 2: Ask Clarifying Questions

If grain or metric definition is ambiguous, ask targeted clarifying questions before generating final SQL.

### Step 3: Propose Analysis Plan

Propose a phased analysis plan:
1. Profiling
2. Joins
3. KPI logic
4. Validation

### Step 4: Generate SQL

Generate SQL in ANSI style unless dialect is explicitly provided.

### Step 5: Include Validation Queries

CRITICAL: Always include validation queries for:
- Duplicates
- Nulls
- Join explosion
- Denominator correctness

### Step 6: Interpretation Guide

Provide a short interpretation guide that explains how to read results safely.

### Step 7: Keep Outputs Practical

Keep output practical and portfolio-ready.

## Expected Outputs

- Objective and decision context
- Assumptions table
- Query and EDA plan
- SQL query pack
- Validation checks
- Risks and caveats
- Recommended next actions

## Examples

**Example 1: Cohort Analysis**
User says: "Here are orders, payments, and users. I need monthly conversion and refund rate by cohort."
Result: Complete SQL pack with cohort logic, validation queries, and interpretation notes.

**Example 2: Revenue Audit**
User says: "Revenue in BI does not match finance report. Audit my SQL approach."
Result: Diagnostic queries to identify discrepancy sources with reconciliation checklist.

**Example 3: Fraud EDA**
User says: "I have fraud labels with 7-day delay. Help me set a safe EDA and validation plan."
Result: Time-aware analysis plan with delayed-label handling and validation strategy.

## Troubleshooting

**Error: Missing or inconsistent primary keys**
Solution: Profile key fields first and document uniqueness assumptions before proceeding.

**Error: Metric definition conflict between teams**
Solution: Document both definitions side-by-side and recommend escalation to KPI owner.

## Edge Cases

- Missing or inconsistent primary keys
- Slowly changing dimensions affecting KPI counts
- Delayed labels in fraud tables
- Data freshness mismatch across joined sources
- Metric definition conflict between teams

## Practical Tips

- Paste sample rows in Markdown table format for faster parsing
- Always specify requested grain (order, user, session, etc.)
- Ask for a "sanity-check query" before trusting the final KPI output
