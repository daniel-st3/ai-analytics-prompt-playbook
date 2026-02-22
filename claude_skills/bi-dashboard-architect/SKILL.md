---
name: bi-dashboard-architect
description: Designs clear, decision-oriented BI dashboards with sound metric definitions, drill paths, and layout architecture. Use when user says "design a dashboard", "dashboard layout", "KPI definitions", "drill path", "reduce dashboard clutter", "reporting rollout", or "BI page optimization".
---

# BI Dashboard Architect

## Instructions

Design clear, decision-oriented dashboards with sound metric definitions.

### Step 1: Understand Audience and Decisions

Start with audience decisions and reporting cadence:
- Who consumes this dashboard?
- What decisions does it support?
- What is the refresh cadence (real-time, hourly, daily)?

### Step 2: Define KPI Contracts

Define each KPI with:
- Formula and calculation logic
- Grain (daily, weekly, per-user, per-transaction)
- Owner and responsible team
- Refresh logic and data source

### Step 3: Recommend Visuals

Recommend visuals that match analytical question type:
- Trend over time → Line chart
- Part-to-whole → Stacked bar or treemap
- Comparison → Grouped bar
- Distribution → Histogram or box plot

Eliminate redundant or low-value visuals.

### Step 4: Design Drill Paths

Specify drilldown paths from executive view to operational detail.

### Step 5: Add Safeguards

Include data quality and interpretation safeguards:
- Filter context warnings
- Data latency indicators
- Metric confidence notes

### Step 6: Rollout Plan

Provide rollout checklist and stakeholder adoption guidance.

## Expected Outputs

- Audience and decision map
- KPI contract table
- Proposed page wireframe (text)
- Drilldown and filter logic
- QA and validation checklist
- Rollout and adoption plan

## Examples

**Example 1: New Dashboard**
User says: "Design a fraud operations dashboard for analysts and team leads."
Result: Full dashboard architecture with KPI contracts, visual recommendations, and drill paths.

**Example 2: Dashboard Cleanup**
User says: "My Power BI page is overloaded. Propose what to remove and what to keep."
Result: Audit of existing visuals with elimination/retention recommendations.

**Example 3: Drill Path Design**
User says: "Define a drill path from exec KPI to transaction-level detail."
Result: Multi-level drilldown specification with filter inheritance logic.

## Troubleshooting

**Error: KPI definition conflicts across teams**
Solution: Create a canonical KPI contract table with single owner per metric and conflict resolution process.

**Error: Overcrowded dashboard pages**
Solution: Apply the "one question per visual" rule and remove vanity charts that don't drive decisions.

## Edge Cases

- KPI definition conflicts across teams
- Filter context producing contradictory numbers
- Slow dashboard due to model relationships
- Overcrowded pages with unclear hierarchy
- Data latency misunderstood by end users

## Practical Tips

- Share at least one screenshot of the current dashboard
- Specify refresh latency expectations (near real-time vs daily)
- Ask for a "decision-first layout" to avoid vanity charts
