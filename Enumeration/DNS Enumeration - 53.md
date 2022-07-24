## DNS Enumeration 

To identify the dns server in subnet
```bash
nmap -p53 -sT -sV -sC -Pn 10.11.1.1/24 --open
```

To identify the subdomain - 
```bash 
dig axfr @10.10.10.13 cronos.htb
```

Forward Lookup
```bash
host www.megacorpone.com
```

Forward Lookup Brute Force
```bash
kali@kali:~$ for ip in $(cat list.txt); do host $ip.megacorpone.com; done 
www.megacorpone.com has address 38.100.193.76 
Host ftp.megacorpone.com not found: 3(NXDOMAIN) 
mail.megacorpone.com has address 38.100.193.84 
Host owa.megacorpone.com not found: 3(NXDOMAIN) 
Host proxy.megacorpone.com not found: 3(NXDOMAIN) 
router.megacorpone.com has address 38.100.193.71
```

Reverse Lookup Brute Force
```bash
for ip in $(seq 50 100); do host 38.100.193.$ip; done | grep -v "not found" 
69.193.100.38.in-addr.arpa domain name pointer beta.megacorpone.com. 
70.193.100.38.in-addr.arpa domain name pointer ns1.megacorpone.com. 
72.193.100.38.in-addr.arpa domain name pointer admin.megacorpone.com. 
73.193.100.38.in-addr.arpa domain name pointer mail2.megacorpone.com. 
76.193.100.38.in-addr.arpa domain name pointer www.megacorpone.com. 
77.193.100.38.in-addr.arpa domain name pointer vpn.megacorpone.com.
```

