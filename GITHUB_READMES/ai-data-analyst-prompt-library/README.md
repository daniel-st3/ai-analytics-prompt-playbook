# AI Data Analyst Prompt Library
Professional, model-specific mega-prompts for data analytics, BI, ML, automation, and portfolio execution.

This repository is a strict-mode prompt system for analysts and students who want reliable outputs, not generic AI text. It includes 40 advanced prompts with dedicated Claude, ChatGPT, and Gemini variants, each designed around realistic analytics workflows.

## Who Is This For?
- Master’s students targeting Data Analyst, BI Analyst, or Analytics Engineer roles
- Junior analysts building portfolio-quality SQL, EDA, and ML projects
- Automation builders using n8n, agents, and practical data workflows
- Self-learners who want verifiable, model-specific prompting standards

## What You Get
- 40 mega-prompts across Data Analytics, BI, ML, Automation, and Career tracks
- Claude variants using XML structure (`<context>`, `<schema>`, `<task>`, `<rules>`)
- ChatGPT variants using **o1/o3 edge-case reasoning first**, then ADA execution
- Gemini variants optimized for long-context, source-grounded outputs
- Verification-first patterns: assumptions, edge cases, and validation tests

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

3. Open the prompt library file.
- File: `PROMPT_LIBRARY.md`
- Pick one prompt from the relevant section.

4. Use with Claude Code / Claude web.
- Copy the Claude XML variant.
- Paste schema + sample rows.
- Ask for assumptions + validation before final output.

5. Use with ChatGPT web.
- Start with o1/o3 and run edge-case reasoning.
- Then switch to Advanced Data Analysis for execution/code.
- Export notebook-ready cells and findings.

6. Use with Gemini Advanced.
- Attach relevant docs/datasets.
- Use Gemini variant prompt.
- Require source-grounded claims and explicit uncertainty labels.

## Strict-Mode Usage Protocol
1. Define objective and decision owner.
2. Paste schema, sample rows, and metric definitions.
3. Run model-specific variant (Claude / ChatGPT / Gemini).
4. Validate output before reusing.
5. Save final prompt + assumptions + result notes.

### Claude Protocol
```text
- Use XML prompt structure.
- Require clarifying questions when grain is ambiguous.
- Request SQL/EDA plan + validation pack.
```

### ChatGPT Protocol
```text
- Step 1: Use o1/o3 to reason through edge cases.
- Step 2: Use ADA to execute validated code.
- Require reproducible cells and checks.
```

### Gemini Protocol
```text
- Attach all relevant context files.
- Require source mapping for assumptions.
- Ask Gemini to separate confirmed facts vs inferences.
```

## Example Mega-Prompts
### Claude (XML)
```xml
<context>
I need a fraud EDA and SQL plan for a portfolio project.
</context>
<schema>
Paste DDL and sample rows.
</schema>
<task>
Generate analysis plan, SQL checks, and validation tests.
</task>
<rules>
Ask clarifying questions for ambiguous grain and include failure modes.
</rules>
```

### ChatGPT (o1/o3 + ADA)
```text
Phase 1: Use o1/o3 to reason through edge cases (grain mismatch, leakage, denominator errors).
Phase 2: In ADA execute EDA and baseline model code.
Return notebook-ready cells, metric table, and validation notes.
```

### Gemini (source-grounded)
```text
Using attached dataset + KPI definitions + policy docs,
produce a source-grounded analysis plan with assumptions linked to source files.
Add a section: confirmed facts vs needs-validation.
```

## Troubleshooting / Handling AI Hallucinations
If SQL grain looks wrong:
```text
Your logic appears row-grain, but KPI must be transaction-grain.
Rewrite using COUNT(DISTINCT transaction_id) where appropriate.
Add a validation query proving the grain.
```

If model invents columns:
```text
Stop and use only these columns: [paste list].
Rebuild output and mark unknown items as "requires clarification".
```

If summary overstates impact:
```text
Rewrite in strict evidence mode.
Only include claims supported by this metrics table: [paste table].
```

## Repository Structure
```text
PROMPT_LIBRARY.md
CLAUDE_SKILLS.md
CUSTOM_GPTS_AND_GEMS.md
TUTORIALS.md
WEBSITE_SECTIONS.md
GITHUB_READMES/
```

## How This Strengthens Your Portfolio
- Demonstrates model-specific AI execution discipline
- Shows verification and risk-awareness, not blind prompt use
- Produces reusable artifacts for GitHub, website, and interviews
- Signals practical readiness for analyst and BI workflows

## Contribution Guidelines
1. Add prompts only if they are original and practically testable.
2. For each new prompt, include Claude, ChatGPT, and Gemini variants.
3. Include validation steps and edge-case checks.
4. Keep writing concise, evidence-oriented, and reproducible.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
