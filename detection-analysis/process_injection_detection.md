# Process Injection Analysis (Blue Team Perspective)

## Project Overview
This project analyses Windows process injection techniques commonly used by malware
to evade detection by executing code within legitimate processes. The focus is on
understanding attacker behaviour and identifying defensive detection opportunities
from a blue team and security operations perspective.

## Background
Process injection is a widely used technique by adversaries to bypass security
controls and persist within trusted Windows processes. This project explores how
such techniques operate at a technical level and how defenders can detect and
mitigate them.

## Objectives
- Understand how Windows process injection works in practice
- Validate injection behaviour using system monitoring tools
- Map observed behaviour to the MITRE ATT&CK framework
- Identify indicators relevant to endpoint detection and response (EDR)
- Provide defensive and monitoring recommendations

## Environment
- Operating System: Windows 10 x64
- Target Process: notepad.exe
- Analysis Tools:
  - Process Hacker
  - Process Monitor (ProcMon)

## Key Techniques Analysed
- OpenProcess
- VirtualAllocEx
- WriteProcessMemory
- CreateRemoteThread
- LoadLibraryA

## Security Value
This project demonstrates practical understanding of Windows internals, attacker
tradecraft, and defensive detection strategies relevant to SOC analysts, security
engineers, and risk-focused cybersecurity roles.

## Disclaimer
This project is for educational and defensive security research purposes only.
