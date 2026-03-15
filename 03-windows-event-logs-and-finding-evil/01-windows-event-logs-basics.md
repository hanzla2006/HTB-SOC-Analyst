
# Windows Event Logs Basics

## What I Understood

This section explains how Windows logs work and why they matter for SOC analysts.

Windows Event Logs store activity from different system components like:

- the operating system itself
- applications
- services
- drivers
- ETW providers

The default logs include:

- Application
- Security
- Setup
- System
- Forwarded Events

These logs help analysts understand what happened on a system. For example:

- logins
- system restarts
- service changes
- malware detections

All of these appear inside the logs. fileciteturn1file0

## My Thought Process

When I was going through this section I was mainly trying to answer:

- where logs are stored
- what logs are important
- which event IDs are commonly used in investigations

The biggest realization was that **Security logs are the most important for detecting attacks**.

## Important Event IDs

Some useful events:

System logs:

- 1074 → System shutdown or restart
- 6005 → Event log service started
- 6006 → Event log service stopped
- 6013 → System uptime

Security logs:

- 4624 → Successful login
- 4625 → Failed login
- 4648 → Logon with explicit credentials
- 4672 → Special privileges assigned
- 4698 → Scheduled task created

## What I Learned

Logs are basically **the timeline of what happened on a machine**.

Without logs, investigations would be almost impossible.
