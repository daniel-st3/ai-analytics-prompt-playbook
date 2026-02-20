# AI Data Analyst Prompt Library
Practical, model-specific prompts for data analytics, BI, ML, and automation workflows.

A curated library of original prompts designed for Claude, ChatGPT (with Advanced Data Analysis), and Gemini. Built for students and junior analysts who want outputs they can ship to dashboards, notebooks, and portfolio repos.

## Who is this for?
- Master’s students in analytics and business intelligence
- Junior data analysts and analytics engineers
- Builders creating n8n/agent workflows for reporting and operations
- Anyone who wants practical prompts instead of generic “AI magic” text

## Features
- 40+ original prompts grouped by analytics use case
- Separate prompt variants for Claude, ChatGPT, and Gemini
- Fraud analytics, SQL star-schema, KPI design, and workflow automation examples
- Portfolio and career prompts for README/CV/interview prep
- Verification-first prompting patterns to reduce hallucinated outputs

## Installation & Setup
1. Clone the repository.
```bash
git clone <your-repo-url>
cd ai-data-analyst-prompt-library
```

2. Open in VS Code.
```bash
code .
```

3. Use with Claude Code.
- Open the prompt file you want.
- Copy a Claude variant prompt.
- Paste into Claude Code or Claude web Project.
- Add your schema + sample rows before running.

4. Use with ChatGPT (web + ADA).
- Open ChatGPT in browser.
- Start a chat with Advanced Data Analysis enabled.
- Upload your CSV/Excel.
- Paste a ChatGPT variant prompt and run.

5. Use with Gemini (web).
- Open Gemini Advanced.
- Attach relevant docs/files.
- Paste a Gemini variant prompt.
- Ask it to reference attachments in the answer.

## How to Use
Choose a category, then replace placeholders.

### Claude
```text
Act as my senior analytics reviewer. Here is schema + sample rows.
Return assumptions, SQL plan, validation checks, and decision-ready summary.
```

### ChatGPT
```text
Use Advanced Data Analysis on uploaded data.
Run code for EDA + baseline model and return notebook-ready cells.
```

### Gemini
```text
Use attached docs + dataset to produce a source-grounded analysis plan.
Cite which attachment supports each key assumption.
```

> Pro tip: Keep one prompt log per project with “prompt used”, “input snapshot”, and “output quality note.” This becomes a strong interview artifact.

## How This Helps Your Portfolio
- Shows you can use AI as a structured analytics tool, not just text generation
- Demonstrates model-specific workflow design (Claude vs ChatGPT vs Gemini)
- Produces reusable assets: SQL packs, notebook stubs, KPI specs, README drafts
- Gives you concrete examples to discuss in interviews

## Contributing
- Open an issue with the use case and desired output format.
- Submit PRs with new prompts in all three model variants.
- Keep prompts original, practical, and testable.

## License
`[Choose a license: MIT / Apache-2.0 / Proprietary]`
