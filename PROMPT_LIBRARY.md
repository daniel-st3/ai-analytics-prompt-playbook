## How to Use This Prompt Library
This library is built for February 2026 workflows and split by model behavior, not just wording. Use placeholders like `{schema}`, `{sample_rows}`, `{business_goal}`, and `{time_window}` so prompts stay reusable across projects.

| Model | Best fit in this library | Prompting style that works best |
|---|---|---|
| Claude (Claude web / Claude Code) | Structured planning, deep reasoning over long specs, workflow design | Ask for phased outputs, assumptions, and validation checks |
| ChatGPT (o3/o1 family + ADA workflows; legacy 4o wording still seen in some teams) | Python-heavy analysis with uploaded files and fast iteration in Advanced Data Analysis | Ask it to run code, show tables/charts, and export notebook-ready snippets |
| Gemini (Gemini Advanced + Gems) | Long-context analysis with multiple docs/PDFs and Google ecosystem context | Ask it to reference attachments and map claims to source docs |

Use this paste template before any prompt:

```text
Business goal:
Data source:
Schema (DDL):
Sample rows (20-50):
Known constraints:
Decision I need to make:
```

Ask for intermediate reasoning and verification like this:

```text
Before final output, include:
1) Assumptions table
2) Validation plan
3) Edge cases
4) Confidence level (High/Medium/Low) with why
```

> Pro tip: For SQL and BI work, paste both grain and primary keys first. Most AI SQL errors come from unclear table grain.

## Capability References (Checked February 20, 2026)
- Claude Code docs: https://docs.claude.com/en/docs/claude-code/overview
- Claude Projects: https://support.anthropic.com/en/articles/9517075-what-are-projects
- ChatGPT Advanced Data Analysis: https://help.openai.com/en/articles/8437071-advanced-data-analysis-chatgpt-enterprise-version
- Creating Custom GPTs: https://help.openai.com/en/articles/8554397-creating-a-gpt
- ChatGPT model selector: https://help.openai.com/en/articles/7864572-what-is-the-chatgpt-model-selector
- Gemini Gems help: https://support.google.com/gemini/answer/15235603?hl=en
- Gemini model/context update: https://blog.google/technology/google-deepmind/gemini-model-thinking-updates-march-2025/
- n8n npm install docs: https://docs.n8n.io/hosting/installation/npm/

## Data Analytics & BI

### DA-01 Fraud EDA Sprint
Quickly frame EDA for a fraud/chargeback dataset.
```text
Claude: Act as a senior fraud analyst. Using {schema} and {sample_rows}, return an EDA plan, 10 SQL checks, and 5 fraud hypotheses. Ask clarifying questions first if needed.
ChatGPT: Use Advanced Data Analysis on uploaded fraud.csv. Run profiling, missingness, class imbalance, and leakage checks. Return Python cells, charts, and a short findings summary.
Gemini: Use attached CSV + policy PDF + dictionary doc. Build an EDA checklist tied to fraud operations and cite which attachment informed each assumption.
```

### DA-02 Star-Schema SQL Builder
Create SQL for BI metrics from a warehouse model.
```text
Claude: Write ANSI SQL for a star schema with {fact_table} and {dimension_tables}. Include joins, grain checks, and common failure points.
ChatGPT: Generate executable SQL plus a small validation query pack (row counts, duplicates, null tests) for my BI model.
Gemini: Using attached schema docs, generate SQL for daily KPI, MTD, and YoY. Add a short lineage note from source to dashboard.
```

### DA-03 Metrics Layer Spec Draft
Define KPI logic before dashboard build.
```text
Claude: Draft a metrics layer spec for {business_goal}. Include metric name, formula, grain, owner, and caveats.
ChatGPT: Build a metrics dictionary table and sample SQL for each metric. Keep it ready to paste into dbt docs or README.
Gemini: Compare attached KPI notes and propose a consolidated definition set with conflict flags and recommended standard names.
```

### DA-04 Data Quality Test Pack
Create practical tests for analytics tables.
```text
Claude: Create SQL data tests for freshness, uniqueness, nulls, accepted ranges, and referential integrity for {table_list}.
ChatGPT: Generate runnable SQL checks and a simple Python script to summarize pass/fail by table.
Gemini: Use attached schema and quality policy to draft tests and map each test to its business impact.
```

