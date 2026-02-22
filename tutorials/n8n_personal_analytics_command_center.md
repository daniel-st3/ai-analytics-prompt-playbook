## Design an n8n Workflow with Claude for a Personal Analytics Command Center

## Overview

This tutorial helps you build a personal analytics command center that runs daily and sends one useful summary with recommended actions. The goal is practical automation, not over-engineered orchestration. You will define a KPI contract, design n8n nodes, implement data transforms, add AI summarization, and harden the flow with retries and monitoring.

A strong command center should reduce repetitive analysis, not replace decision-making. Your first version should be intentionally small: 3-5 KPIs, one delivery channel, and clear error handling. This is exactly the type of project recruiters remember because it shows applied analytics, automation maturity, and operational thinking.

> **New:** Pair this tutorial with the `claude_skills/n8n-workflow-architect/SKILL.md` skill to get Claude to auto-architect and validate your workflow design without having to prompt from scratch each time.

## Prerequisites

1. Install Node.js 20.19+ (or use n8n Cloud trial — free tier works fine for this project).
2. Install n8n locally.
3. Prepare at least one source (CSV / API / Google Sheet).
4. Choose one output channel (Slack / email / Notion).

```bash
mkdir analytics-command-center
cd analytics-command-center
npm init -y
npx n8n
```

Optional global install:

```bash
npm install -g n8n
n8n
```

> **n8n version note:** This tutorial targets **n8n v1.x** (the current stable release as of 2026). If you're on a self-hosted instance, run `n8n --version` to confirm. Key differences from legacy versions: the Merge node no longer uses `mode: wait` — use **Merge (Combine)** with type `combineByPosition` instead. The SplitInBatches node should be on `typeVersion: 3` for proper context handling.

---

## Step-by-Step

### Step 1: Define command center scope and KPI contract

Before touching nodes, write a small contract: which KPIs, what schedule, who consumes output, what action should follow. A good daily brief could be: "Top KPI deltas, one anomaly, one recommended action, confidence level." Keep strict boundaries to avoid noisy reports.

#### Using the n8n-workflow-architect Claude Skill

Load the `claude_skills/n8n-workflow-architect/SKILL.md` skill in Claude, then say:

```text
Create a KPI contract for a personal analytics command center.
Limit to 5 KPIs. Include: metric name, source, formula, threshold, 
alert condition, and what action the brief should recommend when threshold is breached.
Add a fail-safe rule for when source data is stale or missing.
```

#### Using ChatGPT for this step

```text
Use o1/o3 to reason through edge cases before execution.
Then create a KPI contract table with: metric, source, formula, 
threshold, owner, action.
```

#### Using Gemini for this step

```text
Using attached KPI docs and planning notes, produce a source-grounded 
v1 contract and prioritize by business impact.
```

#### Troubleshooting / Handling AI Hallucinations

If KPI formulas are invented or inconsistent with your docs:

```text
Rebuild KPI contract using only these definitions: [paste exact definitions].
Flag anything missing instead of guessing.
```

---

### Step 2: Design node-by-node workflow architecture

Create the sequence: **trigger → source ingestion → normalization → KPI calculation → anomaly check → summary generation → approval gate (optional) → delivery → logging**. For each node, define input and output structure. This is the difference between easy debugging and chaos.

**Recommended node types in n8n v1.x:**

| Function | Node to Use |
|---|---|
| Schedule trigger | Schedule Trigger |
| HTTP source | HTTP Request |
| Google Sheets | Google Sheets node (OAuth2) |
| Transform / compute | Code node (JavaScript or Python) |
| Conditional routing | IF node |
| Merge parallel branches | Merge node (Combine → combineByPosition) |
| Loop over records | Loop Over Items |
| Slack delivery | Slack node |
| Email delivery | Send Email / Gmail |
| Error fallback | Error Trigger workflow |

#### Using the n8n-workflow-architect Claude Skill

```text
Design a complete n8n v1.x node architecture for a daily analytics briefing.
Provide: node sequence, data contracts per node, retry strategy, 
fallback path, and idempotency approach.
Output as a numbered node map.
```

#### Using ChatGPT for this step

```text
Use o1/o3 to reason through edge cases before execution.
Then produce an implementation checklist with sample payload JSON per node.
```

#### Using Gemini for this step

```text
Use attached SOP and payload examples.
Create source-grounded node map with dependency checks and owner responsibilities.
```

#### Troubleshooting / Handling AI Hallucinations

If workflow skips critical validation nodes:

```text
Your design is missing validation after ingestion.
Insert explicit schema and freshness checks before KPI calculations.
Return updated flow diagram.
```

---

### Step 3: Implement transformations and KPI logic

Build incrementally. First test trigger + ingestion alone. Then add normalization. Then KPI calculation. Avoid complex custom code in Code nodes unless necessary — keep formulas deterministic and easy to inspect.

**Key patterns for n8n v1.x Code nodes:**

```javascript
// Access input items (v1.x syntax)
const items = $input.all();

// Normalize a date field
const normalized = items.map(item => {
  const raw = item.json.created_at;
  return {
    json: {
      ...item.json,
      date_day: new Date(raw).toISOString().split('T')[0]
    }
  };
});

return normalized;
```

