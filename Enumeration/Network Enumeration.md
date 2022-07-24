## Network Enumeration

Check common ports and services
```bash
nmap -sT -sV -sC -Pn -oA enum 10.10.10.216
```


Identify the open ports without services 
```bash
nmap -p- --min-rate=1000 -T4 10.10.10.27 -Pn | grep ^[0-9] | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//
```

Add the vhost in /etc/hosts
```bash
echo "192.241.xx.xx  venus.example.com venus" >> /etc/hosts
```