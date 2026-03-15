
# Lateral Movement & Credential Theft

## SharpHound Execution

SharpHound was executed twice.

This means the attacker was likely mapping Active Directory to find attack paths.

## Hash Investigation

The hash of default.exe matched one listed in the threat intelligence report.

Query used:

process.hash.sha256:018d37cbd3878258c29db3bc3f2988b6ae688843801b9abc28e6151141ab66d4

Results showed the malware on:

- WS001
- PKI server

So the attacker had already moved laterally.

## Remote Execution

Logs showed execution through:

PSEXESVC

Which comes from **PsExec**, a tool used for remote command execution.

This is often used during lateral movement.

## Compromised Account

The logs also showed activity under:

svc-sql1

Which strongly suggests that this service account was compromised.

## What I Learned

Service accounts are often targeted because:

- they have elevated privileges
- they are rarely monitored
