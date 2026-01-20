# Risk Assessment – Obfuscated PowerShell Usage

## Risk Context
PowerShell is a legitimate administrative tool widely used in enterprise Windows environments. However, when combined with obfuscation techniques such as Base64 encoding, it poses a significant security and governance risk.

## Identified Risk
The execution of encoded PowerShell commands reduces visibility for security monitoring tools and increases the likelihood of undetected malicious activity.

## Threat Scenario
An attacker may leverage encoded PowerShell to:
- Execute malware without dropping files to disk
- Bypass basic signature-based detection
- Maintain persistence or establish command-and-control channels

## Potential Business Impact
- Unauthorized system access
- Data confidentiality breaches
- Regulatory non-compliance (e.g., ISO 27001 control failures)
- Reputational damage

## Existing Controls
- Endpoint antivirus software
- Basic command-line logging

## Control Gaps
- Lack of advanced PowerShell logging
- Limited behavioural detection rules
- Insufficient user privilege restrictions

## Risk Rating
| Likelihood | Impact | Overall Risk |
|----------|--------|--------------|
| Medium   | High   | Medium-High  |

## Recommended Control Improvements
- Enable enhanced PowerShell logging (Script Block Logging)
- Apply least privilege principles for administrative tools
- Implement behaviour-based detection rules
- Regular review of endpoint execution telemetry

## Governance Alignment
This risk assessment aligns with:
- ISO/IEC 27001 A.12 (Operations Security)
- ISO/IEC 27001 A.9 (Access Control)
- NIST CSF – Detect & Respond functions
