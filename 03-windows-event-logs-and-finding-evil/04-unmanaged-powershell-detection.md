
# Detecting Unmanaged PowerShell Attacks

## Concept

C# is a **managed language**.

It runs inside the **Common Language Runtime (CLR)**.

If we see CLR libraries loaded into a process that normally doesn't use them, something suspicious might be happening. fileciteturn1file0

## Lab Attack

The lab used:

```
spoolsv.exe
```

Normally spoolsv.exe does not run managed code.

But PowerShell injection was used to load .NET code into it.

## Attack Command

Example used:

```
Invoke-PSInject
```

This injects PowerShell into another process.

## Detection Method

We looked for DLL loads:

```
clr.dll
clrjit.dll
```

inside:

```
spoolsv.exe
```

These indicate .NET runtime execution.

## PowerShell Detection

Example query:

```
Get-SysmonEvent 7 ...
```

Then filter for:

```
spoolsv.exe
clr.dll
```

## What I Learned

CLR DLLs appearing in strange processes can indicate:

- unmanaged PowerShell
- execute assembly attacks
- in-memory malware execution
