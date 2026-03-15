
# Skills Assessment Labs

## DLL Hijack Investigation

Logs location:

```
C:\Logs\DLLHijack
```

We filtered:

```
Event ID 7
```

The suspicious file was:

```
DismCore.dll
```

The reason it was suspicious:

```
Signed: false
```

Meaning it was not digitally signed.

## Unmanaged PowerShell Execution

Logs location:

```
C:\Logs\PowershellExec
```

We searched for:

```
clr.dll
```

inside processes that normally should not load it.

This indicates injected .NET code.

## Process Injection

We filtered:

```
Event ID 8
```

And searched for:

```
CreateRemoteThread
```

This is commonly used for process injection.

## LSASS Dump Detection

Logs location:

```
C:\Logs\Dump
```

We filtered:

```
Event ID 10
```

Then looked for access to:

```
lsass.exe
```

This indicates credential dumping attempts.

## Parent Process Anomaly

Logs location:

```
C:\Logs\StrangePPID
```

We filtered:

```
Event ID 1
```

The suspicious process was:

```
WerFault.exe
```

because it launched:

```
cmd.exe
```

which is not normal behavior.

## What I Learned

During this section I practiced:

- analyzing EVTX logs
- using PowerShell for investigation
- detecting credential dumping
- identifying process injection
- spotting abnormal parent-child processes
