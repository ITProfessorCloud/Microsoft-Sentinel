# KQL Detection Engineering Repository

A production-grade collection of KQL analytic rules and hunting queries for Microsoft Sentinel, maintained by [Bartosz Wysocki](https://www.itprofessor.cloud).

Every rule and query in this repository is built to be deployed directly into production Sentinel workspaces with minimal modification. Each file ships with tuning notes, known false positives, MITRE ATT&CK mappings, and investigation guidance baked into the header.

## Repository Structure

```
/analytic-rules/     Scheduled analytic rules — ARM templates (.json) and readable KQL (.kql)
/hunting-queries/    Threat hunting and investigation queries (.kql)
```

Analytic rules ship as pairs: a deployable ARM template and a matching `.kql` file with the raw unescaped query for easy reading and modification.

## Deploying Analytic Rules

1. Open the Azure Portal and navigate to your Sentinel workspace.
2. Go to **Configuration > Analytics > Import**.
3. Upload the `.json` ARM template for the rule you want to deploy.
4. Review the rule settings, adjust any tuning parameters noted in the description, and enable.

Alternatively, deploy via Azure CLI:

```bash
az deployment group create \
  --resource-group <your-rg> \
  --template-file <rule-id>.json \
  --parameters workspace=<your-workspace-name>
```

## Query File Format

Every `.kql` file opens with a structured header covering description, tables, required license, tuning knobs, and known false positives. Read the header before running any query in production.

```
// =====================================================================
// Detection Name
// =====================================================================
// Description : What this finds
// Type        : Scheduled | Hunt | Investigation | Reporting
// Tables      : AuditLogs, IdentityInfo, ...
// Tuning      : ...
// Known FPs   : ...
// Version     : 1.0 | YYYY-MM-DD
// =====================================================================
```

## Requirements

- Microsoft Sentinel workspace
- Relevant data connectors enabled (listed per rule in the query header)

## Contributing

Pull requests are welcome. To contribute a rule or query:

1. Fork the repository.
2. Use the existing `.kql` header format and ARM skeleton for consistency.
3. Include MITRE ATT&CK mappings, tuning notes, and known false positives.
4. Submit a pull request with a short description of what the detection covers.

Rules or queries submitted without tuning guidance or false positive notes will be returned for revision before merging.

## Author

Bartosz Wysocki
[itprofessor.cloud](https://www.itprofessor.cloud)
