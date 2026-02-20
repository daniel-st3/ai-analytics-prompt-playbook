## End-to-End Modern Data Stack Setup in a Weekend

## Overview
This tutorial is a focused weekend build to stand up a modern analytics stack with AI assistance: ingestion (Airbyte), transformation (dbt), orchestration (Dagster or Prefect), and BI modeling/serving (Lightdash). The objective is not full enterprise hardening in two days. The objective is a working, well-structured baseline you can demo, extend, and discuss in senior-level interviews.

By Sunday night, you should have a reproducible local stack with:
- one source-to-warehouse ingestion job,
- a staged dbt project with tests,
- an orchestrated run that coordinates ingestion and transformations,
- and a Lightdash dashboard powered by tested metrics.

The strict-mode process is model-aware:
- **Claude** for XML-based architecture and migration-safe planning,
- **ChatGPT** for o1/o3 edge-case reasoning followed by code execution or command generation,
- **Gemini** for source-grounded synthesis across docs, configs, and architecture notes.

## Prerequisites
1. Install Docker Desktop and confirm it runs.
2. Install Git and VS Code.
3. Install `dbt-core` plus adapter (`dbt-bigquery` or `dbt-snowflake`).
4. Pick orchestrator: Dagster or Prefect.
5. Install Node.js if using Lightdash local tooling.

```bash
mkdir modern-data-stack-weekend
cd modern-data-stack-weekend
git init

python3 -m venv .venv
source .venv/bin/activate
pip install dbt-core dbt-bigquery prefect
# swap adapter if needed: dbt-snowflake
```

For Docker sanity check:

```bash
docker --version
docker compose version
docker ps
```

## Step-by-Step

### Step 1: Define architecture and choose minimal scope
Do not start by spinning containers randomly. First define one concrete pipeline: source -> raw table -> modeled mart -> dashboard KPI. Keep scope tight (for example: one ecommerce orders dataset with three KPIs). This makes debugging feasible in a weekend.

#### Using Claude for this step
```text
<context>
I need a weekend MVP modern data stack with Airbyte + dbt + [Dagster/Prefect] + Lightdash.
</context>
<schema>
Source: [CSV/API], Warehouse: [BigQuery/Snowflake], KPIs: [list].
</schema>
<task>
Design a minimum viable architecture with component boundaries and dependency flow.
</task>
<rules>
Limit scope to one pipeline and three KPIs; include assumptions and failure points.
</rules>
```

#### Using ChatGPT for this step
```text
Phase 1 (o1/o3): reason through edge cases before execution.
- docker resource limits
- warehouse credential setup
- orchestration dependency order
Phase 2: generate setup checklist with command sequence.
```

#### Using Gemini for this step
```text
Using attached architecture references and tool docs, produce a source-grounded weekend implementation plan with decision tradeoffs.
```

#### Troubleshooting / Handling AI Hallucinations
If the AI proposes unsupported architecture complexity:
```text
Reduce design to one ingestion stream, one dbt mart, and one dashboard page.
Remove non-essential components.
```

### Step 2: Stand up Airbyte ingestion
Use Airbyte to ingest one source into your warehouse raw schema. Document source schema and sync mode (`full_refresh` vs `incremental`). For a weekend MVP, one stable source is enough.

#### Using Claude for this step
```text
<context>
I’m configuring one Airbyte connector for weekend MVP.
</context>
<task>
Provide source setup checklist, sync mode recommendation, and validation SQL for loaded raw tables.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then generate operational checklist for Airbyte setup, credential validation, and first-sync QA.
```

#### Using Gemini for this step
```text
Use attached connector docs and schema notes to create source-grounded Airbyte config checklist and post-sync validation plan.
```

#### Troubleshooting / Handling AI Hallucinations
If Airbyte sync appears successful but data is missing:
```text
Generate 5 validation SQL checks for row count, timestamp freshness, null critical keys, duplicate IDs, and schema drift.
```

### Step 3: Build dbt staging and mart models
Create a dbt project with staging and mart layers. Keep logic modular. Add `schema.yml` tests from day one to prevent silent KPI drift.

```bash
dbt init weekend_analytics
dbt debug
dbt run
dbt test
```

#### Using Claude for this step
```text
<context>
I need dbt models from raw Airbyte tables to analytics mart KPIs.
</context>
<schema>
Paste raw table schema and expected KPI formulas.
</schema>
<task>
Generate staging and mart model templates plus schema.yml tests.
</task>
<rules>
Declare grain for every model and include uniqueness/relationship tests.
</rules>
```

