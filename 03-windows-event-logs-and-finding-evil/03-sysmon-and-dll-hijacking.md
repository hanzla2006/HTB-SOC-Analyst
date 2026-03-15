
# Sysmon & DLL Hijacking Detection

## What Sysmon Is

Sysmon is a system monitoring tool that logs detailed activity like:

- process creation
- network connections
- DLL loading

It logs these into Windows Event Logs.

Example events:

- Event ID 1 → Process creation
- Event ID 3 → Network connection
- Event ID 7 → DLL load events fileciteturn1file0

## Lab Goal

Detect a **DLL hijacking attack**.

DLL hijacking happens when an application loads a malicious DLL instead of the legitimate one.

## Attack Setup

The lab used:

```
calc.exe
reflective_dll.x64.dll
```

Steps:

1. Rename DLL to `WININET.dll`
2. Place it in writable directory
3. Run calc.exe

Instead of opening Calculator normally, a message box appeared.

This shows the DLL hijack worked.

## Detection Method

We filtered:

```
Sysmon Event ID 7
```

Then searched for:

```
calc.exe
WININET.dll
```

## Indicators of Compromise

IOC examples:

- calc.exe running outside System32
- WININET.dll loaded from wrong directory
- DLL unsigned

These indicate malicious activity.

## What I Learned

DLL hijacking detection depends heavily on:

- file locations
- digital signatures
- process behavior
