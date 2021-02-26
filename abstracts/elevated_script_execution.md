---
title: Elevated Script Execution
uuid: 2e465a30-2fa2-4417-88bf-9773eb688d54
description: This playbook is designed to find Powershell, Command Prompt, or other scripting host processes that were executed as SYSTEM
attack_techniques:
- T1044 (File System Permissions Weakness)
- T1170 (Mshta)
- T1086 (Powershell)
- T1064 (Scripting)
- T1053 (Scheduled Tasks)
- T1035 (Service Execution)
data_sources:
- process monitoring
- file monitoring
- services
- process command-line parameters
platforms:
- windows
---

# Elevated Script Execution

## Objective

Identify malicious or potentially exploitable instances of script processes (such as Powershell, Command Prompt, mshta, wscript, and cscript) that are executed in context of the `SYSTEM` account.


## Background

The `SYSTEM` account is the highest privileged account on a Windows system. The `SYSTEM` account provides essential operating system functionality (such as Service/task scheduling, and user authentication) or to perform activities prior to user logon. Since the `SYSTEM` context has the highest privilege level in the operating system, processes executed as the `SYSTEM` user may access any local disk or memory resources -- bypassing access controls that affect other user accounts. As such, adversaries frequently seek to elevate privileges to `SYSTEM` during the course of compromising the host. While executing as `SYSTEM` is quite common during normal system operation, the vast majority of `SYSTEM`-level processes are created during system start-up (ie, `ntoskrnl.exe`, `wininit.exe`, `lsass.exe`) or executed as children of a relatively small list of system binaries, such as `services.exe` and `svchost.exe`.

Scripting host processes -- such a powershell, command prompt, cscript, and wscript -- are commonly used by adversaries for post-exploitation activities due to their versatility and stealthiness. Script host processes may evaluate and execute instructions that are read from the commandline or from script files (`.ps1`, `.bat`, `.js`, etc.) on disk. Many applications use these scripting host processes for valid purposes and legitimate instances of `SYSTEM`-level script host processes are typically descendants of `svchost.exe`.

> **Exercise note:** In any environment, there are potentially millions of processes executed as `SYSTEM` in as little as a 30 day window. Restricting our search to instances of `powershell.exe` executing as `SYSTEM`, but where the parent process is not `svchost.exe` reduces the dataset down to a more consumable result set. Similar orders-of-magnitude reduction in data volume can be found with other scripting host processes. 

## Data Collection

Using your SIEM or EDR search interface, set search the last 30 days using the following search criteria.
 
	process_name:powershell.exe AND username:SYSTEM AND -parent_name:svchost.exe
	
Repeat this search for other scripting host processes. Don't forget that powershell can also be executed under the alias of `pwsh.exe`!

> **Exercise note**: Be sure to use whatever groupby, count, and/or visualization tools at your disposal to look at the data in other ways.


## Analysis

Review the parent processes for these elevated powershell processes. Work from the bottom of the list (ie, the rarest parent processes by frequency) towards the top (the most common), filtering and reviewing results for rare or unusual parent processes.

Here are a few things to consider when investigating these anomalous processes:

* Be sure to expand the ancestors in the process hierarchy to determine if the elevated script process is a descendant of a Windows service (but not the direct child of `svchost.exe`)
* Look for unsigned or non-Microsoft binaries as the parent process
* Look for parent or sibling processes that suggest the activity was performed by an actual user (ie, as a descendant of Explorer)
* Look for commandlines that contain specific script files on disk to execute. If possible, confirm whether or not these script files are located in directories that normal users could modify or in temporary directories
* You might notice that legitimate software is responsible for these processes. Insofar as possible, modify the original search to exclude these known-good applications
* You might notice that particular systems generate a disproportionate number of these elevated processes. Consider modifying the original search to exclude specific hosts, then re-evaluate the parent process facet histogram to see if the distribution of values has changed substantially
* If the volume of data is unmanageable, you should consider small variations on the search to focus on processes that generate specific events

Please document your findings.


## Findings

> Did you identify any legitimate applications that were executing script host processes as `SYSTEM`? What is the purpose of these applications? What would be the most effective way to whitelist these for the future?



> Did you find any elevated processes that were executing script files located inside (potentially) user-writable directories? Is it possible to write a detector to identify potential privilege escalation attempts that modify/overwrite the script files?



> Did you find any unsigned or rare binaries that were the parents of an elevated scripting host process? Can these be associated with a legitimate application?



> Did you find any malicious instances of elevated script host process execution? If so, be sure to document the relevant scope (hosts, users, timeframe) and escalate according to standard operating procedures.



> Are there any missing data sources that would substantially improve our ability to identify elevated script host processes?



## Recommendations

* Ensure that legitimate applications executing scripts from the file system are reading from directories with access controls that limit write-permissions to specific accounts.
* Remove any unapproved applications executing elevated script host processes



## Areas for Future Research

* Add scripting host process-specific analysis guidance (for example, provide some background on when to expect legitimate `SYSTEM`-level execution of `wscript.exe`)


## References

|Title|URL|
|-----|---|
|File System Permissions Weakness|https://attack.mitre.org/techniques/T1044/|
|PowerShell|https://attack.mitre.org/techniques/T1086/|
