
# Threat Intelligence – Stuxbot

## Scenario Overview

The module introduces a threat intelligence report about a cybercrime group called **Stuxbot**.

From the report:

- Platform targeted: **Microsoft Windows**
- Attack method: **Phishing**
- Goal: espionage / system compromise

The report explains that victims receive phishing emails that contain a link to a malicious OneNote file. fileciteturn2file0

## Attack Chain (Simplified)

From the diagrams and explanation in the module the attack flow looked like this:

1. Phishing email
2. OneNote file download
3. Hidden button inside OneNote
4. Batch file execution
5. PowerShell script download
6. RAT execution

## RAT Capabilities

The RAT used by the attackers can:

- capture screenshots
- run commands
- execute mimikatz
- provide remote shell

Basically full control of the machine.

## Indicators of Compromise

The report also gave a list of IOCs like:

- malicious OneNote files
- Pastebin scripts
- command & control IPs
- file hashes

These are used during hunting to search for signs of compromise.

## What I Learned

Threat intelligence reports give you:

- attacker techniques
- infrastructure
- IOCs

But you still have to **verify if your environment was affected**.
