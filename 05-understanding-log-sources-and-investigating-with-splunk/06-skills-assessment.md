
# Skills Assessment

Final section of the module.

Goal:

Identify the full attack chain and find the malicious processes.

## Question 1

Find the process that created remote threads in rundll32.exe.

Query used:

index="main" sourcetype="WinEventLog:Sysmon" EventCode=8 TargetImage=*rundll32.exe
| stats count by SourceImage, TargetImage

Answer:

randomfile.exe

## Question 2

Find the process that started the infection.

Answer:

rundll32.exe

## My Thought Process

1. Look for suspicious process injection
2. Identify parent process
3. trace execution chain

The injection event pointed directly to **randomfile.exe**.

Then analyzing the execution chain showed **rundll32.exe** was used as the loader.

## What I Learned

Attack chain usually looks like:

Initial execution → loader → payload → credential dumping → lateral movement.

Understanding that chain makes investigations much easier.
