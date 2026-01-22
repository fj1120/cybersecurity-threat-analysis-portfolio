# PowerShell Obfuscation Detection Analysis

## Attack Overview
PowerShell obfuscation is a common technique used by attackers to evade detection by security controls. 
By encoding, compressing, or dynamically reconstructing commands at runtime, malicious actors can bypass 
signature-based detection and execute payloads stealthily within legitimate Windows environments.

This technique is frequently observed during post-exploitation phases and is often associated with 
credential access, persistence, lateral movement, or command-and-control activities.

---

## Detection Objective
The objective of this analysis is to identify suspicious PowerShell executions that exhibit obfuscation 
patterns, assess their potential security impact, and map the observed behaviour to the MITRE ATT&CK framework.

---

## Data Source
- **Platform:** Splunk
- **Log Type:** Windows Process Creation / PowerShell Operational Logs
- **Scope:** Redacted enterprise-style logs for academic and portfolio demonstration purposes

---

## Detection Logic (Splunk SPL)

```spl
index=windows_logs
| search Image="*powershell.exe*" CommandLine="*-enc*" OR CommandLine="*FromBase64String*"
| stats count by Host, User, CommandLine
| sort - count
```

### Detection Rationale:  
- Use of `–enc` and Base64 decoding functions is a strong indicator of obfuscation.  
- These techniques are commonly used to conceal malicious intent and payloads.  

---

### Incident Analysis  
The detected PowerShell executions show characteristics consistent with obfuscated command execution:  
- Encoded command-line arguments  
- Use of PowerShell-native decoding functions  
- Execution under non-administrative user contexts in some cases  

While obfuscation alone does not confirm malicious intent, the combination of encoding techniques and execution context significantly increases the risk profile of the activity.  

---

### MITRE ATT&CK Mapping  

| Tactics        | Technique ID | Technique Name                  |
|----------------|--------------|---------------------------------|
| Defense Evasion | T1027        | Obfuscated/Compressed Files     |
| Execution      | T1059.001    | PowerShell                      |

---

### Detection Limitations  
- Legitimate administrative scripts may use encoded commands.  
- Additional contextual signals (parent process, network activity, user behaviour) are required to reduce false positives.  

---

### Analyst Notes  
This detection should be treated as a **high-signal behavioural indicator** rather than a standalone alert.  
Recommended next steps include:  

- Correlating with network connections  
- Reviewing parent-child process relationships  
- Assessing user role and historical behaviour  

---

### Conclusion  
This analysis demonstrates how behavioural indicators in PowerShell execution can be leveraged to detect obfuscation techniques commonly used by attackers. The approach aligns with real-world SOC detection practices and supports risk-based security monitoring.
