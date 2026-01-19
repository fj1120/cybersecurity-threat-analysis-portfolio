# Splunk Attack Chain Analysis

## Project Overview
This project focuses on analysing security logs using Splunk to identify suspicious activity and reconstruct a potential attack chain based on real-world detection scenarios.

The objective is to understand how individual alerts and log events can be correlated and mapped to the MITRE ATT&CK framework.

## Data Source
- Log source simulated from enterprise security events
- Analysis performed using Splunk Search Processing Language (SPL)

## Analysis Approach
- Identify anomalous authentication and process execution behaviour
- Correlate multiple log events into a single attack narrative
- Map observed behaviours to relevant MITRE ATT&CK tactics and techniques

## Key Findings
- Evidence of suspicious login behaviour indicating possible initial access
- Subsequent activity suggesting persistence or lateral movement
- Indicators aligned with known ATT&CK techniques

## Skills & Tools Used
- Splunk (log search and analysis)
- MITRE ATT&CK framework
- Attack chain analysis
- Security reporting and documentation
## Outcome
This project strengthened my practical understanding of log-based threat detection, attack lifecycle analysis, and structured security reporting.

## Example Case Study

### Scenario Overview
Simulated log data was analysed to identify a potential multi-stage attack involving suspicious authentication activity and command execution.

### Evidence Observed
- Multiple failed login attempts followed by a successful login
- Execution of unusual commands shortly after authentication
- Outbound network connections to uncommon destinations

### Analysis
The behaviour suggested potential credential compromise followed by post-authentication activity.

### MITRE ATT&CK Mapping
- T1110 – Brute Force
- T1059 – Command and Scripting Interpreter
- T1071 – Application Layer Protocol

### Outcome
This exercise demonstrated how individual low-risk events can form a meaningful attack chain when correlated.
