https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md

### Weak File Permissions - Readable /etc/shadow

### Sudo - Shell Escape Sequences
```bash
sudo -l
```
Visit GTFOBins ([https://gtfobins.github.io](https://gtfobins.github.io/)) and search for some of the program names. If the program is listed with "sudo" as a function, you can use it to elevate privileges, usually via an escape sequence.
***

### Sudo - Environment Variables
`sudo -l`

LD_PRELOAD and LD_LIBRARY_PATH are both inherited from the user's environment. LD_PRELOAD loads a shared object before any others when a program is run. LD_LIBRARY_PATH provides a list of directories where shared libraries are searched for first.
https://www.hackingarticles.in/linux-privilege-escalation-using-ld_preload/
***

### SUID / SGID Executables
when special permission is given to each user it becomes **SUID, SGID, and sticky bits**. When extra bit **“4”** is set to user(Owner) it becomes **SUID** (Set user ID) and when bit **“2”** is set to group it becomes **SGID** (Set Group ID) and  if other users are allowed to create or delete any file inside a directory then **sticky bits** **“1”** is set to that directory.
`chmod u+s {file}`

```bash
find / -perm -u=s -type f 2>/dev/null
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
```
(https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/)

Check for :-
- Known exploit
- Shared Object Injection
***

### NFS 
Files created via NFS inherit the **remote** user's ID. If the user is root, and root squashing is enabled, the ID will instead be set to the "nobody" user.
Check the NFS share configuration on the Debian VM:

`cat /etc/exports`
https://www.hackingarticles.in/linux-privilege-escalation-using-misconfigured-nfs/
***

### Kernel Exploit
Validate the kernel version - `uname -r`

![[Pasted image 20210813014148.png]]