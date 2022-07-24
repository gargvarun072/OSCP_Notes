### Windows Basic Commands

1. Current Directory:- `cd`
2. Show all files in current directory:- `dir`
3. Show complete folder structure:- `Tree`
4. Go back one directory:- `cd ..`
5. Show specific directory files and folders:- `dir <location>`
6. Read the file:- `more user.txt`
7. Search the file - `dir proof.txt /s`
8. Check file permission - `./accesschk.exe /accepteula -wvu "<path of file>"`
9. Copy file - `copy file1 file2`  `/Y -> To overwrite the file`
10. Disable the firewall - `netsh firewall set opmode disable`

### List installed programs
```bash
Get-ChildItem 'C:\Program Files', 'C:\Program Files (x86)' | ft Parent,Name,LastWriteTime
Get-ChildItem -path Registry::HKEY_LOCAL_MACHINE\SOFTWARE | ft Name
```

### List services
```bash
net start
wmic service list brief
tasklist /SVC
```

### What processes are running?
```bash
tasklist /v
net start
sc query
Get-Service
Get-WmiObject -Query "Select * from Win32_Process" | where {$_.Name -notlike "svchost*"} | Select Name, Handle, @{Label="Owner";Expression={$_.GetOwner().User}} | ft -AutoSize
```

### Which processes are running as “system”
```bash
tasklist /v /fi "username eq system"
```

### Do you have powershell magic?
```bash
REG QUERY "HKLM\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine" /v PowerShellVersion
```

```bash
net user /add admin password 
net localgroup administrators admin /add
```