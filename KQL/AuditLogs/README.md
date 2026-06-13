# AuditLogs

KQL queries focused on Microsoft Entra ID auditing, administrative activity, privileged access changes, password operations, and identity security monitoring using the `AuditLogs` table.

## Available Detections

| Rule | Description | Blog |
|------|-------------|------|
| [New Privileged Role Assignment Outside Baseline](https://github.com/ITProfessorCloud/Microsoft-Sentinel/blob/main/KQL/AuditLogs/Analytic%20Rules/New%20Privileged%20Role%20Assignment%20Outside%20Baseline.json) | Detects first-seen privileged Microsoft Entra ID role assignments by comparing the last hour of activity against a 14-day baseline. Enriched with identity context, initiator history, and risk indicators to highlight potentially suspicious privilege escalation activity. | [Read Blog](https://www.itprofessor.cloud/fixing-the-privileged-role-assigned-outside-pim-analytic-rule/) |
