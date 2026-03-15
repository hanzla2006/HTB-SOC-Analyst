
# Command & Control Activity

## PowerShell Activity

Using the process ID of the PowerShell process we investigated additional activity.

Query example:

process.pid:"9944" AND process.name:"powershell.exe"

This revealed:

- file creation
- DNS queries
- network connections

## Command and Control

DNS logs showed connections to **ngrok**.

Ngrok is often used to tunnel traffic and hide command and control infrastructure.

Connections were made over:

port 443

Meaning encrypted communication.

## Persistence & Payloads

Further investigation showed that:

default.exe was executed.

This malware performed several actions:

- contacted C2 servers
- uploaded files
- dropped new payloads

Uploaded tools included:

- svchost.exe (likely fake)
- SharpHound.exe
- payload.exe

SharpHound is a known Active Directory reconnaissance tool.

## What I Learned

Attackers often use legitimate tools like SharpHound during post exploitation.
