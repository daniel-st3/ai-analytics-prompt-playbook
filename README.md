# Strict-Mode AI Prompt & Automation Playbook for Modern Data Teams

Production-ready AI documentation, prompt systems, and implementation playbooks for analytics, BI, data engineering, and data science teams in 2026.

This repository is built for people who care about correctness, repeatability, and enterprise constraints. It is intentionally not a “prompt dump.” It is a structured operating system for model-assisted data work.

## What Makes This Different
- Model-specific workflows, not generic prompts.
- Explicit assumptions, edge-case checks, and validation-first outputs.
- Enterprise-grade topics: lakehouse design, FinOps, causal inference, RAG evaluation, IaC, streaming migration, compliance auditing.
- Every major asset includes **Troubleshooting / Handling AI Hallucinations** guidance.

## Staff-Level Expansion Pack
This repo now includes a Staff-level expansion across architecture, governance, and platform reliability:
- New Claude Skills for Lakehouse (Iceberg/Delta), Causal Inference, Terraform IaC, RAG Evaluation, Reverse ETL, and Data Mesh.
- New Custom GPT blueprints for Cloud FinOps, Dynamic Orchestration, PySpark Refactoring, Bayesian Simulation, Time-Series Debugging, and SOC2/HIPAA auditing.
- New Gemini Gems for executive roadmap synthesis, catalog/lineage sync, API contract analysis, incident trend synthesis, ROI modeling, and metric tie-breaking.
- New advanced tutorial on migrating from batch dbt to real-time Kafka/Flink materialized views.

## Who This Is For
- Lead / Staff Data Engineers
- Lead Analytics Engineers
- Principal Data Scientists
- Senior BI and Analytics Platform owners
- Advanced students targeting senior-ready portfolio work

## Core Philosophy
Use each model for its strongest operating mode.

| Model | Best Role in This Repo | Prompting Pattern |
|---|---|---|
| Claude | Architecture design, system decomposition, governance planning | XML-first structure: `<role>`, `<instructions>`, `<edge_cases>`, `<output_format>` |
| ChatGPT (o1/o3 + ADA) | Edge-case reasoning + executable analytics workflows | Two-phase mode: reason with o1/o3, execute with ADA |
| Gemini | Source-grounded synthesis across large doc sets | Attach docs and require source mapping for every major claim |

## Repository Map

| Folder | What You’ll Find | What You Can Do |
|---|---|---|
| `prompts/` | `mega_prompt_library.md` with 40 strict-mode mega-prompts | Run model-specific prompt workflows across SQL, BI, ML, automation, and career assets |
| `claude_skills/` | 17 Claude Skills (core + staff-level) | Spin up reusable XML-based analysis/architecture modes for real projects |
| `custom_gpts/` | 15 Custom GPT designs | Build specialized ChatGPT assistants with knowledge-base and guardrail policies |
| `gemini_gems/` | 15 Gemini Gem designs | Build source-grounded Gems for strategy synthesis, governance, and roadmap planning |
| `tutorials/` | 5 detailed implementation guides | Ship portfolio and production-style projects with step-by-step and troubleshooting support |

## Start Here (By Goal)

### 1) Build Fast, High-Quality Analytics Output
- Start: `prompts/mega_prompt_library.md`
- Then pick one skill: `claude_skills/eda_sql_coach.md`
- Use tutorial: `tutorials/fraud_detection_analytics_notebook_45_minutes.md`

### 2) Build Reliable Automation and Orchestration
- Start: `claude_skills/n8n_workflow_architect.md`
- Add GPT support: `custom_gpts/airflow_dagster_dynamic_dag_generator_gpt.md`
- Apply in tutorial: `tutorials/n8n_personal_analytics_command_center.md`

### 3) Work on Staff-Level Platform Architecture
- Lakehouse: `claude_skills/data_lakehouse_architect.md`
- IaC: `claude_skills/terraform_iac_builder_data_platforms.md`
- FinOps: `custom_gpts/cloud_data_finops_copilot_gpt.md`
- Real-time migration: `tutorials/migrating_from_batch_to_real_time_flink_kafka_starter_guide.md`

### 4) Build Governance and Compliance Programs
- Privacy: `claude_skills/data_privacy_gdpr_redaction_reviewer.md`
- Compliance audit: `custom_gpts/soc2_hipaa_automated_data_auditor_gpt.md`
- Lineage/compliance synthesis: `gemini_gems/data_lineage_compliance_mapper_gem.md`

### 5) Align Strategy, Metrics, and ROI
- Strategy to roadmap: `gemini_gems/executive_data_strategy_to_roadmap_converter_gem.md`
- ROI model: `gemini_gems/analytics_roi_calculator_gem.md`
- Metric conflicts: `gemini_gems/cross_functional_metric_tiebreaker_gem.md`

## What You Can Build With This Repo
- Enterprise KPI systems with semantic consistency and governance controls
- AI-assisted lakehouse and warehouse architecture plans
- dbt + orchestration + BI implementation blueprints
- RAG quality gates with judge + deterministic evaluation metrics
- Reverse ETL activation flows with idempotency and API reliability
- Compliance evidence pipelines (SOC2/HIPAA-ready controls)
- Strategy-to-roadmap operating plans for data organizations

## How to Use This Repository (Strict Mode)
1. Define objective, decision owner, data grain, and constraints.
2. Choose model and asset type:
- Claude Skill for architecture/planning
- Custom GPT for implementation workflows
- Gemini Gem for multi-document synthesis
3. Run with mandatory checks:
- assumptions
- edge cases
- validation tests
- confidence labeling
4. If output is risky, use the file’s troubleshooting prompts before adoption.
5. Save prompt + input snapshot + output decision notes for reproducibility.

## Quality Standard Enforced Across Files
- No blind output acceptance.
- No hidden assumptions in production paths.
- No architecture recommendations without rollback and validation plans.
- No KPI claims without source-grounded definitions.
- No compliance claims without control mapping and evidence traces.

## Clone and Use
```bash
git clone https://github.com/daniel-st3/ai-analytics-prompt-playbook.git
cd ai-analytics-prompt-playbook
code .
```

## Suggested Weekly Workflow
1. Pick one active business problem.
2. Select one Skill + one GPT/Gem support asset.
3. Execute with strict-mode checks.
4. Record result and update your runbook.
5. Add reusable learnings back into repo.

## Contribution Guidelines
1. Keep contributions original, practical, and testable.
2. Match strict-mode structure and model-specific behavior.
3. Include troubleshooting/hallucination controls in every major file.
4. Prefer small PRs with explicit before/after value.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
