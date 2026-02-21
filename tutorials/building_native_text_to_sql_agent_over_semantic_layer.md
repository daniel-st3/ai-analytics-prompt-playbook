## Building a Native Text-to-SQL Agent over a Semantic Layer

## Overview
This weekend build is for principal-level practitioners who want a production-credible text-to-SQL assistant without catastrophic join hallucinations. The core design principle: **the LLM never reasons directly over raw warehouse tables for business answers**. It must route through a governed semantic layer API (MetricFlow/Cube) that enforces metric contracts, relationship paths, and grain safety.

You will build a Slack bot that:
- interprets business questions,
- maps intent to semantic metrics/dimensions,
- calls semantic APIs for validated query plans/results,
- returns answer + provenance + confidence,
- and blocks unsafe requests that bypass contracts.

This is not a toy NL2SQL project. It is an enterprise control-plane pattern for trustworthy analytics AI.

## Prerequisites
1. A working semantic layer (MetricFlow or Cube) with published metrics and dimensions.
2. Slack app with bot token and event subscriptions configured.
3. Python environment and LangChain-compatible runtime.
4. Service account/API credentials for semantic layer access.
5. Metric governance artifacts (definition docs, owners, SLA, allowed filters).

Example setup scaffold:
```bash
mkdir semantic-text2sql-agent
cd semantic-text2sql-agent
python3 -m venv .venv
source .venv/bin/activate
pip install langchain fastapi uvicorn slack_bolt pydantic requests
```

## Architecture Blueprint
### Control-plane principles
- LLM is planner/interpreter, not SQL authority.
- Semantic API is query authority.
- Policy layer validates entitlements, metric allowlist, and filter constraints.
- Response layer returns value + semantic lineage + confidence and caveats.

### Minimum service components
1. **Intent parser** (LLM): classify metric request, timeframe, dimensions, constraints.
2. **Semantic translator**: map intent to semantic API request schema.
3. **Policy guard**: enforce allowed metrics, dimensions, row-level constraints.
4. **Execution adapter**: call MetricFlow/Cube API.
5. **Result explainer**: summarize result with provenance and warning flags.
6. **Slack interface**: message handling, threaded follow-ups, feedback capture.

## Step-by-Step

### Step 1: Define semantic contract boundary
Create an allowlist contract of what the bot can answer: metric names, dimensions, filters, time grains, and max cardinality. This boundary is your first anti-hallucination control.

#### Using Claude for this step
```text
<context>
We are building a Slack text-to-SQL agent that must never hallucinate joins.
</context>
<task>
Define semantic boundary contract and prohibited query patterns.
</task>
<rules>
LLM may only query semantic API objects, never raw warehouse tables.
</rules>
```

#### Using ChatGPT for this step
```text
Phase 1 (o1/o3): reason through edge cases before execution:
- ambiguous metric names
- cross-domain joins not in semantic graph
- unauthorized dimension access
Phase 2 (ADA optional): generate policy schema and validation code skeleton.
```

#### Using Gemini for this step
```text
Use attached metric definitions and governance docs to produce source-grounded semantic contract and policy matrix.
```

#### Troubleshooting / Handling AI Hallucinations
If AI tries to expose raw SQL tables:
```text
Reject this design.
Regenerate with strict rule: SQL execution only through semantic layer API abstractions.
```

### Step 2: Build intent-to-semantic mapping pipeline
Create a deterministic intermediate representation (IR), e.g.:
- `metric`: `net_revenue`
- `time_grain`: `week`
- `dimensions`: [`region`, `channel`]
- `filters`: [`region in (...)`, `date between ...`]

The IR is critical for validation before execution.

#### Using Claude for this step
```text
Design intent IR schema for semantic query planning.
Include ambiguity handling and clarification triggers.
```

#### Using ChatGPT for this step
```text
Use o1/o3 reasoning first.
Then generate pydantic models and validation functions for intent IR.
```

#### Using Gemini for this step
```text
Use attached semantic dictionary to map business synonyms to canonical metric names with source citations.
```

#### Troubleshooting / Handling AI Hallucinations
If mapping guesses unknown metrics:
```text
Unknown metric names must trigger clarification, not fallback guesses.
Add strict unknown-intent response template.
```

### Step 3: Enforce policy and authorization layer
Before calling semantic API, validate:
- metric entitlement,
- dimension entitlement,
- row-scope authorization,
- time-range and cardinality limits.

This prevents “correct SQL, wrong access.”

#### Using Claude for this step
```text
Define policy gate design for semantic query authorization and scope control.
Include deny-by-default behavior.
```

#### Using ChatGPT for this step
```text
Phase 1 (o1/o3): reason through privilege escalation edge cases.
Phase 2: generate policy enforcement middleware skeleton with explicit error codes.
```

#### Using Gemini for this step
```text
Use attached role matrix and governance docs to produce source-grounded authorization policy map.
```

#### Troubleshooting / Handling AI Hallucinations
If AI suggests permissive fallback behavior:
```text
Replace with deny-by-default policy.
No fallback execution on policy mismatch.
```

