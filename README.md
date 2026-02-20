# Strict-Mode AI Prompt & Automation Playbook for Modern Data Teams

A production-minded AI documentation repository for analytics, BI, and automation workflows in 2026.

This repo is designed for data analysts, BI developers, analytics engineers, and advanced students who want to use AI with **rigor**, not guesswork. Everything here is strict mode:
- explicit assumptions,
- model-specific prompting standards,
- validation-first workflows,
- and practical troubleshooting for hallucinations, bad SQL grain, and failing pipelines.

## Why This Repository Exists
Most prompt repositories stop at generic text generation. This one is intentionally different.

You’ll find:
- **Mega-prompts** for real analytics workflows (not one-liners).
- **Claude Skills** with XML architecture for high-control planning.
- **Custom GPT designs** with knowledge-base retrieval guardrails.
- **Gemini Gem designs** for source-grounded synthesis across Google Workspace artifacts.
- **Long-form tutorials** with step-by-step build paths and troubleshooting prompts.

## Core Philosophy
We use each model for what it does best:

1. **Claude** for XML-based architecture and reasoning structure.
- Prompt style: `<context>`, `<schema>`, `<task>`, `<rules>`
- Best for: planning, migration design, governance workflows, and edge-case risk mapping.

2. **ChatGPT (o1/o3 + ADA)** for edge-case reasoning plus executable workflows.
- Pattern: reason first with `o1/o3`, execute second with `Advanced Data Analysis`.
- Best for: Python/SQL implementation, notebook iteration, and structured debug loops.

3. **Gemini** for source-grounded synthesis with long context.
- Best for: Drive/Docs/Sheets-heavy projects, multi-document alignment, and requirement consolidation.

## Repository Structure
```text
.
├── README.md
├── prompts/
│   └── mega_prompt_library.md
├── tutorials/
│   ├── fraud_detection_analytics_notebook_45_minutes.md
│   ├── n8n_personal_analytics_command_center.md
│   ├── ai_portfolio_github_readme_one_evening.md
│   └── end_to_end_modern_data_stack_setup_weekend.md
├── claude_skills/
│   ├── eda_sql_coach.md
│   ├── n8n_workflow_architect.md
│   ├── portfolio_readme_editor.md
│   ├── bi_dashboard_architect.md
│   ├── job_search_analyst.md
│   ├── dbt_analytics_engineer_mentor.md
│   ├── python_data_viz_storytelling_coach.md
│   ├── ab_test_design_evaluation_specialist.md
│   ├── data_warehouse_migration_architect.md
│   ├── semantic_layer_modeler_cube_metricflow.md
│   └── data_privacy_gdpr_redaction_reviewer.md
├── custom_gpts/
│   ├── fraud_analytics_copilot_gpt.md
│   ├── bi_dashboard_coach_gpt.md
│   ├── portfolio_job_application_assistant_gpt.md
│   ├── sql_performance_cost_optimizer_gpt.md
│   ├── data_quality_governance_copilot_gpt.md
│   ├── cicd_pipeline_builder_data_teams_gpt.md
│   ├── mlops_deployment_copilot_gpt.md
│   ├── ada_spatial_mapper_gpt.md
│   └── kafka_streaming_analytics_debugger_gpt.md
└── gemini_gems/
    ├── analytics_research_gem.md
    ├── sql_bigquery_review_gem.md
    ├── automation_planner_gem.md
    ├── drive_to_dashboard_spec_generator_gem.md
    ├── meeting_transcript_to_data_ticket_converter_gem.md
    ├── stakeholder_okr_to_analytics_kpi_translator_gem.md
    ├── vendor_evaluation_rfp_analyzer_gem.md
    ├── data_lineage_compliance_mapper_gem.md
    └── automated_data_catalog_documenter_gem.md
```

## Quick Start
1. Clone the repository.
```bash
git clone https://github.com/daniel-st3/ai-analytics-prompt-playbook.git
cd ai-analytics-prompt-playbook
```

2. Open in VS Code.
```bash
code .
```

3. Start with one path based on your goal.
- Need practical prompts: open `prompts/mega_prompt_library.md`
- Need structured Claude behavior: open `claude_skills/`
- Building custom assistants: open `custom_gpts/` or `gemini_gems/`
- Need guided implementation: open `tutorials/`

## Recommended Usage Pattern (Strict Mode)
1. Define objective, data grain, and decision owner.
2. Use model-specific prompt style.
3. Force assumptions + edge-case checks.
4. Validate before publishing or automating.
5. Log prompt, version, and outcome for reproducibility.

## Portfolio and Recruiting Value
This repository demonstrates:
- Applied AI workflow design across modern analytics tools.
- Technical rigor in SQL, ML, orchestration, and governance contexts.
- Communication maturity: structured prompts, explicit tradeoffs, and troubleshooting discipline.

## Contribution Guidelines
1. Keep new prompts and docs original and practical.
2. For new assets, include validation and hallucination controls.
3. Preserve strict-mode structure and model-specific clarity.
4. Prefer small, reviewable pull requests with concrete examples.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