### DA-05 Cohort Retention Analysis Prompt
Build retention logic and interpretation.
```text
Claude: Design cohort SQL for signup-month retention with clear denominator rules and churn interpretation notes.
ChatGPT: Using ADA, compute and visualize retention matrix from uploaded data, then summarize top 3 retention levers.
Gemini: Read attached event schema and define a robust retention approach with edge-case handling for reactivations.
```

### DA-06 Executive Dashboard Narrative
Turn KPI movement into a business story.
```text
Claude: Convert these KPI numbers into an executive narrative with drivers, risks, and next actions.
ChatGPT: Create a one-page KPI brief with chart suggestions and an “if asked by leadership” Q&A section.
Gemini: Use attached monthly reports to write a trend narrative with source-grounded claims.
```

### DA-07 Customer Segmentation SQL
Segment customers using behavior and value.
```text
Claude: Propose segmentation logic for {dataset} and generate SQL to assign segments at customer grain.
ChatGPT: Build a segmentation notebook workflow in ADA and output segment profiles with recommended visuals.
Gemini: Using attached CRM notes, create segmentation definitions aligned to marketing and BI reporting needs.
```

### DA-08 Forecast vs Actual Variance
Diagnose variance in operational reporting.
```text
Claude: Build a variance analysis framework by product/region/channel with likely root-cause categories.
ChatGPT: Run Python analysis on uploaded actual_vs_plan.csv and return waterfall chart + commentary draft.
Gemini: Use attached planning docs and output a variance memo that links numbers to operational context.
```

### DA-09 BI Semantic Model Tuning
Improve dashboard performance and clarity.
```text
Claude: Review this semantic model description and propose relationship, naming, and measure design improvements.
ChatGPT: Generate a checklist to optimize model size, DAX/measure behavior, and refresh strategy.
Gemini: Compare attached dashboard screenshots and propose semantic model fixes with user-impact ranking.
```

### DA-10 KPI Definition Alignment Workshop
Resolve KPI disagreements across teams.
```text
Claude: Facilitate KPI alignment: list decision points, tradeoffs, and a final recommended definition set.
ChatGPT: Create a workshop agenda plus a KPI decision log template.
Gemini: Use attached docs from sales/finance/product and produce a conflict-resolution matrix.
```

## Machine Learning

### ML-01 Baseline Fraud Classifier
Build first-pass models fast.
```text
Claude: Propose a baseline modeling plan (logistic regression, random forest, gradient boosting) with evaluation by business cost.
ChatGPT: In ADA, train baseline models on uploaded data and return ROC-AUC, PR-AUC, confusion matrices, and code.
Gemini: Use attached model requirements and produce a model comparison framework with assumptions and risks.
```

### ML-02 Leakage and Bias Audit
Find hidden modeling risks.
```text
Claude: Audit feature list for leakage and bias risk; classify each as safe, risky, or remove-now.
ChatGPT: Generate Python checks for leakage proxies and subgroup performance diagnostics.
Gemini: Cross-check attached feature docs and policy notes, then return leakage/bias mitigation actions.
```

### ML-03 Feature Engineering Ideas
Generate realistic feature candidates.
```text
Claude: Suggest 20 fraud-relevant features with rationale and implementation notes from {schema}.
ChatGPT: Create feature-engineering code stubs in pandas/sklearn for top candidates.
Gemini: Use attached business process docs to suggest temporal, behavioral, and network features.
```

### ML-04 Hyperparameter Budget Plan
Tune models under constraints.
```text
Claude: Design a tuning strategy under {compute_budget} with early stopping and priority order.
ChatGPT: Provide an Optuna/RandomizedSearch setup script and practical defaults.
Gemini: Use attached infrastructure notes to recommend an efficient tuning plan and expected runtime.
```

### ML-05 Imbalanced Class Strategy
Handle low-positive-rate datasets.
```text
Claude: Recommend class imbalance strategy (weights, sampling, threshold tuning) for fraud detection.
ChatGPT: Produce code comparing class-weighted and resampled approaches with PR-focused metrics.
Gemini: Use attached metric targets and propose imbalance handling aligned to business outcomes.
```

