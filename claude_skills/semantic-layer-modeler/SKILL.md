---
name: semantic-layer-modeler
description: Designs robust semantic models, metric definitions, relationship contracts, and caching strategy for headless BI using Cube or MetricFlow. Use when user says "semantic layer", "Cube model", "MetricFlow", "headless BI", "metric definitions", "pre-aggregation", "consistent metrics", or "KPI standardization".
---

# Semantic Layer Modeler (Cube/MetricFlow)

## Instructions

Design robust semantic models, metric definitions, relationship contracts, and caching strategy for headless BI.

### Step 1: Confirm Grain and Ownership

Confirm canonical grain and metric ownership before model drafting.

### Step 2: Define Semantic Entities

Define semantic entities, measures, dimensions, and join paths explicitly.

### Step 3: Prevent Ambiguous Joins

Prevent ambiguous joins by enforcing relationship contracts.

### Step 4: Caching Strategy

Propose caching/pre-aggregation strategy based on query access patterns.

### Step 5: Access Control

Include access control and metric-change governance recommendations.

### Step 6: Query Quality Checks

Add query quality checks for denominator correctness and filter behavior.

### Step 7: Rollout Sequence

Provide rollout sequence with backwards compatibility notes.

### Step 8: Collaboration-Ready Outputs

Keep outputs ready for engineering and analyst collaboration.

## Expected Outputs

- Semantic layer objective
- Entity and metric contracts
- Relationship map
- Caching/pre-aggregation plan
- Governance model
- Validation and rollout checklist

## Examples

**Example 1: Revenue Metrics Model**
User says: "Design a MetricFlow model for revenue, net revenue, and retention with strict consistency."
Result: Complete semantic model with metric contracts and validation queries.

**Example 2: Cache Optimization**
User says: "Our Cube layer has slow queries during Monday peak traffic. Optimize caching strategy."
Result: Pre-aggregation plan with access-pattern-based caching tiers.

**Example 3: Safe Join Paths**
User says: "Help define safe join paths to avoid KPI inflation across sales and finance dimensions."
Result: Relationship contracts with many-to-many prevention and validation tests.

## Troubleshooting

**Error: Semantic definitions conflict with source-of-truth docs**
Solution: Use canonical KPI contracts as provided. Rebuild semantic model and mark every deviation explicitly.

**Error: Caching advice is generic**
Solution: Recompute caching strategy using query frequency table provided by user.

## Edge Cases

- Conflicting metric formulas in different teams
- Many-to-many joins creating inflated aggregates
- Filter context changes breaking historical comparability
- Pre-aggregation invalidation causing stale answers
- Semantic layer drift from underlying dbt/warehouse contracts

## Practical Tips

- Ask for a metric change-governance template before rollout
- Keep one canonical metric dictionary in version control
- Request a smoke-test query pack for CI validation
