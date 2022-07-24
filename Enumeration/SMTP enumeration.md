### Enumeration
```bash
nmap --script=smtp-commands,smtp-enum-users,smtp-vuln-cve2010-4344,smtp-vuln-cve2011-1720,smtp-vuln-cve2011-1764 -p 25 $ip
```

### Manual Enumeration - SMTP
```bash
#connect to smtp
telnet <ip> 25

#Command to check if a user exists
VRFY root 

# Command to ask the server if a user belongs to a mailing list
EXPN root
```

### Manual Enumeration - POP3
```bash
#connect to pop3
telnet <ip> 110

#login into the account
USER root 
PASS root

#Checking emails 
list

#Show emails
RETR <email no.>
```