#### Using ChatGPT for this step
```text
Phase 1: Use o1/o3 to reason through edge cases (grain mismatch, late-arriving updates, null dimensions).
Phase 2: generate dbt SQL + schema.yml examples and command sequence for run/test.
```

#### Using Gemini for this step
```text
Using attached KPI docs and source schema, produce source-grounded dbt modeling plan with test coverage priorities.
```

#### Troubleshooting / Handling AI Hallucinations
If dbt SQL compiles but KPI is wrong due grain:
```text
Restate model grain for each model and rewrite mart logic accordingly.
Add validation queries comparing source totals vs mart totals by date.
```

### Step 4: Add orchestration with Dagster or Prefect
Wire tasks in dependency order: ingest -> dbt run -> dbt test -> publish status. Keep workflow explicit and observable.

#### Using Claude for this step
```text
<context>
I need orchestration for Airbyte -> dbt run -> dbt test.
</context>
<task>
Design robust orchestration flow with retries, failure notifications, and run metadata logging.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 first to reason through edge cases before execution.
Then generate starter pipeline code for Prefect (or Dagster) with retry settings and task dependencies.
```

#### Using Gemini for this step
```text
Use attached orchestration docs and produce source-grounded runbook for schedule, retries, and incident response.
```

#### Troubleshooting / Handling AI Hallucinations
If orchestration code references unavailable packages:
```text
Regenerate using only installed packages from this environment: [paste pip freeze excerpt].
```

### Step 5: Connect Lightdash and publish one decision-ready dashboard
Point Lightdash to your dbt models and define one page with 3-5 KPIs. Keep chart selection tied to decisions.

#### Using Claude for this step
```text
Design a decision-first Lightdash dashboard layout from these dbt marts and KPI contracts.
Include QA checks before sharing with stakeholders.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then create dashboard QA checklist: metric definitions, filter behavior, and refresh timing.
```

#### Using Gemini for this step
```text
Using attached strategy docs and KPI definitions, produce source-grounded dashboard narrative and page spec.
```

#### Troubleshooting / Handling AI Hallucinations
If dashboard metric doesn’t match dbt output:
```text
Create a reconciliation checklist from dbt mart query -> semantic definition -> dashboard tile filter context.
```

### Step 6: Reliability pass and documentation
Before calling the weekend done, add operational quality controls:
- a runbook,
- known failure modes,
- and one rollback approach.
Document exactly how to run everything from zero.

#### Using Claude for this step
```text
Generate a release-readiness checklist for this modern data stack MVP:
- architecture summary
- failure modes
- test evidence
- next hardening steps
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then produce README-ready setup/run/troubleshooting documentation.
```

#### Using Gemini for this step
```text
Use attached build notes and configs to create source-grounded final documentation and risk register.
```

#### Troubleshooting / Handling AI Hallucinations
If docs include commands not tested:
```text
Rewrite docs in verified-command mode.
Mark each command as tested/unverified and list missing validation steps.
```

## Docker Network and Dependency Conflict Playbook
These two issues are the most common blockers in weekend stack setup.

### Docker network issues
Common symptoms:
- services cannot resolve each other by hostname,
- intermittent connection refused,
- containers start but orchestration cannot reach dependencies.

Use this recovery prompt:
```text
I have Docker network issues.
Given this compose file and container logs, produce a step-by-step network diagnostic plan.
Prioritize hostname resolution, exposed ports, bridge network config, and startup order.
```

Practical checks:
```bash
docker compose ps
docker network ls
docker network inspect <network_name>
docker compose logs -f
```

### Dependency conflicts
Common symptoms:
- `ModuleNotFoundError`,
- dbt adapter mismatch,
- orchestrator package conflicts,
- environment works on one machine but not another.

Use this recovery prompt:
```text
Here is pip freeze and error traceback.
Find incompatible package versions and propose a minimal compatible set for dbt + [dagster/prefect] + related tooling.
```

Practical checks:
```bash
pip freeze > requirements.lock.txt
python -m pip check
```

## Using Claude
Use Claude for architecture guardrails, dependency flow design, and structured release-readiness reviews.

## Using ChatGPT
Use ChatGPT with the two-step pattern: o1/o3 edge-case reasoning first, then code/command generation for execution.

## Using Gemini
Use Gemini when context is spread across many docs. Ask it to map each recommendation to source files for traceability.

## Next Steps
1. Add CI/CD with GitHub Actions (`dbt test` and orchestration lint checks).
2. Add observability (freshness dashboard + failure alerting).
3. Expand from one pipeline to two domains only after MVP is stable.
