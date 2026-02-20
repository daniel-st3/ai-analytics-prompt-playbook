## Using AI to Draft a Data Analyst Portfolio and GitHub README in One Evening

## Overview
This tutorial is a practical publishing sprint: convert existing analytics work into high-quality portfolio assets in one evening. You are not inventing achievements. You are packaging real work so recruiters and hiring managers can quickly understand value. The deliverables are clear: improved README(s), website-ready project cards, role-specific resume bullets, and interview talking points.

The strategy is evidence-first. Many weak portfolios fail because they rely on vague language (“analyzed data,” “built dashboard”) without proof. In this sprint, every claim ties to a visible artifact: metric table, chart screenshot, SQL snippet, workflow diagram, or documented limitation. Claude helps structure narrative, ChatGPT helps generate clean Markdown variants, and Gemini helps ground writing across multiple files.

## Prerequisites
1. Install Git and VS Code.
2. Gather one or two analytics projects with notebooks/queries/dashboards.
3. Collect supporting artifacts: screenshots, metrics table, and short method notes.

```bash
mkdir portfolio-evening-sprint
cd portfolio-evening-sprint
git init
code .
```

If your projects are in separate repos:

```bash
git clone <repo-1>
git clone <repo-2>
```

## Step-by-Step

### Step 1: Build an evidence pack per project
Create a simple evidence table for each project:
- problem statement
- business context
- data source + scale
- method used
- key result (metric or outcome)
- limitations
- next iteration
This table becomes the source of truth for every AI-generated asset.

#### Using Claude for this step
```text
<context>
I want evidence-based portfolio documents.
</context>
<task>
Create an evidence-pack template and identify missing proof points from my project notes.
</task>
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then convert my raw notes into an evidence table with confidence level per claim.
```

#### Using Gemini for this step
```text
Using attached notebook, dashboard screenshots, and report docs,
extract a source-grounded evidence pack with explicit references.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If AI adds claims with no proof:
```text
Strict evidence mode: only include claims supported by attached artifacts.
For unsupported statements, write "evidence missing".
```

### Step 2: Draft README v1 with consistent structure
Use a repeatable README structure across projects:
1) What problem this solves  
2) Data + method  
3) Results and limitations  
4) How to run  
5) What to improve next
Consistency makes your GitHub feel intentional and professional.

#### Using Claude for this step
```text
Rewrite this project into a recruiter-friendly README with a 60-second skim section and a technical deep-dive.
Keep all claims evidence-based.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then draft README markdown with setup commands, results table, and limitations.
```

#### Using Gemini for this step
```text
Use attached repo files and evidence pack.
Draft a source-grounded README where each claim maps to an artifact.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If setup instructions are incorrect or generic:
```text
Regenerate setup using only files in this repo tree: [paste tree].
If a command is uncertain, mark it clearly as "verify before publish".
```

### Step 3: Create role-specific portfolio summaries
From each README, create three role-targeted summaries: Data Analyst, BI Analyst, Analytics Engineer. Do not rewrite project facts; change emphasis based on role. For BI focus on metric clarity/dashboard impact; for analytics engineering focus on pipeline and reliability.

#### Using Claude for this step
```text
Create three role-specific summaries from this README without changing core project facts.
Highlight different strengths per role.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Generate role-specific variants and a keyword alignment table for ATS readability.
```

#### Using Gemini for this step
```text
Use attached job descriptions and project artifacts.
Create source-grounded role-fit summaries and identify missing evidence for each role.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If summaries add untrue responsibilities:
```text
Do not add responsibilities not present in my project record.
Rewrite and include an evidence tag after each claim.
```

### Step 4: Build interview stories and resume bullets from evidence
Use your evidence pack to create STAR-style stories and concise bullets. Each story should include a challenge, your action, result, and one reflection. This helps you answer behavioral and technical interview questions with confidence.

#### Using Claude for this step
```text
Extract 6 STAR stories from this evidence pack and map each to interview competencies.
Provide 60-second and 2-minute versions.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Generate resume bullets (Data Analyst and BI variants) with evidence-linked outcomes.
```

#### Using Gemini for this step
```text
Use attached CV + project evidence + target role docs.
Produce source-grounded interview stories and role-specific bullet suggestions.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If bullets sound inflated:
```text
Rewrite in conservative mode.
Use quantified outcomes only when directly supported; otherwise use verified process outcomes.
```

### Step 5: Final quality check and publish workflow
Before publishing, run a final review pass:
- Are claims evidence-based?
- Are setup steps reproducible?
- Are limitations explicit?
- Is project scope clear?
Then push updates and add links to portfolio website and CV.

#### Using Claude for this step
```text
Review this README and portfolio summary as a hiring manager.
Score clarity, rigor, credibility, and suggest top 5 fixes before publish.
```

#### Using ChatGPT for this step
```text
Use o1/o3 to reason through edge cases before execution.
Then produce a final pre-publish checklist and concise changelog summary.
```

#### Using Gemini for this step
```text
Use attached final docs and artifacts.
Perform a source-grounded consistency check and list unresolved weak points.
```

#### Troubleshooting / Handling AI Hallucinations for this step
If AI review misses obvious inconsistencies:
```text
Re-run review using this rule:
Check every claim against evidence table row by row.
Return a mismatch list with file references.
```

## Using Claude
Use Claude to keep narrative consistent across README, portfolio cards, and interview stories. Ask for strict evidence mode when polishing claims.

## Using ChatGPT
Use ChatGPT for rapid generation of format variants and reusable templates. Keep the o1/o3 reasoning-first workflow before final drafting.

## Using Gemini
Use Gemini when your portfolio evidence is spread across many files and formats. Require source mapping so every claim stays defensible.

## Next Steps
1. Add one “automation + analytics” project to differentiate your profile.
2. Add architecture diagrams and one failure lesson per project.
3. Schedule a weekly 45-minute portfolio maintenance ritual.