```javascript
// KPI delta vs previous day
const today = $input.first().json.revenue_today;
const yesterday = $input.first().json.revenue_yesterday;
const delta_pct = ((today - yesterday) / yesterday * 100).toFixed(1);

return [{ json: { delta_pct, is_anomaly: Math.abs(delta_pct) > 15 } }];
```

#### Using the n8n-workflow-architect Claude Skill

```text
Review my draft node logic and identify fragility in data normalization
and KPI calculations. Suggest safer alternatives with explicit 
null/missing-field guards.
```

#### Using ChatGPT for this step

```text
Use o1/o3 to reason through edge cases before execution.
Then generate minimal JavaScript snippets for n8n v1.x Code nodes:
- date normalization
- KPI delta vs previous day
- anomaly flag calculation
Include null guards for every field access.
```

#### Using Gemini for this step

```text
Use attached payload samples to validate field mappings and suggest 
schema-normalization rules.
```

#### Troubleshooting / Handling AI Hallucinations

If generated code uses nonexistent fields:

```text
Only use this field list: [paste list].
Rewrite the transform code and add explicit fallback for missing fields.
```

---

### Step 4: Add AI summary and human approval safeguards

Constrain AI output with a fixed template so summaries stay factual. Recommended template sections: KPI deltas, likely drivers, confidence, and one recommended action. If output affects stakeholders externally, insert a manual approval node before delivery.

**Recommended n8n setup for AI summary:**

Use the **AI Agent** node or **HTTP Request** to call your preferred LLM API. Pass a strict system prompt:

```text
You are a strict analytics summarizer.
You will receive a JSON object with today's KPI values and deltas.
You MUST:
1. Report only the values present in the JSON — no inventions.
2. Label each insight with a confidence level: high / medium / low.
3. Suggest exactly one recommended action.
4. Keep total output under 150 words.
If data is missing or stale, explicitly state "insufficient data for [metric]".
```

For the human approval gate, use n8n's **Wait** node set to "Wait for webhook" mode — the workflow pauses until a manager approves via a generated link.

#### Using the n8n-workflow-architect Claude Skill

```text
Create a strict summary prompt for n8n that limits output to provided 
KPI JSON and requires confidence labels. 
Also design a human-approval gate using the Wait node.
Include a manager review checklist for the approval message.
```

#### Using ChatGPT for this step

```text
Use o1/o3 to reason through edge cases before execution.
Then draft summary prompt templates and short message format for Slack/email.
```

#### Troubleshooting / Handling AI Hallucinations

If AI summary invents reasons unsupported by data:

```text
Regenerate summary in evidence-only mode.
Use only KPI fields provided; if cause is uncertain, state "insufficient evidence".
```

---

### Step 5: Test reliability, monitoring, and rollout

Run three tests: normal run, missing-data run, and anomaly run. Log execution outcomes with timestamps and failure type. Add one weekly review task: adjust thresholds, review false alerts, and refine summary wording.

**n8n v1.x error handling setup:**

1. Enable **"Always Output Data"** on each node to prevent silent stops.
2. Add a secondary **Error Trigger** workflow that catches execution failures and sends a Slack DM to you.
3. Use **Execution Data** retention (Settings → Executions) to keep 30-day history for debugging.

**Test matrix:**

| Test Scenario | Expected Behavior | Pass Criteria |
|---|---|---|
| Normal run | All KPIs computed, summary sent | Message delivered by SLA time |
| Missing source data | Fail-safe activates, stale-data warning sent | No crash, fallback message sent |
| Anomaly detected | Anomaly flagged, approval gate triggered | Approval link works |
| API rate limit hit | Retry with backoff, DLQ alert if 3 failures | 3 retries before alert |
| Credential failure | Error trigger fires, owner notified | Alert within 2 minutes |

#### Using the n8n-workflow-architect Claude Skill

```text
Create a QA and reliability checklist for this n8n v1.x workflow:
- happy path
- partial failure (one source unavailable)
- hard failure (all sources down)
- rollback and escalation
```

#### Using ChatGPT for this step

```text
Produce a test matrix and weekly maintenance checklist I can run every Monday.
```

#### Troubleshooting / Handling AI Hallucinations

If AI suggests impossible reliability features for your current setup:

```text
Limit recommendations to tools currently in this stack: [paste stack].
Re-rank improvements by feasibility this week.
```

---

## Model Selection Guide

| Task | Best Model | Why |
|---|---|---|
| Architecture design | **Claude + n8n-workflow-architect skill** | Auto-loads best practices, step-by-step workflow spec |
| JavaScript code snippets | **ChatGPT (GPT-4o)** | Strong at concise, correct JS for Code nodes |
| Aligning to existing docs/SOPs | **Gemini** | Source-grounded synthesis across multiple documents |
| Debugging failed runs | **Claude** | Strong reasoning about node contracts and error paths |

---

## Next Steps

1. Add a weekly trend branch alongside the daily snapshot.
2. Add incident tagging and root-cause labeling over time.
3. Publish your architecture diagram + reliability lessons in your portfolio repo.
4. Explore connecting the n8n workflow to the **autonomous-data-quality-sentinel** Claude skill for self-healing pipelines.

---
