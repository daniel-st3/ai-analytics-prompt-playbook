# AI-Powered Analytics Workflows
Production-minded analytics automation blueprints for n8n, agents, and model-specific AI execution.

This repository focuses on practical workflow architecture for analytics and BI teams: daily KPI command centers, anomaly alerts, incident triage, and source-to-dashboard orchestration. The approach is strict mode: clear data contracts, explicit failure handling, and model-specific prompt workflows.

## Who Is This For?
- Junior analysts automating repetitive reporting and KPI monitoring
- BI practitioners building reliable alerting and delivery pipelines
- Students creating automation-heavy portfolio projects
- Builders combining n8n + LLM reasoning with practical guardrails

## What You Get
- Workflow patterns for n8n-based analytics operations
- Model-specific prompt workflows for Claude, ChatGPT, and Gemini
- Error handling patterns: retries, fallback paths, dead-letter routing
- Human-in-the-loop approval examples for risk-sensitive actions
- Portfolio-ready documentation patterns for showcasing automation work

## Installation & Setup
1. Clone the repo.
```bash
git clone https://github.com/daniel-st3/ai-analytics-prompt-playbook.git
cd ai-analytics-prompt-playbook
```

2. Open in VS Code.
```bash
code .
```

3. Run n8n locally (optional local setup).
```bash
npm init -y
npx n8n
```

4. Use with Claude Code / Claude web.
- Use Claude to design node-by-node architecture.
- Require data contracts and edge-case handling.
- Request MVP + hardening roadmap.

5. Use with ChatGPT web.
- Step 1 with o1/o3: reason through edge cases first.
- Step 2 with ADA (when needed): generate code snippets/test scaffolds.
- Validate logic before deployment.

6. Use with Gemini Advanced.
- Attach SOP docs, payload samples, and policies.
- Require source-grounded workflow recommendations.
- Ask for confirmed facts vs assumptions.

## Strict-Mode Workflow Protocol
1. Define objective, trigger, SLA, and destination.
2. Specify payload schema and data contracts.
3. Generate architecture with model-specific prompt.
4. Add retries, fallback, and approval checkpoints.
5. Run happy path + failure path tests.
6. Capture lessons in runbook and README.

## Example Prompt Patterns
### Claude (workflow architecture)
```xml
<context>
Design an n8n workflow for daily KPI summary delivery.
</context>
<schema>
Paste source payloads, KPI definitions, and destination format.
</schema>
<task>
Return node sequence, retry logic, and failure routing.
</task>
<rules>
Include idempotency, human approval gate, and test matrix.
</rules>
```

### ChatGPT (o1/o3 + ADA)
```text
Phase 1: Use o1/o3 to reason through edge cases (duplicate triggers, stale source, bad schema).
Phase 2: Generate implementation checklist and minimal code snippets for transforms.
If needed, use ADA for simulation/testing helpers.
```

### Gemini (source-grounded planning)
```text
Using attached SOP docs and payload examples,
produce a source-grounded n8n blueprint with data contracts,
error handling, escalation paths, and rollout checklist.
```

## Troubleshooting / Handling AI Hallucinations
If a workflow references nonexistent fields:
```text
Only use this field list: [paste list].
Rewrite mappings and add fallback behavior for missing required fields.
```

If retry/fallback logic is missing:
```text
Your current design is not production-safe.
Add retry policy, dead-letter path, and escalation rule for repeated failure.
```

If AI recommends tools not in your stack:
```text
Limit recommendations to this stack only: [paste stack].
Re-rank implementation steps by feasibility this week.
```

## How to Showcase This in Your Portfolio
- Include one architecture diagram and one test matrix per workflow.
- Show one failure scenario and how your design recovers.
- Publish a short “MVP vs hardening” roadmap.
- Add a measurable outcome (time saved, incidents reduced, reporting latency improved).

## Contribution Guidelines
1. Submit workflows with objective, node map, and data contracts.
2. Include failure handling and validation checklist.
3. Provide Claude, ChatGPT, and Gemini prompt variants.
4. Keep examples realistic, reproducible, and evidence-based.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