### ML-06 Explainability Brief
Prepare stakeholder-safe explanations.
```text
Claude: Draft a non-technical explanation of model behavior, limits, and safe decision use.
ChatGPT: Generate SHAP analysis code and an interpretation template for business stakeholders.
Gemini: Use attached governance docs to create explainability outputs suitable for review committees.
```

### ML-07 Time-Aware Validation
Avoid temporal leakage in evaluation.
```text
Claude: Define time-based train/validation/test split logic for {date_column} and fraud lag.
ChatGPT: Build split code and evaluation script that preserves event chronology.
Gemini: Use attached lifecycle docs and propose robust temporal validation with backtesting windows.
```

### ML-08 Drift Monitoring Plan
Design post-deployment monitoring.
```text
Claude: Create a drift monitoring blueprint with feature drift, prediction drift, and label delay handling.
ChatGPT: Provide Python examples for PSI/KS drift checks and alert thresholds.
Gemini: Use attached SLA docs to propose a drift dashboard and escalation runbook.
```

### ML-09 Threshold Optimization by Cost
Choose thresholds using business impact.
```text
Claude: Optimize threshold using FN/FP cost assumptions and present scenario analysis.
ChatGPT: Compute threshold sweeps in ADA and output cost curve + recommended operating point.
Gemini: Use attached risk policy and produce threshold recommendations by business segment.
```

### ML-10 Model Card + Experiment Log
Standardize model documentation.
```text
Claude: Draft a model card template tailored to fraud analytics with mandatory and optional fields.
ChatGPT: Generate a Markdown model card and experiment log from provided metrics.
Gemini: Use attached compliance notes to produce documentation ready for team review.
```

## Automation & Agents

### AU-01 n8n Workflow from Plain English
Turn a business request into node-level design.
```text
Claude: Convert this requirement into an n8n workflow with triggers, nodes, error paths, and retry logic.
ChatGPT: Produce a workflow plan plus JSON-ready node configuration checklist.
Gemini: Use attached SOP docs to design an n8n flow aligned to my existing Google stack.
```

### AU-02 Personal Analytics Command Center
Automate daily metric briefings.
```text
Claude: Architect a command-center workflow that ingests data, computes KPIs, and sends an action summary.
ChatGPT: Create implementation steps and test cases for a daily KPI automation pipeline.
Gemini: Use attached calendar/docs/sheets context to define an integrated personal analytics assistant flow.
```

### AU-03 LangGraph Multi-Agent Design
Break a complex task into agent roles.
```text
Claude: Design a LangGraph agent system (planner, analyst, SQL runner, reviewer) with handoff rules.
ChatGPT: Generate pseudo-code for graph nodes, state schema, and guardrails.
Gemini: Use attached architecture docs to propose a scalable multi-agent design with failure handling.
```

### AU-04 ETL-to-Dashboard Refresh Flow
Automate ingestion and reporting.
```text
Claude: Build an automation blueprint from raw source fetch to warehouse load to dashboard refresh notification.
ChatGPT: Provide a task-by-task implementation checklist with validation queries.
Gemini: Use attached data contracts to propose an end-to-end orchestration plan with monitoring points.
```

### AU-05 Anomaly Alert with Human Approval
Avoid noisy automation decisions.
```text
Claude: Design anomaly detection alerts with confidence scoring and manager approval before escalation.
ChatGPT: Create alert logic examples and a response-routing matrix.
Gemini: Use attached incident history to tune alert thresholds and approval workflow rules.
```

### AU-06 Data Dictionary Auto-Builder
Generate docs from schema changes.
```text
Claude: Create a workflow to parse schema metadata and auto-generate a business-friendly data dictionary.
ChatGPT: Write scripts/prompts to produce Markdown dictionary entries per table and field.
Gemini: Use attached schema docs and produce a dictionary workflow with version tracking.
```

### AU-07 Dashboard Incident Triage Agent
Respond when BI breaks.
```text
Claude: Design a triage agent that checks data freshness, broken joins, and failed transformations.
ChatGPT: Create a diagnostic playbook with SQL probes and severity classification.
Gemini: Use attached runbooks to build an incident assistant grounded in prior failures.
```

### AU-08 Meeting Notes to Analytics Backlog
Convert meetings into work items.
```text
Claude: Turn meeting transcript into prioritized analytics tasks with dependencies and estimates.
ChatGPT: Produce a ready-to-paste backlog table with owner, deadline, and acceptance criteria.
Gemini: Use attached docs and transcript to generate a task list linked to strategic goals.
```

