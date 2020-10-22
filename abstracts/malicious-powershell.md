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

### Analytic 1 - non-interactive powershell
* PowerShell being launched by a process other than explorer.exe

### Analytic 2 - unique parent-child relationships
* PowerShell being launched by an uncommon parent / grand-parent
* PowerShell launching uncommon child processes

## Reference Information:
- https://www.fireeye.com/blog/threat-research/2016/02/greater_visibilityt.html
- https://kurtroggen.wordpress.com/2017/05/17/powershell-security-powershell-downgrade-attacks/
- https://github.com/gchq/CyberChef
- https://threat.tevora.com/5-minute-forensics-decoding-powershell-payloads/
- https://conf.splunk.com/files/2016/slides/hunting-the-known-unknowns-the-powershell-edition.pdf
- https://www.sans.org/blog/powershell-byte-array-and-hex-functions/

## Hunters Notes:
* As you iterate through this hunt, add any notes that might be helpful for the next time it is ran. 
* Every time a hunt is conducted, a new report should be created. 
* Include a link to the report of your findings in this section.
