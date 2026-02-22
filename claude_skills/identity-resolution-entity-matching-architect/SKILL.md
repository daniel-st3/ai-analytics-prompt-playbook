---
name: identity-resolution-entity-matching-architect
description: Designs enterprise-grade probabilistic entity resolution systems that merge fragmented records into governed Golden Records (Customer 360). Use when user says "identity resolution", "entity matching", "Customer 360", "record deduplication", "Golden Record", "MDM", "merge pipeline", or "probabilistic matching".
---

# Identity Resolution & Entity Matching Architect

## Instructions

Design enterprise-grade probabilistic entity resolution systems that merge fragmented person/account records into governed Golden Records (Customer 360).

### Step 1: Decompose Identity Problem

Decompose identity problem by entity type (person, household, account, organization) and use case (ops, analytics, compliance).

### Step 2: Blocking Strategy

Propose blocking/candidate-generation strategy balancing recall and compute cost.

### Step 3: Similarity Features

Design similarity features:
- Exact matching
- Fuzzy matching
- Phonetic matching
- Embedding-based matching
- Behavioral matching

Include conflict-aware weighting.

### Step 4: Modeling Approach

Specify modeling approach:
- Rules + probabilistic scorer + active learning
- Confidence calibration method

### Step 5: Golden Record Survivorship

Define Golden Record survivorship and field-level source precedence with temporal rules.

### Step 6: Human-in-the-Loop

Include human-in-the-loop adjudication process for uncertain matches and high-risk merges.

### Step 7: Explainability

Add explainability artifacts: why-matched/why-not-matched evidence trails.

### Step 8: Monitoring

Deliver monitoring plan for:
- Match drift
- Precision decay
- Bias/fairness checks

### Step 9: Governance

Include data governance requirements: lineage, reversibility, and legal hold constraints.

## Expected Outputs

- Identity domain decomposition
- Candidate generation and scoring architecture
- Training/labeling and active-learning plan
- Golden Record and survivorship contract
- Monitoring and governance controls
- Rollout, rollback, and stewardship operations

## Examples

**Example 1: Large-Scale Match Pipeline**
User says: "Design a match pipeline for 240M profiles across CRM, product telemetry, and billing, with precision > 0.995."
Result: Multi-stage pipeline with blocking, probabilistic scoring, and adjudication workflow.

**Example 2: Probabilistic Redesign**
User says: "Our deterministic email+phone matching is collapsing under noisy international formats; redesign with probabilistic matching."
Result: Feature-rich probabilistic matcher with active learning and confidence calibration.

**Example 3: Post-M&A Identity Merge**
User says: "Build post-M&A identity merge plan where two CRMs have conflicting account hierarchies."
Result: Cross-domain merge strategy with conflict resolution and reversible merge journal.

## Troubleshooting

**Error: Unsupported features or unrealistic accuracy targets**
Solution: Constrain design to provided telemetry and feature set. Output achievable precision/recall ranges with assumptions and validation method.

**Error: False-merge blast radius ignored**
Solution: Rebuild with risk-tiered thresholds and explicit no-merge zones for high-consequence entities. Include manual adjudication queue design.

**Error: Survivorship policy is non-reversible**
Solution: Add reversible merge journal and field-level provenance required for unmerge workflows.

## Edge Cases

- Household/shared identifiers creating false merges
- Contact data churn causing entity fragmentation over time
- System-specific identifier reuse introducing cross-entity contamination
- Active-learning labels biased toward easy positives
- Survivorship rules overwriting legally authoritative source fields

## Practical Tips

- Always define separate thresholds for analytics joins vs operational activation
- Keep a frozen benchmark set for regression testing matching model changes
- Track merge/unmerge rates and downstream incident correlation weekly
