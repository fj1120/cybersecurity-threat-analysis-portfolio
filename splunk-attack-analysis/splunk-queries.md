# Splunk Query Examples

## Suspicious PowerShell Execution

```spl
index=security_logs
process_name="powershell.exe"
CommandLine="*-enc*"
Purpose:
Detect encoded PowerShell commands often associated with initial access or execution.

Network Connection to Suspicious External IP
index=network_logs
dest_ip!=10.0.0.0/8
dest_port=443
Purpose:
Identify outbound connections to external IPs that may indicate command and control activity.

Privilege Discovery Commands
index=security_logs
(process_name="cmd.exe" OR process_name="powershell.exe")
(CommandLine="*whoami*" OR CommandLine="*net user*")
Purpose:
Detect discovery activity following initial compromise.
