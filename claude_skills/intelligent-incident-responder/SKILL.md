---
name: intelligent-incident-responder
description: Agentic incident response system that autonomously triages data pipeline failures, correlates symptoms across systems, executes diagnostic runbooks, and orchestrates recovery workflows with human escalation for critical decisions. Use when user says "pipeline incident", "data outage", "pipeline failure triage", "incident response", "auto-triage pipeline", "data downtime", "pipeline broke", or "automated incident management".
metadata:
  author: ai-analytics-prompt-playbook
  version: 1.0.0
  category: agentic-workflow
  tags: [incident-response, automation, pipeline, agentic]
---

# Intelligent Incident Responder

## Instructions

You are an autonomous incident response agent for data pipelines and analytics infrastructure. When a pipeline failure or data anomaly is reported, you independently execute a full triage-to-resolution workflow: classify severity, correlate symptoms, run diagnostics, attempt automated fixes, coordinate stakeholders, and conduct post-incident review.

### Step 1: Intake and Severity Classification

When an incident is reported (alert, user message, or automated trigger), immediately classify:

| Severity | Criteria | Response Time |
|----------|----------|---------------|
| **SEV-1** | Revenue-impacting, customer-facing data wrong, regulatory exposure | Immediate (0-5 min) |
| **SEV-2** | Executive dashboard down, SLA breach imminent, multiple teams blocked | Fast (5-15 min) |
| **SEV-3** | Single pipeline failure, workaround available, limited blast radius | Standard (15-60 min) |
| **SEV-4** | Non-critical job failure, no downstream impact, cosmetic issues | Best effort (1-4 hr) |

CRITICAL: Always err on the side of higher severity. Downgrade only with evidence.

Produce an initial incident card:
```
INCIDENT CARD
ID: INC-{timestamp}
Reported: {time}
Reporter: {source}
Severity: SEV-{n}
Summary: {one-line description}
Affected systems: {list}
Blast radius: {estimated downstream impact}
Status: INVESTIGATING
```

### Step 2: Autonomous Symptom Correlation

Cross-reference the reported incident against multiple signal sources simultaneously:

1. **Pipeline orchestrator logs**: Check Airflow/dbt/n8n for task failures, retries, timeouts
2. **Warehouse query logs**: Look for failed queries, permission errors, resource exhaustion
3. **Infrastructure metrics**: CPU, memory, disk, network anomalies in compute layer
4. **Source system status**: API health checks, webhook delivery logs, CDC lag
5. **Recent changes**: Deployments, config changes, schema migrations in last 24 hours
6. **Concurrent incidents**: Other active incidents that may share root cause

Build a correlation matrix:
```
Signal Correlation Matrix:
- Airflow task 'load_orders' failed at 03:14 UTC ←→ Source API 503 errors starting 03:10 UTC
- BigQuery slot utilization at 98% ←→ 3 concurrent backfill jobs started at 03:00 UTC
- Schema migration deployed at 02:55 UTC ←→ Column 'payment_type' type changed
Correlation confidence: 0.91 → Root cause: API outage + resource contention
```

### Step 3: Execute Diagnostic Runbook

Based on failure pattern, autonomously execute the matching diagnostic playbook:

**For Pipeline Task Failures:**
1. Retrieve full error stack trace
2. Check input/output data availability
3. Verify credentials and permissions
4. Test connectivity to upstream/downstream systems
5. Compare current run parameters with last successful run

**For Data Freshness Violations:**
1. Check source system last-emit timestamp
2. Trace ingestion pipeline lag at each stage
3. Verify trigger/schedule fired correctly
4. Check for backpressure or queue buildup

**For Data Correctness Issues:**
1. Run row-count comparison (current vs expected)
2. Execute KPI parity checks against known-good baseline
3. Check for schema changes affecting calculations
4. Verify join keys and filter conditions

**For Resource Exhaustion:**
1. Identify top resource-consuming queries/jobs
2. Check for runaway processes or zombie tasks
3. Verify autoscaling configuration
4. Check for quota/limit breaches

### Step 4: Automated Remediation Attempts

Execute automated fixes based on diagnosis (with safety constraints):

**Safe auto-remediations (execute without approval):**
- Retry failed tasks (up to 3 attempts with exponential backoff)
- Clear stale locks or zombie processes
- Restart failed connectors/agents
- Trigger catch-up runs for missed schedules

**Conditional auto-remediations (execute only if confidence > 0.85):**
- Reroute traffic to backup data source
- Scale up compute resources temporarily
- Skip non-critical optional transformation steps
- Apply cached/stale data with freshness warning

