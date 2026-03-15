
# Using Get-WinEvent for Log Analysis

## What Get-WinEvent Does

Get-WinEvent is a PowerShell command used to retrieve Windows event logs. fileciteturn1file0

It allows analysts to:

- filter logs
- query multiple logs
- parse events quickly

## Listing Logs

Example:

```
Get-WinEvent -ListLog *
```

This shows all available logs.

## Querying Events

Example:

```
Get-WinEvent -LogName System -MaxEvents 50
```

This retrieves system logs.

## Filtering by Event ID

Example:

```
Get-WinEvent -FilterHashtable @{LogName='Sysmon'; ID=1}
```

This returns Sysmon process creation events.

## Filtering by Date

Example:

```
StartTime
EndTime
```

This is useful during investigations.

## What I Learned

PowerShell log analysis is extremely powerful because:

- it scales better than GUI tools
- allows automation
- supports complex filtering
