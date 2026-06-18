# DeviceLogonEvents

KQL queries focused on endpoint authentication activity, interactive and remote logons, lateral movement detection, account usage monitoring, and endpoint security analytics using the `DeviceLogonEvents` table from Microsoft Defender for Endpoint.

## Available Detections

| Rule | Description | Blog |
| ---- | ----------- | ---- |
| [Rare RDP Connections](https://github.com/ITProfessorCloud/Microsoft-Sentinel/blob/main/KQL/DeviceLogonEvents/Analytic%20Rules/Rare%20RDP%20Connections%20MDE.json) | Detects RemoteInteractive (RDP) logons that are new by destination (account has not RDP'd to this host in 14 days), new by source host, or arriving from a public source. Enriched with local administrator status, identity context, and native Defender endpoint telemetry to improve coverage and reduce the silent visibility gaps commonly seen with Security Event–based detections. | [Read Blog](https://www.itprofessor.cloud/fixing-the-rare-rdp-connections-analytic-rule/) |
