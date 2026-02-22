---
name: data-mesh-domain-modeler
description: Supports enterprise data architects in defining domain-oriented data products, output ports, contracts, ownership boundaries, and federated governance for Data Mesh operating models. Use when user says "data mesh", "domain modeling", "data products", "federated governance", "domain ownership", "data contracts", or "decentralized data architecture".
---

# Data Mesh Domain Modeler

## Instructions

Support enterprise data architects in defining domain-oriented data products, output ports, contracts, ownership boundaries, and federated governance.

### Step 1: Map Capabilities to Domains

Map organizational capabilities to candidate data domains.

### Step 2: Define Data Products

Define domain-owned data products and output ports with explicit consumers.

### Step 3: Specify Contracts

Specify contract requirements:
- Schema definition
- Freshness SLA
- Quality SLO
- Security classification

### Step 4: Design Governance Model

Design federated governance model with policy ownership and escalation paths.

### Step 5: Interoperability Standards

Include interoperability standards: naming, semantics, lineage, observability.

### Step 6: Accountability Matrix

Build accountability matrix for incidents and contract breaches.

### Step 7: Phased Adoption Plan

Provide phased adoption plan minimizing organizational disruption.

### Step 8: Success Metrics

Include metrics to prove mesh maturity and business value.

## Expected Outputs

- Domain architecture map
- Data product and port definitions
- Contract templates
- Federated governance model
- SLO monitoring and incident flow
- Adoption roadmap and success metrics

## Examples

**Example 1: Domain Definition**
User says: "Define domain model and product contracts for Finance, Marketing, and Ops data products."
Result: Complete domain decomposition with ownership matrix and contract templates.

**Example 2: Governance Design**
User says: "Design federated governance with measurable SLO enforcement across 12 domains."
Result: Governance operating model with escalation paths and enforcement automation.

**Example 3: Migration Roadmap**
User says: "Create a migration roadmap from centralized warehouse ownership to data mesh."
Result: Phased adoption plan with pilot domains and maturity metrics.

## Troubleshooting

**Error: Mesh proposed without enforceable contracts**
Solution: Regenerate with machine-checkable contract fields and automated SLA validation requirements.

**Error: Domain boundaries are vague**
Solution: Provide a boundary matrix: domain, owner, shared entities, conflict resolution rule.

**Error: Governance model is purely theoretical**
Solution: Add operational artifacts: review cadence, escalation SLAs, policy exception process.

## Edge Cases

- Domain boundary overlap causing ownership conflicts
- Local domain optimization breaking cross-domain semantics
- Contract proliferation without enforcement automation
- Platform team bottlenecks undermining domain autonomy
- SLA commitments lacking measurable telemetry

## Practical Tips

- Require explicit consumer contracts for every proposed data product
- Start with 2-3 pilot domains and measurable contract adherence KPIs
- Tie mesh adoption to incident reduction and decision-cycle acceleration metrics
