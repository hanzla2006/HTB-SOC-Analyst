
# Log Correlation & Custom XML Queries

## Concept

One important technique in log analysis is **correlating events together**.

This can be done using the **Logon ID** field.

If multiple logs share the same Logon ID, they are part of the same session. fileciteturn1file0

## My Thought Process

When I first saw Logon IDs I didn't really get why they mattered.

But then it clicked:

Instead of looking at logs individually, you can track the **entire chain of activity** that happened after a login.

So basically:

login → privilege changes → processes started → network activity

All connected with the same Logon ID.

## Using XML Queries

Windows Event Viewer allows advanced filtering using XML queries.

Steps:

1. Open Event Viewer
2. Go to **Filter Current Log**
3. Select **XML**
4. Enable **Edit query manually**

This allows very specific filtering.

## Practical Example

In the lab we analyzed:

Event ID:

```
4624
```

Which indicates a **successful login**.

We looked at:

- Logon ID
- Logon type
- account name

Then used the Logon ID to correlate with other events.

## What I Learned

Correlating logs is extremely important.

A single event doesn't mean much, but **multiple related events tell a story**.
