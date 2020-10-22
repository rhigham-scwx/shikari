---
uuid: b765456f-a22d-4236-8ea3-81bb3c08ebbe
created by: rhigham
created date: 09/02/2020
last ran: xx/xx/20xx
classification: collection
priority: 3

---

## Hypothesis
Threat Actors have gained access to one of more mailboxes and are using them to conduct transactions or exfiltrate sensitive information.

## Priority Explanation
Business email compromise has become a very common method of attack.

## MITRE Reference(s)
* https://attack.mitre.org/techniques/T1114/003/
* https://attack.mitre.org/techniques/T1114/002/

## Threat Intel
* https://www.sans.org/blog/sans-data-incident-2020-indicators-of-compromise/
* https://www.agari.com/email-security-blog/business-email-compromise-bec-coronavirus-covid-19/

## Analytics

### Analytic 1 - Email Forwarding Rules - New Forwarding Rules
Pseudocode
`Operations, UserID, Paramters{}.Name, Paramters{}.Value Operations = New-InboxRule OR New-TransportRule`

* Disregard known good domains
* Look for rules that forward email to a suspicious/anomalous external email (exfil)
* Look for rules that forward email to an odd folder (staging)
* Look for rules that block or hide emails. e.g. prevent reporting suspicious email, signin from new device alerts, etc
* UpdateInboxRules

### Analytic 2 - Email Forwarding Rules - Modify Existing Forwarding Rules
Pseudocode
`Operations, UserID, Paramters{}.Name, Paramters{}.Value Operations = New-InboxRule OR New-TransportRule`

* DeliverToMailboxAndForward
* ForwardingSMTPAddress
* ForwardingAddress

### Analytic 2 - Lateral Movement
Pseudocode
``` 
CreationDate, Operations, UserIds, ClientProcessName, SendOnBehalfOfUserSmtp, EmailSubject
  Set-MailboxFolderPermission
  Add-MailboxPermission
  Add-RecipientPermission
  SendOnBehalf
```
### Analytic 3 - Suspicious Login Activity

```
MailboxLogin;
UserLoggedIn;
UserLoginFailed;
PasswordLogonInitialAuthUsingPassword;
ForeignRealmIndexLogonInitialAuthUsingADFSFederatedToken;
PasswordLogonInitialAuthUsingADFSFederatedToken;
ForeignRealmIndexLogonCookieCopyUsingDAToken;
PasswordLogonCookieCopyUsingDAToken.
```

## Future Research
* Non-owner mailbox login activity
* Use Get-TransportRule
* Look for `hidden` inbox rules using MFCMAPI
* Active Sync Exploitation
* Look for emails being sent during off hours
* Look for the odd amounts of emails being sent relative to being recieved (PCR ratio)
* UpdateInboxRules
* MailboxLogin

## Reference Information:
- https://docs.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules#:~:text=The%20main%20difference%20is%20mail,many%20types%20of%20messaging%20policies.
- https://github.com/zolderio/microsoft/tree/master/Office365/ExchangeOnline/rules/mailRules
- https://mgreen27.github.io/posts/2019/06/09/O365HiddenRules.html
- https://docs.microsoft.com/en-us/exchange/client-developer/web-service-reference/createruleoperation
- https://docs.microsoft.com/en-us/exchange/client-developer/web-service-reference/createruleoperation
- https://docs.microsoft.com/en-us/exchange/client-developer/web-service-reference/setruleoperation
- https://docs.microsoft.com/en-us/exchange/client-developer/web-service-reference/deleteruleoperation
- https://www.splunk.com/en_us/blog/security/the-future-is-cloudy-with-a-chance-of-microsoft-office-365.html
- https://www.linkedin.com/pulse/responding-business-email-compromise-part-i-korstiaan-stam/

## Hunters Notes:
* As you iterate through this hunt, add any notes that might be helpful for the next time it is ran. 
* Every time a hunt is conducted, a new report should be created. 
* Include a link to the report of your findings in this section.
