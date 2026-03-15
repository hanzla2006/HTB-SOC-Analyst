
# Detecting Attacker Behavior With Splunk Based On Analytics

Here the focus was building **analytics rules**.

Meaning queries that automatically detect suspicious activity.

## Example Detection Logic

### Rare Processes

Query:

index="main" sourcetype="WinEventLog:Sysmon" EventCode=1
| rare Image

Rare processes are often suspicious.

## Parent Child Anomalies

Example detection:

notepad.exe → powershell.exe

That should basically never happen.

So it could be used as a detection rule.

## Combining Events

Using transactions to link events.

Example:

Process creation → network connection.

This can reveal malware execution chains.

## What I Learned

Good detections require:

- good understanding of normal behavior
- filtering false positives
- focusing on attacker techniques