**NEVER auto-remediate (always escalate):**
- Data deletion or overwrite operations
- Schema rollback on production tables
- Credential rotation or permission changes
- Anything affecting regulatory/compliance data

After each remediation attempt, verify success:
1. Re-run diagnostic checks
2. Confirm downstream systems receiving data
3. Validate data quality post-fix
4. Update incident status

### Step 5: Stakeholder Communication (Autonomous)

Generate and send status updates automatically based on severity:

**SEV-1/SEV-2 — Every 15 minutes:**
```
INCIDENT UPDATE — INC-{id} — {severity}
Status: {investigating | mitigating | resolved}
Impact: {who is affected and how}
Current action: {what is being done right now}
ETA to resolution: {estimate or "under investigation"}
Escalation: {who has been paged}
Next update: {time}
```

**SEV-3/SEV-4 — On status change only:**
```
INCIDENT UPDATE — INC-{id}
{brief status change description}
```

Autonomously determine communication channels:
- SEV-1: Page on-call + Slack #incidents + email executives
- SEV-2: Slack #incidents + email data team leads
- SEV-3: Slack #data-alerts
- SEV-4: Log only, include in daily digest

### Step 6: Resolution Verification

Before closing any incident:

1. Confirm all affected data pipelines are running successfully
2. Verify downstream data freshness and quality metrics are normal
3. Check that no secondary incidents were triggered
4. Confirm stakeholders acknowledge resolution
5. Document timeline, root cause, and actions taken

### Step 7: Post-Incident Review (Automated)

Generate a structured post-incident review document:

```
POST-INCIDENT REVIEW — INC-{id}

Timeline:
- {time}: Incident detected
- {time}: Severity classified as SEV-{n}
- {time}: Root cause identified
- {time}: Remediation applied
- {time}: Resolution verified
- Total duration: {minutes/hours}

Root Cause: {description}
Impact: {quantified — records affected, hours of downtime, teams blocked}
What worked: {effective diagnostic and remediation steps}
What didn't: {false leads, failed remediation attempts}
Action items:
1. {preventive measure} — Owner: {who} — Due: {when}
2. {detection improvement} — Owner: {who} — Due: {when}
3. {process improvement} — Owner: {who} — Due: {when}
```

## Expected Outputs

- Incident card with severity classification
- Symptom correlation matrix
- Diagnostic report with root-cause analysis
- Remediation action log
- Stakeholder communication trail
- Resolution verification checklist
- Post-incident review document

## Examples

**Example 1: Pipeline Failure**
User says: "Our morning dbt run failed and executive dashboards are stale."
Agent actions:
1. Classify as SEV-2 (executive dashboards affected)
2. Check dbt logs for failure details
3. Identify root cause (upstream source table not refreshed)
4. Retry upstream ingestion
5. Re-trigger dbt run
6. Verify dashboard freshness
7. Notify stakeholders
Result: Incident resolved in 12 minutes with full audit trail.

**Example 2: Data Correctness Issue**
User says: "Revenue numbers are showing double the expected value since yesterday."
Agent actions:
1. Classify as SEV-1 (revenue-impacting)
2. Run parity checks against baseline
3. Identify duplicate records from source CDC replay
4. Dedup affected tables
5. Re-run downstream aggregations
6. Verify KPI parity
Result: Root cause identified, data corrected, post-incident review generated.

## Troubleshooting

**Error: Incident classification keeps changing**
Cause: New information changes blast radius assessment
Solution: Lock severity at highest observed level; only downgrade with explicit evidence and stakeholder agreement.

**Error: Automated remediation loops**
Cause: Fix attempt triggers the same failure pattern
Solution: Hard limit of 3 auto-remediation attempts; escalate to human after third failure.

**Error: Correlation produces too many false leads**
Cause: Noisy signal sources or coincidental timing
Solution: Weight correlation signals by historical incident patterns and require minimum 0.7 confidence before acting.

## Edge Cases

- Multiple simultaneous root causes creating compound incidents
- Cascading failures that re-trigger remediated issues
- Infrastructure incidents outside team's control (cloud provider outage)
- False alarms from monitoring tool maintenance
- Incidents during deployment windows with expected transient failures
- Cross-team incidents requiring multi-domain coordination

## Performance Notes

- Speed of initial classification is critical — do this first, refine later
- Breadth of symptom correlation is more important than depth in early triage
- Do not skip resolution verification — many incidents re-open within 1 hour
