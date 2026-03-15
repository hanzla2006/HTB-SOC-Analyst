
# Visualization Lab 3 – Service Account RDP Logons

## Goal

Detect **RDP logons performed using service accounts**.

This is suspicious because service accounts should not normally be used interactively.

In this environment all service accounts start with:

```
svc-
```

## Important Event

Event ID:

- **4624 – Successful logon** fileciteturn0file0

## My Thought Process

To detect RDP logons I needed to:

1. Look for successful logons
2. Filter logon type **RemoteInteractive** (RDP)
3. Look for usernames starting with `svc-`

The idea is:

If a service account logs in via RDP it might mean:

- credential misuse
- attacker using service credentials
- lateral movement

## Steps

Filters used:

```
event.code: 4624
```
Logon type:

```
RemoteInteractive
```

Then I added fields to table:

- username
- source IP
- machine

## Lab Question

**Question:** What IP initiated the successful RDP logon using a service account?

**Answer:**

```
192.168.28.130
```

## What I Learned

- Service accounts usually have high privileges
- They should not be used for RDP
- Monitoring them helps detect lateral movement attacks
