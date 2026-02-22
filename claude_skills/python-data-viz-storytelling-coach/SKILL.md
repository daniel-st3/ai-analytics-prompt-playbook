---
name: python-data-viz-storytelling-coach
description: Turns raw DataFrame outputs into executive-ready visual stories using Seaborn/Plotly with analytical rigor and narrative constraints. Use when user says "data visualization", "chart story", "executive deck", "Seaborn chart", "Plotly visual", "data storytelling", "chart annotations", or "presentation visuals".
---

# Python Data Viz & Storytelling Coach

## Instructions

Turn raw DataFrame outputs into executive-ready visual stories using Seaborn/Plotly with analytical rigor and narrative constraints.

### Step 1: Confirm Context

Confirm audience, decision goal, and chart constraints before plotting.

### Step 2: Narrative Arc

Recommend a narrative arc: context -> trend -> diagnosis -> action.

### Step 3: Chart Type Selection

Select chart types based on analytical question, not aesthetics.

### Step 4: Generate Code

Generate Seaborn/Plotly code with readable labels, legends, and units.

### Step 5: Annotation Guidance

Add annotation guidance for key inflection points and anomalies.

### Step 6: Accessibility Checks

Include accessibility checks:
- Color contrast
- Label readability
- Color-blind safe palettes

### Step 7: Misread Risk Notes

Add one "misread risk" note per chart and how to prevent it.

### Step 8: Reproducibility

Keep charts reproducible from raw DataFrame transformations.

## Expected Outputs

- Story objective and audience
- Recommended chart sequence
- Python code blocks
- Annotation/caption guidance
- Quality and interpretation checks
- Final presentation outline

## Examples

**Example 1: Executive Churn Story**
User says: "I have churn analysis output. Build a 5-chart executive story for operations leaders."
Result: Narrative-driven chart sequence with Python code and slide-ready captions.

**Example 2: Model Metrics for Non-Technical Audience**
User says: "Convert these model metrics into visuals a non-technical hiring manager can understand."
Result: Simplified chart set with plain-language annotations.

**Example 3: Library Selection**
User says: "Help me choose between Seaborn and Plotly for a client review deck."
Result: Comparison with recommendations based on use case.

## Troubleshooting

**Error: Code references missing DataFrame columns**
Solution: Use only provided DataFrame columns. Regenerate all chart code and include one validation snippet per chart.

**Error: Narrative overstates causality**
Solution: Rewrite captions in correlation-safe mode. Mark causal claims as hypotheses unless experimental evidence exists.

## Edge Cases

- Dual-axis visuals causing misleading comparisons
- Outliers compressing key distribution patterns
- Time-series gaps creating false trend interpretations
- Excessive category counts causing unreadable visuals
- Interactive chart defaults hiding critical uncertainty

## Practical Tips

- Ask for a "one-slide summary" and "technical appendix" variant
- Paste target meeting context for better narrative prioritization
- Request a color palette suitable for light and dark projection conditions
