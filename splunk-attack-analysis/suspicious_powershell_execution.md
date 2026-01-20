🛡️ Use Case: Suspicious PowerShell Execution Detection
Scenario

This use case demonstrates how PowerShell execution logs can be analysed to identify potentially malicious behaviour, such as encoded commands commonly used in post-exploitation activities.

The objective is to simulate a basic detection scenario and map it to the MITRE ATT&CK framework.

Splunk Query (SPL Example)
index=security_logs sourcetype=windows_powershell
| search CommandLine="*-EncodedCommand*"
| stats count by User, ComputerName, CommandLine
| sort - count

Explanation:

Searches PowerShell execution logs

Identifies usage of -EncodedCommand, a common obfuscation technique

Aggregates activity by user and host to highlight abnormal patterns

🎯 MITRE ATT&CK Mapping
| Technique ID | Technique Name                             | Tactic          |
| ------------ | ------------------------------------------ | --------------- |
| T1059.001    | PowerShell                                 | Execution       |
| T1027        | Obfuscated / Encrypted File or Information | Defense Evasion |

🧠 Analyst Notes

Encoded PowerShell commands are frequently associated with malware execution and lateral movement.

This detection logic can support early-stage threat identification and incident triage.

In a production environment, this query would be refined using baselines and false-positive tuning.

📌 Value Demonstrated

Threat detection logic using log analysis

Mapping technical findings to MITRE ATT&CK

Translating raw data into risk-relevant insights

⚠️ Disclaimer

This example uses simulated detection logic for educational and portfolio purposes only. No real customer or production data is included
