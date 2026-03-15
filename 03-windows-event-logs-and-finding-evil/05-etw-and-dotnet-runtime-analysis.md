
# Event Tracing for Windows (ETW)

## What ETW Is

ETW stands for **Event Tracing for Windows**.

It is a high-speed logging system built into Windows that records detailed events about system activity. fileciteturn1file0

Unlike normal logs, ETW provides much deeper telemetry.

## Tools Used

The lab used:

```
logman
SilkETW
```

These tools allow monitoring ETW providers.

Example command:

```
logman query providers
```

This lists available providers.

## Practical Lab

The lab simulated execution of:

```
Seatbelt.exe
```

Seatbelt is a .NET reconnaissance tool often used by attackers.

We collected ETW logs from:

```
Microsoft-Windows-DotNETRuntime
```

Then searched the ETW output file:

```
etw.json
```

For the field:

```
ManagedInteropMethodName
```

## What I Learned

ETW provides extremely detailed telemetry about:

- .NET execution
- assembly loading
- runtime behavior

Which is very useful for detecting in-memory attacks.
