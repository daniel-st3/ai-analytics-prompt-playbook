---
name: terraform-iac-builder-data-platforms
description: Generates and reviews Terraform modules for enterprise data platforms (Snowflake, BigQuery, AWS IAM, dbt Cloud) with secure environment promotion and policy-as-code controls. Use when user says "Terraform data platform", "IaC for Snowflake", "BigQuery IAM Terraform", "infrastructure as code", "Terraform modules", "drift detection", or "data platform provisioning".
---

# Terraform IaC Builder for Data Platforms

## Instructions

Generate and review Terraform modules for enterprise data platforms with secure environment promotion, least-privilege access, and policy-as-code controls.

### Step 1: Model Resources by Domain

Model resources by domain and environment with reusable Terraform modules.

### Step 2: Provider and State Strategy

Define provider strategy and backend state management with locking.

### Step 3: Least-Privilege IAM/RBAC

Encode least-privilege IAM/RBAC for Snowflake roles, BigQuery datasets, and cloud identities.

### Step 4: dbt Cloud Provisioning

Include dbt Cloud environment/service token provisioning patterns when requested.

### Step 5: CI Validation Gates

Add CI validation gates:
- Format
- Validate
- Plan
- Policy checks
- Controlled apply

### Step 6: Drift Detection

Design drift detection cadence and incident response for out-of-band changes.

### Step 7: Import/Migration Guidance

Provide import/migration guidance for existing manually managed resources.

### Step 8: Risk Controls

End with risk controls, approval workflow, and rollback strategy.

## Expected Outputs

- IaC architecture and module boundaries
- Resource mapping by environment
- Security model (IAM/RBAC)
- CI/CD and policy gates
- Drift and rollback playbook
- Implementation milestones

## Examples

**Example 1: Snowflake IaC**
User says: "Create Terraform modules for Snowflake roles/warehouses/databases with environment promotion."
Result: Modular Terraform with role hierarchy and environment-specific configurations.

**Example 2: BigQuery IAM**
User says: "Build BigQuery dataset IAM IaC with least-privilege and auditability."
Result: Dataset-level IAM policies with role matrix and audit logging.

**Example 3: CI Pipeline**
User says: "Design CI pipeline for plan/apply approvals and drift detection across three environments."
Result: Complete CI/CD pipeline with policy gates and drift alerting.

## Troubleshooting

**Error: Provider blocks incompatible with user versions**
Solution: Limit output to specified providers/versions. Regenerate module code and mark deprecated constructs.

**Error: Grants are too broad**
Solution: Refactor into least-privilege mode with explicit role matrix and denied-by-default policy.

**Error: State management is vague**
Solution: Add backend + locking + workspace strategy and failure recovery steps for interrupted applies.

## Edge Cases

- Privilege escalation via inherited role grants
- State corruption from concurrent applies
- Provider version drift causing unexpected diffs
- Cross-project BigQuery permissions misalignment
- Manual hotfixes creating irreversible Terraform drift

## Practical Tips

- Always request a role matrix before any Terraform grant code
- Ask for import strategy when migrating pre-existing resources
- Require a "break-glass" procedure with expiration and audit logging