### Step 4: Connect LangChain tool routing to semantic API
Implement tool calls where LLM emits IR, validator approves, adapter calls semantic API endpoint, and response object includes lineage metadata.

Key safeguards:
- no free-form SQL tool,
- request signing and audit logging,
- timeout and retry with idempotent request IDs.

#### Using Claude for this step
```text
Design tool-routing graph for LLM -> validator -> semantic API -> response explainer.
Include error handling and rollback behavior.
```

#### Using ChatGPT for this step
```text
Use o1/o3 reasoning first for failure modes.
Then generate Python skeleton for LangChain tool + semantic API adapter + audit logger.
```

#### Using Gemini for this step
```text
Use attached API docs to produce source-grounded endpoint contract and failure taxonomy.
```

#### Troubleshooting / Handling AI Hallucinations
If AI introduces raw SQL generation path:
```text
Remove any raw SQL execution capability.
All query execution must route through semantic API contract only.
```

### Step 5: Build Slack bot interaction model
Use Slack app with thread-aware responses. Require bot to return:
- answer,
- metric definition link,
- filter context,
- confidence/risk flags,
- “ask follow-up” suggestions.

#### Using Claude for this step
```text
Create response protocol for Slack analytics answers with provenance and risk labels.
```

#### Using ChatGPT for this step
```text
Use o1/o3 reasoning first.
Then generate Slack Bolt handler skeleton with thread context and feedback capture.
```

#### Using Gemini for this step
```text
Use attached communication guidelines and KPI docs to produce source-grounded answer style guide.
```

#### Troubleshooting / Handling AI Hallucinations
If responses omit provenance:
```text
Enforce response schema: answer, metric_id, filters_applied, time_window, source_contract_version, confidence.
```

### Step 6: Evaluation and anti-hallucination testing
Create evaluation suite:
- intent parsing accuracy,
- semantic mapping accuracy,
- policy violation block rate,
- hallucinated join rate (target: near zero),
- user trust score from feedback.

Run adversarial prompts:
- ask for undefined metrics,
- ask for illegal joins,
- ask for out-of-scope dimensions,
- ask for disallowed sensitive breakdowns.

#### Using Claude for this step
```text
Design anti-hallucination test matrix and release gate policy for semantic text-to-SQL agent.
```

#### Using ChatGPT for this step
```text
Phase 1 (o1/o3): reason through adversarial failure cases.
Phase 2 (ADA): generate test harness structure and result scoring tables.
```

#### Using Gemini for this step
```text
Use attached historical support questions and metric policy docs to build source-grounded evaluation benchmark.
```

#### Troubleshooting / Handling AI Hallucinations
If agent answers outside contract:
```text
Treat as critical failure.
Block release and output root-cause triage: intent parser, mapper, policy gate, or adapter fault.
```

## Reference Prompt Patterns

### Claude: Contract-first architecture prompt
```text
<context>
We need a Slack text-to-SQL agent that only queries semantic layer APIs.
</context>
<task>
Design architecture, control points, and rollout gates for zero-raw-table query policy.
</task>
<rules>
No SQL generation path outside semantic API. Include audit and rollback.
</rules>
```

### ChatGPT: o1/o3 + implementation prompt
```text
Phase 1 with o1/o3: enumerate all join-hallucination pathways and policy bypass vectors.
Phase 2: generate Python middleware skeleton for IR validation + semantic API execution + response provenance.
```

### Gemini: source-grounded governance prompt
```text
Using attached semantic contracts, RBAC docs, and KPI definitions,
produce a source-grounded release readiness checklist and unresolved-risk register.
```

## Enterprise Failure Modes and Recovery

### Failure mode: semantic model version drift
- Symptom: bot answers changed without user-visible explanation.
- Recovery: pin semantic contract version in response payload; require compatibility check before promotion.

### Failure mode: permission leak through cached responses
- Symptom: user sees metric breakdown they are not authorized to view.
- Recovery: include authorization scope in cache key; invalidate on role change events.

### Failure mode: ambiguous KPI synonym routing
- Symptom: “revenue” maps to inconsistent metrics across teams.
- Recovery: implement disambiguation prompt and force explicit metric selection.

### Failure mode: policy gate bypass under timeout fallback
- Symptom: emergency fallback returns unvalidated answer.
- Recovery: fallback must degrade to “cannot answer safely,” never bypass policy checks.

## Using Claude
Use Claude to design contracts, control points, and rollout governance before coding.

## Using ChatGPT
Use ChatGPT in strict two-step mode for implementation: o1/o3 reasoning first, then executable code scaffolds.

## Using Gemini
Use Gemini to align semantic, policy, and communication artifacts across large documentation sets.

## Next Steps
1. Add model-context protocol (MCP) integration for contract registry lookup.
2. Implement human feedback capture for ambiguous intent routes.
3. Add continuous evaluation pipeline with weekly adversarial test suite.
