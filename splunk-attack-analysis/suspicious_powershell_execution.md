🛡️ Use Case: Suspicious PowerShell Execution Detection

### Scenario  
This use case simulates a security analyst reviewing PowerShell execution logs to identify potentially malicious behaviour within a corporate Windows environment.

The focus is on detecting encoded PowerShell commands, which are commonly associated with malware execution, credential access, or lateral movement.

Splunk Query (SPL Example)
index=security_logs sourcetype=windows_powershell
| search CommandLine="*-EncodedCommand*"
| stats count by User, ComputerName, CommandLine, ParentProcessName
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

These techniques align with commonly observed post-exploitation behaviours in Windows environments.

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

## Detection Context
This detection focuses on identifying potentially malicious PowerShell activity using encoded commands, which are commonly associated with post-exploitation techniques.

## Investigation Guidance
Analysts should review:
- Parent-child process relationships
- User account privilege levels
- Frequency and repetition of encoded execution
