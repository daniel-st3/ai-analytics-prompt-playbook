# AI-Powered Analytics Workflows
Build practical automations for analytics and BI using n8n, agents, and model-specific AI prompting.

This repository contains workflow blueprints, implementation notes, and prompt packs for creating reliable analytics automations. Focus: clear business outcomes, strong guardrails, and portfolio-ready artifacts.

## Who is this for?
- Junior analysts automating repetitive reporting tasks
- BI developers building alerting and KPI delivery pipelines
- Students exploring n8n + LLM agent patterns with practical scope
- Portfolio builders who want “wow-factor but useful” projects

## Features
- n8n workflow templates (KPI briefings, anomaly alerts, incident triage)
- Prompt guides for Claude, ChatGPT, and Gemini
- Error-handling and human-approval patterns
- Lightweight architecture notes for LangChain/LangGraph orchestration
- README-ready project narratives for portfolio publishing

## Installation & Setup
1. Clone the repository.
```bash
git clone <your-repo-url>
cd ai-powered-analytics-workflows
```

2. Open in VS Code.
```bash
code .
```

3. Install/run n8n (local option).
```bash
npm init -y
npx n8n
```

4. Use with Claude Code.
- Open workflow spec file in repo.
- Paste the Claude prompt variant.
- Ask Claude to convert business requirements into node-level flow.

5. Use with ChatGPT (web).
- Paste workflow context and sample payloads.
- Ask for transform scripts, test cases, and alert templates.

6. Use with Gemini (web).
- Attach SOP docs, payload examples, and policy notes.
- Ask for source-grounded workflow recommendations.

## How to Use
Start with one workflow only (do not overbuild v1).

### Claude workflow prompt
```text
Design an n8n workflow for daily KPI briefing.
Include trigger, transforms, summary node, retry logic, and human approval gate.
```

### ChatGPT workflow prompt
```text
Generate implementation checklist + JS snippets for n8n Function nodes:
date normalization, KPI deltas, anomaly flags.
```

### Gemini workflow prompt
```text
Use attached docs and payload samples to propose a robust n8n flow with data contracts and failure handling.
```

## How This Helps Your Portfolio
- Demonstrates end-to-end thinking: data ingestion to decision delivery
- Shows practical automation design, not only notebooks
- Highlights reliability mindset (retries, approvals, observability)
- Creates strong interview stories around impact and operational maturity

## Contribution Guidelines
- Submit workflows with objective, architecture diagram, and test cases.
- Include one Claude, one ChatGPT, and one Gemini prompt variant per workflow.
- Document limitations and assumptions clearly.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
