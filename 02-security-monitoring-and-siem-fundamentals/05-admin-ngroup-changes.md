
# Visualization Lab 4 – Users Added or Removed from Administrators

## Goal

Monitor when users are added or removed from the local **Administrators group**.

This is very important because gaining admin privileges usually means full control of the machine.

## Important Event IDs

Windows Security Log:

- **4732 – User added to group**
- **4733 – User removed from group** fileciteturn0file0

## My Thought Process

If someone adds themselves or another user to the Administrators group it could indicate:

- privilege escalation
- malicious persistence
- admin abuse

So the idea is to track these changes.

## Filters Used

```
event.code: 4732 OR event.code: 4733
group.name: administrators
```

Then I built a table with fields:

- Member SID (who was added/removed)
- group name
- action performed
- host machine

Fields used:

- winlog.event_data.MemberSid.keyword
- group.name.keyword
- event.action.keyword
- host.name.keyword

We also restricted the time range.

The lab specifically asked for events:

```
March 5 2023 → present
```

## Lab Question

**Question:** What date did all returned events occur?

**Answer:**

```
2023-03-05
```

## What I Learned

- Admin group changes are extremely sensitive events
- Monitoring these logs helps detect privilege escalation
- Time filtering helps isolate relevant incidents
