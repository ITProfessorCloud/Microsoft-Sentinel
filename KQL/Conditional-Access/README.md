# Conditional Access Health Check Queries

Grade every Conditional Access policy by real sign-in data using KQL.

## What's Here

**01-CA-Policy-Health-Check.kql**: Comprehensive health check that grades every CA policy in your tenant based on actual behavior over the last 14 days. Shows true MFA coverage, block rates, and report-only disruption potential.

## Source

Blog: https://www.itprofessor.cloud/conditional-access-policy-health-check-kql/

## Available Detections

| Rule | Description | Blog |
| ---- | ----------- | ---- |
| [Conditional Access Bypass - Open Gate or Legacy Auth](https://github.com/ITProfessorCloud/Microsoft-Sentinel/blob/main/KQL/Conditional-Access/Analytic%20Rules/conditional-access-bypass-open-gate.json) | Detects Conditional Access bypasses rather than Conditional Access failures. Two branches are unioned: a successful authentication over a legacy protocol that grant controls cannot reach, and a true fail-open where an enforcing policy reports a per-policy failure on a sign-in that nonetheless succeeded. Additive scoring layers sign-in risk, single-factor sessions, privileged targets, and a prior run of failures against the same account, while service accounts and app passwords are suppressed. | [Read Blog](https://www.itprofessor.cloud/fixing-attempt-to-bypass-conditional-access-analytic-rule/) |
