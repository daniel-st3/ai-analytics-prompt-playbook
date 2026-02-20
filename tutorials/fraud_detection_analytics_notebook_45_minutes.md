## Build a Fraud Detection Analytics Notebook with AI in 45 Minutes

## Overview
This tutorial is a fast, portfolio-ready sprint to build a fraud analytics notebook that is useful in interviews and realistic for business work. The objective is not perfect accuracy in one session; it is analyst judgment: clear framing, defensible checks, baseline models, and transparent limitations. In 45 minutes, you will produce four artifacts: EDA summary, model comparison table, threshold decision note, and README-ready conclusion.

## Prerequisites
1. Install Python 3.10+ and VS Code.
2. Create a project folder and virtual environment.
3. Install required packages.
4. Prepare a dataset with a binary fraud label (for example, `is_fraud`).

```bash
mkdir fraud-notebook-ai
cd fraud-notebook-ai
python3 -m venv .venv
source .venv/bin/activate
pip install pandas numpy scikit-learn matplotlib seaborn jupyterlab
jupyter lab
```

Optional Conda setup:

```bash
conda create -n fraud-ai python=3.11 -y
conda activate fraud-ai
pip install pandas numpy scikit-learn matplotlib seaborn jupyterlab
```

## Step-by-Step

### Step 1: Define the analysis contract before writing code
Start by writing one markdown cell with business objective, primary decision, alert capacity, target variable, unit of analysis, and constraints. Most weak notebooks fail from unclear scope, not weak coding. Keep it specific: “prioritize likely fraudulent transactions while limiting false positives.”

#### Using Claude for this step
```text
<context>
I am building a fraud notebook for portfolio and interview use.
</context>
<schema>
Here is DDL + sample rows.
</schema>
<task>
Create an analysis contract with objective, target definition, grain, and decision criteria.
</task>
<rules>
Ask clarifying questions if grain/label timing is ambiguous.
</rules>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Identify ambiguity in target definition, label timing, and population scope.
Then provide a concise analysis contract template I can paste in my notebook.
```

#### Using Gemini for this step
```text
I attached fraud data dictionary, policy PDF, and KPI notes.
Create a source-grounded analysis contract and map each assumption to source files.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If the AI invents fields or assumes a label that does not exist, use this follow-up prompt:
```text
Stop. Only use columns explicitly present in this schema list: [paste list].
Rebuild the contract and mark unknown items as "requires clarification".
```

### Step 2: Run focused EDA with validation intent
Use EDA to answer model-risk questions, not to generate random plots. Check class imbalance, duplicate keys, missingness, suspicious leakage features, and time-based label distribution. Add one “data trust” table with pass/fail checks.

#### Using Claude for this step
```text
<context>
I need focused EDA for fraud modeling, not generic profiling.
</context>
<task>
Provide prioritized checks: must-run, useful, optional.
Include SQL/pandas test for each check.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then in ADA run EDA code for:
- class balance
- missingness by segment
- duplicate transaction checks
- temporal fraud-rate trend
Return notebook-ready cells and chart interpretations.
```

#### Using Gemini for this step
```text
Use attached data dictionary and fraud operations SOP.
Recommend which EDA checks are most operationally actionable and why.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If SQL or code uses wrong grain (for example, counts rows when KPI needs unique transaction IDs):
```text
Your current logic appears row-grain, but KPI is transaction-grain.
Rewrite checks using COUNT(DISTINCT transaction_id) where appropriate.
Add one validation query proving grain correctness.
```

### Step 3: Train three baseline models quickly
Train logistic regression, random forest, and gradient boosting. Use a temporal split if data is time-sensitive; random split may inflate performance. Compare ROC-AUC and PR-AUC, plus practical metrics like recall at fixed precision and expected alerts/day.

#### Using Claude for this step
```text
<context>
I need a baseline model plan for fraud with business-aware evaluation.
</context>
<task>
Design experiment order, evaluation metrics, and threshold decision logic.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then in ADA generate sklearn code for logistic regression, random forest, and gradient boosting.
Return metrics table (ROC-AUC, PR-AUC, recall@precision) and top feature signals.
```

#### Using Gemini for this step
```text
Use attached policy and model-governance notes.
Provide a source-grounded recommendation for which baseline to present as primary and why.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If model code fails or imports break:
```text
The code failed with this error: [paste error].
Provide a corrected minimal version that runs with pandas + scikit-learn only.
Do not introduce extra libraries.
```

If performance is suspiciously high (possible leakage):
```text
Performance seems unrealistic. Run a leakage audit on features and retrain after removing risky columns.
Show before/after metrics and explain differences.
```

### Step 4: Choose threshold using business constraints
A baseline model without threshold policy is incomplete. Define false-positive and false-negative costs, review-team capacity, and acceptable customer friction. Build a threshold sweep table and pick balanced and conservative options.

#### Using Claude for this step
```text
<context>
I need an operating threshold policy for fraud alerts.
</context>
<task>
Build threshold decision options using FP/FN costs and reviewer capacity.
Include policy recommendation and monitoring plan.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then in ADA compute threshold sweep and expected alert-volume table.
Provide conservative, balanced, and aggressive options.
```

#### Using Gemini for this step
```text
Using attached operations constraints and escalation rules,
propose threshold policy with source-grounded justification.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If the AI proposes thresholds without clear assumptions:
```text
Do not recommend thresholds until you show explicit assumptions for FN cost, FP cost, and review capacity.
Recompute with transparent formulas.
```

### Step 5: Package results for GitHub and interviews
Create final notebook sections: “What I found,” “What I trust,” “What could be wrong,” and “Next iteration.” Then generate a README snippet summarizing problem, method, metrics, limitations, and next steps.

#### Using Claude for this step
```text
<context>
I need portfolio-ready deliverables from this notebook.
</context>
<task>
Generate: executive summary, README section, and interview talking points.
Keep wording credible and concise.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then produce README-ready markdown with setup, results table, and limitations.
```

#### Using Gemini for this step
```text
Use attached notebook outputs + documentation.
Create source-grounded portfolio narrative and confidence labels for each claim.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If generated write-up overstates impact:
```text
Rewrite in strict evidence mode.
Only include claims directly supported by this metrics table: [paste table].
Mark unsupported statements as "not validated".
```

## Using Claude
Use Claude as planning and QA layer for analysis contracts, leakage warnings, and concise interview-ready explanations.

## Using ChatGPT
Use ChatGPT with ADA for execution: code, plots, and rapid iteration. Keep the two-phase pattern: o1/o3 reasoning first, ADA execution second.

## Using Gemini
Use Gemini for multi-document grounding when policy docs and KPI definitions matter.

## Next Steps
1. Add drift monitoring section (feature drift + threshold review cadence).
2. Build one dashboard page from notebook outputs.
3. Publish notebook + README + screenshot in a dedicated repo.

---

