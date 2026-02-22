---
name: data-privacy-gdpr-redaction-reviewer
description: Identifies PII exposure risks in schemas, SQL, and analytics workflows and recommends actionable masking, hashing, redaction, and RBAC controls. Use when user says "PII review", "GDPR audit", "data privacy", "redaction", "data masking", "RBAC policy", "privacy compliance", or "sensitive data review".
---

# Data Privacy & GDPR Redaction Reviewer

## Instructions

Identify PII exposure risks in schemas, SQL, and analytics workflows; recommend actionable masking, hashing, redaction, and RBAC controls.

### Step 1: Inventory Sensitive Fields

Inventory potentially sensitive fields and classify by risk level (high / medium / low).

### Step 2: Detect Identifiers

Detect direct and indirect identifiers in schema and query outputs.

### Step 3: Recommend Controls

Recommend control type per field:
- **Hash** - for deterministic pseudonymization
- **Mask** - for display-level protection
- **Tokenize** - for reversible pseudonymization
- **Redact** - for complete removal
- **Restrict** - for access-based control

### Step 4: RBAC Model

Propose RBAC model aligned to least-privilege access.

### Step 5: Flag Risky Joins

Flag risky joins that reconstruct identity from quasi-identifiers.

### Step 6: Audit Requirements

Include logging and audit requirements for data access events.

### Step 7: Remediation Sequence

Provide remediation sequence with quick wins and long-term controls.

### Step 8: Keep Recommendations Implementable

Keep recommendations implementable for analytics teams, not just security teams.

## Expected Outputs

- Scope and regulatory context
- PII classification inventory
- Query-level risk findings
- Recommended controls by priority
- RBAC/access policy draft
- Compliance remediation roadmap

## Examples

**Example 1: Pre-Launch Privacy Review**
User says: "Review these marts and SQL queries for GDPR risk before sharing with external vendor."
Result: Complete PII inventory with field-level control recommendations and remediation timeline.

**Example 2: RBAC Design**
User says: "Design an RBAC policy for analysts, managers, and external contractors."
Result: Role-based access matrix with least-privilege design and audit controls.

**Example 3: Hashing vs Masking**
User says: "Identify fields that require hashing vs masking in this customer 360 model."
Result: Field-level classification with control type rationale and implementation guidance.

## Troubleshooting

**Error: Privacy classification is uncertain**
Solution: Classify only with evidence from provided fields and policies. Mark uncertain items as "requires legal/compliance confirmation".

**Error: Recommendations are too abstract**
Solution: Rewrite controls as implementation tasks with owner, effort, and timeline.

## Edge Cases

- Pseudonymized fields still re-identifiable after joins
- Export workflows bypassing dashboard-level masking
- Service accounts with excessive read permissions
- Retention windows violating policy requirements
- Inconsistent masking logic between warehouse and BI layers

## Practical Tips

- Include real query examples to catch hidden leakage paths
- Ask for "quick win in 7 days" and "full remediation in 90 days" plans
- Request a final compliance sign-off checklist for release reviews
