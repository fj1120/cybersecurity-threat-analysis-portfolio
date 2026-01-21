# Detection Analysis: Suspicious PowerShell Execution

## Detection Objective

The objective of this detection is to identify suspicious or malicious PowerShell executions
that may indicate post-exploitation activity, such as command execution, payload download,
or lateral movement, while minimising false positives from legitimate administrative use.

## Threat Context

PowerShell is a powerful administrative tool commonly abused by attackers due to its
native presence on Windows systems and ability to execute in-memory payloads.

Adversaries often leverage PowerShell for:
- Obfuscated command execution
- Downloading and executing remote payloads
- Bypassing traditional security controls

This behaviour aligns with MITRE ATT&CK technique T1059.001 (Command and Scripting Interpreter: PowerShell).

## Detection Signals

Potential indicators of suspicious PowerShell activity include:

- PowerShell launched with encoded or obfuscated command parameters (e.g. -EncodedCommand)
- Execution from unusual parent processes (e.g. Office applications, browsers)
- PowerShell initiating outbound network connections
- High-frequency PowerShell executions within a short time window
- PowerShell running under non-administrative user accounts unexpectedly
- 
## Example Detection Logic

A basic detection approach may include monitoring process creation events
where the process name is powershell.exe or pwsh.exe and command-line arguments
contain suspicious patterns such as:

- EncodedCommand
- Invoke-WebRequest
- DownloadString
- FromBase64String

These indicators should be correlated with user context and parent process
to reduce false positives.

## Detection Limitations and False Positives

Legitimate system administrators and automation tools may use PowerShell
with advanced parameters, which can generate false positives.

Detection accuracy can be improved by:
- Establishing baselines for normal PowerShell usage
- Whitelisting known administrative scripts
- Correlating PowerShell activity with additional telemetry such as network or file events

 ## Defensive Value

Effective monitoring of PowerShell activity provides high visibility into
post-exploitation techniques and enables early detection of attacker behaviour
before significant impact occurs.

