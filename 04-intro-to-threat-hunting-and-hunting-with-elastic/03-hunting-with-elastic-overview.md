
# Hunting With The Elastic Stack

## Available Data Sources

The organization in the lab is using the **Elastic stack as a SIEM**.

Logs available include:

- Windows logs
- Sysmon logs
- PowerShell logs
- Zeek network logs fileciteturn2file0

So basically we have both **host telemetry and network telemetry**.

## My Thinking Here

When starting a hunt I tried to think:

Where would evidence of this attack appear first?

Since the report mentioned **invoice.one**, the first step is to search for that filename.

## Query Used

The module suggested starting with Sysmon download events.

Example query:

event.code:15 AND file.name:*invoice.one

This checks for file downloads related to that name.

## What I Learned

Threat hunting usually starts with:

- threat intelligence
- IOCs
- suspicious file names or hashes
