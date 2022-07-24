https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md
https://tryhackme.com/room/windows10privesc

## Windows Priviledge Escalation

### All kernel Exploits
```
https://github.com/SecWiki/windows-kernel-exploits
```

### Command History File 
```
C:\Users\sql_svc\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```

### Powershell with Sherlock(Windows patch validator)
```
powershell -exec bypass -Command "& {Import-Module .\Sherlock.ps1; Find-AllVulns}"
```

### Windows XP SPI (Service PACK 1)
```url
https://sohvaxus.github.io/content/winxp-sp1-privesc.html
```

![[Pasted image 20210813014226.png]]