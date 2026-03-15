
# Visualization Lab 2 – Failed Logons (Disabled Users)

## Goal

Monitor failed logon attempts against disabled accounts.

This is interesting because disabled accounts should never be used.

## Key Logs

Event ID:

- **4625 – Failed logon** fileciteturn0file0

But we also need a **SubStatus** value.

Important field:

```
winlog.event_data.SubStatus = 0xC0000072
```

This indicates:

> login failed because account is disabled.

## My Thought Process

I basically combined two filters:

1. Failed logons
2. Disabled account reason

Filters used:

```
event.code: 4625
winlog.event_data.SubStatus: 0xC0000072
```

Then I built a table visualization again.

Fields included:

- username
- host
- logon type
- count

The lab asked specifically for the **logon type**.

## Lab Question

**Question:** What is the logon type in the returned document?

**Answer:**

```
Interactive
```

## What I Learned

- Windows logs contain extra error codes explaining failures
- SubStatus values can tell the real cause of login failures
- Disabled account login attempts may indicate credential stuffing or scanning
