# Strict-Mode AI Prompt & Automation Playbook for Modern Data Teams

Production-ready AI documentation for analytics, BI, data engineering, and enterprise AI architecture in 2026.

This repository is not a prompt collection. It is an operating model for serious teams that want AI outputs to be **auditable, testable, and safe to deploy**.

## What This Repo Gives You
- Model-specific workflows that match real strengths of Claude, ChatGPT, and Gemini.
- Enterprise-grade blueprints for architecture, reliability, governance, privacy, and cost control.
- Practical assets you can apply immediately: Skills, GPT/Gem designs, tutorials, and mega-prompts.
- Built-in anti-hallucination controls across all major files.

## Expansion Packs Included

### Staff-Level Expansion (Already Included)
- Lakehouse architecture (Iceberg/Delta), causal inference, Terraform IaC, RAG evaluation, reverse ETL, data mesh.
- FinOps, dynamic orchestration, PySpark refactoring, Bayesian simulation, anomaly debugging, SOC2/HIPAA checks.
- Real-time migration guide (batch dbt to Kafka/Flink).

### Principal-Level / Enterprise AI Expansion (Now Included)
- Identity resolution and entity matching architecture (Golden Record / Customer 360).
- Differential privacy and synthetic data strategy.
- Unstructured data pipelines via warehouse-native AI functions (Cortex/Mosaic).
- Event-driven orchestration architecture beyond cron DAGs.
- LLM fine-tuning data curation, alert-fatigue tuning, graph/network debugging, semantic cache optimization.
- M&A integration strategy, enterprise data contracts, AI ROI forecasting, and board-level data storytelling.
- Native Text-to-SQL agent tutorial over a semantic layer (anti-hallucination by design).

## Core Philosophy (Strict Mode)

| Model | Best Role | How This Repo Uses It |
|---|---|---|
| Claude | Architecture and system design | XML-first prompts (`<role>`, `<instructions>`, `<edge_cases>`, `<output_format>`) |
| ChatGPT (o1/o3 + ADA) | Reasoning + execution | Two-phase flow: reason with o1/o3, execute with ADA/Python |
| Gemini | Source-grounded synthesis | Multi-doc grounding with explicit source mapping and conflict handling |

## Repository Structure

| Folder | Current Scope | What You Can Do |
|---|---|---|
| `prompts/` | 1 mega library (40 strict-mode prompts) | Run advanced analytics/BI/ML/automation prompting playbooks |
| `claude_skills/` | 21 skills | Reuse architecture-grade Claude operating modes for production problems |
| `custom_gpts/` | 19 GPT designs | Build specialized assistants with enterprise guardrails and KB retrieval patterns |
| `gemini_gems/` | 19 Gem designs | Build source-grounded synthesis assistants for strategy/governance/program planning |
| `tutorials/` | 6 deep tutorials | Execute complete projects from notebook builds to real-time and semantic-agent systems |

## Fast Navigation

### Start Here: Data/BI Builders
- `prompts/mega_prompt_library.md`
- `claude_skills/eda_sql_coach.md`
- `tutorials/fraud_detection_analytics_notebook_45_minutes.md`

### Start Here: Analytics Engineering / Platform
- `claude_skills/dbt_analytics_engineer_mentor.md`
- `claude_skills/terraform_iac_builder_data_platforms.md`
- `custom_gpts/airflow_dagster_dynamic_dag_generator_gpt.md`
- `tutorials/end_to_end_modern_data_stack_setup_weekend.md`

### Start Here: Principal / Enterprise Architecture
- `claude_skills/identity_resolution_entity_matching_architect.md`
- `claude_skills/differential_privacy_synthetic_data_generator.md`
- `claude_skills/unstructured_data_pipeline_designer_cortex_mosaic.md`
- `claude_skills/event_driven_orchestration_architect.md`
- `gemini_gems/mna_data_integration_strategist_gem.md`
- `gemini_gems/enterprise_data_contract_negotiator_gem.md`

### Start Here: Enterprise AI + Semantic Reliability
- `custom_gpts/llm_fine_tuning_dataset_curator_gpt.md`
- `custom_gpts/semantic_cache_optimizer_gpt.md`
- `claude_skills/rag_pipeline_evaluator_llm_as_judge.md`
- `tutorials/building_native_text_to_sql_agent_over_semantic_layer.md`

## What You Can Build with This Repo
- KPI systems with semantic consistency and explicit governance contracts.
- Lakehouse and warehouse architectures with performance and cost controls.
- Event-driven data platforms with replay-safe idempotency patterns.
- RAG and GenAI systems with measurable retrieval/hallucination quality gates.
- Privacy-preserving synthetic datasets with formal DP-aware release controls.
- Data contract operating models between software and analytics teams.
- Executive and board-ready strategy narratives grounded in data evidence.

## Recommended Execution Workflow
1. Define objective, decision owner, and risk tier.
2. Select asset type:
- Claude Skill for architecture and operating controls.
- Custom GPT for implementation acceleration and simulation.
- Gemini Gem for multi-doc synthesis and policy reconciliation.
3. Run strict-mode checks every time:
- assumptions
- edge cases
- validation tests
- confidence levels
4. Use each file’s **Troubleshooting / Handling AI Hallucinations** section before production rollout.
5. Log prompt, input snapshot, output decision, and follow-up changes.

## Clone and Use
```bash
git clone https://github.com/daniel-st3/ai-analytics-prompt-playbook.git
cd ai-analytics-prompt-playbook
code .
```

## Team Usage Pattern (Weekly)
1. Pick one high-impact business/system problem.
2. Use one primary Skill + one GPT/Gem companion.
3. Execute with strict validation and red-team prompts.
4. Capture lessons in runbook/docs.
5. Promote reusable patterns back into this repo.

## Contribution Guidelines
1. Keep additions original, practical, and high-rigor.
2. Preserve strict-mode formatting and model-specific behavior.
3. Include troubleshooting/hallucination controls in every major new file.
4. Prefer focused PRs with explicit before/after value and validation evidence.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
