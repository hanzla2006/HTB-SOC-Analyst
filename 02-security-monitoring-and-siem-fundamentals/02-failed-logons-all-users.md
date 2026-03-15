
# Visualization Lab 1 – Failed Logon Attempts (All Users)

## Goal

Create a visualization that shows failed Windows logon attempts.

This uses Windows Event ID:

- **4625 – Failed logon attempt** fileciteturn0file0

## My Thought Process

When building the visualization I tried to think like a SOC analyst.

If attackers try brute force or password spraying, they will generate a lot of failed login events. So monitoring event ID 4625 makes sense.

Steps I followed:

1. Set time range to **last 15 years**
2. Filter events:
   - `event.code: 4625`
3. Select dataset:
   - `windows*`
4. Build a table visualization
5. Add rows:
   - `user.name.keyword`
6. Add metrics:
   - `count`

At this point the table shows usernames with failed login attempts.

Then we improved it with more context:

Extra fields added:

- host.hostname.keyword (machine name)
- winlog.logon.type.keyword (logon type)

We also renamed columns to be easier to read.

## Cleaning the Data

The SOC manager suggested removing noisy accounts.

So we filtered out:

- DESKTOP-DPOESND
- WIN-OK9BH1BCKSD
- WIN-RMMGJA7T9TC

Also excluded computer accounts:

```
NOT user.name: *$ AND winlog.channel.keyword: Security
```

This prevents machine accounts from polluting the results.

## Lab Question

**Question:** Number of logins for `sql-svc1`

**Answer:**

```
2
```

## What I Learned

- Failed logon monitoring is very important for detecting attacks
- Filtering noisy accounts is necessary
- Visualization helps quickly identify suspicious users
