# PowerShell Abuse Hunting Queries

8 production-ready KQL queries for hunting PowerShell abuse in Microsoft Defender for Endpoint.

## What's Here

PowerShell is in every serious Windows intrusion. Not because attackers are creative, but because it works, it's already there, and it leaves just enough logs to make you think you're covered when you're not.

These are eight hunting queries. Every single one fired on actual simulated attacker behaviour.

## Queries

1. **01-PowerShell-Version-Downgrade.kql**: Targets attackers using Version 2 to bypass AMSI, Script Block Logging, and Constrained Language Mode.
2. **02-Suspicious-Long-Command-Lines.kql**: Identifies fileless execution patterns where attackers hide payloads in long, obfuscated command strings.
3. **03-Base64-Encoded-PowerShell.kql**: Detects classic first-stage loader patterns and decodes Base64 to search for malicious indicators.
4. **04-High-Special-Character-Ratio-Obfuscation.kql**: Targets obfuscation tools like Invoke-Obfuscation by measuring special character ratios.
5. **05-PowerShell-Download-Cradles.kql**: Provides comprehensive coverage for various download methods including Net.WebClient, Invoke-WebRequest, BITS, and HttpClient.
6. **06-PowerShell-Weakening-Windows-Defender.kql**: Looks for command-line attempts to disable Defender features or add exclusions to staging paths.
7. **07-Suspicious-PowerShell-Cmdlets.kql**: Uses DeviceEvents with PowerShellCommand ActionType to catch suspicious cmdlet execution mapping to attack phases.
8. **08-AMSI-Bypass-Attempts.kql**: Detects common AMSI bypass techniques such as field flipping or in-memory patching.

## How to Use

1. Copy any query you find useful.
2. Paste it into the Advanced Hunting portal in Microsoft Defender XDR.
3. Modify and tweak the queries as needed for your specific environment.

## Source

Full blog post: [Hunting PowerShell Abuse in MDE: Eight Queries, Real Results](https://www.itprofessor.cloud/hunting-powershell-abuse-mde-kql/)
