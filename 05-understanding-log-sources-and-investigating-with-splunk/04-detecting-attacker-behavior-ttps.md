
# Detecting Attacker Behavior With Splunk Based On TTPs

This section focused on using **MITRE ATT&CK style detection logic**.

Instead of looking for specific malware, we look for **attacker techniques**.

Examples:

- credential dumping
- lateral movement
- command execution
- persistence

## Example Detection Ideas

### PowerShell Execution

index="main" Image="*powershell.exe"

Attackers use PowerShell for:

- download payloads
- execute scripts
- privilege escalation

### Credential Dumping

Look for processes interacting with **LSASS**.

### Network Recon

Tools like:

- net view
- SharpHound

These indicate attackers mapping the network.

## Why TTPs Are Better

Signatures detect **known malware**.

But TTP detection finds **unknown malware doing known techniques**.

Which is way stronger for real SOC environments.