### AU-09 Safe Web-to-Dataset Ingestion
Collect external data responsibly.
```text
Claude: Draft a compliant ingestion workflow with source validation, schema checks, and audit trail.
ChatGPT: Provide Python ETL skeleton + data quality gates for new external data sources.
Gemini: Use attached policy docs to design an ingestion pipeline with governance checkpoints.
```

### AU-10 Weekly Learning Automation
Keep skills current without burnout.
```text
Claude: Design a weekly automation that tracks learning goals, project progress, and interview prep.
ChatGPT: Create a lightweight data model and scripts to update weekly learning dashboards.
Gemini: Use attached schedule/docs and generate a personalized learning workflow with reminders.
```

## Career & Portfolio

### CP-01 Portfolio Project Ideator
Generate targeted project ideas from role goals.
```text
Claude: Propose 10 portfolio projects aligned to data analyst/BI roles, ranked by impact and effort.
ChatGPT: Create project briefs with datasets, KPIs, SQL tasks, and dashboard outputs.
Gemini: Use attached job descriptions and produce role-aligned project ideas with skill coverage map.
```

### CP-02 README Rewrite for Recruiters
Improve clarity and impact fast.
```text
Claude: Rewrite this README for recruiter readability: problem, method, results, stack, and next steps.
ChatGPT: Generate a polished README with badges, usage steps, and measurable outcomes.
Gemini: Use attached repo files and craft a concise README grounded in actual project artifacts.
```

### CP-03 Resume Bullet Quantifier
Turn tasks into measurable achievements.
```text
Claude: Convert these raw tasks into STAR-style resume bullets with quantified impact.
ChatGPT: Rewrite bullets with stronger action verbs and analytics outcomes.
Gemini: Use attached CV + project notes to generate role-specific bullet sets.
```

### CP-04 Interview Drill Generator
Practice realistic analyst interviews.
```text
Claude: Create a 45-minute mock interview (SQL, BI, analytics case, communication) with scoring rubric.
ChatGPT: Generate questions plus model answers and common mistakes.
Gemini: Use attached role description and tailor an interview drill with personalized feedback criteria.
```

### CP-05 LinkedIn Project Post Draft
Share projects with professional tone.
```text
Claude: Draft a LinkedIn post about this analytics project with hook, method, result, and CTA.
ChatGPT: Produce 3 post variants (short, medium, storytelling) with suggested visuals.
Gemini: Use attached report + charts to create a grounded post with credibility-friendly language.
```

### CP-06 Targeted Cover Letter
Match one application quickly.
```text
Claude: Write a concise cover letter matching my profile to this job description; keep it specific and evidence-based.
ChatGPT: Generate a tailored letter plus a 6-line version for quick applications.
Gemini: Use attached CV + job post + portfolio links and write a focused, ATS-friendly draft.
```

### CP-07 STAR Story Extractor
Build interview-ready stories.
```text
Claude: Extract 6 STAR stories from my project notes and map each to common interview themes.
ChatGPT: Convert raw notes into polished STAR narratives with concise talking points.
Gemini: Use attached docs and create STAR stories tied to target role competencies.
```

### CP-08 30-60-90 Plan Builder
Show onboarding readiness.
```text
Claude: Build a 30-60-90 day plan for a junior data analyst role with measurable milestones.
ChatGPT: Create a plan table with goals, deliverables, risks, and dependencies.
Gemini: Use attached company context to tailor the 30-60-90 plan to business priorities.
```

### CP-09 Mock Technical Review
Get structured feedback on your project.
```text
Claude: Review this analytics project like a hiring manager; score problem framing, rigor, and communication.
ChatGPT: Produce a rubric-based review and concrete fixes I can ship this week.
Gemini: Use attached repo and docs for a grounded technical review with priority recommendations.
```

### CP-10 Skill-Gap Roadmap from Job Ads
Plan learning with clear priorities.
```text
Claude: Compare my skill profile to these job postings and create a 12-week skill-gap roadmap.
ChatGPT: Build a weekly plan with mini-projects and checkpoints.
Gemini: Use attached job ad set + CV to produce a weighted gap analysis and action plan.
```
