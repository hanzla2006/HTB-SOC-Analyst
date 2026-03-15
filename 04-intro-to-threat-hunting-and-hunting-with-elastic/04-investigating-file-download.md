
# Investigating The Suspicious File Download

## Discovery

The query returned evidence that **Bob downloaded invoice.one** using Microsoft Edge.

Timestamp:

March 26 2023 @ 22:05:47

This file was saved in the Downloads folder.

## My Thought Process

At this point we still don't know if the file is malicious or if it was executed.

So the next step is verifying:

1. Was the file downloaded?
2. Was it opened?
3. Did it spawn any processes?

## Corroborating Logs

Another query used:

event.code:11 AND file.name:invoice.one*

This confirms the file creation event.

## Network Investigation

Sysmon did not capture network connections from the browser.

So the investigation switched to **Zeek DNS logs**.

Query example:

source.ip:192.168.28.130 AND dns.question.name:*

From the DNS logs we observed connections to:

- Gmail
- file hosting sites
- Microsoft Defender SmartScreen

This confirms the file was downloaded from a hosting provider.

## What I Learned

Network logs are extremely useful when host telemetry is missing.
