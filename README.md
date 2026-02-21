# Strict-Mode AI Prompt & Automation Playbook for Modern Data Teams

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Markdown](https://img.shields.io/badge/Built%20with-Markdown-000000.svg)](https://www.markdownguide.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./README.md#-contribution-guidelines)

> A strict-mode operating system for AI-assisted analytics, data engineering, and enterprise AI delivery in 2026.  
> Everything here is designed for teams that need outputs to be **auditable, testable, and safe to deploy**.

Production-ready AI documentation for analytics, BI, data engineering, and enterprise AI architecture.

## ✨ What This Repo Gives You
- Model-specific workflows that match real strengths of Claude, ChatGPT, and Gemini.
- Enterprise-grade blueprints for architecture, reliability, governance, privacy, and cost control.
- Practical assets you can apply immediately: Skills, GPT/Gem designs, tutorials, and mega-prompts.
- Built-in anti-hallucination controls across all major files.

## 📦 Expansion Packs Included
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

<details>
<summary><strong>▶ Staff-Level Expansion Files</strong></summary>

### Claude Skills (Staff)
- `claude_skills/data_lakehouse_architect.md`
- `claude_skills/causal_inference_econometrics_coach.md`
- `claude_skills/terraform_iac_builder_data_platforms.md`
- `claude_skills/rag_pipeline_evaluator_llm_as_judge.md`
- `claude_skills/reverse_etl_data_activation_strategist.md`
- `claude_skills/data_mesh_domain_modeler.md`

### Custom GPTs (Staff)
- `custom_gpts/cloud_data_finops_copilot_gpt.md`
- `custom_gpts/airflow_dagster_dynamic_dag_generator_gpt.md`
- `custom_gpts/pyspark_big_data_refactoring_copilot_gpt.md`
- `custom_gpts/bayesian_experimentation_simulator_gpt.md`
- `custom_gpts/anomaly_detection_time_series_debugger_gpt.md`
- `custom_gpts/soc2_hipaa_automated_data_auditor_gpt.md`

### Gemini Gems (Staff)
- `gemini_gems/executive_data_strategy_to_roadmap_converter_gem.md`
- `gemini_gems/data_catalog_lineage_sync_dataplex_gem.md`
- `gemini_gems/vendor_api_contract_analyzer_gem.md`
- `gemini_gems/incident_postmortem_trend_synthesizer_gem.md`
- `gemini_gems/analytics_roi_calculator_gem.md`
- `gemini_gems/cross_functional_metric_tiebreaker_gem.md`

### Tutorial (Staff)
- `tutorials/migrating_from_batch_to_real_time_flink_kafka_starter_guide.md`

</details>

<details>
<summary><strong>▶ Principal-Level Expansion Files</strong></summary>

### Claude Skills (Principal)
- `claude_skills/identity_resolution_entity_matching_architect.md`
- `claude_skills/differential_privacy_synthetic_data_generator.md`
- `claude_skills/unstructured_data_pipeline_designer_cortex_mosaic.md`
- `claude_skills/event_driven_orchestration_architect.md`

### Custom GPTs (Principal)
- `custom_gpts/llm_fine_tuning_dataset_curator_gpt.md`
- `custom_gpts/alert_fatigue_data_observability_tuner_gpt.md`
- `custom_gpts/graph_analytics_network_flow_debugger_gpt.md`
- `custom_gpts/semantic_cache_optimizer_gpt.md`

### Gemini Gems (Principal)
- `gemini_gems/mna_data_integration_strategist_gem.md`
- `gemini_gems/enterprise_data_contract_negotiator_gem.md`
- `gemini_gems/ai_roi_finops_forecaster_gem.md`
- `gemini_gems/board_level_data_storyteller_gem.md`

### Tutorial (Principal)
- `tutorials/building_native_text_to_sql_agent_over_semantic_layer.md`

</details>

## 🧠 Core Philosophy (Strict Mode)

| Model | Best Role | How This Repo Uses It |
|---|---|---|
| Claude | Architecture and system design | XML-first prompts (`<role>`, `<instructions>`, `<edge_cases>`, `<output_format>`) |
| ChatGPT (o1/o3 + ADA) | Reasoning + execution | Two-phase flow: reason with o1/o3, execute with ADA/Python |
| Gemini | Source-grounded synthesis | Multi-doc grounding with explicit source mapping and conflict handling |

## 🗂️ Repository Structure

| Folder | Current Scope | What You Can Do |
|---|---|---|
| `prompts/` | 1 mega library (40 strict-mode prompts) | Run advanced analytics/BI/ML/automation prompting playbooks |
| `claude_skills/` | 21 skills | Reuse architecture-grade Claude operating modes for production problems |
| `custom_gpts/` | 19 GPT designs | Build specialized assistants with enterprise guardrails and KB retrieval patterns |
| `gemini_gems/` | 19 Gem designs | Build source-grounded synthesis assistants for strategy/governance/program planning |
| `tutorials/` | 6 deep tutorials | Execute complete projects from notebook builds to real-time and semantic-agent systems |

<details>
<summary><strong>▶ Expand Full File Tree</strong></summary>

```text
.
├── README.md
├── LICENSE
├── prompts/
│   └── mega_prompt_library.md
├── tutorials/
│   ├── ai_portfolio_github_readme_one_evening.md
│   ├── building_native_text_to_sql_agent_over_semantic_layer.md
│   ├── end_to_end_modern_data_stack_setup_weekend.md
│   ├── fraud_detection_analytics_notebook_45_minutes.md
│   ├── migrating_from_batch_to_real_time_flink_kafka_starter_guide.md
│   └── n8n_personal_analytics_command_center.md
├── claude_skills/
│   ├── ab_test_design_evaluation_specialist.md
│   ├── bi_dashboard_architect.md
│   ├── causal_inference_econometrics_coach.md
│   ├── data_lakehouse_architect.md
│   ├── data_mesh_domain_modeler.md
│   ├── data_privacy_gdpr_redaction_reviewer.md
│   ├── data_warehouse_migration_architect.md
│   ├── dbt_analytics_engineer_mentor.md
│   ├── differential_privacy_synthetic_data_generator.md
│   ├── eda_sql_coach.md
│   ├── event_driven_orchestration_architect.md
│   ├── identity_resolution_entity_matching_architect.md
│   ├── job_search_analyst.md
│   ├── n8n_workflow_architect.md
│   ├── portfolio_readme_editor.md
│   ├── python_data_viz_storytelling_coach.md
│   ├── rag_pipeline_evaluator_llm_as_judge.md
│   ├── reverse_etl_data_activation_strategist.md
│   ├── semantic_layer_modeler_cube_metricflow.md
│   ├── terraform_iac_builder_data_platforms.md
│   └── unstructured_data_pipeline_designer_cortex_mosaic.md
├── custom_gpts/
│   ├── ada_spatial_mapper_gpt.md
│   ├── airflow_dagster_dynamic_dag_generator_gpt.md
│   ├── alert_fatigue_data_observability_tuner_gpt.md
│   ├── anomaly_detection_time_series_debugger_gpt.md
│   ├── bayesian_experimentation_simulator_gpt.md
│   ├── bi_dashboard_coach_gpt.md
│   ├── cicd_pipeline_builder_data_teams_gpt.md
│   ├── cloud_data_finops_copilot_gpt.md
│   ├── data_quality_governance_copilot_gpt.md
│   ├── fraud_analytics_copilot_gpt.md
│   ├── graph_analytics_network_flow_debugger_gpt.md
│   ├── kafka_streaming_analytics_debugger_gpt.md
│   ├── llm_fine_tuning_dataset_curator_gpt.md
│   ├── mlops_deployment_copilot_gpt.md
│   ├── portfolio_job_application_assistant_gpt.md
│   ├── pyspark_big_data_refactoring_copilot_gpt.md
│   ├── semantic_cache_optimizer_gpt.md
│   ├── soc2_hipaa_automated_data_auditor_gpt.md
│   └── sql_performance_cost_optimizer_gpt.md
└── gemini_gems/
    ├── ai_roi_finops_forecaster_gem.md
    ├── analytics_research_gem.md
    ├── analytics_roi_calculator_gem.md
    ├── automated_data_catalog_documenter_gem.md
    ├── automation_planner_gem.md
    ├── board_level_data_storyteller_gem.md
    ├── cross_functional_metric_tiebreaker_gem.md
    ├── data_catalog_lineage_sync_dataplex_gem.md
    ├── data_lineage_compliance_mapper_gem.md
    ├── drive_to_dashboard_spec_generator_gem.md
    ├── enterprise_data_contract_negotiator_gem.md
    ├── executive_data_strategy_to_roadmap_converter_gem.md
    ├── incident_postmortem_trend_synthesizer_gem.md
    ├── meeting_transcript_to_data_ticket_converter_gem.md
    ├── mna_data_integration_strategist_gem.md
    ├── sql_bigquery_review_gem.md
    ├── stakeholder_okr_to_analytics_kpi_translator_gem.md
    ├── vendor_api_contract_analyzer_gem.md
    └── vendor_evaluation_rfp_analyzer_gem.md
```

</details>

## 🧭 Fast Navigation

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

## 🏗️ What You Can Build with This Repo
- KPI systems with semantic consistency and explicit governance contracts.
- Lakehouse and warehouse architectures with performance and cost controls.
- Event-driven data platforms with replay-safe idempotency patterns.
- RAG and GenAI systems with measurable retrieval/hallucination quality gates.
- Privacy-preserving synthetic datasets with formal DP-aware release controls.
- Data contract operating models between software and analytics teams.
- Executive and board-ready strategy narratives grounded in data evidence.

## ✅ Recommended Execution Workflow
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

## 🚀 Quick Start
```bash
git clone https://github.com/daniel-st3/ai-analytics-prompt-playbook.git
cd ai-analytics-prompt-playbook
code .
```

## 🔁 Team Usage Pattern (Weekly)
1. Pick one high-impact business/system problem.
2. Use one primary Skill + one GPT/Gem companion.
3. Execute with strict validation and red-team prompts.
4. Capture lessons in runbook/docs.
5. Promote reusable patterns back into this repo.

## 🤝 Contribution Guidelines
1. Keep additions original, practical, and high-rigor.
2. Preserve strict-mode formatting and model-specific behavior.
3. Include troubleshooting/hallucination controls in every major new file.
4. Prefer focused PRs with explicit before/after value and validation evidence.

## 📜 License
This project is licensed under the **MIT License** - see the `LICENSE` file for details. Free to use, copy, and adapt for your own workflows.
