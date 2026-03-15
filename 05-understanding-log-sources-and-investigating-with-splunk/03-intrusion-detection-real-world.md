
# Intrusion Detection With Splunk (Real-world Scenario)

This was probably the most interesting part of the module.

Instead of analyzing logs from one host, we analyzed **logs from an entire environment**.

## First Step – Understand The Data

Query used:

index="main" | stats count by sourcetype

Goal:

See what kinds of logs exist.

Example sourcetypes:

- WinEventLog:Sysmon
- linux:syslog

## Investigating Sysmon Logs

Focus on process creation events.

EventCode = 1

Query:

index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | stats count by ParentImage, Image

This shows **parent → child process relationships**.

## Suspicious Process Chain

One thing that stood out:

notepad.exe → powershell.exe

That is weird because Notepad normally doesn't spawn PowerShell.

## Investigating The Command

The PowerShell command was downloading a file from:

10.0.0.229

So next step was investigating that IP.

## Pivot To Network Investigation

Query:

index="main" 10.0.0.229

Found:

The IP belongs to a Linux system.

Which means:

- Windows machine downloaded malware
- from a Linux server

## DCSync Detection

Query used:

index="main" EventCode=4662 Access_Mask=0x100 Account_Name!=*$

This identifies potential **DCSync attacks**.

The GUID showed:

DS-Replication-Get-Changes-All

Meaning someone tried replicating AD secrets.

So basically attacker stole domain credentials.

## LSASS Access

Another suspicious event:

Processes accessing **lsass.exe**.

Query:

index="main" EventCode=10 lsass | stats count by SourceImage

Strange ones:

- notepad.exe
- rundll32.exe

These processes shouldn't normally touch LSASS.

## Detection Idea

Look for **UNKNOWN memory regions in CallTrace**.

Query:

index="main" CallTrace="*UNKNOWN*" | stats count by SourceImage

This can indicate:

shellcode injection.

## What I Learned

Detection is about:

- filtering noise
- removing false positives
- focusing on suspicious behavior patterns
