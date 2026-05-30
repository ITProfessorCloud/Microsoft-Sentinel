# Azure Key Vault Threat Hunting Queries

8 production-ready KQL queries for detecting threats targeting Azure Key Vault.

## What's Here

These queries help you spot attackers who've made it to Key Vault. Once an attacker has access to your secrets, the game has already shifted significantly in their favour. Use these queries to detect:

- First-time vault access patterns
- Privilege escalation via config changes
- Cross-vault enumeration
- Off-hours and anomalous access
- Managed identity abuse
- UEBA-correlated sensitive operations
- Reconnaissance via failure chains
- Certificate exfiltration attempts

## Queries

1. **01-First-Time-Vault-Access.kql**: Builds a 30-day baseline of identity/vault access and fires on any new access in the last 24 hours.
2. **02-Vault-Config-Change-Followed-By-Secret-Reads.kql**: Identifies privilege escalation where an identity modifies vault configuration and subsequently reads secrets within 30 minutes.
3. **03-Cross-Vault-Secret-Enumeration.kql**: Detects aggressive mapping of the secret estate by tracking identities accessing 3+ vaults and 5+ secrets within 24 hours.
4. **04-Off-Hours-Weekend-Or-New-IP-Access.kql**: Scores identity activity based on anomalous timing (off-hours/weekend) or use of a previously unseen IP address.
5. **05-Managed-Identity-From-External-IP.kql**: Detects when a managed identity (which should only originate from Azure) attempts access from a non-Azure/non-private IP address.
6. **06-UEBA-Correlated-Sensitive-Operations.kql**: Joins high-risk Key Vault operations (deletion, purging, etc.) with Microsoft's Behavior Analytics signals to flag potentially compromised accounts.
7. **07-Failure-Enumeration-Then-Successful-Read.kql**: Detects reconnaissance behavior where an identity guesses secret names (generating 404/403 errors) and then successfully accesses a secret shortly after.
8. **08-Certificate-Operations-Hunt.kql**: Tracks the lifecycle of certificate operations, specifically highlighting sensitive operations like backup, restore, and purging.

## How to Use

1. Copy any query you find useful.
2. Paste it into the Microsoft Sentinel portal to run it against your data.
3. Modify and tweak the queries as needed for your specific environment.

## Source

Full blog post: [Azure Key Vault: The High-Value Queries Your SOC Isn't Running](https://www.itprofessor.cloud/azure-key-vault-threat-hunting-kql/)
