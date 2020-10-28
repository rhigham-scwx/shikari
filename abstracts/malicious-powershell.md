---
uuid: c2de5be3-db84-4c43-a835-3b6cc973cb3a
created by: scwx
created date: 09/03/2020
last ran: xx/xx/20xx
classification: execution
priority: 1-5
---

## Hypothesis
Adversaries are using PowerShell to perform malicious actions such as discovery of information and execution of code.

## Priority Explanation
PowerShell is a common methos of living off the land and avoiding detection by many adversaries.

## MITRE Reference(s)
Reference (links) to attack techniques from MITRE ATT&CK.
- https://attack.mitre.org/techniques/T1546/013/
- https://attack.mitre.org/techniques/T1059/001/

## Threat Intel
Any actors that use these techniques?
Is there an active campaign in which these techniques are used?

## Analytics

### Analytic 1 - Remote PowerShell
pseudocode
```process = search Process:Create
wsmprovhost = filter process where (exe == "wsmprovhost.exe" and parent_exe == "svchost.exe")
```

### Analytic 2 - Suspicious PowerShell Process, Spawned from Explorer, with Network Connections
```
event_simpleName="DnsRequest"
 |rename ContextProcessId as TargetProcessId
 |join TargetProcessId 
  [ search event_simpleName="ProcessRollup2" AND FileName="explorer.exe" 
  |dedup CommandLine
  |rename TargetProcessId_decimal as ParentProcessId_decimal 
  |join ParentProcessId_decimal 
  [ search event_simpleName="ProcessRollup2" FileName="powershell.exe" 
  |dedup CommandLine]] 
 |table ComputerName timestamp ImageFileName DomainName CommandLine
```

### Analytic 3 - Powershell Downloading Files

```
event_simpleName="ProcessRollup2" FileName=powershell.exe (CommandLine=*Invoke-WebRequest* OR CommandLine=*Net.WebClient* OR CommandLine=*Start-BitsTransfer*) 
 |regex CommandLine!="((?i)169\.254\.169\.254)"
 |stats count values(ComputerName) values(UserName) values(CommandLine) by FileName
 ```

### Analytic 4 - Obfuscated or Encoded PowerShell

Query 1
```event_simpleName="ProcessRollup2" FileName=powershell.exe (CommandLine=*-enc* OR CommandLine=*encoded*) UserName!=SPAMMYUSER earliest=-24h@h
 |regex CommandLine!="(?i)Office.ValidateResult.scratch|SPAMMMY_POWERSHEL_ENC*" 
 |rex field=CommandLine "(?<CommandLineTrim>[^\\\\]+)$" 
 |stats values(UserName) values(CommandLine) values(ComputerName) count by CommandLineTrim
 |sort -count
```  

Query 2
```
event_simpleName="ProcessRollup2" CommandLine="*powershell*" 
 | regex CommandLine!="(?i)\b_SPAMMYSTTRING2>*|\b_SPAMMYSTTRINGHERE.*" 
 | regex CommandLine="(([A-Z|a-z|0-9]{200}))" 
 |fields CommandLine ComputerName
```
### Analytic 5 - Unusual commmand line arguments
```
event_simpleName=ProcessRollup2 OR event_simpleName=SyntheticProcessRollup2 (FileName=cmd.exe OR FileName:powershell.exe) AND (CommandLine="*Invoke-Expression*" AND CommandLine="*$env:*") earliest=-24h@h
```

## Reference Information:
- https://www.fireeye.com/blog/threat-research/2016/02/greater_visibilityt.html
- https://kurtroggen.wordpress.com/2017/05/17/powershell-security-powershell-downgrade-attacks/
- https://github.com/gchq/CyberChef
- https://threat.tevora.com/5-minute-forensics-decoding-powershell-payloads/
- https://conf.splunk.com/files/2016/slides/hunting-the-known-unknowns-the-powershell-edition.pdf
- https://www.sans.org/blog/powershell-byte-array-and-hex-functions/
- https://www.crowdstrike.com/blog/tech-center/powershell-hunting/

## Hunters Notes:
* As you iterate through this hunt, add any notes that might be helpful for the next time it is ran. 
* Every time a hunt is conducted, a new report should be created. 
* Include a link to the report of your findings in this section.
* Need to add powershell downgrade
