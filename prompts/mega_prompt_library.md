# Mega Prompt Library
Strict-mode prompt system for analytics, BI, ML, automation, and career workflows in 2026.

## Table of Contents
- [How to Use This Prompt Library](#how-to-use-this-prompt-library)
- [Capability References (Checked February 20, 2026)](#capability-references-checked-february-20-2026)
- [Data Analytics & BI](#data-analytics--bi)
  - [DA-01 Fraud EDA Blueprint](#da-01-fraud-eda-blueprint)
  - [DA-02 Star-Schema KPI SQL Pack](#da-02-star-schema-kpi-sql-pack)
  - [DA-03 Metrics Layer Spec Builder](#da-03-metrics-layer-spec-builder)
  - [DA-04 Data Quality Guardrail Suite](#da-04-data-quality-guardrail-suite)
  - [DA-05 Cohort Retention Analyzer](#da-05-cohort-retention-analyzer)
  - [DA-06 Executive KPI Narrative Writer](#da-06-executive-kpi-narrative-writer)
  - [DA-07 Customer Segmentation Builder](#da-07-customer-segmentation-builder)
  - [DA-08 Forecast vs Actual Root-Cause Framework](#da-08-forecast-vs-actual-root-cause-framework)
  - [DA-09 BI Semantic Model Refactor Prompt](#da-09-bi-semantic-model-refactor-prompt)
  - [DA-10 KPI Definition Alignment Facilitator](#da-10-kpi-definition-alignment-facilitator)
- [Machine Learning](#machine-learning)
  - [ML-01 Baseline Fraud Model Accelerator](#ml-01-baseline-fraud-model-accelerator)
  - [ML-02 Leakage and Bias Inspection Engine](#ml-02-leakage-and-bias-inspection-engine)
  - [ML-03 Feature Engineering Strategy Lab](#ml-03-feature-engineering-strategy-lab)
  - [ML-04 Compute-Aware Hyperparameter Plan](#ml-04-compute-aware-hyperparameter-plan)
  - [ML-05 Imbalanced Classification Operating Plan](#ml-05-imbalanced-classification-operating-plan)
  - [ML-06 Explainability Delivery Pack](#ml-06-explainability-delivery-pack)
  - [ML-07 Time-Based Validation Architect](#ml-07-time-based-validation-architect)
  - [ML-08 Drift Monitoring Blueprint](#ml-08-drift-monitoring-blueprint)
  - [ML-09 Threshold Optimization by Business Cost](#ml-09-threshold-optimization-by-business-cost)
  - [ML-10 Model Card and Experiment Log Generator](#ml-10-model-card-and-experiment-log-generator)
- [Automation & Agents](#automation--agents)
  - [AU-01 n8n Workflow Architect (From Plain English)](#au-01-n8n-workflow-architect-from-plain-english)
  - [AU-02 Personal Analytics Command Center](#au-02-personal-analytics-command-center)
  - [AU-03 LangGraph Multi-Agent Blueprint](#au-03-langgraph-multi-agent-blueprint)
  - [AU-04 ETL-to-Dashboard Orchestration Plan](#au-04-etl-to-dashboard-orchestration-plan)
  - [AU-05 Anomaly Alert + Human Approval Flow](#au-05-anomaly-alert--human-approval-flow)
  - [AU-06 Data Dictionary Auto-Documentation Flow](#au-06-data-dictionary-auto-documentation-flow)
  - [AU-07 Dashboard Incident Triage Agent](#au-07-dashboard-incident-triage-agent)
  - [AU-08 Meeting Notes -> Analytics Backlog Generator](#au-08-meeting-notes---analytics-backlog-generator)
  - [AU-09 Safe External Data Ingestion Workflow](#au-09-safe-external-data-ingestion-workflow)
  - [AU-10 Weekly AI Learning & Portfolio Automation](#au-10-weekly-ai-learning--portfolio-automation)
- [Career & Portfolio](#career--portfolio)
  - [CP-01 Portfolio Project Idea Engine](#cp-01-portfolio-project-idea-engine)
  - [CP-02 README Rewriter for Recruiters](#cp-02-readme-rewriter-for-recruiters)
  - [CP-03 Resume Bullet Quantifier](#cp-03-resume-bullet-quantifier)
  - [CP-04 Interview Drill Builder](#cp-04-interview-drill-builder)
  - [CP-05 LinkedIn Project Story Generator](#cp-05-linkedin-project-story-generator)
  - [CP-06 Targeted Cover Letter Composer](#cp-06-targeted-cover-letter-composer)
  - [CP-07 STAR Story Extractor](#cp-07-star-story-extractor)
  - [CP-08 30-60-90 Day Plan Generator](#cp-08-30-60-90-day-plan-generator)
  - [CP-09 Portfolio Technical Review Simulator](#cp-09-portfolio-technical-review-simulator)
  - [CP-10 Skill-Gap Roadmap from Job Postings](#cp-10-skill-gap-roadmap-from-job-postings)

## How to Use This Prompt Library
This version is optimized for practical analytics work in February 2026 and intentionally separates Claude, ChatGPT, and Gemini behavior. Each entry is a **mega-prompt**: copy it, replace placeholders, and run it as a complete workflow rather than a single command.

### Model-specific operating style
| Model | Best use in this library | How to run it well |
|---|---|---|
| Claude (Claude web / Claude Code) | Deep planning, structured reasoning, workflow design | Use XML blocks with clear `<context>`, `<schema>`, `<task>`, `<rules>`, then ask for phased output |
| ChatGPT (o1/o3 + Advanced Data Analysis) | Edge-case reasoning plus code execution in ADA | First use o1/o3 to reason through edge cases, then use ADA to execute validated code |
| Gemini (Gemini Advanced + Gems) | Long-context synthesis with docs and Google ecosystem context | Attach docs/Sheets/PDFs and require explicit source-grounded assumptions |

### Universal paste template
```text
Business goal:
Decision owner:
Data source(s):
Schema DDL:
Sample rows (20-50):
Metric definitions:
Known constraints:
Deadline:
```

### Mandatory verification add-on (append to any prompt)
```text
Before final answer, include:
1) Assumptions table
2) Edge-case table
3) Validation queries/tests
4) Failure modes and mitigation
5) Confidence level with reason
```

> Pro tip: For SQL/BI prompts, always provide table grain and primary key/foreign key assumptions. Missing grain is the #1 cause of wrong KPI output.

## Data Analytics & BI

### DA-01 Fraud EDA Blueprint
Build a complete exploratory analysis plan for transaction fraud.

#### Claude variant (XML-heavy)
```xml
<context>
I am a master's student targeting data analyst/BI roles. I need a portfolio-grade fraud EDA workflow that is practical, auditable, and easy to explain in interviews.
</context>
<schema>
Paste DDL + 20-50 sample rows for: transactions, users, devices, merchants.
</schema>
<task>
Design a high-rigor EDA plan for fraud detection.
Return: profiling checks, class imbalance diagnostics, leakage scan, temporal analysis, and top hypothesis list.
</task>
<rules>
1. Ask up to 5 clarifying questions if grain or target is ambiguous.
2. Separate "must-run" checks from "nice-to-have" checks.
3. For every hypothesis, include SQL/pandas validation method.
4. Highlight likely data quality traps (duplicates, null leakage, target leakage).
5. Keep recommendations realistic for a 45-90 minute sprint.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use a two-phase workflow:
Phase 1 (Reasoning): With o1/o3, reason through edge cases before execution.
- Identify grain risks, leakage risks, late-arriving labels, and denominator pitfalls.
- Produce a concise EDA plan with tests.
Phase 2 (Execution): Move to Advanced Data Analysis and execute code on uploaded fraud.csv.
- Run profiling, missingness map, imbalance stats, temporal patterns, and top feature sanity checks.
- Output notebook-ready Python cells + chart interpretations.
Final output must include: assumptions, validation tests, and "what could be wrong" section.
```

#### Gemini variant
```text
I attached: fraud dataset, data dictionary, and fraud policy PDF.
Create a source-grounded EDA workflow.
Requirements:
- Build a checklist with priority (critical/high/medium).
- Tie each assumption to a source file.
- Propose 5 analyst actions based on likely fraud patterns.
- Include one section: "If labels are delayed, how conclusions change."
Return output as: Executive summary, technical checklist, and next 7-day action plan.
```

### DA-02 Star-Schema KPI SQL Pack
Generate robust SQL for KPI reporting in a star schema.

#### Claude variant (XML-heavy)
```xml
<context>
I am building BI metrics from a warehouse star schema and need SQL that survives business review.
</context>
<schema>
Paste fact and dimension DDL, including key constraints and expected grain.
</schema>
<task>
Create SQL for: daily revenue, conversion rate, refund rate, and active customers.
</task>
<rules>
1. State assumed grain before writing SQL.
2. Provide ANSI SQL first; note dialect-specific adjustments if needed.
3. Add validation queries for duplicates, join explosion, and null join keys.
4. Provide an "audit SQL pack" section.
5. End with a table of common failure modes.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 (o1/o3): reason through edge cases before execution.
- Evaluate grain mismatch, SCD behavior, and denominator definitions.
- Draft SQL strategy and validation checklist.
Phase 2 (ADA): generate executable SQL and optional Python-based query-test scaffolding.
Deliverables:
1) KPI SQL queries
2) Validation SQL pack (row counts, uniqueness, null joins)
3) Short notes for BI README
If ambiguity exists, stop and ask clarifying questions before producing final SQL.
```

#### Gemini variant
```text
Use attached schema docs and KPI definitions to produce a production-minded SQL pack.
Requirements:
- Reconcile conflicting metric definitions across docs.
- Provide final standardized SQL + rationale.
- Include a data lineage note from source -> warehouse -> dashboard.
- Add a "review checklist" that analysts can paste into PRs.
```

### DA-03 Metrics Layer Spec Builder
Draft a reusable metrics contract for BI teams.

#### Claude variant (XML-heavy)
```xml
<context>
I need a metrics layer specification that avoids KPI confusion across teams.
</context>
<schema>
Paste tables, dimensions, and current KPI definitions.
</schema>
<task>
Produce a metrics layer spec including formula, grain, owner, update cadence, and caveats.
</task>
<rules>
1. Flag conflicting definitions explicitly.
2. Provide one recommended canonical definition per KPI.
3. Include SQL pseudocode and test criteria.
4. Add "business interpretation guidance" for non-technical users.
5. Keep format suitable for docs and onboarding.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution:
- denominator ambiguity, late data, filtered populations, and segment leakage.
Then, in ADA, generate a metrics dictionary table and SQL skeletons.
Output must include:
- Canonical metric contract table
- Validation tests
- "When not to use this metric" notes
- Markdown export ready for GitHub README/docs
```

#### Gemini variant
```text
Using attached KPI docs, meeting notes, and data model files:
- Build a consolidated metrics contract.
- Map each metric to source documents.
- Highlight unresolved conflicts and recommended tie-break decisions.
- Add an adoption plan for analysts and dashboard owners.
```

### DA-04 Data Quality Guardrail Suite
Create data quality checks for analytics pipelines.

#### Claude variant (XML-heavy)
```xml
<context>
I want a practical quality suite for analytics tables powering BI and ML.
</context>
<schema>
Paste critical tables with PK/FK assumptions and freshness expectations.
</schema>
<task>
Design SQL tests: freshness, uniqueness, null thresholds, accepted ranges, and referential integrity.
</task>
<rules>
1. Prioritize tests by business impact.
2. Provide fail conditions and severity levels.
3. Include "false alarm" handling guidance.
4. Add one weekly quality review routine.
5. Format for easy conversion to dbt tests.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify likely silent failures (join drift, category explosion, timezone misalignment).
Then, in ADA, generate:
- SQL quality checks
- A Python summary script for pass/fail dashboard output
- Alert threshold recommendations
Include a section: "How to debug if this test fails suddenly."
```

#### Gemini variant
```text
Given attached schema docs and quality policy:
- Generate a data quality framework with severity labels.
- Link tests to business consequences.
- Produce a handoff-ready checklist for analysts.
- Include a lightweight incident-response runbook.
```

### DA-05 Cohort Retention Analyzer
Design retention logic with clear denominators.

#### Claude variant (XML-heavy)
```xml
<context>
I need a cohort retention analysis that is interview-ready and business-usable.
</context>
<schema>
Paste user events schema, signup table, and activity definitions.
</schema>
<task>
Create retention logic for monthly cohorts, including reactivation handling.
</task>
<rules>
1. Define cohort assignment rules explicitly.
2. Explain denominator choices and alternatives.
3. Provide SQL and validation checks.
4. Include interpretation notes for product and BI stakeholders.
5. Add pitfalls (seasonality, partial periods, late events).
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 (o1/o3): reason through edge cases before execution.
- cohort assignment ambiguity
- reactivation users
- partial month bias
Phase 2 (ADA): compute retention matrix and visualize trends.
Return:
1) SQL or Python logic
2) retention heatmap workflow
3) interpretation notes
4) edge-case checklist for QA
```

#### Gemini variant
```text
Using attached event dictionary + KPI docs:
- Propose a standardized retention framework.
- Generate source-grounded assumptions.
- Add cross-team interpretation notes (product, marketing, finance).
- Include a "decision-ready" summary for weekly review.
```

### DA-06 Executive KPI Narrative Writer
Translate KPI changes into clear business action.

#### Claude variant (XML-heavy)
```xml
<context>
I need an executive-ready KPI narrative from latest metrics and anomalies.
</context>
<schema>
Paste KPI table, prior period data, and segment breakdowns.
</schema>
<task>
Write a concise narrative: what changed, likely drivers, risks, and actions.
</task>
<rules>
1. Distinguish fact vs inference.
2. Quantify impact in absolute and percentage terms.
3. Include confidence level per claim.
4. Suggest 3 follow-up analyses.
5. Keep tone clear and recruiter-friendly.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
- Check metric comparability across periods.
- Detect anomalies that might be data quality artifacts.
Then use ADA to produce supporting tables/charts.
Output:
- One-page exec brief
- Technical appendix with checks
- Suggested Q&A for leadership meeting
```

#### Gemini variant
```text
Using attached monthly reports and dashboard exports:
- Build an executive narrative grounded in source files.
- Mark each claim as confirmed/probable/needs-validation.
- Provide action recommendations by urgency.
- Add a "what changed since last report" section.
```

### DA-07 Customer Segmentation Builder
Develop business-usable segmentation definitions.

#### Claude variant (XML-heavy)
```xml
<context>
I need segmentation logic for BI and campaign targeting.
</context>
<schema>
Paste customer, transaction, and engagement tables.
</schema>
<task>
Propose segment definitions and SQL assignment logic.
</task>
<rules>
1. Keep segments mutually exclusive if possible.
2. Include rationale tied to business value.
3. Provide validation tests for stability over time.
4. Add recommended visuals for dashboarding.
5. End with "how to operationalize in n8n/CRM" notes.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1: with o1/o3, reason through edge cases before execution.
- cold-start users, sparse history, seasonality, high-spend outliers.
Phase 2: with ADA, build segmentation analysis and profile summaries.
Deliverables:
- segmentation rules
- assignment code
- segment KPI table
- caveats and monitoring plan
```

#### Gemini variant
```text
Use attached CRM strategy docs and datasets.
Create segmentation definitions that align with documented goals.
Include:
- source-grounded assumptions
- activation strategy per segment
- governance notes for periodic refresh
```

### DA-08 Forecast vs Actual Root-Cause Framework
Analyze plan variance in operational reporting.

#### Claude variant (XML-heavy)
```xml
<context>
I need a repeatable framework to explain forecast vs actual variance.
</context>
<schema>
Paste plan table, actuals table, and dimension hierarchy.
</schema>
<task>
Create variance decomposition logic by product, region, and channel.
</task>
<rules>
1. Separate volume vs mix vs price effects where possible.
2. Include SQL/pandas method for each decomposition.
3. Provide a narrative template for leadership updates.
4. Include risk flags for unreliable segments.
5. Add actions for next planning cycle.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution:
- currency effects, late postings, hierarchy mapping drift.
Then run ADA to compute decomposition tables and visuals.
Return:
- variance waterfall logic
- top driver table
- reliability checks
- decision memo draft
```

#### Gemini variant
```text
Given attached planning notes and financial docs:
- Build a source-grounded variance framework.
- Reconcile dimension definitions across files.
- Provide weekly operating review format.
```

### DA-09 BI Semantic Model Refactor Prompt
Tune BI model relationships and metric behavior.

#### Claude variant (XML-heavy)
```xml
<context>
I need to improve a BI semantic model that is slow and confusing.
</context>
<schema>
Paste model relationships, table list, and current KPI measures.
</schema>
<task>
Diagnose model issues and propose a refactor plan.
</task>
<rules>
1. Identify cardinality and filter-direction risks.
2. Highlight ambiguous relationships.
3. Suggest naming and measure standardization.
4. Provide rollout plan with regression checks.
5. Keep recommendations tool-agnostic where possible.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Check relationship ambiguity, many-to-many risks, and measure filter context pitfalls.
Then provide implementation checklist and sample validation scripts/tables.
Output must include:
- prioritized fixes
- regression test checklist
- stakeholder communication notes
```

#### Gemini variant
```text
Use attached model screenshots/docs and produce a refactor plan.
Requirements:
- map issues to source artifacts
- rank fixes by effort/impact
- provide "safe rollout" steps for BI consumers
```

### DA-10 KPI Definition Alignment Facilitator
Resolve cross-team KPI disputes.

#### Claude variant (XML-heavy)
```xml
<context>
Multiple teams disagree on KPI definitions; I need a decision-ready alignment framework.
</context>
<schema>
Paste current KPI definitions from each team + sample queries.
</schema>
<task>
Create a facilitated decision framework and final recommendation set.
</task>
<rules>
1. Build a conflict matrix with root causes.
2. Propose canonical definitions with tradeoff notes.
3. Include governance process for future KPI changes.
4. Provide a workshop agenda + decision log template.
5. Keep language accessible for technical and business stakeholders.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify hidden definition conflicts (scope, denominator, exclusion rules, timezone).
Then create:
- KPI alignment workshop plan
- canonical metric table
- SQL validation snippets
- communication memo for rollout
```

#### Gemini variant
```text
Use attached finance, product, and sales docs to build a source-grounded KPI alignment pack.
Include:
- decision matrix
- unresolved risks
- phased adoption plan
- stakeholder-specific talking points
```

## Machine Learning

### ML-01 Baseline Fraud Model Accelerator
Create a baseline model suite with business-aware evaluation.

#### Claude variant (XML-heavy)
```xml
<context>
I need a baseline fraud modeling workflow I can explain clearly in interviews and portfolio docs.
</context>
<schema>
Paste feature list, target definition, class ratio, and temporal coverage.
</schema>
<task>
Design baseline experiments for logistic regression, random forest, and gradient boosting.
</task>
<rules>
1. Recommend split strategy with temporal leakage protection.
2. Define evaluation metrics tied to business cost.
3. Include threshold tuning approach.
4. Provide error analysis plan by key segments.
5. Include "minimum viable model card" fields.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use two phases:
Phase 1 (o1/o3): reason through edge cases before execution.
- leakage, target lag, extreme imbalance, overfitting traps.
Phase 2 (ADA): execute Python code for three baseline models.
Return:
- training/evaluation code
- ROC-AUC and PR-AUC comparison
- threshold sweep by business cost
- concise recommendation and caveats
```

#### Gemini variant
```text
Using attached modeling notes, policy docs, and dataset summary:
- Build a baseline experiment plan with explicit assumptions.
- Ground recommendations in attached evidence.
- Provide a stakeholder-ready model comparison table.
```

### ML-02 Leakage and Bias Inspection Engine
Audit features before model training.

#### Claude variant (XML-heavy)
```xml
<context>
I need a strict pre-model audit for leakage and bias risk in fraud features.
</context>
<schema>
Paste feature dictionary, generation timing, and sensitive attribute proxies.
</schema>
<task>
Classify each feature: safe, risky, or remove.
</task>
<rules>
1. Explain leakage mechanism for every risky feature.
2. Add fairness/bias audit suggestions by subgroup.
3. Recommend mitigations and monitoring checks.
4. Provide a go/no-go checklist before training.
5. Keep language practical for junior analysts.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First, with o1/o3, reason through edge cases before execution.
- temporal leakage
- proxy discrimination
- post-outcome features
Then in ADA, generate code to test leakage and subgroup performance gaps.
Output must include:
- risk matrix
- automated checks
- remediation plan
```

#### Gemini variant
```text
Use attached governance policy + feature docs.
Create a source-grounded leakage/bias audit framework with:
- feature risk ratings
- mitigation actions
- review cadence and owners
```

### ML-03 Feature Engineering Strategy Lab
Generate portfolio-grade feature ideas with implementation detail.

#### Claude variant (XML-heavy)
```xml
<context>
I want feature engineering ideas that are realistic for fraud analytics and explainable to recruiters.
</context>
<schema>
Paste transaction, user behavior, device, and merchant features currently available.
</schema>
<task>
Propose 25 candidate features with rationale and implementation notes.
</task>
<rules>
1. Group features by temporal, behavioral, and network categories.
2. Include leakage risk level for each feature.
3. Provide SQL/pandas sketch for top 10 features.
4. Rank by expected impact vs implementation complexity.
5. Add monitoring suggestions for feature drift.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 (o1/o3): reason through edge cases before execution.
Identify sparse history, cold-start, and temporal-window pitfalls.
Phase 2 (ADA): generate feature engineering code prototypes.
Deliverables:
- prioritized feature backlog
- code snippets
- evaluation plan to isolate feature lift
- caution notes for leakage and overfitting
```

#### Gemini variant
```text
Using attached process docs and schema references, design a feature strategy.
Requirements:
- tie each feature family to a business fraud mechanism
- identify data dependencies
- provide staged rollout plan
```

### ML-04 Compute-Aware Hyperparameter Plan
Tune under tight compute/time budgets.

#### Claude variant (XML-heavy)
```xml
<context>
I have limited compute and need an efficient tuning plan for baseline fraud models.
</context>
<schema>
Paste dataset size, feature count, model candidates, and compute constraints.
</schema>
<task>
Design a budget-aware tuning strategy.
</task>
<rules>
1. Define tuning priority by model and parameter sensitivity.
2. Include early stopping and pruning rules.
3. Provide expected runtime bands.
4. Add fallback strategy if tuning budget is exhausted.
5. Include reproducibility checklist.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then in ADA, generate tuning scripts (Optuna/RandomizedSearch) with practical defaults.
Required outputs:
- staged tuning plan
- code templates
- resource-saving techniques
- decision rule for selecting final model
```

#### Gemini variant
```text
Given attached infrastructure and SLA notes:
- recommend compute-efficient tuning strategy
- include reliability guardrails
- provide reporting format for experiment tracking
```

### ML-05 Imbalanced Classification Operating Plan
Handle low base-rate fraud safely.

#### Claude variant (XML-heavy)
```xml
<context>
My fraud positive rate is low; I need a strategy balancing detection and false alerts.
</context>
<schema>
Paste class distribution, review capacity, and false positive/false negative cost assumptions.
</schema>
<task>
Create an imbalanced-class strategy with threshold policy.
</task>
<rules>
1. Compare class weights, sampling, and threshold optimization.
2. Tie recommendations to operational capacity.
3. Include evaluation metrics beyond ROC-AUC.
4. Add post-deployment monitoring requirements.
5. Provide "what to communicate to stakeholders" summary.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Then use ADA to test weighted and resampled pipelines.
Return:
- comparison table (precision, recall, PR-AUC, cost estimate)
- threshold policy options
- alert volume simulation
- practical recommendation with caveats
```

#### Gemini variant
```text
Use attached risk policy and ops constraints to produce a source-grounded imbalanced-class plan.
Include:
- threshold governance
- escalation strategy
- monthly calibration routine
```

### ML-06 Explainability Delivery Pack
Prepare explainability outputs for non-technical stakeholders.

#### Claude variant (XML-heavy)
```xml
<context>
I need explainability content that is technically honest and business-readable.
</context>
<schema>
Paste model type, top features, and performance summary.
</schema>
<task>
Create explainability materials for operations and management.
</task>
<rules>
1. Separate global vs local explanations.
2. Include limitations and uncertainty communication.
3. Provide sample stakeholder Q&A.
4. Suggest one visual and one table per audience.
5. Avoid overclaiming model certainty.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 to reason through edge cases before execution.
Then in ADA, generate SHAP/permutation importance workflow and concise interpretation outputs.
Deliver:
- explainability notebook cells
- stakeholder brief
- misinterpretation warning list
```

#### Gemini variant
```text
Using attached governance docs and model summary:
- build a source-grounded explainability pack
- include approvals-ready language
- add recommended review checkpoints
```

### ML-07 Time-Based Validation Architect
Design leak-resistant temporal validation.

#### Claude variant (XML-heavy)
```xml
<context>
My data is temporal; I need validation that reflects real deployment behavior.
</context>
<schema>
Paste date fields, label latency, and event processing lag assumptions.
</schema>
<task>
Define train/validation/test strategy with backtesting windows.
</task>
<rules>
1. Prevent temporal leakage explicitly.
2. Include rolling-window and holdout alternatives.
3. Add performance stability checks over time.
4. Provide clear split pseudocode.
5. Explain tradeoffs for small datasets.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1: o1/o3 reasons through edge cases before execution.
Phase 2: ADA produces split code and temporal backtest scripts.
Include:
- leakage prevention checks
- drift-aware evaluation summary
- decision guidance if performance degrades over time
```

#### Gemini variant
```text
Use attached lifecycle docs and dataset notes.
Create a source-grounded validation framework with:
- split logic
- review cadence
- model refresh triggers
```

### ML-08 Drift Monitoring Blueprint
Define monitoring for post-launch model health.

#### Claude variant (XML-heavy)
```xml
<context>
I need a realistic monitoring plan for fraud model drift and delayed labels.
</context>
<schema>
Paste deployed feature list, prediction volume, and current alert thresholds.
</schema>
<task>
Design drift monitoring and response workflow.
</task>
<rules>
1. Include feature, prediction, and outcome drift checks.
2. Define threshold levels (warning/critical).
3. Add action playbook per drift type.
4. Include false alarm mitigation guidance.
5. Provide minimal dashboard spec.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 to reason through edge cases before execution.
Then in ADA, generate code templates for drift metrics (PSI/KS and trend checks).
Output must include:
- monitoring KPIs
- alert logic
- escalation matrix
- retraining decision rule
```

#### Gemini variant
```text
Using attached SLA docs and incident history, produce a source-grounded drift monitoring plan.
Include weekly and monthly review routines and ownership mapping.
```

### ML-09 Threshold Optimization by Business Cost
Select operating threshold using cost-sensitive analysis.

#### Claude variant (XML-heavy)
```xml
<context>
I need a threshold policy that balances fraud capture and customer friction.
</context>
<schema>
Paste predicted probabilities, labels, and FN/FP cost assumptions by segment.
</schema>
<task>
Generate threshold recommendations with scenario analysis.
</task>
<rules>
1. Provide at least 3 policy options (conservative, balanced, aggressive).
2. Simulate operational volume impact.
3. Include segment-specific threshold considerations.
4. State assumptions transparently.
5. End with recommendation + monitoring plan.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First with o1/o3, reason through edge cases before execution.
Then use ADA to compute threshold sweep, cost curves, and capacity impact.
Return:
- threshold decision table
- cost and workload simulation
- recommended policy + rollback trigger
```

#### Gemini variant
```text
Using attached policy docs and capacity constraints:
- create a source-grounded threshold framework
- include segment-level adaptations
- provide governance notes for periodic re-tuning
```

### ML-10 Model Card and Experiment Log Generator
Document models for review and reproducibility.

#### Claude variant (XML-heavy)
```xml
<context>
I need standardized model documentation for portfolio, team review, and future maintenance.
</context>
<schema>
Paste model metadata, dataset details, metrics, and known limitations.
</schema>
<task>
Produce a complete model card and experiment log template.
</task>
<rules>
1. Include intended use and out-of-scope use.
2. Add ethics, bias, and monitoring sections.
3. Provide required vs optional fields.
4. Keep wording concise and auditable.
5. Include change-history format.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then in ADA, structure a model card and experiment log from provided metrics/results.
Deliverables:
- Markdown model card
- experiment registry table
- review checklist before deployment/demo
```

#### Gemini variant
```text
Using attached governance templates and model artifacts:
- produce source-grounded model documentation
- highlight missing fields
- provide a completion checklist for audit readiness
```

## Automation & Agents

### AU-01 n8n Workflow Architect (From Plain English)
Turn a business request into a node-level n8n design.

#### Claude variant (XML-heavy)
```xml
<context>
I am building practical analytics automations with n8n and need robust workflow architecture.
</context>
<schema>
Paste trigger source, sample payloads, destination system, and SLA requirements.
</schema>
<task>
Design a node-by-node n8n workflow including error paths and retries.
</task>
<rules>
1. Define data contract at each node.
2. Include idempotency strategy.
3. Add dead-letter handling for repeated failures.
4. Mark human-approval checkpoints.
5. Provide MVP and hardening roadmap.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify duplicate triggers, malformed payloads, and downstream rate limits.
Then provide implementation details:
- node sequence
- field mappings
- test payloads
- validation checklist
If useful, generate helper scripts in ADA for payload simulation.
```

#### Gemini variant
```text
Using attached SOP docs and payload samples:
- produce source-grounded n8n architecture
- include Google ecosystem integration notes where relevant
- provide runbook for failures and manual recovery
```

### AU-02 Personal Analytics Command Center
Automate daily KPI briefing with actionable output.

#### Claude variant (XML-heavy)
```xml
<context>
I want a personal analytics command center that summarizes daily performance and recommends next actions.
</context>
<schema>
Paste KPI definitions, data sources, scheduling constraints, and destination channel.
</schema>
<task>
Design an n8n workflow for daily KPI ingestion, calculation, anomaly detection, and summary delivery.
</task>
<rules>
1. Keep v1 limited to 3-5 critical KPIs.
2. Include anomaly threshold logic and confidence labeling.
3. Add fail-safe path when source data is incomplete.
4. Provide output template for short action brief.
5. Include weekly review and threshold tuning routine.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 (o1/o3): reason through edge cases before execution.
- missing data windows
- stale sources
- false anomaly spikes
Phase 2: produce node-level implementation checklist and optional ADA helper code for KPI calculations.
Output:
- workflow blueprint
- alert policy table
- daily summary prompt template
- test matrix
```

#### Gemini variant
```text
Use attached KPI docs and Google Sheets/Docs examples to build a source-grounded command center design.
Include:
- ingestion plan
- summary format
- governance checks
- escalation policy
```

### AU-03 LangGraph Multi-Agent Blueprint
Break complex analytics task into specialized agents.

#### Claude variant (XML-heavy)
```xml
<context>
I need a multi-agent workflow for analytics tasks using LangChain/LangGraph.
</context>
<schema>
Paste target workflow, tools available, and constraints on latency/cost.
</schema>
<task>
Design agent roles, state schema, routing logic, and review gates.
</task>
<rules>
1. Define planner, analyst, executor, and reviewer responsibilities.
2. Specify state handoff contract between nodes.
3. Add guardrails against tool misuse and infinite loops.
4. Include failure recovery strategy.
5. Provide minimal viable graph first, then expansion plan.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Then provide LangGraph pseudo-code and state definitions.
Required output:
- agent role table
- graph transitions
- quality control rules
- cost/latency optimization notes
Use ADA only when code simulation or quick data tests are needed.
```

#### Gemini variant
```text
Using attached architecture docs and project constraints, create a source-grounded multi-agent design.
Include:
- role separation
- escalation/human intervention rules
- observability plan
```

### AU-04 ETL-to-Dashboard Orchestration Plan
Automate ingestion to reporting refresh.

#### Claude variant (XML-heavy)
```xml
<context>
I need an orchestration workflow from raw source ingestion to dashboard refresh notification.
</context>
<schema>
Paste source systems, transformation steps, warehouse target, and BI refresh dependencies.
</schema>
<task>
Design end-to-end orchestration with monitoring and rollback paths.
</task>
<rules>
1. Include checkpoint validation between stages.
2. Add schema-change detection and fallback logic.
3. Define success/failure alerting rules.
4. Include data quality gates before refresh.
5. Provide production hardening checklist.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then produce orchestration checklist, SQL validation pack, and testing plan.
If needed, use ADA to generate helper scripts for reconciliation reports.
Final output must include a rollback procedure and incident logging format.
```

#### Gemini variant
```text
Using attached data contracts and dashboard dependencies:
- build a source-grounded orchestration blueprint
- include dependency map
- provide runbook for delayed or failed refresh cycles
```

### AU-05 Anomaly Alert + Human Approval Flow
Design low-noise alerts with review gate.

#### Claude variant (XML-heavy)
```xml
<context>
I need anomaly alerting that avoids noise and includes human approval before escalation.
</context>
<schema>
Paste metrics, baseline period, threshold policy, and communication channel.
</schema>
<task>
Create alert workflow with confidence scoring and approval logic.
</task>
<rules>
1. Define anomaly detection method and confidence score.
2. Add suppression rules for noisy periods.
3. Include human approval step before external escalation.
4. Provide post-alert feedback loop for threshold tuning.
5. Include KPI to measure alert quality.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First, with o1/o3, reason through edge cases before execution.
Focus on seasonal spikes, missing denominators, and bad baselines.
Then produce:
- alert decision matrix
- implementation checklist
- optional ADA script for baseline calculation
- false-positive reduction plan
```

#### Gemini variant
```text
Use attached incident logs and policy docs.
Create a source-grounded anomaly + approval workflow with:
- confidence tiers
- escalation paths
- reviewer instructions
```

### AU-06 Data Dictionary Auto-Documentation Flow
Generate analytics dictionary as schema evolves.

#### Claude variant (XML-heavy)
```xml
<context>
I need an automated workflow that keeps data dictionary docs current as schema changes.
</context>
<schema>
Paste metadata sources (information_schema/API), current naming conventions, and doc format requirements.
</schema>
<task>
Design automation to generate/update dictionary entries and changelog notes.
</task>
<rules>
1. Include field-level business description generation rules.
2. Add confidence tag when description is inferred.
3. Create review queue for ambiguous fields.
4. Include versioning and approval flow.
5. Provide output format suitable for GitHub docs.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then provide scripts/prompts that:
- parse schema metadata
- create/update markdown docs
- flag uncertain definitions for manual review
Use ADA for sample transformation scripts if needed.
```

#### Gemini variant
```text
Using attached schema docs and naming standards, design a source-grounded dictionary automation.
Include integration ideas for Google Docs/Sheets where teams collaborate on definitions.
```

### AU-07 Dashboard Incident Triage Agent
Respond quickly when BI dashboards break.

#### Claude variant (XML-heavy)
```xml
<context>
I need an incident triage agent for broken dashboards and suspicious KPI jumps.
</context>
<schema>
Paste critical dashboards, upstream tables, freshness SLAs, and known failure patterns.
</schema>
<task>
Design triage workflow: detect issue, diagnose likely root cause, and route response.
</task>
<rules>
1. Prioritize checks: freshness, schema drift, join explosion, filter logic break.
2. Include severity classification and owner routing.
3. Provide incident summary template.
4. Add post-mortem checklist.
5. Keep response steps executable within 15-30 minutes.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then generate:
- SQL triage probes
- severity rubric
- communication templates
- optional ADA notebook for rapid diagnostics
Include "first 10 minutes" response sequence.
```

#### Gemini variant
```text
Using attached runbooks and outage history:
- produce source-grounded incident triage assistant design
- include quick diagnosis map and escalation tree
- recommend metrics to track incident reduction
```

### AU-08 Meeting Notes -> Analytics Backlog Generator
Convert meetings into actionable analytics tasks.

#### Claude variant (XML-heavy)
```xml
<context>
I need to convert meeting transcripts into a prioritized analytics execution backlog.
</context>
<schema>
Paste transcript, project context, and team capacity constraints.
</schema>
<task>
Extract tasks, dependencies, owners, effort estimates, and acceptance criteria.
</task>
<rules>
1. Separate decisions, requests, and open questions.
2. Prioritize tasks by business impact and urgency.
3. Flag ambiguous requirements for follow-up.
4. Output in backlog table format.
5. Include weekly planning recommendations.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 with o1/o3: reason through edge cases before execution.
- ambiguous ownership
- conflicting deadlines
- unclear success criteria
Phase 2: generate backlog table and optionally ADA script to parse structured notes.
Return a final backlog with priorities and dependencies.
```

#### Gemini variant
```text
Using attached transcripts + project docs:
- create source-grounded analytics backlog
- map each task to original evidence
- add a review section for unresolved assumptions
```

### AU-09 Safe External Data Ingestion Workflow
Ingest web/external data with governance checks.

#### Claude variant (XML-heavy)
```xml
<context>
I need to ingest external data safely into analytics workflows without compromising quality or compliance.
</context>
<schema>
Paste source types, expected schema, update frequency, and governance constraints.
</schema>
<task>
Design ingestion workflow with validation, auditing, and rollback.
</task>
<rules>
1. Define source trust scoring criteria.
2. Add schema validation and anomaly thresholds.
3. Include audit log requirements.
4. Provide quarantine path for suspicious records.
5. Include compliance review checkpoints.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then produce ETL skeleton + quality gates and optional ADA checks for sampling/validation.
Output must include:
- ingestion flow
- quality control checklist
- rollback plan
- compliance warning list
```

#### Gemini variant
```text
Using attached governance and source documentation:
- produce source-grounded ingestion architecture
- include policy alignment table
- suggest monitoring KPIs for source reliability
```

### AU-10 Weekly AI Learning & Portfolio Automation
Automate personal growth tracking with outcomes.

#### Claude variant (XML-heavy)
```xml
<context>
I want a weekly automation that tracks learning goals, project progress, and application readiness.
</context>
<schema>
Paste current goals, available time, project list, and target roles.
</schema>
<task>
Design a weekly workflow that collects progress, updates dashboards, and suggests next actions.
</task>
<rules>
1. Keep process lightweight (<60 minutes/week maintenance).
2. Include objective progress metrics.
3. Add reminders for portfolio and interview prep tasks.
4. Provide one weekly review template.
5. Include anti-burnout constraints.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First with o1/o3, reason through edge cases before execution.
Then generate automation plan, progress schema, and optional ADA scripts for weekly status summaries.
Deliverables:
- weekly data model
- KPI definitions
- update workflow
- actionable recommendations
```

#### Gemini variant
```text
Use attached calendar, notes, and project docs to create a source-grounded weekly automation plan.
Include optional integration ideas for Google Docs/Sheets trackers.
```

## Career & Portfolio

### CP-01 Portfolio Project Idea Engine
Generate role-targeted analytics projects with execution detail.

#### Claude variant (XML-heavy)
```xml
<context>
I am a master's student targeting data analyst/BI/analytics engineer roles and need portfolio projects with strong hiring signal.
</context>
<schema>
Paste target role descriptions, current skills, and available weekly time.
</schema>
<task>
Generate 10 project ideas with business problem, dataset, methods, expected outputs, and timeline.
</task>
<rules>
1. Rank ideas by portfolio impact vs effort.
2. Include one KPI-focused dashboard project, one ML project, and one automation project.
3. Provide interview talking points for each idea.
4. Include "what recruiters will notice" notes.
5. Keep scope realistic for student schedule.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify over-scoped project risks and missing skill-coverage gaps.
Then produce a portfolio project roadmap with:
- project briefs
- deliverables
- dataset options
- weekly milestones
If needed, generate simple planning tables in ADA.
```

#### Gemini variant
```text
Using attached job descriptions and current portfolio notes:
- generate source-grounded project ideas
- map each idea to required role competencies
- include prioritization for fastest signal to recruiters
```

### CP-02 README Rewriter for Recruiters
Turn technical project notes into high-clarity README.

#### Claude variant (XML-heavy)
```xml
<context>
I need a recruiter-friendly README that still satisfies technical reviewers.
</context>
<schema>
Paste raw project notes, repo tree, metrics, and screenshots list.
</schema>
<task>
Rewrite README with clear problem, method, results, reproducibility, and next steps.
</task>
<rules>
1. Keep claims evidence-based.
2. Add 60-second skim section at top.
3. Include setup/run instructions.
4. Add limitations and improvement roadmap.
5. Include 3 interview-ready talking points.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Check for missing evidence, inflated claims, and unclear outcomes.
Then generate a polished README draft with:
- concise narrative
- reproducible setup
- metrics table
- impact summary
Use ADA only for formatting tables/charts when needed.
```

#### Gemini variant
```text
Using attached notebook outputs, report PDF, and repo files:
- draft a source-grounded README
- map each key claim to available artifact
- provide an honesty check section for weak evidence
```

### CP-03 Resume Bullet Quantifier
Convert raw task lists into impact-oriented bullets.

#### Claude variant (XML-heavy)
```xml
<context>
I need stronger resume bullets for data analyst and BI roles.
</context>
<schema>
Paste current bullets, project outcomes, metrics, and job target.
</schema>
<task>
Rewrite bullets using action + method + measurable result format.
</task>
<rules>
1. Avoid generic verbs and vague claims.
2. Quantify impact where evidence exists.
3. Provide alternatives when no numeric impact is available.
4. Tailor bullets for data analyst and BI analyst variants.
5. Keep each bullet concise and ATS-friendly.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify weak claims and missing quantification opportunities.
Then produce bullet sets for:
- Data Analyst applications
- BI Analyst applications
- Analytics Engineer applications
Include one evidence-note per bullet to maintain credibility.
```

#### Gemini variant
```text
Using attached CV, project notes, and job ads:
- create source-grounded bullet rewrites
- map bullets to target role competencies
- flag bullets that need stronger evidence
```

### CP-04 Interview Drill Builder
Create realistic analytics interview practice sessions.

#### Claude variant (XML-heavy)
```xml
<context>
I need a structured mock interview for analytics roles (SQL, BI, case thinking, communication).
</context>
<schema>
Paste target role description and my current strengths/weaknesses.
</schema>
<task>
Generate a 45-minute interview drill with scoring rubric and feedback guide.
</task>
<rules>
1. Include SQL challenge, KPI interpretation, and stakeholder communication question.
2. Provide ideal answer frameworks.
3. Add common mistakes and recovery tips.
4. Include calibration scale (junior-ready to strong-hire).
5. End with 2-week improvement plan.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Then generate a complete mock interview pack:
- timed question sequence
- scoring rubric
- model answers
- follow-up drills for weak areas
Use ADA optionally to auto-score structured responses.
```

#### Gemini variant
```text
Use attached role descriptions and my project artifacts.
Produce a source-grounded interview drill with role-specific feedback criteria.
Include a post-drill debrief template.
```

### CP-05 LinkedIn Project Story Generator
Create concise, credible project posts.

#### Claude variant (XML-heavy)
```xml
<context>
I want to publish portfolio projects on LinkedIn with a clear value narrative.
</context>
<schema>
Paste project summary, key metric improvement, and chart screenshot notes.
</schema>
<task>
Write 3 LinkedIn post variants (short, medium, storytelling) with CTA.
</task>
<rules>
1. Keep claims factual and evidence-based.
2. Avoid hype language.
3. Mention tools only when relevant to outcome.
4. Add one learning takeaway per variant.
5. Include first-comment idea to drive discussion.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Check for overselling and unclear impact statements.
Then produce 3 polished post variants and optional ADA-generated visual caption ideas.
Include hashtags that are relevant but not spammy.
```

#### Gemini variant
```text
Using attached project artifacts and report excerpts:
- create source-grounded LinkedIn post options
- include evidence-backed claims
- provide a professional CTA aligned with analyst networking
```

### CP-06 Targeted Cover Letter Composer
Write role-specific cover letters quickly.

#### Claude variant (XML-heavy)
```xml
<context>
I need a tailored cover letter for analytics roles that is specific, concise, and credible.
</context>
<schema>
Paste CV summary, target job description, and relevant project evidence.
</schema>
<task>
Generate a focused cover letter plus 6-line short version.
</task>
<rules>
1. Map claims directly to job requirements.
2. Include one concrete project example with measurable result.
3. Keep tone professional and practical.
4. Avoid generic filler phrases.
5. End with clear value proposition.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First with o1/o3, reason through edge cases before execution.
Identify requirement gaps and propose honest framing strategies.
Then draft:
- full cover letter
- concise application-note version
- optional follow-up email text
No fabricated achievements.
```

#### Gemini variant
```text
Using attached CV, job post, and portfolio links:
- create source-grounded tailored cover letters
- highlight strongest evidence by requirement
- provide one conservative and one confident tone option
```

### CP-07 STAR Story Extractor
Build interview stories from project history.

#### Claude variant (XML-heavy)
```xml
<context>
I need interview-ready STAR stories from my analytics projects.
</context>
<schema>
Paste project notes, challenges faced, decisions made, and outcomes.
</schema>
<task>
Extract 6 STAR stories mapped to common interview competencies.
</task>
<rules>
1. Keep each story concise but specific.
2. Include measurable result where possible.
3. Add one "what I would improve" reflection.
4. Tag each story by competency (SQL, communication, ownership, troubleshooting).
5. Provide short and long answer versions.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Identify weak evidence and missing result details before writing.
Then generate STAR stories with:
- 60-second version
- 2-minute version
- follow-up Q&A prep
```

#### Gemini variant
```text
Using attached project docs and interview prep notes:
- generate source-grounded STAR stories
- connect each story to role requirements
- include interviewer red-flag avoidance tips
```

### CP-08 30-60-90 Day Plan Generator
Show onboarding readiness for analyst roles.

#### Claude variant (XML-heavy)
```xml
<context>
I need a realistic 30-60-90 day plan for a junior data analyst/BI role.
</context>
<schema>
Paste target role scope, expected tools, and team context.
</schema>
<task>
Create a milestone-based onboarding plan with measurable deliverables.
</task>
<rules>
1. Prioritize fast wins in first 30 days.
2. Include stakeholder alignment actions.
3. Define KPI-driven deliverables for each phase.
4. Add risk and dependency notes.
5. Keep plan practical for junior-level ramp-up.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
First use o1/o3 to reason through edge cases before execution.
Then produce a table-style 30-60-90 plan including:
- objectives
- deliverables
- risks
- success metrics
Use ADA optionally for timeline visualization.
```

#### Gemini variant
```text
Using attached company notes and role description:
- create source-grounded 30-60-90 plan
- align milestones to business priorities
- include communication checkpoints with manager/stakeholders
```

### CP-09 Portfolio Technical Review Simulator
Get hiring-manager style feedback on a project.

#### Claude variant (XML-heavy)
```xml
<context>
I want a rigorous technical review of my analytics project before applying to jobs.
</context>
<schema>
Paste README, SQL/notebook snippets, outputs, and architecture notes.
</schema>
<task>
Review project like a hiring manager and provide scored feedback.
</task>
<rules>
1. Score problem framing, technical rigor, reproducibility, and communication.
2. Flag highest-priority defects and risks.
3. Provide concrete fixes ranked by impact.
4. Include "interview defense" talking points.
5. Keep criticism direct and actionable.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Use o1/o3 first to reason through edge cases before execution.
Then provide rubric-based review and, where useful, ADA-generated check tables.
Output:
- major issues
- medium issues
- quick wins
- final project readiness score
```

#### Gemini variant
```text
Using attached repo files and docs:
- produce source-grounded technical review
- cite evidence for each finding
- provide 1-week remediation plan
```

### CP-10 Skill-Gap Roadmap from Job Postings
Build a targeted upskilling plan based on market demand.

#### Claude variant (XML-heavy)
```xml
<context>
I want a focused 12-week learning roadmap based on real data analyst/BI job requirements.
</context>
<schema>
Paste CV/skills inventory and 5-10 target job postings.
</schema>
<task>
Create weighted skill-gap analysis and weekly execution roadmap.
</task>
<rules>
1. Prioritize gaps by frequency and hiring impact.
2. Include project-based learning tasks.
3. Add measurable weekly checkpoints.
4. Keep total weekly workload realistic.
5. Include portfolio artifact output for each phase.
</rules>
```

#### ChatGPT variant (o1/o3 + ADA)
```text
Phase 1 with o1/o3: reason through edge cases before execution.
- ambiguous skill requirements
- overfitting to one job post
- unrealistic pacing
Phase 2: produce a 12-week roadmap and optional ADA table/tracker format.
Include clear weekly deliverables and role-aligned outcomes.
```

#### Gemini variant
```text
Using attached job descriptions, CV, and portfolio notes:
- generate source-grounded gap analysis
- produce prioritized weekly roadmap
- include evidence-based rationale for each learning priority
```
